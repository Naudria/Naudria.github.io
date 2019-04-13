---
layout: post
title:      "Rails With JS Project: The Death of Me"
date:       2019-04-13 19:21:12 +0000
permalink:  rails_with_js_project_the_death_of_me
---

Wow. What a bear of a project that was.

Rather than add a Javascript frontend to my Rails app from my previous project, I chose to create an entirely new doman model. This was mainly because both my Sinatra and Rails projects were based on the same domain model, so I thought it made sense to diversify my portfolio.

Ack.

I had to come up with a new idea, struggle with relationships and associations, styling... all on top of the new elements of Javascript, JSON and AJAX. I managed to get three object models (users, beers, and comments) and meet the minimal requirements for the project after 3 weeks of agony. No, really—sheer agony.

Unlike Ruby, I don't think Javascript is an intuitive language. I find myself getting lost in a tangle of "{ }"s and "( )"s. That said, after 3 weeks, I finally felt like I had a decent grasp of what was happening.

I dynamically rendered two index pages—beers and comments—via JS and an Active Model Serialization JSON backend. On the user's page, I displayed the index of all beers added, which I grabbed using fetch requests. The backend rendered the beers in JSON format and appended them to user's and beers' index pages. I did the same with a beer's comments, which are rendered on a beer's show resource. Individual beers are rendered dynamically rendered as well.

I rendered a form for creating a new beer that is submitted dynamically and displayed through JavaScript and JSON without a page refresh.

Finally, I created Beer and Comment prototype objects and add  functions to those prototypes to concatenate (format) the beers and comments separately. I then used the objects to append the their respective information to the DOM.

See my final project [here.](https://github.com/Naudria/beers-app) 



