- Routing starts at our firewall
	- We can manage our rules and who is allowed/not allowed to connect to one network to another
- We can enter the command:
	- sudo firewall-cmd --list-all-zones

- We have different zones, our interface applies to one of these zones, and all of these different rules are applied to the interfaces based on that particular zone

- To see one specific zone 
	- sudo firewall-cmd --list-all --zone=public

- Configuring eth0 network interface to be on the external zone of our firewall:
	- ![[Screenshot 2023-03-25 at 12.11.18 AM.png]]
- Remember to restart the network service
	- On a CentOS machine enter:
		- sudo systemctl restart network 
	- Ensure settings are applied to firewall:
		- sudo firewall-cmd --list-all --zones=external
- Rules associated with external interface on the firewall will be applied to the ip address that is currently on the eth0 interface 

- To change an interfaces zone using the firewall-cmd command enter:
	- sudo firewall-cmd --change-interface=eth1 --zone=internal
- Note: change is temporary if firewall or computer is restarted, change is lost 
	- --permanent option will prevent changes from being lost:
		- sudo firewall-cmd --change-interface=eth1 --zone=internal --permanent 