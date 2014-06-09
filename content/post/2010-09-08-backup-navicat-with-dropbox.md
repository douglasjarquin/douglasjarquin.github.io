---
layout: post
title: Backup Navicat with Dropbox
date: '2010-09-08T16:01:00-04:00'
tags:
- tips
- navicat
- dropbox
tumblr_url: http://douglasjarquin.com/post/1091826229/backup-navicat-with-dropbox
---
I recently started using Navicat for MySQL as my Mac database administration application of choice, and quickly wondered how I could back up my data. Particularly, Navicat has a great query interface, and in a few days I compiled 27 queries that I really did not want to have to rebuild.

Without over engineering a solution, and since there is no sensitive data to worry about as passwords are stored in Keychain, I decided to backup with Dropbox (referral link). I couldn’t move the directory into my Dropbox directory, which is my preferred method, so I went the symlink route.

 Note: Replace the word username above with your username.
