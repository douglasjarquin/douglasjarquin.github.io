---
layout: post
title: Start backing up your Mac to S3 in 5 minutes
date: '2008-08-31T00:00:00-04:00'
tags:
- mac
- s3
tumblr_url: http://douglasjarquin.com/post/1273930477/start-backing-up-your-mac-to-s3-in-5-minutes
---
There are many tutorials out there on how to back up your Mac to Amazon S3, but over time this process has been simplified.

Requisites

Before we get started we will need a few things. Also, make sure you have your Amazon S3 access identifiers at hand. You can get those from your AWS account.

Amazon S3 account
Mac OS X Leopard
Terminal Skills
Back it up

In order to keep this under five minutes I am simply going to list the steps required and not going to really go into any major detail.

First

Install the S3Sync Ruby Gem. Read more about Ruby Gems here.

Second

Add your Amazon access identifiers to the top of your .bash_login file.

Third

Execute the command to backup where my_backup_bucket is the name of your bucket.

I personally do not like to schedule the backups with a cron because every time it runs I am doing something important. I suggest you create an alias for the command in your .bash_login file like this:

Then all you have to do is type backup whenever you want to run this command. Easy.

If the Terminal is not your kind of interface or your just want to backup a few folders of important files, I suggest you go with a full blown S3 file manager. Here are some of the applications I have used.

Applications

Flow
Forklift
S3Fox
Transmit
References

Use Amazon S3 to automatically backup your mac
Automatically backup you Mac to Amazon S3
