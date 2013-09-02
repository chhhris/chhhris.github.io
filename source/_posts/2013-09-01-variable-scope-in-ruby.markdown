---
layout: post
title: "Variable Scope in Ruby"
date: 2013-09-01 18:24
comments: true
categories: 
---

# Variable Scope in Ruby
## Defining scope between Global, Class, Instance and Local variables in Ruby

If you're learning Ruby, one of the first concepts you'll likely encounter - after Objects and Classes - is the concept of variables and how they differ by "scope." 

For this post I'll focus on the latter point and try to illustrate how scope is defined across the different kinds of variables available to the Ruby programmer.

* Local variables. Expressed lower case e.g. `var`, `str`, `fido`, `pommes_frites`

* Instance variables. Can start with lower or upper case letters. Can't miss with their prepended '@' sign e.g. `@user`, `@bike`, `@Selfie`

* Class variables. Same rules apply as with their instance cousins, only prettier (or uglier, depending on your pov) with the double '@' signs in front! `@@User`, `@@parcheesi`, `@@Brooklyn`

* Global variables. They're like pawns in chess who make it to the back row: they can be whatever they want, whenever they want (so long as they begin with a '$' sign). Upper case. Lower case. Periods. Colons. Eat your heart out. `$9`, `$!!`, `$foo_bar`, `$AmericasGotTalent`, `$meow`

Now that you see how to tell the variables apart, let's play with some example code to begin distinguishing between each variable's scope.

Let's create a class and create an example of each variable.

	class Verryables
	  print local_var = "local var at class level"
	  p @instance = "instance var at class level"
	  p @@class_var = "class var at class level"
	  p $GlobalVar = "global var at class level"
	end
	
Simple. Run the code and you get exactly what you'd expect. 

	  #=> "local var at class level"
	  #=> "instance var at class level"
	  #=> "class var at class level"
	  #=> "global var at class level"
	  
Now let's define an instance method to see what happens when we ()i) try to print the above class level variables, and (ii) reassign the variables. 

	class Verryables
	  ...
	
	  def instance_method
		p local_var 	#=> results in "undefined local variable"
		p @instance 	#=> returns nil
		p @@class_var
		p $GlobalVar
	  end
	  
	  def second_instance_method
	    puts "second instance method"
		p @instance
		p @@class_var
		p $GlobalVar
	  end
	end
	
What do you think the result would be? If you're new to Ruby, think for a minute about what you expect will happen when we run it…

Survey says:

	#=> "undefined local variable"
	#=> nil
	#=> "class var at class level"
	#=> "global var at class level"
	
	#=> "second instance method"
	#=> nil
	#=> "class var at class level"
	#=> "global var at class level"

Is that what you were expecting? Now let's play around and try to see what happens if we reassign (or define, as the case may be) these variables. 

Here we'll change the messages, print them, and then go back up to the class level and print out the original variables to demonstrate which variables changed and which stayed the same. 

	class Verryables
	  puts ">> class level definitions"
	  p local_var	= "local var at class level"
	  p @instance	= "instance var at class level"
	  p @@class_var	= "class var at class level"
	  p $GlobalVar	= "global var at class level"
	
	  def instance_method
	    puts ">> begin instance method"
		# p local_var (commented out, else "undefined local var" blows up the program)
		p @instance
		p @@class_var
		p $GlobalVar
		puts ">> assigned and reassigned, as the case may be"
		p local_var		= "local var from instance_method"
		p @instance 	= "instance var from instance_method"
		p @@class_var	= "class var from instance_method"
		p $GlobalVar	= "global var from instance_method"
	  end
	  
	  def second_instance_method
		puts ">> second instance method"
		p @instance
		p @@class_var
		p $GlobalVar
	  end
	  
	  def self.class_method
	    puts ">> begin class method"
		# p local_var #=> undefined local variable
		p @instance
		p @@class_var
		p $GlobalVar
	  end
	end
	
