---
layout: post
title:      "React/Redux Portfolio Project"
date:       2018-09-30 21:33:46 +0000
permalink:  react_redux_portfolio_project
---

My React/Redux portfolio project is an application to help you manage your monthly expenses, short- and long-term goals, and monthly budget.

There is also a Goal Ideas section that allows users to filter based on a category (e.g. Charity ,Travel)  [Note: My future to-do list also includes the ability to pick a price range (e.g. $25-50)] to see a series of goal ideas that they may wish to add to their own goals, such as donating to an organization each month, [treating your self ](https://gph.is/2cekLTm)to something fun, or booking a trip somewhere. 

In the beginning of the project I had a budget form that had 10+ fields with categories like "housing" or "car loan", but then I realized I could make smaller budget cards, similar to my goal cards, that could be added and deleted, so if you suddenly had a new expense item for a month or more, you could add it without filing everything under a "miscellaneous" category. Now, you start out by entering your monthly income (which you can later edit if needed), and then separate expenses with their own categories. 

**Current Open Issues:**
I need to reload the page before a new Goal appears in Current Goals after submitting the form. I do not have this problem with Expenses.

**Refactoring/Wishlist**
I have a lot of refactoring to do in this app, plus additional features to add:
- Conditional styling based on if a goal is paid or not paid
- Add a payment as you start to put money towards a goal
- Remove repeated code, like handleChange
- Filter GoalIdeas based on multiple criteria https://react-select.com/
- Testing! https://github.com/mjackson/expect


**Notes:**
Taken from: https://www.fullstackreact.com/30-days-of-react

React is a JS framework, and it is the user interface, or view layer, of the application.

With React, we write to the Virtual DOM, which is a representation of the web browser DOM. 

My Application Structure and React
"For example, take a form.  A form might consist of many interface elements, like input fields, labels, or buttons. Each element inside the form can be written as a React component. We'd then write a higher-leİel component, the form component itself. The form component would specify the structure of the form and include each of these interface elements inside it.

Importantly, each component in a React app abides by strict data management principes. Complex, interactive user interfaces often involve complex data and application state. The surface area of React is limited and aimed at giving us the tools to be able to anticipate how our application will look with a given set of circumstances."


**Final Project Review Requirement Checklist**
This form reviews all requirements in the spec.md form, as well as project standards set out in earlier in the course. ALL REQUIREMENTS must be complete, or the  review will need to be rescheduled. If you do not have one of the requirements below completed during the review, the review will be immediately stopped and you will need to complete it and reschedule your review.

**ES6 Requirements**
One of the requirements of the project is: "The code is written in ES6 as much as possible"
Here are a few examples of ES6 features used in this project:
* Arrow functions
* Spread operator
* const variables
* export import default
* Promises
* https://medium.freecodecamp.org/write-less-do-more-with-javascript-es6-5fd4a8e50ee2
http://es6-features.org/#Constants


create-react-app was used to create your React app *
Yes

There are 2 container components *
/BudgetContainer
/BudgetInput
/GoalContainer
/GoalIdeas

There are 5 stateless components *

There are 3 routes *
/home
/ideas
/status
/completed

**react-router is being used with proper RESTful routing **

**Redux and redux-thunk middleware are being used to modify state change and make use of async actions to send data and receive data from the server **

"A fetch() request returns something called a Promise. A promise object is an object that represents some value that will be available later. We can access the data when the promise "resolves" and becomes available by chaining a then() function onto our fetch() call." [Learn.co](https://learn.co/tracks/full-stack-web-development-v5/redux/redux-and-apis/redux-thunk-readme)
...
"So we need a way to dispatch an action saying we are loading data, then to make a request to the api, and then to wait for the response and then dispatch another action with the response data." -- > Middleware

"We'll tell our store to use the Redux Thunk middleware. This middleware will do a couple of interesting things. First, Redux Thunk allows us to return a function inside of our action creator. Normally, our action creator returns a plain JavaScript object, so returning a function is a pretty big change. Second, that function inside of Redux Thunk receives the store's dispatch function as its argument. With that, we can dispatch multiple actions from inside that returned function."

```
export function createExpense(newExpense) {
  return function(dispatch) {
    return fetch('/api/v1/expenses', {
        method: 'POST',
        headers: {'Accept': 'application/json', 'Content-Type': 'application/json'},
        body: JSON.stringify({
          expense: {
            name: newExpense.name,
            amount: newExpense.amount,
            category: newExpense.category
          }
        })
      }).then(response => response.json())
        .then(newExpense => dispatch({ type: 'ADD_EXPENSE', newExpense }));
    }
  }
	```
"So you can see above that we are returning a function and not an action, and that the power we now get is the ability to dispatch actions from inside of the returned function. So with that power, we first dispatch an action to state that we are about to make a request to our API. Then we make the request. We do not hit our then() function until the response is received, this means that we are not dispatching our action of type 'ADD_CATS' until we receive our data. Thus we are able to send along that data."


**Use of Rails API backend to persist data for the application ***

**Good understanding of the react/redux state flow ***

**Good understanding of state and props in React ***
Preferable to use props whenever we can, but  sometimes we need to hold on to the state of a component. State is intended to be completely internal to the Component and it's children (p47 pdf)

**Knowledge of async JS with Promises ***

https://www.fullstackreact.com/30-days-of-react/day-15/

"As defined by the Mozilla, a Promise object is used for handling asynchronous computations which has some important guarantees that are difficult to handle with the callback method (the more old-school method of handling asynchronous code).

A Promise object is simply a wrapper around a value that may or may not be known when the object is instantiated and provides a method for handling the value after it is known (also known as resolved) or is unavailable for a failure reason (we'll refer to this as rejected).

Using a Promise object gives us the opportunity to associate functionality for an asynchronous operation's eventual success or failure (for whatever reason). It also allows us to treat these complex scenarios by using synchronous-like code."

"The then() function is called with whatever the return value is of the promise itself"



Helpful resources:
https://www.fullstackreact.com/articles/how-to-get-create-react-app-to-work-with-your-rails-api/

https://github.com/uanders/react-redux-cheatsheet/blob/master/article/react-redux-concept-workflow.md

https://www.fullstackreact.com/30-days-of-react/




