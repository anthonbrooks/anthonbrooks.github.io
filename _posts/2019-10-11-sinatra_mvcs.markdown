---
layout: post
title:      "Sinatra MVCs "
date:       2019-10-11 14:36:33 -0400
permalink:  sinatra_mvcs
---


I have now started my first web app built with Ruby and the Sinatra Framework and it has been a lot of fun. My app is called Poppy, a place where people can leave reviews for movies and see the reviews that others leave. Making this web app, I utilized the concepts of MVCs: Models, Views, and Controllers, and RESTful routes to make my idea come to life.

## Model/View/Controller

The MVC convention separates different types of files into different directories depending on the function of the file. The Model folder contains the Ruby classes for the different entities present in a web app. The View folder contains the content that clients are going to see in their browser. Lastly, the Controller bridges the Model and View and handles routing in a Sinatra app. 

### Model

The model in a Sinatra web app is represented as a Ruby class and it allows developers to give each entity specific attributes and connect entities to the database. For example, a blog would have Users and Posts. A User can have ownership of many Posts but a Post must belong to one user. This type of logic is handled in the Object Model. I used the Active Record Ruby gem and Bcrypt gem to handle some methods for models. 

Active Record gives us shortcuts to handle these types of attributes for Objects. Instead of writing out methods for each association, Active Record gives us the macros ```belongs_to``` and ```has_many``` which create the associations automatically for the Post and User. 

Bcrypt secures passwords as a hash in the database and gives us the macro ```has_secure_password``` for the User model in this case. This macro would ensure that plain-text passwords are not saved in the database so that bad actors cannot simply read each User's password and access their account. Bcrypt will hash the password and add a 'salt' (random characters in the hash) so that if two people have the same password, their password hash will not be identical as well. 

### View 

The views of a Sinatra app are html or erb documents that are displayed in a client's browser. Views utilize Models and Controllers. The view files display the data and content that you want users of your app to see, like a blog post or a form to write a new post.  

### Controller 

The controller ties everything together and defines how your app will handle HTTP requests. In controller files you define what a ```get``` request, for example, to ``` '/' ``` will render for the client. Also, you can query the database to show specific data on each page using ```params``` and methods provided by Active Record. 

The controller is where the magic of CRUD comes to life. In a view file you could have a form to write a blog post or edit a blog post but you need relevent controller actions to handle saving that input to the database and show that information for the writer and others to view. 

To have an effective controller you need methods for each action: 

* Create - HTTP ```post``` request 
* Read - HTTP ```get``` request 
* Update - HTTP ```patch``` request 
* Delete - HTTP ```delete``` request 

In a Rack app you must include the line ```use Rack::MethodOveride``` in your config.ru file to import the ```MethodOveride``` class from Rack. This class allows the ```patch``` and ```delete``` methods to function correctly. 

## REST

In order for users to type in a specific URL and get the expected page, RESTful Routes are used. REST stands for REpresentational State Transfer and it is a convention for web apps to structure URLs. REST allows you to use HTTP methods to specify what page is rendered for users depending on what is typed into the URL bar or clicked on the screen. RESTful Routes are defined in the Application Controller of a Sinatra app and you can have controllers for each entity of your app to separate concerns and keep each file neat, for example: a Users Controller and Blog Post Controller. 

To start, most websites have a homepage or 'root', which is defined as an HTTP ```get``` method. In this method you would tell your controller to get a resource from your view templates and display that to the client/browser. The rendered page can have links to other pages, forms to fill out (sign-up/sign-in forms, or forms to create a blog post), and all sorts of other data like photos, videos, and of course, text. 

The next important HTTP method that is defined in the controller is the ```post``` method. This method allows a user to create or submit and save data to the database. So, if a user signs-up for a website and submits that form, a new row in the database is created for that person and the specific parameters passed in will be placed in the appropriate columns. So if the sign-up form has entries for Name, email, and password, each one will be saved in a different column in a row corresponding to the user with an ActiveRecord generated unique-ID. The password will not be saved as a hash thanks to Bcrypt. 

Within the ```post``` method you would often use the ```redirect``` method to lead the user to somewhere new after a form is submitted. If a user is signing-in to your webapp, you might want to ```redirect``` them to the user's homepage. If a user has just written a new blog post, you could ```redirect``` the user to a preview of what the blog post would look like to all visitors so that they can review it and ```edit``` or ```delete``` the post, which leads to the next HTTP methods defined in the Controller. 

To edit something such as a blog post in our example, the HTTP ```put``` or ```patch``` methods are used. This updates the object in the database. 

Finally if your user wants to remove post from the world-wide web for whatever reason, the HTTP ```delete``` method is there to save the day. The ```delete``` method simply destroys the object from the database so after sumbitting this request, it would be as if the blog post never existed. No trace of the  object is left. 

My initial idea was to create an app where people can write reviews, comment on reviews, and also make friends and movie dates with those friends. However, I have a lot to learn before I can set up relationships between users and implement those functionalities. I learned a lot doing this project and I enjoyed it. If you want to check out my code go to: 

[Poppy](http://github.com/anthonbrooks/poppy)
