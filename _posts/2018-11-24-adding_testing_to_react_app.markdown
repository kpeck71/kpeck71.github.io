---
layout: post
title:      "Adding Testing to React App"
date:       2018-11-24 16:15:13 +0000
permalink:  adding_testing_to_react_app
---

I used create-react-app for my application so Jest is already installed and configured in my app, and now, I'll just need to add Enzyme.

Here are some steps to follow for this:
https://medium.com/@leonardobrunolima/react-tips-testing-react-component-with-jest-enzyme-basics-38a15d5dd72a

**Unit and Integration Tests - and Smoke Tests**
> For unit tests, how one defines a “unit” depends on the language or framework. However, the idea is that you want to test that unit in isolation. So, for example, for an object-oriented language a unit test might revolve around a class. Ideally, those unit tests test only the behavior of that class and nothing else in the system.
> 
> Integration tests, on the other hand, will test two or more parts of a system together.
> 
> Guess how we break down “units” in React apps? Yep – components. So each set of unit tests will be centered around a component in isolation.
> 
> Integration tests, on the other hand, might test multiple components together. Or, in the “most integrated” form, we might write full “end to end” tests. These are tests where we boot up our app in a browser environment (like Selenium) and have automated tests that click around and interact with our full-blown app, much like a user.  
From [A Practical Guide to Testing React Apps](http://acco.io/a-practical-guide-to-testing-react-apps/)
 
I hadn't heard of smoke tests before, but I liked this description:  "Smoke tests only tell us things didn’t blow up."

Testing the app "at rest" and when responding to user interactions. Local state interactions; Parent interactions
 
 
### Sources
https://jestjs.io/docs/en/tutorial-react


