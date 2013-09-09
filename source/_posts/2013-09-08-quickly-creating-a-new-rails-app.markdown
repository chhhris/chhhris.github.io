---
layout: post
title: "Quickly creating a new Rails app"
date: 2013-09-08 22:31
comments: true
categories: 
---

# Cheat sheet for creating a new Rails app, adapted from the excellent [Rails Guides](http://guides.rubyonrails.org/getting_started.html)

Create a new project

    $ rails new <project name>

Switch into the correct folder
    
    $ cd <project name>

Get the database up
    
    $ rake db:create
    
To start the rails server:

    $ rails s
    
Create a controller

    $ rails generate controller home index
    
If you're using Rails v3.2.13, remove the default home page

    $ rm public/index.html

Open `config/routes.rb` and uncomment the root url route

    root :to => "home#index"
    
Scaffold a resource

    $ rails generate scaffold <Model_Name> column_name:data_type column_name:data_type 
    
Run another migration

    $ rake db:migrate
    
