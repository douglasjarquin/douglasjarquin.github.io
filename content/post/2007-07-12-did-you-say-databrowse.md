---
layout: post
title: Did you say Databrowse?
date: '2007-07-12T00:00:00-04:00'
tags:
- django
- tutorial
tumblr_url: http://douglasjarquin.com/post/1273820532/did-you-say-databrowse
---
Databrowse is a Django application that basically lets you browse your data. You can define which models you want to browse and they are then exposed to Databrowse. Besides being very pretty, Databrowse has come in very handy. And since it is so easy to setup, you can see for yourself in just a few minutes.

Setup

Installing Databrowse is a snap. You could use the documentation, but I want to show you how I did it and save you some time.

First add django.contrib.databrowse to your INSTALLED_APPS setting.

{% highlight python %}

Add ‘django.contrib.databrowse’ to your INSTALLED_APPS

''django.contrib.databrowse'',
{% endhighlight %}

Now you need to register your models with Databrowse. I did this in my root urls.py, however I plan to try to move the code in to the individual apps once I can figure out how.

# Import your model classes in your root urls.py
from apps.blog.models import Entry


Now we register those models with Databrowse.

# Register your models with Databrowse 
# I put this right after my import statements
# Entry corresponds with ''from apps.blog.models import Entry''
databrowse.site.register(Entry)
databrowse.site.register(Project)


Last but not least you need to give your Databrowse app a url.

# You can give it any name you wish
(r''^databrowse/(.*)'', databrowse.site.root),


Now visit your Databrowse url and enjoy looking inside your data.
