- How to determine who is capable of running sudo located in ==sudoers file== 
- ==/etc== administrative or configurations are stored within this file 
	- .conf files are the configuration files within the /etc file 
	- There are also .conf files within the folders located in the /etc file 

- To read the sudoers file you must have the correct permissions
	- We can view the sudo permissions without having to be a super user 
	- Within the sudoers file when we see the following:
		- %sudo 
			- This is a group within the sudoers file

- To edit the sudoers file enter:
	- sudo visudo 
	- We modify the .tmp version of this file as a safety measure 

- To delete a user use:
	- sudo userdel -r bob
		- -r to delete the users home directory as well 


[[Groups]]