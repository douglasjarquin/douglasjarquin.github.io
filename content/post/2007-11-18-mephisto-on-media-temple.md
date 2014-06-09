---
layout: post
title: Mephisto on Media Temple
date: '2007-11-18T00:00:00-05:00'
tags:
- media temple
- mephisto
- rails
tumblr_url: http://douglasjarquin.com/post/1273846775/mephisto-on-media-temple
---
At $20 a month, Media Temple’s Grid-Service is an incredible bargain. I recently broke up with Django and decided to move my work back to Ruby on Rails. What follows is another tentative guide to installing Mephisto on Media Temple’s Grid Service.

First things first

Enable Rails container

Log in to your (mt) account center and select your primary domain.
Click into the “(gs) GridContainers” section.
Click the “manage” link for the Rails GridContainer.
Click ‘Enable Container’.
Note: You will need about 45 MB of ram dedicated to Mephisto.

Create the database

Click into the ‘Manage Databases’ section.
Click the ‘Add A Database’ tab.
Give your database a name and select a database type.
Click ‘Next’.
Setting up Ruby on Rails

ssh serveradmin%domain.com@domain.com **OS X Terminal
serveradmin@domain.com **Windows
mtr generate_config **serveradmin@domain.com and password
mtr setup_rubygems
source ~/.bash_profile
gem install rails -y
gem install mysql --source=http://gems.mediatemple.net
gem install postgres --source=http://gems.mediatemple.net\r\ngem install daemons gem_plugin -y
gem install mongrel --source=http://gems.mediatemple.net


Install Mephisto

cd $HOME/../../containers
mkdir rails &amp;&amp; cd rails
svn co -r 2920 http://svn.techno-weenie.net/projects/mephisto/trunk mephisto
cd mephisto
gem install tzinfo --remote
cp config/database.example.yml config/database.yml


Note: Here we checkout revision 2920 instead of the head. 2920 is the latest revision of Mephisto to work without rails edge, although the 0.7.3 release was revision 2501.

Initialize Mephisto

rake db:bootstrap RAILS_ENV=production
mtr add mephisto $PWD domain.com
mtr start mephisto
mtr generate_htaccess mephisto
mtr create_link mephisto domain.com


Note: We do not have to manually create the log directory. It is automatically created when we rake the db.

That’s it! Now visit yourdomain.com to see our result.

References

Mephisto on Media Temple
Initial Setup of Ruby on Rails on (RoR) Container
