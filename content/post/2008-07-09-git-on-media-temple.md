---
layout: post
title: Git on Media Temple
date: '2008-07-09T00:00:00-04:00'
tags:
- git
- media temple
tumblr_url: http://douglasjarquin.com/post/1273916314/git-on-media-temple
---
Unless you have been sleeping under a rock, which I hear is good for your health, you have come to hear about Git. Originally created by Linus Torvalds, Git is an open source version control system that has quickly gained a lot of traction with Rails developers. This could be credited to the great GitHub, but I think it is because of Git’s feature set. Visit the office Git website to learn more.

At $20 a month Media-Temples Grid-Service is an incredible bargain. I make extensive use of all of it features, including the recently added ability to host Git repositories. What follows is a tutorial on how to host your Git repositories on Media Temple’s Grid-Service from Mac OS Leopard.

Prerequisites

Git 1.5.6.2
Mac OS X Leopard
Terminal Skills
There are binaries available for installing Git on Mac OS X. Visit the git-osx-installer project on Google Code.

Domain

In order to be able to clone your repositories from the Grid over HTTP you need to create a domain specifically for Git. You can setup git.domain.com, but any domain will do. Remember to setup the domain in your Grid account. Without this you will only be able to clone Git repositories over ssh which is a pain.

The project

We are going to setup an example project called icecream-man. Change into a directory that is safe to work in and let’s get to it. If you already have a Git project setup you can skip this section.

# This is where I keep all of my projects
cd Sites/
mkdir icecream-man
cd icecream-man
git init
touch .gitignore
git status
git add .
git commit -v -a


Attack of the Clones

Before we can push our local Git repositories to the Grid we have to create a bare clone. A short aside about what git means by bare: A default git repository assumes that you’ll be using it as your working directory, so git stores the actual bare repository files in a .git directory alongside all the project files. Remote repositories don’t need copies of the files on the filesystem unlike working copies, all they need are the deltas and binary what-nots of the repository itself. This is what bare means to git. Just the repository itself.

cd Sites/
git clone --bare icecream-man icecream-man.git
touch icecream-man.git/git-daemon-export-ok


Upload the repository

To get the project on our Grid I use scp, but you could just as easily FTP the icecream-man.git directory into your Grid account.

scp -r icecream-man.git serveradmin%s#####.gridserver.com@s#####.gridserver.com:domains/git.domain.com/html/icecream-man.git


Now we have to ssh into our Grid account and finalize the setup.

ssh serveradmin%s#####.gridserver.com@s#####.gridserver.com
cd domains/git.domain.com/html/icecream-man.git
git --bare update-server-info
chmod a+x hooks/post-update


Pulling

Now we are ready to clone our Git repository from our Grid account. We are able to clone using a pretty URL thanks to our Git specific domain. Yeah!

git clone http://git.domain.com/icecream-man.git


Pushing

Once you have made some local commits that you want to push to the Grid you can use this command:

git push ssh://serveradmin%s#####.gridserver.com@s#####.gridserver.com/home/#####/domains/git.domain.com/html/icecream-man.git master


Here is what I do so that I do not have to type in that long command every time I want to push my changes to the remote Git repository. Git allows for each project to have multiple tracked repositories. Since we cloned our project from http://git.domain.com/icecream-man.git Git thinks it can push there to. Let’s add another remote repository and tell Git to push our changes there.

cd Sites/icecream-man/
git remote add grid ssh://serveradmin%s#####.gridserver.com@s#####.gridserver.com/home/#####/domains/git.domain.com/html/icecream-man.git


Now we can push changes to our Grid account using git push grid master. Git knows that the remote repository named grid corresponds to the Grid’s push URL. Much better, I know. We can take this even further and create an alias for the command in our “.bash_login" file. To view the available remote locations type "git remote" from inside the project directory. Then you can view the details of a remote repository by typing "git remote show grid”. I use this very heavily, and am successfully hosting six active Git repositories on my Grid account. Without this tiny shortcut I do not think I would be able to do it, and I would be GitHub bound.

References

Using Git on the (gs) Grid-Server
Git Documentation
Setting up a new remote git repository
