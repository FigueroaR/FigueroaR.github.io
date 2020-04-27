---
layout: post
title:      "Rails Api | Tweeter clone | part 2"
date:       2020-04-27 02:19:46 +0000
permalink:  rails_api_tweeter_clone_part_2
---


![](https://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2017/01/1483894573Fotolia_117678863_Subscription_Monthly_M.jpg)


We will continue with our theme of creating Tweeter’s backend. At this point we need to scaffold a table, migrate that table, create our associations, console into our project and create users and tweet. Sound Simple enough? Lets dive in then! 

First lets create out “Tweet” table 

```rails g scaffold Tweet content user_id:integer```

And we get

```
class CreateTweets < ActiveRecord::Migration[6.0]

  def change

    create_table :tweets do |t|

      t.string :content

      t.integer :user_id

      t.timestamps

    end

  end

end```

So now we have a user table and Tweet table and we need to migrate them.

```rails db:migrate```

At this point our controller and model have been set up. 

```class Tweet < ApplicationRecord
end```

& 

```
class TweetsController < ApplicationController
  before_action :set_tweet, only: [:show, :update, :destroy]

  #GET /tweets
  def index
    @tweets = Tweet.all

    render json: @tweets
  end

  # GET /tweets/1
  def show
    render json: @tweet
  end

  # POST /tweets
  def create
    @tweet = Tweet.new(tweet_params)

    if @tweet.save
      render json: @tweet, status: :created, location: @tweet
    else
      render json: @tweet.errors, status: :unprocessable_entity
    end
  end

  # PATCH/PUT /tweets/1
  def update
    if @tweet.update(tweet_params)
      render json: @tweet
    else
      render json: @tweet.errors, status: :unprocessable_entity
    end
  end

  # DELETE /tweets/1
  def destroy
    @tweet.destroy
  end

  private
    # Use callbacks to share common setup or constraints between actions.
    def set_tweet
      @tweet = Tweet.find(params[:id])
    end

    #Only allow a trusted parameter "white list" through.
    def tweet_params
      params.require(:tweet).permit(:content, :user_id)
    end
end
```

This outcome applies to our User table too. However, our models need an association, how would our table look now? Both User and Tweet

```
class User < ApplicationRecord

  has_many :tweets

end
```


```
class Tweet < ApplicationRecord

  belongs_to :user

end
```

What happened here? Well we are bringing in extra methods that can be called upon when we need to derive associated information. I do need some extra users in the database however, so I'll dig into the console and add them manually.


```rails c```


```User.create(username: "rocky", phoneNum: 2021234567, email: "rocky@email.com", password_digest: "rocky")```

& a Tweet

```Tweet.create(content: "First tweet!", user_id: 1)```

The user id column is so important, that is where we put the id of the user who creates the Tweet.
Now when we run ```Tweet.all``` or ```User.all``` in our console and we see we have populated information. To see our data display as json data, we simply go to our localhost and use the routes.  Run ```rails s``` in your terminal and In this case we will go to ```localhost:3000/users``` & ```localhost:3000/tweets``` in our browser, (yes it has to be plural or according to your routes if changed). All our information we inserted manually should be there waiting for us.


That was not so bad! Next, we will utilize active model serializers to display information that is associated with one another








