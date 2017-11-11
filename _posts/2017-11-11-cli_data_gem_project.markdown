---
layout: post
title:      "CLI Data Gem Project"
date:       2017-11-11 14:53:12 +0000
permalink:  cli_data_gem_project
---


My CLI Data Gem project is an app that lists all of the episodes, and episode details, of the podcast [Code Newbie](https://www.codenewbie.org).

**The False Start(s)**
This project started as a news scraper. I made the mistake of starting to build some of the code out, but I had not tried to scrape the details of the website - neither the article list nor the article details. I ended up spending WAY too much time trying to scrape the page, only to change my website and try to scrape a different news site. That one also gave me a lot of trouble, and I wasted so much time trying to get it right when I should have placed in dummy text and worked on my code instead.

I also ran in to a lot of problems with my git repo and the IDE. I would lose my work when the IDE disconnected, and I had trouble pushing files to my repo. I wish I had practiced more with git during the earlier lessons other than simpy pulling and pushing labs.

**The Process**
I created a program that - ideally - would scrape all the podcasts listed on Code Newbie's website, and then allow the user to learn more about a particular episode. By selecting "more", you then see the full show description and more details about the episode guest.

I started by building my Episode class. I first added too many methods to that file, but a re-watch of some of the video lectures reminded me to split out the responsibility of each class and to simplify my classes, which was very helpful. 

The Scraper class was a little trickier. I knew what I wanted - a scraper that grabbed all the episodes, and one that grabbed a single episode's details - but I ran in to problems scraping the episode detail. There are over 150 episodes of Code Newbie that go back to September 2014, so the styling and class names on the episode detail pages are all different! Blerg!
I would like to go back and add functionality that captures the different style of the episode detail pages so I can make the scraper actually work.

The CLI class took the most trial and error, especially with my if and/or case statements. I originally had a lot of if statements, but that got a little confusing when I went to a deeper level, so to speak, in the options menu. For example, when I was in an episode's "more" space and had a new list of options to work with, I added too many options for whatever type of input a person might enter, and it just didn't work. Some of the problems I had were just due to missing code - like forgetting to add 'gets' when I wanted to grab some input. But I also tried to add too many responses for invalid inputs, and that really messed up the flow of the CLI. I have finally removed them, and I think it works fairly well. But, there is plenty of room for improvement.

I really liked how worlds-best-restaurant scraped data was formatted and how it provided the option to look at restaurant names by a range of 10, so I also added an option that lets the user either pick a range of episodes to look at, or to view a list all 156+ episodes. Adding the range option to my code was a little different from the restaurant example because the episode number does not equal the index (or index-1) number of the episode array, but .reverse was a simple way to solve that.

**The Program I'd Like to Have**
I think it would be fun to also build out some functionality that allowed the user to see a list of topics that are covered in the episodes, and then let them pick a topic and see a list of episodes related to that topic. There is no data on the Code Newbie site with tags or topic classification that I could use, but it would be a fun feature to have. 

I also wanted to add "open to listen" functionality that allowed the user to open the episode's URL and then listen to the episide in their browser. I could not get system(open...) to work. I also tried using the gem Launchy, but that did not work either. I would like to work through those errors in more detail and get it working! 

And I still really want to add some kind of responses for invalid entries! 

**PS**

The worlds-best-restaurants gem was very helpful and a great example of how something like this could be set up. I loved so many things about it.

I also found the Anti-Pattern video lecture from Avi to be really helpful (well, all the video lectures are always super helpful!).


