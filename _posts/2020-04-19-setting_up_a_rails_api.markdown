---
layout: post
title:      "Setting up a rails API"
date:       2020-04-20 02:59:03 +0000
permalink:  setting_up_a_rails_api
---




![](https://i.ytimg.com/vi/Z9wKRqTR5Q4/maxresdefault.jpg)

A good question is: Why would we want a rails Application Programming Interface? Well… you came to the right place. A short quick and simple explanation. An Api serves to maintain, hold and transfer information. Let’s pretend we are a start up and we have a product called tweeter. Tweeter is an application where we can send tweets (thoughts &/or information) on the internet. Now we need a location (databse) to hold our users who sign up and tweet. Our API talks to our database who stores all out information. This is crucial for any application. For now we are involved in the backend (database) and API – (middle backend) of our application. 



Continuing with our start up example. We need to set up our rails API.
First line of code we need to write is 

```rails new tweeter –api```

we of course called out api tweeter but you can give it any name you like 

```rails new any-name –api```.

And that is it, our API is up and running. We do not however have a database set up. 
For that we need to create a table and rows of information. It is simple, lets look. 
So our user here will have a username, email, phone number and a password (we will call it password_digest). 

```rails g scaffold User userName email password_digest phoneNum:integer```

```rails g scaffold Tweet content user_id:integer```

On our column, some will be representer as strings, no need to declare it a string, but phone number which are integers must be declared as integers. Booleans & integers must be declared with their corresponding column. 

Next we run ```rails db:migrate``` and we have our first table, model, controller, but for now we wont worry about our views, we will take a look at associations our next talk. 

Do not forget to bundle our gem ‘bcrypt’ it is essential on our Gemfile. Visit our Gemfile and uncomment or add – ```gem ‘bcrypt’```. Then in our terminal run ‘bundle install’. We are closer now to setting up tweeter. 

