---
layout: post
title:      "Planning your Next App"
date:       2020-03-18 23:51:21 +0000
permalink:  planning_your_next_app
---


![](https://www.projectmanagementworks.co.uk/wp-content/uploads/2017/04/golden-rules-of-project-management.jpg)

Although coding is important, designing a structure is just as important.
I like metaphors so ill share a few with you. For example, let say we want to go on a camping trip with our friends, we would most likely need to plan out a strategy before executing our plan. 
We need things like supplies such as: water, food, wood, tents, sleeping bags, mosquito repellents, swiss knife, torch, some type of hunting billhook & a gps for good measure. 
Logistics such as: How would we get there, how long would we camp for and how would we distribute our supplies during the trip. Along with some emergency plans. Maybe we need to leave early because someone got hurt, we need an evacuation plan, or maybe if we get stuck in the forest for some odd reason, wee need to be able to call for help, any signal counts.



Now out trip is starting to come together! Same thing with building out large-scale web application. We need to see our supplies, our personnel, finance, duration, location of work & these are not even inside the structure of the application itself, it is a lot of work. After we secure our supplies, we need to plan out our structure. What framework are we going to use? Database? – Backend? and how about our Frontend? What language? Framework? And how will we interact with our information? 

![](https://image.freepik.com/free-vector/instagram-post-template_23-2147671656.jpg)

in this case ill share what my thought process was when I attempted to build a clone of Instagram.com. I will say this for now, its easy to bite more than you can chew. Plan accordingly.

First, supplies in this case was my computer and time. Check.

Now a structure for the backend and front end are needed. For the backend, a Rails API seemed like the perfect choice. While setting up your backend, it is essential to have your models and associations drawn out, it is very useful without a doubt. So, In this case, its all about the post. The post has a user and attached to the post we have comments with likes. Each of those likes and comments have their own perspective users that we should be able to access. Sounds simple enough right? Our user has many posts, but the user also has the posts he or she has likes or commented on. And our likes point back to our user and same as the comment. They all are intertwined.

Each post has an image, content and location, we’ve all used Instagram, you know the deal. But what should be pointed out is that we never really consider the dynamic tasks that an application does. We just see the finished product. Every application is a piece of art that can’t always be appreciated by all users. The backend is the most under appreciated asset to any web application or mobile application in general. That’s because we never get to see the backend, we just experience it, but if it is well planned out then the experience tends to be amazing.

But we can’t forget about the frontend. That’s is how we access the backend information through middleware that might or might not be implemented, depending on the task. If a frontend infrastructure is not well thought out, a well-built backend essentially can not come to fruition. All that hard work goes to waste. It is important to think critically about the frontend as well as a backend.

![](https://files.cults3d.com/uploaders/13701151/illustration-file/924dfe5c-ebed-4bc5-9f77-f98a60e51130/arbre%20yinyang%202_large.JPG)

I have an image in my head when I think of the frontend and backend. Ying Yang. Because they both work with one another, yes the frontend can essentially work on its own, and we can have a backend work alone, but when both unite, it is an amazing structure working and depending on one another.
React was the main ingredient for the frontend. In this case we added middleware like “Provider”, “Thunk” and “CreateStore” part of redux. I won’t get into their specific technicalities, but further own I’ll provide a picture on how the structure was built. 

The same idea goes into the frontend as when we built the back end. All the information is the same. But in this case, we will be moving around our information to display it to the user. That’s the main difference. Backend API helps store information and create it. React helps send and move around the information. See the coordination here? It is great!

In react however we used a tool called Redux. This tool is great because it provided us with what we call Global state. Here comes another metaphor. Imagine having your information ready for you in a cloud and accessing that cloud with your arm whenever you feel like it and pulling it all down for whenever you feel like it. Yeah that is Global State. There is some previous work to have redux set up and using it on our project but in this case, we are painting a broad brush on how it works.

The information that is in our global state or “cloud” is information we pulled from our backend and temporarily stored in a global state or “cloud”, so we can access it when we feel like it. It is very useful not having to always go to the backend, in this case we can call the backend our warehouse. It’s better to take out of the warehouse what need and then having it next to us in our global state or “cloud”. We only go to the warehouse if we really need to, like creating a new User, Post, Comment or a Like, and editing them or deleting them.

![](https://www.daymuse.com/sites/daymuse.com/files/timeline.png)

Here is how we would in theory start the process of planning out a large-scale project. This information is consisting of a one-man team. But if we have multiple people working on a project, we then will delegate parts of the application to each individual and work in coordination. That planning is done before the execution of our application as we mentioned earlier. 


