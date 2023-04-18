- cat /etc/network/interfaces
	- This will display the network configuration file data

- Configuring interfaces file:
```
auto lo
iface lo inet loopback # This is the syntax of the 
					   # Network configuration

auto eth0
iface eth0 inet static 
# iface eth0 inet dhcp
		address 172.20.11.100
		netmask 255.255.0.0
```

- 255.255.0.0
- 172.20.118.100
	- The first two 255's refer to numbers associated with the network
	- The last two 0's refer to the numbers associated with the device 

- **systemctl** command to restart, stop, start, check status of service
- sudo systemctl restart networking
	- To update network configuration

[[Static Configuration in CentOS with ifcfg Files]]