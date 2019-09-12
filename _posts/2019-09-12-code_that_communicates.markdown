---
layout: post
title:      "Code That Communicates"
date:       2019-09-12 16:56:15 -0400
permalink:  code_that_communicates
---


As of the time of writing this blog post I am now completely done with my first Ruby Project. For my project, I made a Command Line Interface (CLI) program that scrapes the [BarnesAndNoble.com](https://www.barnesandnoble.com/b/books/_/N-1fZ29Z8q8) website and shows the user the top twenty selling books at the moment. 

Doing this project I learned a lot about deploying a working app and a lot about programming in Ruby. Initially I completed most of my code and had a working program in a few hours but I knew that my work was not done. My first issue was that a user could not exit the program gracefully, only using C-c. That method got old quickly because it showed an Interrupt error and I knew that I had to fix this. I tried many different ways to make an exit method in my CLI class. I tried a while loop that would stay inside of the program until a user typed 'no' when prompted to continue or not. After hours of trying to figure this out and googling, I saw a snippet of code in article that had a method, with one word at the end of the method, 'exit'. 

When I saw that, I realized how nice Ruby is as a programming language. I was trying to use class variables and loops to stay in the program until a certain condition is met, in this case, the user typing 'no'. Ruby is so elegant that all I had to do was put the word 'exit' in my method. In similar cases when I made a CLI app in the Python programming language, I had to make an 'quit' method and implement conditional logic to set a variable to false when a particular input is read. In Ruby all of that logic was handled in three lines. I only needed to check the input from the user and then call Ruby's 'exit' method.

Once I was able to exit the program gracefully without any errors, I began refactoring my code and cleaning up my git repo. I used the Separation of Concerns principle to isolate chunks of my code and make my methods shorter. At one point, some of my methods were over twenty and thirty lines long. I knew that these methods were hard to follow, so I broke them up into seperate methods and invoked the dependent methods inside of one another. 

While refactoring my code, I also learned about Rubocop, a Ruby linter, that a friend recommended. I used Rubocop to find any Ruby style conventions that were broken in my code. Rubocop lets you know if any errors are 'Fatal', 'Warnings', or simply 'Convention' errors and I am glad that all my code was functioning and I had no 'Fatal' errors or 'Warnings'. I had over 100 Convention errors mostly for lack of comments and my use of double-quotes rather than single quotes. Here I learned that double-quotes should only be used when interpolating (e.g. #{variable} - this would point to a variable that stores data) and using special characters (e.g. \n - the newline character, which breaks to the next line). 

The last and most universal thing that I learned when trying to clean up my code and git repository was the powerful '.gitignore' file. I wondered how I could git rid of those ugly 'foo~' files in my repositories and the same friend who mentioned Rubocop told me to learn how to use a '.gitignore' file and I am forever grateful. The '.gitignore' allowed me to hide the temporary backup files created by my text editor. Before I learned about '.gitignore' I tried to delete those 'foo~' files and I ended up breaking my local branch and got all kinds of errors from git. Now I know how to not only make my code more handsome but also my github repositories. 

The biggest topic that I learned from doing this project as far as programming in Ruby was how to make my code communicate not only with other code, but also with the Web. I created different files for each class and a main 'environment' file that required all of the classes. I was able to create book instances inside of my CLI class without all of the code in one long file; one more use of the Separation of Concerns. 

Last, but certainly not least, I used the Ruby library Nokogiri to scrape HTML documents on the web using CSS selectors to retrieve the information that I wanted. I'm glad that I have some experience with HTML and CSS which made this part of the project a breeze. I read a little about Nokogiri and I was able to get the exact text that I wanted from the Barnes and Noble website.

I learned a lot doing this project and I had lots of fun doing it. Before the project I already wanted to learn how to scrape the web with my code so that I could implement that into my other programs and now that I understand it. The sky is the limit! Thanks for reading and you can check out my Ruby Gem here: 

[barnes_and_noble_bestsellers Ruby Gem](https://github.com/anthonbrooks/barnes_and_noble_bestsellers)
