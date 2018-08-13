---
layout: post
title:      "App Architecture: Model–View–Controller"
date:       2018-08-13 01:19:23 +0000
permalink:  app_architecture_model_view_controller
---


When I wrote my first CLI app, in it I had a controller that communicated with the user and fetched the requested data; it was the heart of my simple program. In addition, to actually get that information, I had a Scraper class that *"modeled"* my data from a website. Unfortunately, for the command-line, the notion of a view is left out.

Now, when I connect to a Sinatra server and send HTTP requests, this architectural design of model-view-controller comes in handy. Although I had to take a moment to grasp the complexity of it, now I appreciate the separation of concerns in a program.

So, if I want to fill in a form online, I communicate with the controller which then converts, or *manipulates* my input, and sends it to the model. This is where all the data, logic and rules of the application are stored. When we're dealing with OOP, the model will have objects of that data, and the data itself will be stored in a database (of course!). After the model gets the raw data, it wraps it up in a nice object package and sends it back to the controller, which then transfers those data objects to the view, which is what I will see on my screen. Finally, the controller makes its final bow, and sends HTML in HTTP response.

The advantages of this architectural pattern are the following:
* **Separation of concerns** make it easy for many developers to work on the same app.
* **Cohesive code:** related actions are logically grouped together.

The disadvantages may be:
* **Code complexity:** because of added layers of abstraction, new developers might find it cumbersome to decompose the MVC.
* **One language is not enough:** developers need to be skilled enough to be able to abstract the data into objects using an OO language like Ruby, as well as understand what is going on "under the roof", i.e., the database.
