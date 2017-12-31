---
layout: post
title:      "Sinatra Portfolio Project"
date:       2017-12-31 17:21:44 +0000
permalink:  sinatra_portfolio_project
---

My Sinatra Portfolio Project is a recipe collection that allows users to create, edit, and view recipes. Only a user that created a recipe can then edit the recipe, and only logged-in users can view the details of other user recipes. There are also optional categories that a recipe can have, and a recipe can have many categories. 

I went back and forth about being able to edit or delete categories. They can be used by multiple users, so I did not want to be able to delete them or edit them.

After the NYC and Fwitter labs, I felt prepared for this project and setting up the routes. I have never used the has_and_belongs_to_many  association before. It seemed like an OK alternative to the has_many :through. This is what was listed in the Rails guide. 

The simplest rule of thumb is that you should set up a has_many :through relationship if you need to work with the relationship model as an independent entity. If you don't need to do anything with the relationship model, it may be simpler to set up a has_and_belongs_to_many relationship (though you'll need to remember to create the joining table in the database).


Other thoughts:

Switching from Learn IDE to a local enviroment
-After losing 5+ hours of work on Fwitter (Ahh!) I switched to a local environment and (coding) life has improved immensely.

Commit more
-I find that I play around with my code so much that I've editing multiple files and only commit when the code I've been working on finally works. I need to commit more.

Layout
-I'd like to learn more about setting up layouts for my views. I have a pretty basic footer and header, but would like to add more styling. 








