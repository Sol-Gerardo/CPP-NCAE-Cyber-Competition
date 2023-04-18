- systemctl status apache2
	- This allows us to check the status of services 

- To check what services to host websites are installed on a computer check the following:
	- systemctl status apache2
	- systemctl status nginx
	- systemctl status httpd

- Note attackers may target the apache2.conf file so it is good practice to create a backup of this file and store it in a different location in case this file is modified maliciously 

- For a website we can declare a port and IP address to listen on 
	- \<VirtualHost \*:80\> 
		- This means that our web server will listen on any IP address on port 80
	- DocumentRoot is where the website exists
	- Configuration files are not the webpages 
	- The files that run our website are mostly located in /var/www/html or /var/www

- index.html 
	- This is a file that is loaded when you visit a website 
	- When you visit a website the index.html is loaded
		- Or index.php

- If we create a directory in the /var/www/html path
	- sudo mkdir /var/www/html/james 
	- We can visit this directory on our web browser:
		- 192.168.11.2/james

- We can create an index.html file in the james directory
	- Then we can copy our shadow file to the james directory and change its permissions 
	- sudo cp /etc/shadow /var/www/html/james/
	- sudo chmod 777 /var/www/html/james/shadow
		- We can now view the contents of the shadow file in a web browser:
			- 192.168.11.2/james/shadow

- We can use the following
	- curl \https://192.168.11.2 
		- This allows us to make a web request
		- Useful when we do not have a GUI\

- wget is used to download stuff
	- wget \http://192.168.11.2
- curl may not be installed on all operating systems  

- systemctl status apache2
- ![[Screenshot 2023-03-24 at 11.16.50 PM.png]]
	- If the status of the service says disables the service will not start automatically when the system is rebooted 

- By performing the following:
	- sudo systemctl enable apache2
		- When the computer starts the service will automatically turn on

- To stop a service:
	- sudo systemctl stop apache2

[[Router Configuration and Mini Hack Completion]]