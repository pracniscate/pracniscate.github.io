---
layout: post
title:      "Sinatra MVC project"
date:       2018-09-06 00:35:37 +0000
permalink:  sinatra_mvc_project
---


Here I am again, working from the ground up to build an app that would magically (or should I say, programmatically) transform into something I see on a daily basis: a website. Now that I understand the basic routes, get and post requests, the separation of concerns and the need for a database that takes care of itself by not saving empty values or complete gibberish, I appreciate every website a lot more. Years ago I would not have figured out how a line of some random code transforms into a color or an animation, and now I am building it all on my own.

Needless to say, I've had a lot of fun doing this project. The idea to collect extinct animals came as a random search on Wikipedia, my most friendly web companion in knowledge, and a day after I decided on that instead of to-do lists and favorite book editions, I should go for something that we had on this Earth, but now these creatures exist only as a record.

As it is well known, the first step is almost always the hardest. Luckily though, a fellow cohort student suggested I use the Corneal gem to generate the basic app structure, the bare bones. It was as simple as `corneal new extinct-animals-sinatra-app` and before my eyes I had a beautiful layout with crucial files such as `config.ru` which requires my environment file and mounts the controllers, `Gemfile` which allows me to use other people's code in the form of little Ruby gems, `db` folder that would later contain my migration files as well as the schema of my database and the `development.sqlite` file which updated every time I inserted a new animal or a user while interacting with my website.

So first off, I created my migration files, and decided what attributes I want my `users` and `animals` to have. In the database, these attributes all have their own column. Then, I created my models for these respective classes, and defined the relationship between them: a user `has_many` animals, and an animal `belongs_to` the user. Like so:

```
class User < ActiveRecord::Base
    has_many :animals
end 

class Animal < ActiveRecord::Base
    belongs_to :user
end

```

Might I mention here how I love the readability of Ruby! While my tables took the plural form of the nouns, my models settled for the singular form, just so that the keywords of their relationship wouldn't break the English language.

Now, for my users to be able to have a pleasant experience and for them to be remembered once they logged into my website (or clicked on any link and didn't lose the connection to the database), I had to enable sessions. This would send users a cookie, and by this means my app and the user's browser could "remember" each other. To improve the security of my sessions, I set a random 64-byte value of numbers and letters, as it was recommended in Sinatra README. I respect mine and by extension, my potential users' privacy.


I then added an authentication method by writing `has_secure_password` in my user model. This method is accessible via the `bcrypt` gem, and the `password_digest` attribute which I had given my column in my database user table. The validations automatically added with this `authenticate` method were: 1) when creating a new account, a password must be created as well, 2) password length should be less than or equal to 72 bytes, 3) password confirmation (if I used the `password_confirmation` attribute).

With the help of control flow (if/else statements), I am able to show the `log out` option if user is logged in, and the two `log in` and `sign up` buttons if the user is not logged in. Pretty simple and straightforward, but I have respect for these little lines of logic.

Further, I started to create my forms and routes. This is where I was having the most fun. While at first the routes seemed a little confusing to me, with the help of the previous labs like FTwitter and NYC-Sinatra, and finally, my own little app, I now have a very good understanding of how the controller sets up a route, the view renders the form, and upon successful submission, the controller shows or redirects the user to another page, and, if there was an error, how the controller can show a flash error message, and view renders that same page again. I've learned through my own little bit of research that single error pages are ought to be avoided because it requires unnecessary user action, i.e going back one page.

The styling part of this project was very refreshing, although not new for me. I've tinkered with Cascading Style Sheets before, just for fun - especially when I didn't know what I was doing. I am amazed and very pleased with myself by how much I have already learned, and overall, I welcomed CSS as an old friend.

My biggest struggle in Sinatra was realizing that the order of controller files is important. At first, I had `animals_controller`, `application_controller`, and `users_controller`. I was mounting these controllers like so:

```
use UsersController
use AnimalsController
run ApplicationController
```

...and was getting an error for undefined `AnimalsController`. So, to fix this, I required the controller files with `require_relative '../app/controllers/[controller_name]'`, which fixed the problem - only temporarily. I had to again dive deep into my search engine, and finally figure out that the order matters. My solution was to rename my `animals_controller` to `ex_animal_controller`, to give preference to my general `ApplicationController`, which was the one I chose to run.

Then, another issue I had was not being able to sign up or log in. I was going back and forth from one form to another. I attended a couple study groups, and it turned out that I was missing `name="password"` for both my forms! Which, subsequently, meant that I was getting the value of `nil` because I was not calling my input by what it was meant to be - its name - password!

Overall, I could say that this project went a lot smoother than my first one; I knew what to expect, and I knew how to debug, and ask for help when I was beginning to *not* see my code. Coding is very much different from reading a book. There are chapters within a sentence, or even a part of one line that you could go deeper one layer at a time. Also: missed characters **do** count!

`=` is used to assign a new value:

```
extinct = dinosaurs
```

`==` checks a condition, which in my case was:

```
@animal.user == current_user
```

This part of code was checking if the currently logged in user had created that particular animal. If not, that user could not edit or delete any information pertaining to that animal.

