---
layout: post
title: "Sinatra is having a moment"
date: 2013-06-19 21:52
comments: true
categories: 
---



# Sinatra is having a moment.

## Frank Sinatra is balling out, but the ancient crooner has no idea why.

<br>
Seriously, though. What is it about Sinatra?

* Sinatra is small and flexible. If you're not trying to build Basecamp who needs all the overhead!?

* Doesn't follow the MVC pattern (MVC is _so_ late 20th century).
* Who's on it? Oh, I don't know… Apple, LinkedIn, Heroku, GitHub, the (_entire!?_) British Government, the list goes on. (via [Wikipedia](http://en.wikipedia.org/wiki/Sinatra_(software)).)

* Sinatra is a featherweight at a svelte <2,000 lines of code vs. the heavyweight champion Rails at ~100,000 lines of code. 

* [DHH](http://david.heinemeierhansson.com/) '04 vs. [Blake Mizerany](https://github.com/bmizerany) '07.
<br><br>
---
![Sinatra official imagery](http://24.media.tumblr.com/92c85e0a3d2a8d5ce1d33106ad6d9088/tumblr_movo37Klas1qd3p27o1_500.png)

---
> Sinatra is great for the micro-style, Rails is not. As long as you stay micro, Sinatra will beat Rails. If you go beyond micro, Rails will beat Sinatra.
<br/><br/>
> If your app has 5-10 end points, there’s a real benefit to just rolling your own with Sinatra. Essentially if your entire controller structure can fit in a page or two of code, running it in a single file is great.
<br/><br/>
> A large part of Rails’ success is by giving people a curated selection of the best technologies (“best” defined by me and the Rails community). I change Rails every week to better fit what I’d want the perfect framework to be.

>> DHH on Sinatra vs. Rails (via [RubySource](http://rubysource.com/rails-or-sinatra-the-best-of-both-worlds/))

---
# Below is a bunch of crap that I plan to revisit when I myself have a moment.

First thing's first, let's examine how Sinatra apps are packed.

## Example i. [Tilt](https://github.com/rtomayko/tilt/tree/tilt-1)
<br>
What is Tilt? Tilt is a thin interface over a bunch of different Ruby template engines in an attempt to make their usage as generic possible. 

This is useful for web frameworks, static site generators, and other systems that support multiple template engines but don't want to code for each of them individually.

** Packing structure **

  /bin/ tilt
  /docs/ TEMPLATES.md
  /docs/ common.css

  /lib/tilt/ #template implementation files in .rb e.g. nokogiri.rb, less.rb, haml.rb, coffee.rb
  /lib/tilt/ tilt.rb # module w. classes and mapping implementations

  /test/ #testing files in .rb e.g. tilt_lesstemplate_test.less, test_helper.rb, tilt_cache_test.rb, et al.
  /test

  autotest
  .gitignore
  .travis.yml
  CHANGELOG.md
  .COPYING
  Gemfile
  HACKING
  README.md
  Rakefile
  tilt.gemspec

___
## Example ii. [Brochure](https://github.com/sstephenson/brochure)


What is Brochure? Brochure is a Rack application for serving static sites with ERB templates (or any of the many template languages supported by Tilt). 

It's the good parts of PHP wrapped up in a little Ruby package — perfect for serving the marketing site for your Rails app.


**Folder Structure**

  lib/
  test/
  .gitignore
  Gemfile
  LICENSE
  README.md
  Rakefile
  brochure.gemspec
  config.ru.example
  
## Pithy wrap-up goes here.