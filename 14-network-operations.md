# Chapter 14: Network Operations
 
## Learning Objectives

            * Explain basic networking concepts, including types of networks and addressing issues.
            * Configure network interfaces and use basic networking utilities, such as ifconfig, ip, ping, route and traceroute.
            * Use graphical and non-graphical browsers, such as Lynx, w3m, Firefox, Chrome and Epiphany.
            * Transfer files to and from clients and servers using both graphical and text mode applications, such as Filezilla, ftp, sftp, curl and wget.

##  Networking Configuration and Tools route

### Decoding IPv4 Addresses
A 32-bit IPv4 address is divided into four 8-bit sections called octets.

Example:
IP address →     172     .16      .31      .46
Bit format →     10101100.00010000.00011111.00101110

Note: Octet is just another word for byte.

### Network Configuration Files
For Debian family configurations, the basic network configuration files could be found under /etc/network/, while for Fedora and SUSE family systems one needed to inspect /etc/sysconfig/network. 

### The ip Utility
To view the IP address:
`$ /sbin/ip addr show`

To view the routing information:
`$ /sbin/ip route show`

ip is a very powerful program that can do many things. Older (and more specific) utilities such as ifconfig and route are often used to accomplish similar tasks. A look at the relevant man pages can tell you much more about these utilities.

### ping
ping is used to check whether or not a machine attached to the network can receive and send data; i.e. it confirms that the remote host is online and is responding.

To check the status of the remote host, at the command prompt, type `ping <hostname>`.

ping is frequently used for network testing and management; however, its usage can increase network load unacceptably. Hence, you can abort the execution of ping by typing CTRL-C, or by using the -c option, which limits the number of packets that ping will send before it quits. When execution stops, a summary is displayed.

### route
One can use the route utility or the newer ip route command to view or change the IP routing table to add, delete, or modify specific (static) routes to specific hosts or networks. The table explains some commands that can be used to manage IP routing:

 
**Task** 	                        **Command**
Show current routing table 	    $ route –n or ip route
Add static route 	            $ route add -net address or ip route add 
Delete static route 	        $ route del -net address or ip route del 

### traceroute
traceroute is used to inspect the route which the data packet takes to reach the destination host, which makes it quite useful for troubleshooting network delays and errors. By using traceroute, you can isolate connectivity issues between hops, which helps resolve them faster.

To print the route taken by the packet to reach the network host, at the command prompt, type `traceroute <address>`

### More Networking Tools
let’s learn about some additional networking tools. Networking tools are very useful for monitoring and debugging network problems, such as network connectivity and network traffic.

 
**Networking Tools** 	**Description**
ethtool 	            Queries network interfaces and can also set various parameters such as the speed
netstat 	            Displays all active connections and routing tables. Useful for monitoring performance and 
                            troubleshooting
nmap 	                Scans open ports on a network. Important for security analysis
tcpdump 	            Dumps network traffic for analysis
iptraf 	                Monitors network traffic in text mode
mtr 	                Combines functionality of ping and traceroute and gives a continuously updated display
dig 	                Tests DNS workings. A good replacement for host and nslookup

`sudo nmap -sP 10.0.2.15/24` -> displays the open port in the network

 ## Browsers, wget and curl 
 
 ### Graphical and Non-Graphical Browsers

 ### wget

 Sometimes, you need to download files and information, but a browser is not the best choice, either because you want to download multiple files and/or directories, or you want to perform the action from a command line or a script. wget is a command line utility that can capably handle the following types of downloads:

            Large file downloads
            Recursive downloads, where a web page refers to other web pages and all are downloaded at once
            Password-required downloads
            Multiple file downloads.

To download a web page, you can simply type `wget <url>`

### curl
Besides downloading, you may want to obtain information about a URL, such as the source code being used. curl can be used from the command line or a script to read such information. curl also allows you to save the contents of a web page to a file, as does wget.

You can read a URL using curl <URL>. For example, if you want to read http://www.linuxfoundation.org, type `curl http://www.linuxfoundation.org`

To get the contents of a web page and store it to a file, type `curl -o saved.html http://www.mysite.com` The contents of the main index file at the website will be saved in saved.html.

##  Transferring Files 

### FTP Clients
FTP clients enable you to transfer files with remote computers using the FTP protocol. These clients can be either graphical or command line tools. Filezilla, for example, allows use of the drag-and-drop approach to transfer files between hosts. All web browsers support FTP, all you have to do is give a URL like ftp://ftp.kernel.org where the usual http:// becomes ftp://.

Some command line FTP clients are:

            * ftp
            * sftp
            * ncftp
            * yafc (Yet Another FTP Client).

### SSH: Executing Commands Remotely
Secure Shell (SSH) is a cryptographic network protocol used for secure data communication. It is also used for remote services and other secure services between two devices on the network and is very useful for administering systems which are not easily available to physically work on, but to which you have remote access.

To login to a remote system using your same user name you can just type ssh some_system and press Enter. ssh then prompts you for the remote password. You can also configure ssh to securely allow your remote access without typing a password each time.

If you want to run as another user, you can do either ssh -l someone some_system or ssh someone@some_system. To run a command on a remote system via SSH, at the command prompt, you can type ssh some_system my_command.

### Copying Files Securely with scp
We can also move files securely using Secure Copy (scp) between two networked hosts. scp uses the SSH protocol for transferring data.

To copy a local file to a remote system, at the command prompt, type `scp <localfile> <user@remotesystem>:/home/user/` and press Enter.

You will receive a prompt for the remote password. You can also configure scp so that it does not prompt for a password for each transfer.

