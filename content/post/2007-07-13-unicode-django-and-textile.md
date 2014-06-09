---
layout: post
title: Unicode Django and Textile
date: '2007-07-13T00:00:00-04:00'
tags:
- django
- textile
tumblr_url: http://douglasjarquin.com/post/1273836193/unicode-django-and-textile
---
Thanks to Django’s great unicode support which merged on July 4 a textile error has emerged. Luckily, there is a remarkably simple fix.

The problem

You used to be able to do this:

textile.textile(self.body)


But that would lead to this error:

''ascii'' codec can''t decode byte 0xb4 in position 0: ordinal not in range(128)


This happens because textile is trying to map 8-bit ASCII code into HTML numerical entity equivalents, but it is not receiving ASCII.

The Fix

So now you have to do this:

textile.textile(str(self.body))


Honestly, I am not 100% sure why this works but it does. I plan on investigating a little further to find a definite answer but my current guess is that str() gives us the ASCII encoding we need.
