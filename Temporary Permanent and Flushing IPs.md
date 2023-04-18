- To add an IP we enter the following:
	- ip addr add 192.168.118.3 dev ens18
	- ens18 is our network adapter
	- dev is how we specify which device to assign this IP to
	- This is known as a **temporary IP address**
	- This IP is NOT added to our network configuration file and is lost after a restart 

- Enter control + a to get to the front of a command
- Enter control + e to get to the end of a command

- To remove temporary IP addresses we can perform a "flush"
	- This will get rid of any temporary IP addresses
	- Enter the following:
		- sudo ip addr flush dev ens18

- ifconfig command does not show temporary addresses, while on the other hand ip a or ip addr does show additional IP addresses

- To restart the Ubuntu network enter:
    - sudo service network-manager restart 

[[Using Networking Service with Netcat]]
