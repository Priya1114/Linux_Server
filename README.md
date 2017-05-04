# Linux_Server

Project 7 under the Full Stack Web Developer Nanodegree at Udacity:

public Ip: 54.205.252.64

SSH PORT: 2200

User: grader

Tasks given and method for completion:

.Start a new Ubuntu Linux server instance on Amazon Lightsail.
.You will get your respective public and private IP address and key_pair as well.

Create a new user named grader

.sudo adduser grader

.Give sudo access to grader.
   $ sudo nano /etc/sudoers.d/grader
Add the following text to the the newly created file:
   grader ALL=(ALL:ALL) ALL
   
Update all currently installed packages

.sudo apt-get update
.sudo sudo apt-get upgrade   

. Setup SSH keys for grader.
  $ ssh-keygen -t rsa
  
  Source:https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2
  
 . Enforce key-based authentication | Change the SSH port from 22 to 2200 | Disable login for root user.
    $ nano /etc/ssh/sshd_config 
    $ sudo service ssh restart
    
 . Change timezone to UTC.
      $ sudo timedatectl set-timezone UTC
      
 . Configure the Uncomplicated Firewall (UFW)

  $ sudo ufw default deny incoming
  $ sudo ufw default allow outgoing
  $ sudo ufw allow 2200/tcp
  $ sudo ufw allow www
  $ sudo ufw allow ntp
  $ sudo ufw enable
  
  . Install and Configure Apache2 and mod-wsgi and Git
    $ sudo apt-get install apache2 libapache2-mod-wsgi git
    $ sudo a2enmod wsgi
  . Install and configure PostgreSQL
    $ sudo apt-get install libpq-dev python-dev
    $ sudo apt-get install postgresql postgresql-contrib
    $ sudo su - postgres
    $ psql
    
Create a new User named catalog: # CREATE USER catalog WITH PASSWORD 'password';

Create a new DB named catalog: # CREATE DATABASE catalog WITH OWNER catalog;

Connect to the database catalog : # \c catalog

Revoke all rights: # REVOKE ALL ON SCHEMA public FROM public;

Lock down the permissions only to user catalog: # GRANT ALL ON SCHEMA public TO catalog;

Log out from PostgreSQL: # \q. Then return to the grader user: $ exit

.Create flask app :https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps

Install Flask and other dependencies

  $ sudo apt-get install python-pip
  $ sudo pip install Flask
  $ sudo pip install httplib2 oauth2client sqlalchemy psycopg2 sqlalchemy_utils
  
.Clone the Catalog app from Github

Make a catalog named directory in /var/www
  $ sudo mkdir /var/www/catalog
Change the owner of the directory catalog
 $ sudo chown -R grader:grader /var/www/catalog
Clone the Project_Catalog from github to the catalog directory:
 $ git clone https://github.com/CPriya14/Catalog_Project

 Restart Apache to launch the app

 $ sudo service apache2 restart 
    
