---
layout: post
title: "JavaScript Closures"
date: 2013-08-27 23:46
comments: true
categories: 
---

# Closures in JavaScript
## What are JavaScript closures?

A closure is a kind of object that combines two things: 

1. a function
2. that function's environment

The function's environment consists of any local variables that were in-scope at the time that the closure was created.

### How do you create a closure in JavaScript?

Simply, in JavaScript, if you use the function keyword inside another function, you are creating a closure. 

As such, local variables remain accessible after returning from the function you called; the inner function still has access to the outer function’s variables even after the outer function has returned.

Here's an example of a simple closure in JavaScript:

	<script>
	
	var sayHello = function alertGreeting(name){
  		var greeting = "Hello";
  		function displayName() {
    		alert(greeting + " " + name);
  		};
  		displayName();
	};
	
	sayHello("Chris");

	</script>

[Sample the code on JS Fiddle](http://jsfiddle.net/chhhris/ee46b/)

There's a lot, lot more on closures but I just wanted to get the basic definition down. If you want to go deeper, here are a few resources to get you started.

* Mozilla Developer Network [post on JS closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Closures).
* Best real-world example utilizing JS closures I've found, MDN's [example on JS Fiddle](http://jsfiddle.net/vnkuZ/).
* Interesting, albeit a bit too *bubbly*, post on [JavaScript Is Sexy](http://javascriptissexy.com/understand-javascript-closures-with-ease/).