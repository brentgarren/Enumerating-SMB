# Enumerating-SMB
Server Message Block
	SMB - Server Message Block Protocol - is a client-server communication protocol used for sharing access to files, printers, serial ports and other resources on a network.
	Servers make file systems and other resources (printers, named pipes, APIs) available to clients on the network. Client computers may have their own hard disks, but they also want access to the shared file systems and printers on the servers.

	The SMB protocol is known as a response-request protocol, meaning that it transmits multiple messages between the client and server to establish a connection. Clients connect to servers using TCP/IP (actually NetBIOS over TCP/IP as specified in RFC1001 and RFC1002), NetBEUI or IPX/SPX.
	How Does it Work?
		Client >SMB Request> Server
		Server >SMB Response> Client
	Once they have established a connection, clients can then send commands (SMBs) to the server that allow them to access shares, open files, read and write files, and generally do all the sort of things that you want to do with a file system. However, in the case of SMB, these things are done over the network.
<br>

Enumerating SMB
	Typically, there are SMB share drives on a server that can be connected to and used to view or transfer files. SMB can often be a great starting point for an attacker looking to discover sensitive information.

Port Scanning
	The first step of enumeration is to conduct a port scan, to find out as much information as you can about the services, applications, structure and operating system of the target machine.
<br>

**Enum4Linux**
	Enum4linux is a tool used to enumerate SMB shares on both Windows and Linux systems. It is basically a wrapper around the tools in the Samba package and makes it easy to quickly extract information from the target pertaining to SMB. It's installed by default on Parrot and Kali,  [github](https://github.com/portcullislabs/enum4linux).
Enum 4 Linux Options<br>
	-U             get userlist  
	-M             get machine list  
	-N             get namelist dump (different from -U and-M)  
	-S             get sharelist  
	-P             get password policy information  
	-G             get group and member list<br>
	-a             all of the above (full basic enumeration)<br>
	
We can remotely access the smbclient via -- smbclient //[IP]/[SHARE] 
	Followed by the tags:
	
	smbclient //[IP]/[SHARE] -U [name] -P [port]
	-U [name] : to specify the user

	-p [port] : to specify the port
<br>

Its important to always check for misconfigurations such as allowing anonymous access<br>
	Username = Anonymous<br>
	Password = " "
