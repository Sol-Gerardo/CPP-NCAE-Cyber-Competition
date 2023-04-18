- Use **less** command to view output in an orderly fashion 

- To pipe information and send it somewhere else use:
	- cat /etc/group | less 
	- This redirects the output of cat to the less command

- Using **grep**:
	- grep \[KEYWORD\] \[PATH\]
	- Example:
		- cat /etc/passwd | grep jerry 
	- Redirect output to file 
	- cat /etc/shadow | grep jerry > sandboxhash

[[Background on Services]]