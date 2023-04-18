- Use **groups** command to see the existing groups in the system
- **id** shows the id of each group, user, etc. 

- How to modify an individual users group account 
- sudo usermod -a -G sudo bob
	- -a to append a group to the user 
	- -G to specify what group to add
	- Be sure to log out/log back in again

- The file where the groups are located is:
	- cat /etc/groups
	- sudo:x:27:jerry
		- sudo is the group
		- 27 is the group id
		- jerry is the user assigned to this group

[[Passwords and Shadow Hashes]]