- r = read = 4
- w = write = 2
- x = execute = 1
- - = none = 0
- d = directory
- - = file 

- **Example 1**:
	- d rwx r-x r-x
		- The first letter, d, is the Directory
		- rwx is the Owner group (first group)
		- r-x is the Group group (second group)
		- r-x is the Everyone else group (last group)

- **Example 2**:
	- - rw- rw- r--
		- - Is a File 
		- rw- is the Owner group (first group)
			- Owner cannot execute file 
		- rw- is the Group group (second group)
			- Group cannot execute
		- r-- is the Everyone else group (last group) 
			- Everyone else cannot write or execute 

- To change/assign permissions:
	- chmod 777 james/
		- First number is the Owner
		- Second is the Group
		- Third is the Everyone else group

[[Exploring Sudoers and Removing Users]]