---
layout: post
title: Subversion on Media Temple
date: '2007-10-28T00:00:00-04:00'
tags:
- media temple
- subversion
tumblr_url: http://douglasjarquin.com/post/1273855172/subversion-on-media-temple
---
Using Subversion on the Media Temple Grid-Service is much easier than it seems. Actually, it is easier than my previous host.

Setup the repository

ssh serveradmin%domain.com@domain.com **OS X 
Terminalserveradmin@domain.com **Windows
cd data
mkdir svn && cd svn
svnadmin create --fs-type fsfs reponame


Initial import

On your local machine.

mkdir reponame && cd reponame
mkdir trunk
mkdir tags
mkdir branches
svn import . svn+ssh://serveradmin%domain.com@s#####.gridserver.com/home/#####/data/svn/reponame/ -m "Initial import"


Checking out

Now that we have our subversion repository setup and our code checked in, we should check out a copy for development.

svn co svn+ssh://serveradmin%domain.com@s#####.gridserver.com/home/#####/data/svn/reponame/trunk reponame


Deployment

If you are going to deploy your website from a local subversion repository.

ssh serveradmin%domain.com@domain.com **OS X Terminalserveradmin@domain.com **Windows
cd domains
cd domain.com
mv html html-2
svn co file:///home/#####/data/svn/reponame/trunk html


That does it. Rinse and repeat as needed.

References

Setup a Subversion repository
A Novices Tutorial on Subversion
