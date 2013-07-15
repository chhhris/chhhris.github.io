---
layout: post
title: "Open Source: How to Git Started"
date: 2013-07-14 23:22
comments: true
categories: 
---


# Open Source is Super Easy
### `<h2>`
### Contributing to Open Source projects is EZ ;)
### `</h2>`


There are loads of ways to contribute to your favorite open source projects. I list out a bunch of them below. 

I'll also discuss how I ate my own dog food, mostly because I love using that expression. Altho I was actually pretty excited to submit my first open source pull request.

***

## Gitting started.

Working on any open source project on GitHub is just as easy as working on your own team projects. If you know how to use GitHub, you know how to contribute to open source. 

Take Ruby, for example. To paraphrase the rubyist [Mike Perham](http://www.mikeperham.com/2010/12/08/contributing-to-ruby/) (who you probs don't read but definitely should), Ruby Core has made contributing as simple as:

1. **Fork the Ruby repo** - <http://github.com/ruby/ruby>
2. **Commit changes to your repo** -- e.g. <https://github.com/chhhris/ruby>
3. **Submit a pull request** - GitHub has a great primer at <https://help.github.com/articles/using-pull-requests>

***

## Ways to contribute.
I think it's fairly common knowledge that you don't have to be a prodigy to contribute to meaningful open source projects. And that's especially true because there are so many ways to contribute. 

I've adapted [Andy Lester's post](http://blog.smartbear.com/programming/14-ways-to-contribute-to-open-source-without-being-a-programming-genius-or-a-rock-star/) on Smart Bear to list some easy, helpful ways to get involved with Ruby. 

### Stay informed

* **Join a mailing list** - 

Ruby Weekly produces a very informative and engaging weekly newsletter - sign up at <http://rubyweekly.com/>.
![RubyMeetup](/images/ruby-weekly.png)
The official mailing lists are maintained here - <http://www.ruby-lang.org/en/community/mailing-lists/>

* **Join a user group** - 

Ruby has a dedicated [Meetup.com page](http://ruby.meetup.com).
![RubyMeetup](/images/ruby_meetup_com.png)

* **Follow dedicated blogs** - 

There are several active, dedicated Ruby blogs. Ruby Source is a particularly good one - http://rubysource.com/
![RubyMeetup](/images/ruby-source-blog.png)

* **Join an IRC channel** -

IRC is confusing at first glance so I'll have to spend some more time looking into it. 
![RubyMeetup](/images/irc-ruby.png)

### Review open tickets

* **Troubleshoot and add detail to open bugs** -
* **Close old bugs that have been fixed** -

You'll need an account in order to review, edit and submit bug reports: <https://bugs.ruby-lang.org/projects/ruby/wiki/HowtoReport>
![RubyMeetup](/images/bug-tracking.png)

### Code

* **Test a beta or release candidate**
* **Fix a bug**
* **Write a test**

### Contribute to the community

* **Improve Documentation**
* **Answer a question**
* **Improve the project website**

***

## Let's do it.

This last idea - improving the project website - is where I ended up getting my foot in the door. I was perusing Ruby's official website and found a couple links to resources on del.icio.us that had, well, gone stale. 

My first step was to locate the source code for Ruby's official website. After a few minutes scouring the main Ruby repo in vain, I discovered that the project website is, logically, maintained on a separate repo: <https://github.com/ruby/www.ruby-lang.org/>.

![RubyMeetup](/images/ruby-lang-github.png)

Before making any edits, I went to the project's Readme file for any instructions. First thing was a link to a Wiki page entitled ["Guidelines for Contributors."](https://github.com/ruby/www.ruby-lang.org/wiki)

The guidelines were very clear and straightforward. Basically, the Ruby-Lang site is built on Jekyll and they suggest most edits/contributions/etc be made as edits directly on the GitHub hosted page (as opposed to cloning the repo, making changes locally, and pushing back to the remote). 

![RubyMeetup](/images/ruby-lang_community-weblogs_github-edit.png)

The project owners had specific instructions for how you should describe your work when submitting the pull request. Bottom line, they ask you to be crystal clear about 1) what page you're working on, and 2) which language version (as the site is maintained in many languages around the world).

The body text is optional. 

![RubyMeetup](/images/ruby-lang_github-submitting-pull-request.png)

And that's it! Even though it was such a minor contribution on a relatively obscure page, the main objective for me was to de-mystify and better understand the logistics for submitting to an open source project. And I'm so glad I did, because it's a lot simpler than I imagined!

Below is a screenshot of pending pull requests for the ruby-lang.org website. You can see yours truly at the top of the list ;)

![RubyMeetup](/images/ruby-lang_github-pull-requests.png)

`</end>`

### Postscript:

A couple hours after I submitted the pull request I heard back from a couple team members..

![RubyMeetup](/images/ruby-lang-response.png)