The action here will be in the second set of print outs (note: I've added a puts messages at the beginning of each method to help us see what messages are being printed from which method).

Survey says: 


	class Verryables
	  puts ">> class level definitions"
	  p local_var	= "local var at class level"
	  p @instance	= "instance var at class level"
	  p @@class_var	= "class var at class level"
	  p $GlobalVar	= "global var at class level"
	  
	  #=> ">> class level definitions"
	  #=> "local var at class level"
	  #=> "instance var at class level"
	  #=> "class var at class level"
	  #=> "global var at class level"
	
	
	  def instance_method
	    puts ">> begin instance method"
		# p local_var (commented out, else "undefined local var" blows up the program)
		p @instance
		p @@class_var
		p $GlobalVar
		puts ">> assigned and reassigned, as the case may be"
		p local_var		= "local var from instance_method"
		p @instance 	= "instance var from instance_method"
		p @@class_var	= "class var from instance_method"
		p $GlobalVar	= "global var from instance_method"
	  end
	  
	  #=> ">> begin instance method"
	  #=> nil
	  #=> "class var at class level"
	  #=> "global var at class level"
	  #=> ">> assigned and reassigned, as the case may be"
	  #=> "local var from instance_method"
	  #=> "instance var from instance_method"
	  #=> "class var from instance_method"
	  #=> "global var from instance_method"
	 
	  def second_instance_method
		puts ">> second instance method"
		# p local_var #=> undefined local variable
		p @instance
		p @@class_var
		p $GlobalVar
	  end
	  
	  #=> ">> second instance method"
	  #=> "instance var from instance_method"
	  #=> "class var from instance_method"
	  #=> "global var from instance_method"
	  
	  def self.class_method
	    puts ">> begin class method"
		p local_var
		p @instance
		p @@class_var
		p $GlobalVar
	  end
	  
	  #=> ">> begin class method"
	  #=> undefined local variable
	  #=> "instance var at class level"
	  #=> "class var from instance_method"
	  #=> "global var from instance_method"

	end
	
Phew, that's bordering on TL;DR but I hope at least it helps illustrate how each variable responds when changing scopes (in this case, we went from the Class level, down to an instance of the class, and then back up to the Class level).

Here's the definition for each variable, and how the code above illustrates it. 

* **Local variable** (`local_var` in the earlier example). 

    As the name implies, local variables have limited scope - within a method definition, for example. Local variables don’t survive the scope change between class definitions and their inner method definitions. As such, local variable names can be reused in different scopes. 
    
    Using our earlier example, we could use the name `local_var` throughout the program, and so long as each usage was within a different scope, each `local_var` will be treated as completely separate.
    
    That's why, despite having defined a `local_var` at the class level, when we initially called it within our instance method, the result was "undefined local variable." Then within the instance method, we defined a `local_var`, but as the program moved to the class method we again received an "undefined" error. 

    Think of scope as apartments in a building, and your keys as local variables. The key that gets you into one apartment is going to work for another apartment. 

* **Instance variable** (`@instance` in the earlier example)

    Instance variables are only visible to the object to which they belong. An instance variable initialized in one method definition, inside a particular class, is the same as the instance variable of the same name referred to in other method definitions of the same class.

    In our code above, we defined an instance variable `@instance` at the class level, and you can see that when we intitially called it, the return was `nil`. However when we defined `@instance` within instance method, and called it within the second instance method, we demonstrated that `@instance` is the same across both instance methods of the same class. We've established that the `@instance`'s scope encompasses both the class and the instance method. 
    
    Then jumping back to the class level, via class_method, we can see the `@instance` that got printed was the original defined at the top class level. Thus, instance variables share scope across *instances* of the class, but that instance variables do not survive the change in scope from class level to the class instance.

* **Class variable** (`@@class_var` in the earlier example)

    Class variables' scope is shared between a class and instances of that class, yet is not visible to any other objects. Typically, this means class variables are used to share data between class-method definitions and instance- method definitions.
    
    To illustrate this, our example shows how definig our class variable `@@class_var` at the class level, we are then successfully able to call it within the instance method. 
    
    Because `@@class_var`'s scope is shared vertically, we can reassign its value anywhere, and the change in state will be maintained elsewhere in the program. Therefore, when we call `@@class_var` again in the second instance method, the new message is printed, and finally when we call it again in the class method. In the final class method, `@@class_var` didn't change back to the original class level definition, like we saw with the instance variable `@instance`.


* **Global variable** (`$GlobalVar` in the earlier example)

   Within a class, global variables offer the same functionality as class variables. What distinguishes a global variable from a class variables is that global variables are visible all over the program, from within a class to instances of the class, to between classes and objects. 
   
   In the example above, since we've only defined one class, there's no practical dinstinction between how the global variable behaved v. the class variable. 
   
   So let's quickly create a new example, with two distinct classes, to demonstrate how global and class variables differ. 
   
	  class Class1
	    $GlobeTrotter = "Global variable from class 1."
	    p $GlobeTrotter

	    @@ClassVariable = "Class variable from class 1."
	    p @@ClassVariable
	  end

	  class Class2
	    puts ">> calling Class 2"
	    p $GlobeTrotter
	    p @@ClassVariable
	  end

	  c1 = Class1.new
	  c2 = Class2.new
    
	  #=> "Global variable from class 1."
	  #=> "Class variable from class 1."
	  #=> ">> calling Class 2"
	  #=> "Global variable from class 1."
	  #=> uninitialized class variable @@ClassVariable in Class2 (NameError)

There you have it. We've explored bit how scope differs between the four kinds of variables in Ruby. Even though these concepts are quite basic, in my experience as a developer so far, I haven't had many opportunities to use class and global variables (whereas local and instance variables are quite common, particularly in Rails apps), so it's been a helpful exercise in getting it all properly sorted in my head :)

Would love your feedback, and I'd welcome any thoughts or clarifications in the comments below. Jk: since I don't have comments enabled why don't you tweet at me! 
<a href="https://twitter.com/intent/tweet?screen_name=chhhris" class="twitter-mention-button" data-related="chhhris">Tweet to @chhhris</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+'://platform.twitter.com/widgets.js';fjs.parentNode.insertBefore(js,fjs);}}(document, 'script', 'twitter-wjs');</script>