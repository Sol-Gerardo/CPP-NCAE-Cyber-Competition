# 2. Static IP, Ports, and Services 
## (Tutorial) Ping Across Networks 
- If no DHCP server is available then the node (device) cannot receive an IP address
	- We can assign the node an IP instead 

- The network is the 192.168.23.0 network
	- The node will be the 7th device on the network 
	- We can assign the IP address 192.168.23.7 to the node 

- We can distinguish the network from the device by setting a subnetmask 
	- The subnetmask will be 255.255.255.0

- The 255.255.255 declares that the first 3 numbers of the nodes IP address are the network we are communicating to 
	- The 0 means the last number which identifies the device 

- The subnet mask, such as 255.255.255.0, in which the first three numbers indicate which networks we can communicate with 
	- In this case 192.168.23.0

- The last number identifies the device on the network "Connection Profile" that was already configured
- From there we go to the IPv4 tab in the settings application 
	- We set the Ubuntu VM's IP to 192.168.23.7 
	- The Netmask will be 255.255.255.0
	- We can leave the Gateway blank for now 

- We now recieve a flag on the desktop:
	- tutorial flag: flag{your_first_flag}

## Static IP, Ports, and Services 
- From there we open a web browser (Firefox) 
- We can enter the following IP into the URL bar:
	- 192.168.23.101
- Now we are routed to a web server and connect to it on port 80 

- We need to switch networks to establish a secure connection using SSH 
- Switch to the 192.168.42.0 network and keep the .7 as our last octet value
- Our netmask remains the same (255.255.255.0) because we still want to identify the first 3 numbers as our network and last number as our device on the network

- We can now communicate securely over port 22
- On the VM we can delete the old network profile and set our IP to 192.168.42.7 
- The netmask can remain the same 255.255.255.0
- Next we open the terminal and edit the sshd_config file:
	- Enter the command sudo nano /etc/ssh/sshd_config
		- Must be done as sudo
	- This is located in /etc/ssh/sshd_config path
	- Now we set uncomment the Port 22 portion
	- We also set the "ListenAddress" to 192.168.42.7
	- Now save the configurations we made to the file 
- Lastly, we need to allow incoming connections over port 22 
- This requires us to configure the VM's firewall 
	- We run the following command:
		- sudo ufw allow 22/tcp
	- We also enter the command:
		- sudo systemctl restart sshd 
	- This restarts the sshd service and implements the configurations that we made 
	- We can confirm ssh is running by entering thet following command:
		- sudo systemctl status
- The following flag appears:
	- flag: flag{i_can_haz_flag?}

## DHCP 1
- We need to remove our old "Connection Profile"
- Now we set the IP to be 192.168.3.66 
- The netmask is the same as the other profiles 
	- 255.255.255.0
- We also set the Gateway IP to 192.168.3.1
- Next we establish an ssh connection to the router to see what is wrong with the DHCP server:
	- ssh root@192.168.3.1
	- password: password
- Navigate to the following file:
	- cd /etc/dhcp/dhcpd.conf
	- Execute the command:
		- sudo nano /etc/dhcp/dhcpd.conf
	- There is an error within the file 
		- Change the subnet 168.192.3.0 address to 192.168.3.0
		- Change the netmask from 255.255.255.255 to 255.255.255.0
	- Next run the systemctl stop dhcpd.service command
	- Then run the systemctl start dhcpd.service command
	- Ping the IP address 192.168.3.100 
		- We should get replies 
	- Open a web browser and enter the following IP into the URL bar
		- 192.168.3.100
	- We now see the following flag:
		- flag: flag{teach_a_man_to_ping}

## DHCP 2
- We need to assign the Ubuntu server a specific IP address since the ssh service is listening on the IP address 192.168.3.200
- The Ubuntu server IP address is:
	- 192.168.3.100
- To assign a specific IP address to the Ubuntu server we need to configure the dhcpd.conf file on the DHCP server
	- We need to ssh into the DHCP server 
- We uncomment the in the dhcpd.conf file:

	```
		#host rrc-ubuntu2{
		#  hardware ethernet MAC_ADDRESS;
		#  fixed-address IP_ADDRESS;
		#}
	```

- From there we enter 192.168.3.200 in place of the IP_ADDRESS
- The issue is now we don't know the MAC_ADDRESS 
	- We can obtain this by using the arp command
	- This will resolve IP addresses and display the IP address along with its MAC address
- From there we can get the MAC address for the 192.168.3.100 IP and put it in place of the MAC_ADDRESS in the dhcpd.conf file 
- The DHCP server will now assign the 192.168.3.200 IP address to the Ubuntu server
- Now we can SSH into the Ubuntu Server and get the flag
	- flag: flag{arp_arp_goes_the_seal}

## Bill's Encryption
- Switch to the 192.168.23.7 network
	- Subnetmask: 255.255.255.0
- Read the flag: 
	- flag{gptgtnarnfypucxiigywknpsyzgldhqc}
- Switch to the 192.168.42.0 network 
- Step 1.) Read in text and key files
- Step 2.) Perform Vignere subsitution on the text using the key file 
- Step 3.) After Vignere substitution, perform a custom transposition of letters:
	- Shift;
		- odd position letters move 2 places to left
		- even position letters move 4 places to right 

- Performing plaintext conversion on the encrypted message:

g  p   t   g     t     n    a     r    n     f     y       p      u      c      x         i     i      g       y      
6 15 19  6   19   13   0   17  13    5    24    15    20    2      23     8    8     6     24  

w    k     n       p      s       y      z        g        l      d    h     q    c
22  10   13    15     18    24   25       6       11    3    7     16   2
 
- The key was found in the Documents folder inside a hidden directory:
- cd into the .Bill directory
- Then perform key conversion on the supersecretkey plain text

key: supersecretkey

- Convert key:

s       u      p      e       r         s       e         c      r      e        t       k      e     y  
18    20    15    4      17       18     4         2     17    4       19    10     4    24    

- ![[Screenshot 2023-03-02 at 8.06.11 AM.png]]
- ![[Screenshot 2023-03-02 at 8.10.00 AM.png]]

## Subnetting and Firewalls 
### Initial network
- Change IP to static IP of 192.168.99.7/24
	- Subnet mask 255.255.255.0
- ![[Screenshot 2023-03-02 at 9.28.29 AM.png]]

### Split 2
- The subnet mask was split and there are now two networks 
- One of the host bits in the mask was borrowed 
- The new mask is now:
	- 255.255.255.128 or /25
- There are now two networks within 192.168.99.0/24
- The two networks are now:
	- 192.168.99.0/25 and 192.168.99.128/25
- The end result is 2 subnets with 126 possible devices on each network 
- ![[Screenshot 2023-03-02 at 9.29.30 AM.png]]

### Split 4
- The network was split again resulting in four networks
- The network took another host but to create the networks and turned them into /26 networks with a mask of:
	- 255.255.255.192
- ![[Screenshot 2023-03-02 at 9.30.16 AM.png]] 

### Split 8
- Subnetting process occurs again
- Splitting to 8 networks
- We now have 8 new networks within 192.168.99.0
- We have a new mask of 255.255.255.244 or /27
- ![[Screenshot 2023-03-02 at 9.30.43 AM.png]]

- The 6 subnet is trying to send information by SSH
- We need to reconfigure our network settings to the 6th subnet

### Subnet notes
- ![[Screenshot 2023-03-04 at 10.56.31 AM.png]]
- ![[Screenshot 2023-03-04 at 10.58.26 AM.png]]