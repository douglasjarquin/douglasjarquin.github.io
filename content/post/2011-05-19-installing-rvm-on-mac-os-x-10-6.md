---
layout: post
title: Installing RVM on Mac OS X 10.6
date: '2011-05-19T16:43:00-04:00'
tags:
- ruby
- rvm
- zsh
tumblr_url: http://douglasjarquin.com/post/5646143798/installing-rvm-on-mac-os-x-10-6
---
I recently got a new MacBook Pro, and haven’t gotten around to installing RVM yet. So when I took on this task today, I was totally surprised buy the issues I faced.

Prerequisites

Git
Terminal chops
Installation

The default installation method is the easiest, so I suggest you follow it. As documented on the official RVM site, just use this one-liner:



That’s it, or so I thought.

Caveats

RVM will likely not work as expected

I kept getting the following error messages:

 

Not exactly sure what is causing it yet, but the solution is to remove RVM, and retry the installation.

 

I actually had to repeat this process four times before I did not see these errors anymore.

Command not found

The next problem I faced was that the rvm command wasn’t in my path. Luckily, I found the executable after a quick search. It lives at:

 

However, simply adding that to your path isn’t the solution. It actually didn’t even work for me. Instead, add the following to your .bashrc or .zshrc, respectively.

Bash

 

ZSH

 

Conclusion

So, my curious side wants to know exactly why this is happening, but I got nowhere. Some have solved the problem by setting some permissions, but that solutions seemed to hacky for me.

Hope it helps.

References

https://gist.github.com/965395
http://episko.posterous.com/brew-zsh-git-and-rvm
http://gabebw.wordpress.com/2010/08/02/rails-vim-rvm-and-a-curious-infuriating-bug/
http://stackoverflow.com/questions/4755538/rvm-is-not-working-in-zsh
