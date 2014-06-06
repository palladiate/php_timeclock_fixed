php_timeclock_fixed
===================

PHP Timeclock Fixed

This is a fixed version of PHP Time Clock 1.04, found here: 

http://timeclock.sourceforge.net/install.php

It was broken, mostly an effect of too much time passing, and MySQL deprecating a few
things that the original software used. Anyhow, here's the instructions for installation.

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

3. Now that we've got that squared away, lets import our tables.
	
	