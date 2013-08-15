---
layout: post
title: "The difference between procs, blocks and lambdas"
date: 2013-08-06 11:07
comments: true
categories: 
---

# What are Procs and lambdas: Closure in Ruby

First: What is a closure? *(Somehow my English degree didn't teach me this :)*

Closures allow declarative programming languages - specifically, languages that do not normally maintain *state* - to persist data. 

They are found in [many popular languages](http://stackoverflow.com/questions/1423002/how-different-programming-languages-use-closures) including 

* JavaScript 
* Ruby 
* Python 
* C# and 
* Objective-C.

In Ruby, every `Proc` object is a closure, which means that each code block you write captures references to data from its surrounding scope for later use. [(Source)](https://practicingruby.com/articles/shared/mvzhovpjbghr). The core properties of closures, and by extension Ruby procs and lambdas, are:

1. You can pass `Procs` and lambdas around like objects (to be called later).

2. `Procs` and lambdas remember the values of all the variables that were in scope when the function was created. `Procs` and lambdas are then able to access those variables when they're called even if those variables are no longer be in scope.

Let's dive into some code to examine scope vis a vis procs and lambdas:

		def proc_can_see_outer_scope_locals
		  y = 10
		  	lambda { p defined?(y) }.call
		end
		
		proc_can_see_outer_scope_locals #=> "local-variable"
		
		def proc_can_modify_outer_scope_locals
		  y = 10
		  lambda { y = 20 }.call
		  p y
		end
		
		proc_can_modify_outer_scope_locals #=> 20
		
		def proc_destroys_block_local_vars_on_exit
		  lambda { y = 10 }.call
		  p defined?(y)
		end
		
		proc_destroys_block_local_vars_on_exit #=> nil
		
		# Code snippet courtesy of the Practicing Rubyist.
 

For the record, Procs can be executed [3 ways](http://www.skorks.com/2010/05/closures-a-simple-explanation-using-ruby/). 

		# 1 call method
		puts Proc.new{|x|"blah1"*x}.call(2)
		
		# 2 array syntax
		puts Proc.new{|x|"blah1"*x}[2]
		
		# 3 dot syntax
		puts Proc.new{|x|"blah1"*x}.(2)
		

### What are the differences between `Procs` and lambdas?

Procs and lambdas behave differently upon being returned. As soon as procs are returned, they will escape the function. 

For example, if you call return within a method, as soon as the proc hits the method is escaped and that value is returned. Nothing after the initial `return` will be called.

		def my_method
		  puts "before proc"
		  my_proc = Proc.new do
		    puts "inside proc"
		    return
		  end
		  my_proc.call
		  puts "after proc"
		end
 
		my_method

		#=> before proc
		#=> inside proc
		
		# code snippets courtesy of Alan Skorks.


The final `puts` in the method was never executed because the `return` within `my_proc.call` dumped us out of the method. 

Whereas a lambda will let the function continue after the return value, until the whole function has been run.

		def my_method
		  puts "before proc"
		  my_proc = lambda do
		    puts "inside proc"
		    return
		  end
		  my_proc.call
		  puts "after proc"
		end
		 
		my_method
		
		#=> before proc
		#=> inside proc
		#=> after proc

Possible downside with lambdas is that they can leak memory. This happens when local variables, which would normally be garbage collected by Ruby's native gc, are instead persisted by lambda's reference to them. 

## Resources for further reading:

1. Skorks on [Closures](http://www.skorks.com/2010/05/closures-a-simple-explanation-using-ruby/), and Skorks on [Procs and lambdas](http://www.skorks.com/2010/05/ruby-procs-and-lambdas-and-the-difference-between-them/).
2. [Practicing Ruby](https://practicingruby.com/articles/shared/mvzhovpjbghr)
3. JavaScript 101 is garbaggio #=> find something better. 