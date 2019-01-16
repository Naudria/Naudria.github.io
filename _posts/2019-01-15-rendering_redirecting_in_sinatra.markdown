---
layout: post
title:      "Rendering / Redirecting in Sinatra"
date:       2019-01-15 12:07:09 -0500
permalink:  rendering_redirecting_in_sinatra
---

The controller methods render and redirect both end up showing a user a different page in the browser, but they are very different. We use render in a controller when we want to respond within the current request, and redirect_to when we want to spawn a new request.

# RENDER

Rendering doesn't change the URL of the page you are visiting; rather, Sinatra automatically matches an action in the controller with an appropriately named view file. Render tells Sinatra which view or asset to show a user, without losing access to any variables defined in the controller action. Render keeps the data from the controller so you can access it in the view page the user requested. 

```
get '/books/:id' do
      @book = Book.find(params[:id])
      erb :"books/show"
  end
```
In the above route, we create an instance variable that passes to a show view via rendering. The instance variable is accessible in the view that was defined in the controller action because the view is rendered.

# REDIRECT

Redirect, however, tells your browser to send a request to a completely different URL, and that view to which you redirect will NOT have access to any variables defined in the controller. Redirect sends a new request to another URL without bringing the data or variables defined in the controller with it. 

```
post '/books' do
    if logged_in? && !params[:title].empty? && !params[:author].empty? && !params[:genre_id].nil?
      @book = current_user.books.create(title: params[:title], author: params[:author], genre_id: params[:genre_id])
       flash[:message] = "Book has been added."
      redirect "/books"
     
    else
          flash[:message] = "When creating a new book, please provide a title, author and genre."
      redirect '/books'
  
    end
  end

```

In the above route, the goal is to create a book, not show anything to the User. Therefore, it makes more sense to create a brand new HTTP request and redirect to the action whose job it ** IS** to show this instance variable, i.e., /books or /books/#{@book.id}. This creates a separation of concerns. 




