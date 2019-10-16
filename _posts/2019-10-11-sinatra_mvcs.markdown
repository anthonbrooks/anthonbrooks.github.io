---
layout: post
title:      "Sinatra MVCs "
date:       2019-10-11 14:36:33 -0400
permalink:  sinatra_mvcs
---


I have now started my first web app built with Ruby and the Sinatra Framework and it has been a lot of fun. My app is called Poppy, a place where people can leave reviews for movies and see the reviews that others leave. Making this web app, I utilized the concepts of MVCs: Models, Views, and Controllers, and RESTful routes.

## Model/View/Controller

The MVC convention separates different types of files into different directories depending on the function of the file. The Model folder contains the Ruby classes for the different entities present in a web app. The View folder contains the content that clients are going to see in their browser. Lastly, the Controller bridges the Model and View and handles routing in a Sinatra app. 

### Model

The model in a Sinatra web app is represented as a Ruby class and it allows developers to give each entity specific attributes and connect entities to the database. For example, a blog would have Users and Posts. A User can have ownership of many Posts but a Post must belong to one user. This type of logic is handled in the Object Model. I used the Active Record Ruby gem and Bcrypt gem to handle some methods for models. 

Active Record gives us shortcuts to handle these types of attributes for Objects. Instead of writing out methods for each association, Active Record gives us the macros ```belongs_to``` and ```has_many``` which create the associations automatically for the Post and User. 

Bcrypt secures passwords as a hash in the database and gives us the macro ```has_secure_password``` for the User model in this case. This macro would ensure that plain-text passwords are not saved in the database so that bad actors cannot simply read each User's password and access their account. 

### View 

The views of a Sinatra app are html or erb documents that are displayed in a client's browser. Views utilize Models and Controllers. The view files display the data and content that you want users of your app to see. 

### Controller 

The controller ties everything together and defines how your app will handle HTTP requests. In controller files you define what a ```get``` request, for example, to ``` '/' ``` will render for the client. Also, you can query the database to show specific data on each page using ```params``` and methods provided by Active Record. 

## REST



My initial idea was to create an app where people can write reviews, comment on reviews, and also make friends and movie dates with those friends. However, I have a lot to learn before I can set up relationships between users and implement those functionalities. I learned a lot doing this project and I enjoyed it. If you want to check out my code go to: 

[Poppy](http://github.com/anthonbrooks/poppy)
