php_timeclock_fixed
===================

PHP Timeclock Fixed

This is a fixed version of PHP Time Clock 1.04, found here: 

http://timeclock.sourceforge.net/install.php

It was broken, mostly an effect of too much time passing, and MySQL deprecating a few
things that the original software used. 

Anyhow, here's the instructions for installation.

** Testing is done on Ubuntu Server 14.04 LTS, with the latest versions of MySQL, PHP, 
and Apache from the official Ubuntu repos, though there is no reason this software 
shouldn't work on any php stack.

1. Create a MySQL database for this application. The database name used in the example 
below is timeclock, but you can name it whatever you want... Just be sure to record it. 

	mysql -uroot -e "create database 'timeclock'"

2. Create a MySql user for phptimeclock to interact with your database. 

a. Enter the MySQL interactive prompt
	
	mysql -u root -p
	
b. Run the below command to create your new user. The user I'm making here is 
"sqltimeclock". You can make yours whatever you want, just be sure to record it. This is 
also where you set that user's password, so be careful. The password in this example
is "PHPT1ME!"
	
	CREATE USER 'sqltimeclock'@'localhost' IDENTIFIED BY 'PHPT1ME!';

c. Grant the user you just created access to the database it needs to mess with.
	
	GRANT ALL PRIVILEGES ON timeclock . * TO 'sqltimeclock'@'localhost';

d. Now we flush out the privileges to make sure we're good.
	
	FLUSH PRILEGES;

e. Now we get out of interactive mode. 
	
	EXIT

3. Now, use git to clone the project into your webroot

	git clone https://github.com/enforce1/php_timeclock_fixed.git
	
4. Now that we've got that squared away, lets import our tables.
	
	mysql -u sqltimeclock -p timeclock < create_tables.sql

5. Use your favorite text editor to update config.inc.php with your MySQL database
information

6. Open up your web browser, and point it to your web host. The initial Login is admin 
with password admin


	