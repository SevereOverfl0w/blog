---
layout: post
title:  "Ruby and dependency management"
date:   2014-05-27 11:20:39
tags: [ruby]
---


Coming to Ruby and it's dependency management system has been a little confusing
as it is so very different compared to Python's system.

### Python

Python's "best practices" for dependency management revolve around virtualenv
and pip/easy_install. You create a virtualenv for each environment in a folder
that is usually alongside the projects directory, and then install packages
to that virtual environment using pip. To install a dependency from a  list you

``` $ pip install -r requirements.txt ```

and to make that list just,
``` $ pip freeze > requirements.txt ```

All fairly simple.

### Ruby
Ruby is similar but with a few distinct differences.

Firstly, instead of the virtualenv package, you use [RVM](http://rvm.io).
RVM works by first letting you choose a version of Ruby to install, an example 
for 2.1.2:
``` $ rvm install 2.1.2 ```

You then create a gemset within this version, you can then switch to that,
``` $ rvm 2.1.2 ```

Incredible right? But we don't want to clutter our global 2.1.2 with all
dependencies from every project we ever work on, so we create a gemset whilst
in our target version (Here named jekyll):
``` $ rvm gemset create jekyll ```


This will allow us to swap to 2.1.2 with gemset jekyll:
``` $ rvm 2.1.2@jekyll ```


So now we have an environment just for our jekyll-related dependencies!
To install new gems (The name for a Ruby library), you use the gem command:
``` $ gem install jekyll ```
But this doesn't work so well, for example if we are working in a team, we need
to all be on the same package version, with an easy list to install into any
environment. This is where [Bundler](http://bundler.io) comes in!

Bundler let's you create a Gemfile as below:

~~~ ruby
source 'https://rubygems.org'
gem 'nokogiri'
gem 'rack', '~>1.1'
gem 'rspec', :require => 'spec'
~~~

This specifies a list of dependencies, and where to get them from, for a person
to install these just:
``` $ bundle install ```
Bundle will take care of the rest for you!

The main difference between Python and Ruby in terms of package management
seem to be:

* A more "global" environment in Ruby, not a physical folder you can see and rm
    It's an interesting approach, one that isn't comfy yet, but I assume soon
    will be.
* Segregation of dependency listing and dependency install utilities, again,
    coming from python makes me unsure how I feel about this, but I feel like
    it's something that will soon become natural.
