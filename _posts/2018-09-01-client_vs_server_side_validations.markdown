---
layout: post
title:      "Client vs. Server Side Validations"
date:       2018-09-01 16:10:01 +0000
permalink:  client_vs_server_side_validations
---


It is nearly impossible to imagine an internet with no user input. The magical world of intricate web connections would be immensely limiting with static webpages following one after another... So this is where forms and validations come in. Apart from allowing us to communicate with other internet-friendly users, forms provide us with the ability to enter a website and see its *hidden* content, then make a secure purchase, update our user profile, delete it if the satisfaction was not guaranteed, etc.

*Well, why should I use validations?*

If the answer doesn't already seem straight-forward, validations ensure that the database will have correct and valid data saved in it, while not allowed characters or blank spaces will not get a pass.

*Two types of validations*

While working on my Sinatra app, I've found that there are two types of validations that come into play: client- and server-side. For the **server** side, I am using Ruby's Active Record, which takes in the role of my app's data and logic (also known as **model**) to validate the presence of important user inputs like username and password. On the server side, this user information will be sent to the database and validated with my server-side programming language.

Of course, in the future I hope to become familiar with many other languages for this specific purpose. For example, Python, PHP, Elixir, C++, Rust, Haskell, or any other. While it has been an interesting experience with Ruby so far, I know that to be a successful programmer, I have to grow my branches. (Nonetheless, I am still excited to start my Ruby on Rails challenge after I finish my Sinatra project!)

The **client-side** validation is more user-friendly in that it does not require of the user to submit and send that information to the server to be validated; rather, input is being validated *while the user is typing it*. And that is by far the best experience anyone would want. This is achieved by means of scripting languages such as **JavaScript**, AJAX, jQuery etc.

With client-side validations, the form never gets submitted if there is a single error. Rather, the user can see the wrong input by means of dynamic display on the screen such as a red input line where the information needs to be provided or corrected. But, if the user should turn off the scripting language used, without the use of server-side validations, unvalidated data could sneak into the database, which is always bad news.

To achieve maximum user satisfaction and database cleanliness, it is recommended to use both client- and server-side validations.

