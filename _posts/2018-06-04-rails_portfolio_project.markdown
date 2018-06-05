---
layout: post
title:      "Rails Portfolio Project"
date:       2018-06-04 21:31:02 -0400
permalink:  rails_portfolio_project
---


My Rails project is based on a Recipe project I did for Sinatra with some new functionality.  I was a little disappointed in my self for picking something that I already worked on, but then I watched a live Q&A with some bootcamp admissions and career coaches, and one of the guys recommended either working in a New technology (like a new language) but with an old problem, or solving a New problem with your old technology, rather than trying to do too much at once. I liked that.

The Recipe Manager works like so...

View and create Recipes (if logged in). Users can also edit their own recipes, but not the recipes of other users.
View Ingredients and Recipes containing an ingredient from the ingredient show page.
View Categories, sort by most popular (through an ActiveRecord scope method) or alphabeticaly, and view all recipes that fall under a category on the category show page.

Specs:
- [x] Include at least one has_many relationship:
 User has_many Recipes
 
- [x ] Include at least one belongs_to relationship (x belongs_to y e.g. Post belongs_to User)
 Recipe belongs_to User
 
- [x] Include at least one has_many through relationship:

Category
 has_many :category_recipes 
 has_many :recipes, through: :category_recipes

Ingredient
 has_many :recipe_ingredients 
 has_many :recipes, through: :recipe_ingredients
	
User
  belongs_to :user, :counter_cache => true
  has_many :recipe_ingredients
  has_many :ingredients, through: :recipe_ingredients
  has_many :category_recipes
  has_many :categories, through: :category_recipes
	
- [x] The "through" part of the has_many through includes at least one user submittable attribute 
Category attributes for Recipes; ingredients Attributes in recipes model

- [x] Include reasonable validations for simple model objects (list of model objects with validations e.g. User, Recipe, Ingredient, Item)
Category has Title
Recipe has ingredients
User has unique email; User has a name

- [x ] Include a class level ActiveRecord scope method (model object & class method name and URL to see the working feature)
- User.most_recipes URL: /users/most_recipes)
- Category.sort_by_populatiry URL: /categories/sort_by_popularity

I think I forgot to show my form validation errors in my video walkthrough...


**Omnitauth**
I ran in to a lot of trouble with Facebook Omniauth. I turned to Google Omniauth and ran into fewer issues, but I did learn a valuable lesson when working one-on-one with Dakota to solve an error I was seeing with my #google_login method. I had found some documentation from Google that looked like it fit my code, except for a couple of lines that used "Marshal" 
Like:
session[:user] = Marshal.dump user

The documenation was on authenticating users, but it was for Google Cloud. Dakota reminded me to look more closely at the documentation and read it step by step. Docs can be super helpful but they are not always an exact match for your particular case. Look at it closely!  This one step may not look quite like what I am doing, but what, in my code, corresponds to this line of code in the docs? Blindly copying and pasting may work some times by dumb luck, but even if the documenation is not an exact match (and will likely never be), it can still apply to your code and help.

**Broken / Wishlist Features**
If your form has an error (like a blank name or blank instructions) you can't save it because of the validations (good) but the existing data does not stay populated in the form when you have to go back to update the missing information (bad).

If I have a category selected, and then write in the name of the same category, it lists the category twice on the recipe page. BUT, it is the same category both times, it is not duplicating a category. Why is this happening?

I tried to add search functionality and just couldn't get it to work - this is something I'd like to conquer soon! 

I would also like to use JS to add and remove fields by clicking a plus/minus button. This could also be used to enter multiple new categories at a time (I don't need JS to do this, but I'm working through the JS section so it's on my mind!). 


