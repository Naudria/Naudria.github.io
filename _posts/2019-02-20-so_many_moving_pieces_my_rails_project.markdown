---
layout: post
title:      "So Many Moving Pieces: My Rails Project"
date:       2019-02-20 16:23:22 +0000
permalink:  so_many_moving_pieces_my_rails_project
---


For my Rails portfolio project, I chose to expand on my Sinatra project and create a simple Rails app that lets users rate books they’ve read and add them to a master list of books. It also allows them to rate books added by other users. A user is able to create an account, either by setting their email and password or authenticating through Facebook, add new books and ratings, edit books and ratings they created, and logout. 

The project required at least one `has_many`, at least one `belongs_to`, and at least two `has_many :through `relationships, and a book review app fit the bill: The models are User, Book, and Rating. A User `has_many` Ratings, and many Books, through Ratings. A Book `has_many` Ratings, and many Users, through Ratings. Ratings `belong_to` both User and Book. 

The reason for a many-to-many relationship between Users and Books is because a Book may have many different Users, while a User may have many different Books. Rating serves as the join table, storing information about each User’s review of each Book. These relationships allowed for nested routes: because ratings are children of the resources books,  ratings belong to books. Therefore, ratings can be nested in books.

I found myself "rake routes"-ing constantly during the building of this app. While it seems, on the surface, fairly intuitive, my ‘/books/:id’ convention became ‘/books/:book_id/ratings/:id’ once I navigates into my ratings routes. Whenever my application receives a request to any of the actions defined in my RatingsController, a book ID is passed in the format of ‘params[:book_id].’ If I want my books#index action to display a collection of ratings that belong to the book that I am navigating under, I will need to pass ‘params[:book_id]’ in as an argument to stipulate that I only want ratings from the book who’s ID matches.

Whew. I can see why resources shouldn't be nested deeper than one level—it gets complicated quickly!

I kept having to remind myself that every time I was creating a new rating, what I was *really* doing was creating a new rating object that belongs to a book object, so I had to let my helper methods (such as` form_for`) know which book I was referencing with each rating. 

Find my project here: https://github.com/Naudria/my-favorite-books


