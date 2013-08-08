---
layout: post
title: "The difference between procs, blocks and lambdas"
date: 2013-08-06 11:07
comments: true
categories: 
---

# Procs, blocks and lambdas: Closure in Ruby

Closures allow declarative programming languages - that do not normally maintain state - to persist data. Note, closures are found in JavaScript, Ruby, and many/several (?) other languages. 

Closures appear in Ruby in the form of Procs, blocks and lambdas. All three share the same core feature, which is that they let you take blocks (loops and iterations) and save them as a function. This function can then be passed as an argument to other methods and functions. 

***

Examples of blocks include … [ collect? map? #=> not sure]

Procs are a class. They can be created in 3 ways. Proc.new also as an argument (proc {|n| n.operation }) and ONE OTHER WAY.

Lamdbas are like prods only they are saved as a method. They can be created the same as #2 above e.g. (lambda {|n| n.operation })

***

Procs and lambdas behave differently upon being returned. As soon as procs are returned, they will escape the function. 

   * So if you have a nested loop but call return in the inner loop, as soon as the proc hits the function is escaped and that value is returned, so any additional return values in the outer loop will not be called. 

Whereas a lambda will let the function continue after the return value, until the whole function has been run. 

Possible downside with lambdas is that they can leak memory. This happens when local variables, which would normally be garbage collected by Ruby's native gc, are instead persisted by their [ association ?? ] with the lambda. 

## Resources for further reading:

1. Skorks (two posts -- on closures and procs / lambdas)
2. Rubyist thing
3. JavaScript 101 is garbaggio #=> find something better. 