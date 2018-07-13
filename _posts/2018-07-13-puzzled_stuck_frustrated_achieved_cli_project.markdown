---
layout: post
title:      "Puzzled, Stuck, Frustrated; Achieved: CLI Project"
date:       2018-07-13 00:28:53 -0400
permalink:  puzzled_stuck_frustrated_achieved_cli_project
---


These three headline words have been making my days oh too overwhelming. As though I had thrown myself into a self-created chaos of my own volition, I pushed on, kept rowing the boat, was thrown off-course multiple times... until I reached my destination. Today.

My first command line application is complete!

And all this learning pain, confusion, self-doubt is no longer on my horizon - at least for the time being. I'm sure I will encounter them again and again; and next time, I will have more baggage on my shoulders, I will be more equipped to deal with whatever problems will want to face me.

Bring it on.

But for now, I want to share a little bit of the specific problems I solved, each one by one. The goal was to tackle each one individually but of course, as I've already alluded, my journey was *not* a peaceful one.

*Whew.*

It's all good, right? Let us take a deep breath and remember Aristotle's words:

> “Learning is not child's play; we cannot learn without pain.”

For me, the most frightening step wasn't the one when I had a blank canvas in my text editor - although it did take me some time to figure out how to set up my working environment so that I could have little distraction and instead focus on the core logic of the CLI app.

Should I use Atom? If so, which terminal should I depend on? How do I install it? How do I connect git to the editor? How do I create an SSH key? And then, when I finally got set up to work with the Learn IDE, more questions followed: okay, so what is the best way to create a gem? I failed a couple of times running `bundle gem [gem-name]` and now am feeling like such a noob admitting this. Really, all you need is one line of code in your terminal, and you've got all your basic structure of  the gem laid out in front of you! Simple, no?

The great stuff about coding is that you *don't have to do* all the tedious stuff yourself; you can borrow it and successfully launch your ideas while they're fresh.

Looking back at my younger self, I would advise myself not to be over-ambitious and instead deal with the main functionality of the program or app. Further add-ons and fancy stuff can be added later on. It's best to have a simply working code at first; and when you feel like you're playing dolls in the kindergarten, then it's time to expand your work.

So I had some setbacks trying to scrape two lists, sure. That was not necessary. I noticed how repetitive the code was becoming: first, I had two separate classes called `editors_books` and `readers_books`, then I obviously had to add the exact same attributes for both classes, and have almost identical methods performing the same logic.

Yes, I wanted to do more. But I had a hunch that this wasn't the way to go. And, while pairing up with a technical coach, we'd decided to abandon this double-list idea, and scrape only one page of the books and then provide the summaries of the desired books.

This only means that I wasted time trying to jump over a higher hill than I was supposed to. I hurt my knees - and I am glad for this project to have revealed my weaknesses with such simple fixes. Yes, I may have typed `editors` and `readers` a hundred times in my terminal trying to access one or the other not-functioning list; hence the strength of the lesson. A simple `yes` or `y` would have sufficed, I know now.

Another big stop was not paying *full attention to details* - like LINKS! You'd think that that's an important step while scraping websites, but it is so seductive to hide under the developer's tools and grab the keywords under certain `div`s, `span`s and classes.

While scraping summaries, I had a frustrating moment getting this `404 OpenURI::HTTPError` in my terminal. I was like, what do you want from me???! Is the server protecting itself from random scrapes, is there a bug hiding at the back-end? I went ahead and tried changing the `User-Agent` to `Aliens from Space`, as someone on Stock Overflow recommended. No luck. Then, I learned about `Net::HTTP` library which uses persistent connections and can submit different requests.

It still did not work. No matter how much I fancied the library.

Well, the problem was rooted within the links, something I didn't check. See, instead of calling `Nokogiri::HTML(open("https://www.bookdepository.com/bestbooksever#{url}"))`, I needed to omit the `bestbooksever` part because those books exist in the base url, `https://www.bookdepository.com` plus the specific name for each book.

And now, back to the joy of having coded my first app! Yay!!

I'd like to thank to Mohammed Chisti, David Kennell, and Kenlyn Terai who helped me get unstuck and keep a positive attitude, and motivated me to continue. You're brilliant. <3
