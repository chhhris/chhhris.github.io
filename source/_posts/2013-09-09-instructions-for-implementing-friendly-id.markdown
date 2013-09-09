---
layout: post
title: "Instructions for implementing Friendly ID"
date: 2013-09-09 01:26
comments: true
categories: 
---

# Step-by-step instructions for implementing Friendly ID in a Rails app.

## You already know RESTful urls are n00b sauce, otherwise you wouldn't be here.

If you're not familiar, [Friendly ID](https://github.com/norman/friendly_id) is a sweet gem that turns Rails standard RESTful urls (e.g. /users/1/) into more friendly and best practice string-based urls (e.g. /chris-lake)

The following instructions were curated from Norman Clarke's Rails [QuickStart guide](https://github.com/norman/friendly_id) and Ryan Bates's [RailsCast](http://railscasts.com/episodes/314-pretty-urls-with-friendlyid). 

Add FriendlyID to your Rails app's gemfile.

	gem 'friendly_id', '5.0.0.beta4' #=> Or whatever the current version is.

From terminal run bundle install, per usual:

	$ bundle install


For all the models you want to add FriendlyId's, run the following migration.

	$ rails g migration add_slug_to_[your model name here] slug:string

Ryan Bates says it’s a good idea to add an index for finding records, and at this point in my coding career, I'm a follow Ryan Bates's advice. (Btw, that dude is the man. I hope he takes the time he needs to get his head straight.)

In the migration file - let's use a User model by way of example - `/db/migrate/20120101000000_add_slug_to_user.rb`, add the index like so.

	class AddSlugToUsers < ActiveRecord::Migration 
	  def change
        add_column :users, :slug, :string
        add_index :users, :slug
      end
    end

Please remember to run the migration. 

	$ rake db:migrate

To fill the slug in for existing records, we need to go into each record and save it. 

	$ rails c
	> User.find_each(&:save)
 
We'll want our slugs to update when records are changed in the db. At the same time it seems to be a good practice to still recognize older slugs and their legacy urls. We can do this by using FriendlyID’s `history` option in our model `/app/models/user.rb`.

	class User < ActiveRecord::Base
	  extend FriendlyId
	  friendly_id :name, use: [:slugged, :history]
	end
 
This history needs to be stored somewhere so you'll also want to add a table to your database schema to store the slug records. FriendlyID provides a generator for this purpose:

	$ rails generate friendly_id
	
And again.

	$ rake db:migrate
	
Ryan Bates points out that, at this point, if our customer visits a legacy url, it will just work. Better would be to redirect them to the new url. We can do this by adjusting the show page on the controller - `/app/controllers/users_controller.rb`

Not sure if I'll even bother implementing this, but here's the syntax.

	def show
	  @user = User.find(params[:id])
	  if request.path != user_path(@user)
	    redirect_to @user, status: :moved_permanently
	  end
	end