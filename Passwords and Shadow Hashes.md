- This command allows you to change a password
	- passwd 
		- This changes the password for your own account
	- passwd user
		- This will change a users account 

- The path /etc/passwd file 
	- This file does have information for the user account, but does not have password information

- Passwords are stored in the following file:
	- sudo cat /etc/shadow
	- These passwords are ran through a hashing algorithm

- Salt characters are added to the password to make password cracking more difficult 

- Use **python3** to start writing python code
	- import crypt
		- To import libraries that allow us to simulate the process of creating hashes similar to the ones in the shadow file 
	- Using crypt function:
		- crypt.crypt("PASSWORD", "SALT")

	- Use **quit()** to exit python programming mode

[[Less Grep and Pipe]]