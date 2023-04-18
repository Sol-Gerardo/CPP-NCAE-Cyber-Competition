- /etc/network/interfaces does not located on every operating system
- ls /etc/sysconfig/network-scripts
	- This is where we can find the files for each interface associated with the file 
- Each interface will have its own configuration file unlike the Kali OS which had one file for all of the interfaces 
- ![[Screenshot 2023-03-23 at 6.30.15 PM.png]]
- We need to decide which network interface will connect our router to the external network and which network interface will connect us to the internal interface 

- Note: our nano machine does not come installed with **nano**
	- As a result we use the **vi** command

- To configure our CentOS network configuration file:
	- sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0
		- We change:
			- BOOTPROTO=dhcp
			- To:
				- BOOTPROTO=static
		- We change:
			- ONBOOT=no
			- To:
				- ONBOOT=yes
			- To boot with this interface when the system is shutdown or restarted
		- To assign an IP:
			- IPADDR=172.20.11.1
		- To assign a netmask:
			- NETMASK=255.255.0.0 (this is a /16 network)

- Remember to restart the service:
	- sudo systemctl network

- Note: we configured our eth0 to connect to the external network

- We will now configure our eth1 network interface to connect to our internal network:
	- sudo vi /etc/sysconfig/network-scripts/ifcfg/eth1
	- ![[Screenshot 2023-03-23 at 6.46.26 PM.png]]
	- Our NETMASK is now a /24 network

[[Static Configuration in Ubuntu Netplan]]