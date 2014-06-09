---
layout: post
title: The bash_login file
date: '2008-02-17T00:00:00-05:00'
tags:
- bash
- terminal
tumblr_url: http://douglasjarquin.com/post/1273863856/the-bash-login-file
---
The /.bash_login file is a pretty good place to put your shell paths and variables for Mac’s Terminal. For future reference here is a copy of my .bash_login file:

# Path, Shell variables
export PATH="/usr/local/bin:/usr/local/sbin:$PATH"
export SVN_EDITOR="/usr/bin/mate -w"

# Backpack
alias todo=''ruby /Applications/backpack/todo.rb''

# Finder 
alias ot=''open .''

# General
alias code=''cd Documents/code/''
alias sites=''cd Sites/''
alias backup=''. /Applications/s3backup/backup.sh''

# Git
alias gst=''git status''
alias gu=''git pull''
alias gp=''git push''
alias gd=''git diff | mate''
alias gc=''git commit -v''
alias gca=''git commit -v -a''
alias gb=''git branch''
alias gba=''git branch -a''

# Rails
alias ss=''./script/server''
alias sc=''./script/console''
alias sg=''./script/generate''
alias sp=''./script/plugin''

# Ruby
alias sgi=''sudo gem install''

# s3sync
alias s3cmd=''ruby /Applications/s3backup/s3cmd.rb''

# SSH

# Static Matic
alias sm=''staticmatic''
alias smb=''staticmatic build .''
alias smp=''staticmatic preview .''
alias sms=''staticmatic setup''

# Subversion
alias sup=''svn update''
alias sst=''svn status''
alias scom=''svn commit''
alias sd=''svn diff | mate''
alias slog=''svn log | mate''
alias sex=''svn export''
alias srm=''svn rm''

# TextMate
alias et=''mate .''
alias etr=''mate app config lib db public test vendor/plugins''
