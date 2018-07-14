---
layout: post
title:      "Rails and JS Project"
date:       2018-07-14 22:06:33 +0000
permalink:  rails_and_js_project
---


Adding JS to a Rails project gave me a lot of ideas on how to improve my Recipe Manager app, but I did end up going down a few roads that I then abandoned in order to meet the requirements. At least it was some good practice!

* On the Recipe Show view, users can click through to previous and next recipes without reloading the page
* On the Category Index page, you can click a category and then all it's recipes will appear on the page (a category has_many recipes)
* On the Category Index page, you can add a new category and see it without a page reload


**Prototype Method**

I liked this overview of prototypes on Hackernoon
https://hackernoon.com/a-definitive-guide-to-javascript-prototypes-2c263788021e

> ...a JavaScript prototype refers to
> 
> 1. An object,
> 2. albeit with limited features, where
> 3. the final version of an object will share some characteristics of its prototype.
> 
> Point 1 highlights a distinct point about prototypal inheritance as compared to traditional class-based inheritance. The prototype is an object that can be used on its own. However, a traditional class is not an object and thus cannot be used like an object.
> 
> Note that although later versions of JavaScript have a class keyword, it still uses prototypal inheritance under the hood.
> 
> Point 2 is valid because a prototype typically has fewer properties compared to an object that uses it as its prototype. For example, both alex and Person.prototype are able to greet (although alex does it with the help of Person.prototype), but alex has an additional name.
> 
> As for point 3, a JavaScript object does share some characteristics of its prototype(s) because of prototypal inheritance.
> 
> Since objects are linked in the prototype chain, if you change a prototype, the behavior of existing and future objects linked to that prototype could be affected.
> 

I wish I had the opportunity to build more robust prototype methods, but for the purpose of the project my method was a  formatRecipe method that created the recipe HTML to append to my recipes-container div in my categories index page. I also have a prototype to add a newly-created Category to the category index page. 


**Wishlist**
* Change the links like "Most Recipes", "Most Popular", and "Order by Name" on the Recipe and Ingredient show pages so there is no page redirect
* Fix formatting across all pages so it's more appealing and uniform
* Fix formatting on the Category index page so the category recipe container is not on the bottom of the page but more of a sidebar div
* Allow editing of a recipe and the recipe_ingredients on the same page and not two separate pages


