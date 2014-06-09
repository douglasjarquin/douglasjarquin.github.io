---
layout: post
title: Poor man's Git hosting
date: '2011-06-24T22:23:00-04:00'
tags: []
tumblr_url: http://douglasjarquin.com/post/6887909560/poor-mans-git-hosting
---
For those who don’t know me, I am very cheap. Actually, it’s a point of pride, and something I reflect in a positive light. I don’t think it’s bad to be frugal. This is true for the way I host my Git repositories too.

At any given time I have a dozen of so tiny repositories filled with little experiments of mine. Instead of paying $300 a year, I just stick them in my free Dropbox account.

Up

From your git working directory:

 

Then, to push your changes to Dropbox, just run:

 

Obviously, change out master for your branch name. Alternatively, you could set th branch to track from Dropbox by default with:

 

Down

Once your repository lives in Dropbox, cloning it is as simple as:

 

If you want to have a dropbox remote instead of the default origin run:

 

Pushing up changes follows the same steps listed above, and this all works for shared directories, too.

Shout Outs

I can’t take credit for any of this, so below are the multiple sources where I pieced this together from.

http://solutions.treypiepmeier.com/2010/02/22/using-dropbox-to-share-git-repositories/
http://www.cimgf.com/2008/06/03/version-control-makes-you-a-better-programmer/
