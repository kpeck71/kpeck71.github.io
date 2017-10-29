---
layout: post
title:      "TTT with AI + Ruby Book Club"
date:       2017-10-29 21:19:46 +0000
permalink:  ttt_with_ai_ruby_book_club
---


I just finished the Tic Tac Toe with AI project. I have some improvements and computer logic that I would like to play around with more in the future, but right now I've been working on it for so long that I just need a break!

But to make myself accountable, here is what I would like to improve upon / better understand:

1. Improve CLI and working with inputs. The 0, 1 and 2 player works, but it could be clearer.
2. Improve/finish war games version.
3. Improve computer logic and make it closer to unbeatable.
4. Have a better understanding of the Learn solution for won?:

 def won?
    WIN_COMBINATIONS.detect do |combo|
      @board.cells[combo[0]] == @board.cells[combo[1]] &&
      @board.cells[combo[1]] == @board.cells[combo[2]] &&
      @board.taken?(combo[0]+1)
    end
  end


I've been listening to the [CodeNewbie podcast](https://www.codenewbie.org/podcast) and I really love it - the host Saron Yitbarek is so fantastic, the guests and topics are really great, and it also introduced me to the [Ruby Book Club](http://rubybookclub.com/) podcast that Saron co-hosts with Nadia Odunayo. Right now I'm listening to the series about *Confident Ruby* by Avdi Grimm, which is now on my book list. I often don't fully understand the concepts that are being discussed because they are slightly advanced (same with reading the *Well-Grounded Rubyist* but Nadia and Saron just discussed one idea from Avdi's book that seems really helpful - to paraphrase... 

If you start thinking in the frame of mind of all of the pieces you already have (classes, methods, models etc), then you might be missing better solutions. And you might be trying to force things into something that doesnt' fit. Instead, look at what messages need to be received. Based on these messages, now I know that these are the 'people' that need to receive them. From there, you'll see the people/roles that need to exist, and then you can figure out what are the corresponding classes/objects I need to set up. I know I often jump right in to writing code without reading and re-reading the lab and so I'm sure I will need to remind myself of this in the future!
