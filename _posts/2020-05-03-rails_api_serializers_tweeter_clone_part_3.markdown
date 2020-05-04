---
layout: post
title:      "Rails API serializers | Tweeter Clone | part 3"
date:       2020-05-04 01:44:55 +0000
permalink:  rails_api_serializers_tweeter_clone_part_3
---


![](https://i.stack.imgur.com/CGF5m.png)


To setup our Active model serializers we need a few steps. It will be so quick; it will surprise you.
Before we start let us look at the data that is presented to us when we initialize our localhost and hit our routes from our backend
```
[
   {
      id: 1,
      username: "rocky",
      phoneNum: 2021234567,
      email: "rocky@email.com",
      password_digest: "rocky"
   }
]
```
Our password is being shared; we do not want that. So, lets fix it.
First, we must access our gem files and add our gem.

```gem active_models_serializers```

Then install

```bundle install```

Once we have set our gem up, we need to create the serializer objects based on the models we have created.

```rails g serializer User```

```rails g serializer Tweet```

Great. Now we have our serializers:
```
class UserSerializer < ActiveModel::Serializer
  attributes  :id
end
```
Oh no, we have only one attribute on our serializers. 
```
[
   {
      id: 1
   }
]
```


Here is where we add or remove our information. Naturally with our routes, our information is being sent through our controllers. But with our serializer we control the data and what is being displayed. 

```
 class UserSerializer < ActiveModel::Serializer
  attributes :id,
  	:username,
    :phoneNum,
    :email
end
```

Fantastic, we now are sending the specific information we want to share and display Our data now looks like this. 

```
[
   {
      id: 1,
      username: "rocky",
      phoneNum: 2021234567,
      email: "rocky@email.com",
   }
]
```

A cool trick is to associate data through our serializers, it’s just like creating associations between our models. It looks something like this. 

```
class UserSerializer < ActiveModel::Serializer
  attributes :id,
  	:username,
    :phoneNum,
    :email

    has_many :tweets
end
```

Our data now looks something like this.
```
[
   {
      id: 1,
      username: "rocky",
      phoneNum: 2021234567,
      email: "rocky@email.com",
      tweets: [
         {
            id: 1,
            content: "My first Tweet",
            user_id: 1
         }
      ]
   }
]
```
How cool is that? We now have finished building Tweeter's Backend, what an accomplishment!

