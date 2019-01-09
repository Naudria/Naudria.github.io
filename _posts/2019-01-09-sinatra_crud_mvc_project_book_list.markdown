---
layout: post
title:      "Sinatra CRUD MVC Project: Book List"
date:       2019-01-09 12:28:13 -0500
permalink:  sinatra_crud_mvc_project_book_list
---



For my Sinatra project I decided to create Book List, a very simple app that allows a user to view and add to a master list of favorite books—including the book's title, author and genre—and share them with other users. I am constantly looking for new books to read, and to share my faves with others, so this seemed useful (albeit so basic it would need a lot more complexity to reach the usefulness of GoodReads). Still, I kept it simple in order to ensure I understood every bit of it!

I started off creating the file structure with a handy little gem called [Corneal](https://thebrianemory.github.io/corneal/). It is important to structure the Models-Views-Controllers correctly, and this generator makes it easy. Then I made a checklist of things a User should be able to do:


* Sign up for a new account
*  Log in to her account
*  See an index of books added by all users
*  View any book's info
*  Edit the book's info only if she created the book
*  Add new books to the index
*  Delete a book only if she created the book

I decided to start from the bottom up, with the database. I generated migrations from the command line with rake db:create_migration NAME=create_users and rake db:create_migration NAME=create_books. I created tables for each and made sure my Book table referenced the User table with a user_id. The tables also identified the types of data I wanted to store for each table: Users need a username, password, and email; Books need a title, author, genre, and user_id. 

Then I created models for Users and Books that enacted the relationship with macros for each class:

![](https://imgur.com/sF8Njvt)

A User has_many Books, and a Book belongs_to a User. In the Terminal, I ran rake db:migrate to migrate my tables and obtain the schema file.

Next, I implemented CRUD methods using RESTful routes. According to the RailsGuide, routing connects incoming HTTP requests to the code in your application’s controllers, and helps you generate URLs without having to hard-code them as strings. 

# Users Controller
The users controller implements the user sign-in/sign-out, sign-up. The authenticate method was used to confirm the password with the saved password in the password_digest column in the data base.

# Books Controller
The books controller implements the creation, showing, updating and deleting actions of the books. It GETs information from the forms to create/edit/delete instances of Book, depending on whether the User attempting the action is the User who created the Book in the first place. This aspect was the hardest part of the project for me:

![](https://imgur.com/KEI9lSQ)

I created views for Users and Books, each with the appropriate forms and inputs. The easiest part was the CSS—I like making my apps look pretty, but only when they work. 

Watch my demo video [here](https://youtu.be/PpKxeXdeWNc) and see the repo on Giithub [here](https://github.com/Naudria/Book-List).






