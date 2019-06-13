---
layout: post
title:      "Quotalicious: My Final React - Redux Project!"
date:       2019-06-13 15:39:25 +0000
permalink:  quotalicious_my_final_react_-_redux_project
---


For my final project, I was torn between doing something original and doing something I could manage to finish in 3 weeks without pulling my hair out. I settled on an app that fetches quotes from the  [https://favqs.com/](http://) API and allows the user to add them to specific lists. Building the Rails server and adding the data persistence was a little confusing because my associations weren't as cut and dry as` has_many `and `belongs_to`. In my Routes file I added a member route on lists called favorite, then one called favorited_by on quotes. My join table is favorite_quotes.

Hooking up the React frontend was simple thanks to[ this](https://www.fullstackreact.com/articles/how-to-get-create-react-app-to-work-with-your-rails-api/) article. Perhaps the most confusing aspect of the project was the Redux part. For an app as simple as mine, it seemed tedious to use Redux to load the data, but I appreciate the reasons for using it in more complex apps. I really had to break down the steps for myself to grasp it:

1.  Component AllLists gets rendered in the browser.
2.  AllList's componentDidMount lifecycle method gets called.
3.  We call the action creator fetchLists from componentDidMount.
4.  fetchLists runs code to make an API request from favqs.com.
5.  API responds with data.
6.  fetchLists returns an 'action' with the fetched data on the payload propery.
7.  Listreducer sees the action, returns the data off the payload (lists).
8.  Because we generated some new state object, redux/react-redux cause our app to be rerendered.

Steps 1-3 are generally the component's responsibility; they must fetch the data they need by calling an action creator.

Steps 3-6 is where Redux-Thunk comes into play: Action creators are responsible for making API requests. Middleware such as Thunk has the ability to stop, modify, or otherwise mess with actions to solve async issues.

Steps 7 and 8 are where we get the fetched data into a component by generating new state in our redux store, then getting that into our component through mapStateToProps.

The other obstacle I had with this project was understanding good vs bad reducer code. For instance,  in order to add an element to an array, you wouldn't do this:

```
state.push('whatever')
```

Rather, you would do this:

```
[...state, 'whatever]
```

This is, presumably, because reducers must be "pure" -- they can only return values that use its input arguments (state, action).

All in all, I was happy with the results of my project. I intend to add the ability to create lists and user authentication in the near future. See my repo at https://github.com/Naudria/Quotalicious
