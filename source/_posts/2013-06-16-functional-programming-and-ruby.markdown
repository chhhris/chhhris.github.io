---
layout: post
title: "Functional Programming and Ruby"
date: 2013-06-16 18:43
comments: true
categories: 
---

# Functional Ruby

Functional Programming ("FP") wasn't on my radar until I started hacking at The Flatiron School two weeks ago (and by _hacking_ I mean as in a _hacking cough_ :). 

Since my ego is super attracted to highbrow challenges and feeling intellectually superior, when I heard that FP was baller status because it's both exceedingly powerful and exceedingly difficult to master, my interest was piqued. When I saw this speakerdeck presentation from Pat Shaughnessy ((["Get yo ass down to O'Shag Hennessy!" "Who?" "O'Shag Hennessy!!" "Principal O'Shaughnessy???"](http://www.youtube.com/watch?v=Dd7FixvoKBw))) analyzing Ruby's relationship to FP I was like, "challah!"

And here it is:

<script async class="speakerdeck-embed" data-id="f6c17b106e0a0130b5df22000a1e9b3c" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

## Anyway what is functional programming?
+ higher order functions
+ lazy evaluation ([def.](http://en.wikipedia.org/wiki/Lazy_evaluation)_delays the evaluation of an expression until its value is needed (non-strict evaluation) and which also avoids repeated evaluations. _)
+ memoization ([def.](http://en.wikipedia.org/wiki/Memoization)_an optimization technique used primarily to speed up computer programs by having function calls avoid repeating the calculation of results for previously processed inputs._)

### A few more takeaways from this presentation #=> 

+ One of the coolest factoids is a screenshot of an old-school email from Matz to another developer explaining that Ruby might best be thought of MatzLisp.

[id]: http://24.media.tumblr.com/6723cfa607a806c3bd52664edc56a83f/tumblr_moicu2vmgC1qd3p27o1_1280.png  "Screenshot of email from Matz explaining how he invented Ruby"

+ Ruby, and in particular Ruby 2.0, has a lot of functional features. 
+ Ruby and Haskell can resemble each other, but only on the surface.

[id]: http://25.media.tumblr.com/86c92e5b13db2b2d04808348f504d3ad/tumblr_moijcsUUqR1qd3p27o1_1280.png "Screenshot comparing Haskell and Ruby functions"

+ Under the hood, Ruby's support of functional features is limited.


### What I'm still scratching my head about... 

+ Could've used Pat's commentary around a few of the slides. 

In the example below, I can't tell if he's saying "This Ruby code doesn't work but this is what it would look like, _in theory_, if Ruby were truly on par with Haskell" (hence the NoMethodError on the following slide). Huh??

[id]: http://25.media.tumblr.com/b5c202e103b09ab356a696973b339a2d/tumblr_moik72Ti7L1qd3p27o1_1280.png "Slide comparing Ruby and Haskell code"

[id]: http://25.media.tumblr.com/8293e19ad17d09ddee1d5ea5f19dbda7/tumblr_moik72Ti7L1qd3p27o2_1280.png "Next slide showing the Ruby code resulting in NoMethodError"

+ 





