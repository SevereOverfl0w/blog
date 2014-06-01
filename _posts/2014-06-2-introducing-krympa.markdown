---
layout: post
title:  "Introducing Krympa"
date:   2014-06-02 15:18:10
tags: [python, pyramid]
---

I have just finished building 0.0.0 of Krympa, my URL shortener built in Pyramid
/Python. It was an interesting experience. I based a lot of the code on
Flask-Dwarfr, my Flask based URL shortener.

From an outwards view, Flask was MUCH simpler to implement and design, the code
was also significantly cleaner. But that doesn't take into account that I had
a lot of helper libraries in Flask, in Pyramid, I went it alone, opting **NOT**
to use supporting libraries.

This is partially due to me wanting to implement Krympa a little differently to
before, I wanted to be able implement an API so that applications could hook
into my URL shortener easily. This meant I had to implement some kind of system
for error handling, the resulting code was fairly ugly looking, but for now it
works. I am going to review my choice of JSON output now that I have implemented
a javascript API for it.

The JSON decision I made was that a basic structure should always be kept:

~~~
{'status': 'string', response: {}}
~~~

This structure would allow for easy first-level serialization of the object,
for where you MUST know the structure of the JSON. It allows me to do things
such as the following:

~~~
{'status': 'error', response: {'errmsg': 'You fail whaled'}}
~~~

The above JSON will at a first level, ALWAYS serialize in this format:

~~~
{
	status: string,
	response: JSONObject
}
~~~

I could then do an condition on the status for either success, or error, to 
interpret response appropriately, as I will (theoretically, if documentation is
good), know exactly what parameters will be returned by my API call.

The alternative is to do as follows for an error do:

~~~
{
	'errmsg': 'You fail whaled'
}
~~~

and for success:

~~~
{
	'url': 'http://s.lycantech.co/3axBc'
}
~~~

This makes error checking harder in some ways, some languages may enforce some
kind of exception or errror when attempting to access an index that doesn't
exist, so your code goes from (Python represented):

~~~
if decoded['status'] is 'success':
	url = decoded['response']['url'] #Being assumptious!
	print(url)
elif decoded['status'] is 'error':
	print("Oh no: ", decoded['response']['errmsg']) #Being assumptious!
~~~

to

~~~
try:
	url = decoded['url']
except KeyError: #Python's This-isn't-an-index
	print("Oh no: ", decoded['errmsg']) #Being assumptious!
else:
	print(url)
~~~

I feel like the take away is: Is it better to ask permission, or forgiveness
when coding? Theoretically my original JSON design allows for the exception
based logic present in many languages also, just with slightly different
indexes. So I'm going to stick with it.


---

Future features for Krympa:

+ Pluggable storage classes (Hayo SQLAlchemy!)
+ Code refactor (See above)
+ Grunt/Bower/Yeoman integration for easier frontend dev
+ (Possibly), install scripts and guides.