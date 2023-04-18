- To configure the network on an Ubuntu OS we use the **netplan** directory:
	- ls /etc/netplan
	- Inside we will find a **.yaml** file(s)
		- There can be more than one .yaml file 

- To configure the .yaml file enter:
	- sudo nano /etc/netplan/01-network-manager-all.yaml

- Our network configuration will look like this:
	- ![[Screenshot 2023-03-23 at 7.27.46 PM.png]]

- To apply network configurations enter:
	- sudo netplan apply

[[Temporary Permanent and Flushing IPs]]