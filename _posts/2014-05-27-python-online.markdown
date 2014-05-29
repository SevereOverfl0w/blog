---
layout: post
title:  "The state of Python on the web"
date:   2014-05-27 11:20:39
tags: [python, web]
---

There are 3 main levels of python web framework. The big (Django), the micro
(Flask) and the inbetween (Pyramid).

## Django

Django is a powerful framework, many compare it to RoR, but I'm not sure how
true this fact is. Django is gaining a lot of momentum, but I still feel like
it has a long way to go. Django's admin interface is incredible for quickly
building an interface to debug models, and allowing admins to control aspects
of the site. It also has a great multitude of libraries which you can drop into
 a project very quickly, my favourites include: Django REST framework,
Django-Guardian, and Django-allauth. But there are so many great extensions.

The real problem with Django (And it's third-party libraries!), are it's high
opinionation. I've always felt there was a balance to be found between high and
 low opinionation. In this case Django is off the chart, if you want to do
something Django hasn't considered you'd do, you're quickly going to feel like
you're surrounded by sharks. You very quickly begin fighting the framework,
overriding functions, making 'dirty' fixes, and it often feels like you spend
a long time finding out how to override default behaviour you don't like,
instead of working on your product, which is what makes you happy.

## Flask

Flask is a great framework. I love using it, it gets out of my way, and let's
me concentrate on the task at hand, instead of making me fight the framework.
I very often use it for prototyping a new idea or concept to see what kind of
road blocks there may be when an idea is practically implemented.

The best part of Flask is being able to pick and choose my own components, I
have often found Django's ORM to be great, but not the best. SQLAlchemy is the
single greatest ORM known to python. I can use it with Flask, but not with
Django (Well, not without giving up the parts of Django that make it Django)

The real issues with Flask came when I started to try and use it for bigger
projects, it just isn't up to the task. I would mainly put this down to how
young it is as a project. The supporting libraries one would use to build a
big website just aren't all there yet. But as time goes on, libraries will
mature and the framework will too, until turning Flask into Django is a case
of installing a library or two with pip.

## Pyramid

Pyramid is in the middle, and currently is one of my favourites. It let's me
use SQLAlchemy, Wtforms, Colander, any library I please, effortlessly.
In usage, it's very similar to Flask, highly unopinonated, get's out of my way,
and let's me concentrate on the task at hand, great! However, it goes a little
further than Flask does, it features a few higher level features such as
an extensible authorization framework. But it's unopinonated and
flexible, allowing me to do more with them than with Django.

This continues onto the third party libraries. They're all so flexible, yet
there's a lot of common usage pattern related things in all of the libraries.
I have found that patterns I like to utilize (Particularly Classes for making
generic views to get me going quicker), aren't always available to me, which
can be awkward. I think the biggest problem with Pyramid, is it's lack of
an active community. Compared to Flask & Django's, it's extremely quiet,
making sometimes obscure problems hard to solve. Pyramid isn't a cool
microframework like Flask, or a heavy hitter like Django, and that puts it in
an awkward position for grabbing attention from people looking for a type
of framework.

All in all, I feel like Pyramid is the best and most promising framework, 
 given enough third party libraries that continue the current trend of
 flexibility, it can be the best micro & large framework!
