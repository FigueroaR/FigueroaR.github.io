---
layout: post
title:      "Meetup Mock WebApp"
date:       2020-01-16 22:05:07 -0500
permalink:  meetup_mock_webapp
---


This Rails Application is meant to represent [Meetup](https://www.meetup.com/) in a smaller scale and as a fun project. Here is a bit of a technical summary. You can download it [here](https://github.com/FigueroaR/meetup_mock_web_app)

5 Major concepts 

- Models

- Controller 

- Views 

- Database

- Routes

These components pulls the string in the back end & as we all know Ruby on Rails is magic. 
First off, in any project, it is ideal to visualize the project and have expectations that we would like to incorporate. Frontend web development usually takes all the credit when it comes to being creative a creative field, it has its merits and we should give credit where it is due.
Backend Development is a creative field on a different scale. With backend, we get visuals, but visuals come after we build the roads, then we fix up the destination we have arrived at.

So, what is the first visualization we need? In my Opinion, It should be the relation between (the people or) models that we have created. How will the interact with one another? ...and why?




**Model Associations**

In this app we have a few models: 

- User 

- Event

- Rsvp(reservations)

- Comments 

It is very helpful to draw the lines of how each relation interacts with one another. It is part of the creative process. 
[here](https://github.com/FigueroaR/meetup_mock_web_app/tree/master/app/models) we see how each model is interconnected, in technical terms - Associations 

- [User](https://github.com/FigueroaR/meetup_mock_web_app/blob/master/app/models/user.rb) associations:

   - has_one_attached :photo
   - has_many :rsvps
   - has_many :events, through: :rsvps
   - has_many :comments
	
	
- [Rsvp](https://github.com/FigueroaR/meetup_mock_web_app/blob/master/app/models/rsvp.rb) Associations:

   - belongs_to :user
   - belongs_to :event


- [Events](https://github.com/FigueroaR/meetup_mock_web_app/blob/master/app/models/event.rb) Association:

   - has_one_attached :photo
   - has_many :rsvps
   - has_many :users, through: :rsvps
   - has_many :comments

   

[Comment](https://github.com/FigueroaR/meetup_mock_web_app/blob/master/app/models/comment.rb) Associations:

   - belongs_to :event
   - belongs_to :user
   

It is very recommended that we add *validations* to our data. 
for example, an [event](https://github.com/FigueroaR/meetup_mock_web_app/blob/master/app/models/event.rb) would need these requirements: 

- validations

  - validates :name, presence: :true
  - validates :city, presence: :true
  - validates :country, presence: :true
  - validates :content, presence: :true


We wouldn’t want to save an empty event, rinse & repeat with other models (depending on what properties they have).



**Controllers**

Thanks to our controller we can manipulate out models and make them function the way we want to. 
This entire app is based on the events, wo most of the visuals or magic will be happening on the Event controller (although each controller is actively contributing). 

Each controller has actions, some basic actions are: 

- Index

- Show

- Edit

- Delete

See [here](https://github.com/FigueroaR/meetup_mock_web_app/blob/master/app/controllers/events_controller.rb)


A controller is composed on *actions*, These actions work in conjunction with our views and routes (keep that in mind). Thanks to these controllers we can CRUD (create, read, update & delete) our data. Simple enough right?



**Databse**

remember the picture we drew? It is time to draw that picture inside the database. - How you ask?. Let's take a look, shall we? 

see schema [here](https://github.com/FigueroaR/meetup_mock_web_app/blob/master/db/schema.rb)


This is where we put/have each individual piece of information of each model via migrations.
Each string, integer or datetime is a column on the *table* of that *Model* we intend to work with. 
This data can later be called upon user the *Model* and *Associations*. Like I said Ruby on Rails is magic. 



**Routes**

Routes are amazing, they can guide you places and help direct your information properly, if used correctly, you can go many places. 

See routes [here](https://github.com/FigueroaR/meetup_mock_web_app/blob/master/config/routes.rb)

Each *GET* send you to a url, each *To* is the controller you activate *#* is the action in that controller that you can activate. It can end there if you want it to. But if you want to redirect to a different location you may do so from that *action* in the *controller* you just called. Isn't that so cool? Well i think it is. We are giving out free information via these routes. Like we said before Magic! 



**Views**

This is the part where we finally get to see the visuals of the Web App we are building; it speaks for itself. 
Here we need some HTML to finish our product correctly and display our information. It is not so bad, but if we can’t to use *Ruby* we can use some simply symbols within our views. To read some Ruby in out *html* form use "*<%  add ruby code here  %>*".  "*<%  %>*",  Simply evaluates the code,  but if we want to display some *ruby* in *HTML*, let’s use this "*<%=  a ruby output  %>*".  Remember to use "<%= %> or <% %> symbols with ruby code only. 

Example [here](https://github.com/FigueroaR/meetup_mock_web_app/blob/master/app/views/events/index.html.erb)



