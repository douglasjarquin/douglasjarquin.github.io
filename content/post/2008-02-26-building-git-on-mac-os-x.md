---
layout: post
title: Building Git on Mac OS X
date: '2008-02-26T00:00:00-05:00'
tags:
- git
- mac
tumblr_url: http://douglasjarquin.com/post/1273868506/building-git-on-mac-os-x
---
You have surely heard of the latest thing to happen to version control. Git, written be Linux creator Linus Torvalds, is a popular version control system designed to handle very large projects with speed and efficiency. Installing Git on Mac OS X Leopard is actually pretty simple and blazingly fast. It installed so quickly I thought it was a mistake.

Prerequisites

Mac OS X 10.5 Leopard (untested in Tiger)
Xcode 3.0
Terminal skills

Set Options since we don’t have GNU gettext installed

export TCL_PATH=/usr/bin/tclsh
export NO_MSGFMT=1
With those environment variables set we can move on to building Git.

# Get and Install Git
curl -O http://kernel.org/pub/software/scm/git/git-1.5.6.2.tar.bz2
tar xjvf git-1.5.6.2.tar.bz2
cd git-1.5.6.2/
./configure
make
sudo make install
cd


That’s it, enjoy.

Reference

Git
Updates

July 9, 2008: Git binaries are now available from the official git-osx-installer Google Code project.
