---
layout: post
title: "A simple expanation of how the NSA program PRISM works"
date: 2013-06-11 08:44
comments: true
categories: 
---

## Or, how the author of the infamous top-secret PPT presentation has clearly never seen the inside of a SQL table.

When [The Guardian](http://www.guardian.co.uk/world/2013/jun/07/prism-tech-giants-shock-nsa-data-mining) broke the story of the US Government's digital intelligence gathering operation (code named "PRISM"), the oft-quoted line from the Top Secret presentation an NSA analyst gave to his colleagues was that the NSA had "direct access" to the servers at Google, Microsoft, Facebook, Yahoo!, Apple, among others (with Dropbox "coming soon" and Twitter [conspicuous by its absence](http://www.avc.com/a_vc/2013/06/feature-friday-standing-up-for-your-users.html)). 

The response from these tech companies was swift and [unequivocal](http://www.guardian.co.uk/world/2013/jun/07/prism-tech-giants-shock-nsa-data-mining). Turns out the NSA doesn't actually tap directly into the servers at these companies; instead, it has computers on-site to which NSA analysts post queries. The NSA computers then download the relevant data.

The imprecision of the NSA's presentation is clearly, obviously due to the fact that the author has never performed a SQL JOIN on two tables in a database tables!

In short, the way the PRISM works is the NSA collects as much data - every Google search, email, FB post and Verizon phone call - it can get its hands on. The NSA then cross-references this huge mountain of data with lists of known or suspected terrorists, persons of interest, et al. In other words, the NSA data analysts perform an [INNER JOIN](http://www.codinghorror.com/blog/2007/10/a-visual-explanation-of-sql-joins.html) on the two tables! 

Here's a neat visualizing from [Seldom Matt](http://blog.seldomatt.com/blog/2012/10/17/about-sql-joins-the-3-ring-binder-model/):

![Image of "binder method" for visualizing and inner join](http://25.media.tumblr.com/1702c57a6fd3a1048d1ab062d2cff590/tumblr_mo8cqssYw01qd3p27o1_500.png)