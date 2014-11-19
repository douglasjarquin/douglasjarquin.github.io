---
layout: post
title: Beast on Media Temple
date: '2007-10-17T00:00:00-04:00'
tags:
- beast
- rails
- media temple
tumblr_url: http://douglasjarquin.com/post/1273839841/beast-on-media-temple
---
What follows is a tentative guide to installing Beast, a forum application written in Ruby on Rails, on Media Temple Grid-Service.

First things first

Enable Rails container

Log in to your (mt) account center and select your primary domain.
Click into the “(gs) GridContainers” section.
Click the “manage” link for the Rails GridContainer.
Click “Enable Container”.
Note: You will need about 35 MB of ram for Beast.

Create database

Click into the “Manage Databases” section.
Click the “Add A Database” tab.
Give your database a name and select a database type.
Click “Next”
Setup email

You must have a beast@domain.com user setup for sending activation emails.

Setting up Ruby on Rails

ssh serveradmin%domain.com@domain.com **OS X Terminal
serveradmin@domain.com **Windows
mtr generate_config **serveradmin@domain.com and password
mtr setup_rubygemssource ~/.bash_profile
gem install rails -y
gem install mysql --source=http://gems.mediatemple.net
gem install postgres --source=http://gems.mediatemple.net
gem install daemons gem_plugin -y
gem install mongrel --source=http://gems.mediatemple.net


Installing the Beast

cd $HOME/../../containers
mkdir rails &amp;&amp; cd rails
svn co -r 2873 http://svn.techno-weenie.net/projects/beast/trunk beast
cd beast
gem install RedCloth
gem install ruby-openid
cp config/database.example.yml config/database.yml


Note: Instead of installing beast from the stable 1.0 branch we checkout revision 2873 from the trunk. This way we can update to stable versions of the trunk without having to worry about merging branches. Stable 1.0 is actually revision 2907, but I have not been able to install it successfully.

Edit database.yml

production:
adapter: mysql
database: db#####_beast_production
username: db#####
password: xxxxxxx
host: internal-db.s#####.gridserver.com


Edit environment.rb

Add your email settings to the end of the beast/config/environment.rb file.

# email settings
ActionMailer::Base.smtp_settings = {
  :address =&gt; "mail.domain.com",
  :port =&gt; 25,
  :domain =&gt; "domain.com",
  :authentication =&gt; :login,
  :user_name =&gt; "beast@domain.com",
  :password =&gt; "xxxxxxx"
}


Initialize Beast

rake db:schema:load RAILS_ENV=production
mtr add beast $PWD domain.com
mtr start beast
mtr generate_htaccess beast
mtr create_link beast domain.com


References

Mephisto on Media Temple
Initial Setup of Ruby on Rails on (RoR) Container
Sending Mail with Ruby on Rails
Getting Started with Beast
You can now see a working example by visiting http://yourdomain.com.
