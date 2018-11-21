---
layout: post
title:      "Adding Tests to Rails Project"
date:       2018-11-17 12:30:38 -0500
permalink:  adding_tests_to_rails_project
---


In this post I'm going to talk about some tests I've added to an existing Ruby on Rails project (knowing that it is a much better idea to build your project with tests rather than adding them after). But hey, I need the practice!

Learning about the TDD (test-driven development) philosophy has been really fascinating. When I was at Flatiron School, I remember thinking that I should add tests to my projects as I worked, but as someone with a full-time job working on the program in the morning, at night, and on weekends, I was worried about taking extra time to work on tests when they were not a requirement in the program. Looking back, I regret not taking that time to start diving into tests in Rails, and later React, but alas! Life goes on, and here I am trying to make up for lost time. 

## Setup
I'm using Rspec and Capybara for this, and I followed [these instructions](https://medium.com/@lukepierotti/setting-up-rspec-and-factory-bot-3bb2153fb909) to set up my app. 

**NOTE**: If you're following other tutorials/blogs, the author may use `gem 'factory_girl_rails` or `gem factory_girl` but you need to use [factory_bot_rails](https://github.com/thoughtbot/factory_bot/blob/v4.9.0/UPGRADE_FROM_FACTORY_GIRL.md) or `gem factory_bot'
You will also need to replace any references to FactoryGirl * like `config.include FactoryGirl::Syntax::Methods` with FactoryBot. 
And lastly, FactoryBot is removing static attributes, so if you are reading an older article/tutorial and see attributes that looks like this...
```
factory :robot do
  name "Ralph"
end
```
...know that these will no longer be supported. Instead, use dynamic attributes (like this:)
```
factory :robot do
  name { "Ralph" }
end
```
You'll get a Deprecation Warning message in your console when you run your tests, but it's good to be aware of it. More info here: [Deprecating static attributes in factory_bot 4.11](https://robots.thoughtbot.com/deprecating-static-attributes-in-factory_bot-4-11)


## Errors
https://stackoverflow.com/questions/36187084/getting-actionviewtemplateerror-invalid-css-after-when-accessing-a-page

   Failure/Error: <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track': 'reload' %>
     
     ActionView::Template::Error:
       Invalid CSS after "...ba, font-weight": expected ";", was ": bold !importa..."

After setting up my factories.rb file and factory_bot.rb file, I also got this error message:

Failure/Error: config.include FactoryBot::Syntax::Methods
NameError: uninitialized constant FactoryBot

I fixed this by adding `require 'factory_bot_rails'` to my factory_bot.rb file

## Feature Tests
**user_creates_new_recipe_spec.rb**
```
  scenario "when a user creates a duplicate recipe" do
    recipe = Recipe.create(name: "My Recipe")
    visit "/recipes/new"
    puts page.body
    fill_in "recipe[name]", with: recipe.name
    click_button "Create Recipe"
    expect(page).to have_content("Name has already been taken")
  end
	```
	
My first test was a features assertion test that mimicked a user going around the app and creating a new recipe. One of the first errors I had to deal with was WHY on earth didn't the test see the nice big "Create Recipe" button, or why it didn't see the "Recipe name" field despite trying to use label text or name or id. Then, after seeing this Stack Overflow suggestion, I added `puts page.body` after my `visit "/recipes/new"` . Looking at the HTML in my console, I saw this message and realized I had to mock a login for this test:
```<div class="alert alert-dismissible alert-info">Only logged-in users can create recipes.</div>```
As noted by this [blog post](https://robots.thoughtbot.com/how-we-test-rails-applications) from thoughtbot, 
`You could use the built-in User.create, but that gets tedious when you have many validations on your model. With User.create you have to specify attributes to fulfill the validations, even if your test has nothing to do with those validations. On top of that, if you ever change your validations later, you have to reflect those changes across every test in your suite. The solution is to use either factories or fixtures to create models.`


## Models

## Articles/Tutorials/Tools

[Testing Rails Applications](https://guides.rubyonrails.org/testing.html) from RailsGuides

Upcase, from thoughtbot, a platform with (now free) tutorials on Ruby/Rails topics. I used the [Test-Driven Rails](https://thoughtbot.com/upcase/test-driven-rails) tutorial. 
I'm noticing that a lot of these tutorials are a few years old, and some things are outdated. For example, the tutorial uses 'before_filter' in the TodosController, which had to updated to 'before_action'. Check out the Discussions on the lessons and you'll often find the updated answer there.  

[Test-Driven Development in Rails](https://medium.com/coding-and-web-development/test-driven-development-in-rails-part-1-3febc43ade24), Medium article with YouTube video tutorials

[Red, Green, Refactor](http://bikeshed.fm/139) episode of The Bike Shed (a great podcast!)

[Characteristics of a Good Test](https://www.codecademy.com/articles/tdd-u2-good-test), Codeacademy article
