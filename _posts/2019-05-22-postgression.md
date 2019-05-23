---
layout: post
title: Postgres-sion
---
One of the goals I had for my Sinatra project was deploying it to Heroku. There's just something about having a live version of an application that can be accessed, tested, and used by others. However, even as I was starting to look into how to accomplish this goal, I ran into an issue: Heroku deployment requires using Postgres for your database. I had set up my database in SQLite3, which had worked great thus far! All of the Sinatra labs I'd been working on used SQLite3 and I knew nothing else. But in order to deploy, I would have to figure out how to make Postgres work for my application.

The first major hurdle was simply the lack of information. Sinatra isn't as widely used as its bigger sibling Rails, and so it was difficult to find specific, detailed information on deploying a Sinatra app to Heroku, much less connecting a Sinatra app to Postgres. Most of the tutorials were for either Rails-specific or dealt with extremely simple Sinatra apps. Because my application already had its database in place and was fairly built-out, I had to do a lot of extrapolation to figure out how to make Postgres work for me.

Additionally, Postgres and SQLite3 are inherently different in that SQLite3 is serverless. This makes it very convenient for learning SQL, since the lack of a server makes things very simple; you can get up and running with SQLite3 without too much trouble. However, with Postgres, I had to download some extra applications to manage things (and figure out how the management apps for both my Windows and Mac OS development environments worked!) and get everything set up before I could start testing my new database to ensure that it functioned. This process almost made me regret undertaking this venture. Almost.

After some trial and error, I was able to get things working. Rake made things very simple in that I was able to use my existing migrations and simply run rake db:migrate; everything showed up in the Postgres database without a hitch. Once I got a working build deployed to Heroku, everything was running smoothly. My database has since been able to persist data from multiple users without any issues.

Although this entire situation was frustrating and took me a couple days to properly sort out, I'm very glad that I decided to take on this extra challenge. I understand the process of setting up a database a little bit better now and I'm excited to have some familiarity with another way of handling data.
