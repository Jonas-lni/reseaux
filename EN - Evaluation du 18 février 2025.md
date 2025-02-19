# Assessment of February 18, 2025
# TCP/IP UDP Network


1- Introduction
   
2- List of manipulations performed
   
2-1 The commands used (example: configura on of an IP address, simula on of dynamic routing).

2-1-1 Insertion of

2-1-2 Cabling and physical connection

2-1.3 Configuration of network interfaces

2-3 Activation and backup of the configuration of each

2-4 Adding routes

2-5 Servers and Computers (PC) Configuration

3- The context (connectivity tests, DHCP configuration)
   - Connectivity test in each subnet
   - Connectivity test between subnets

4- The expected results after each manipulation

5- Problems encountered and solutions

6- Theoretical Analysis

7- Conclusion

8- Ressources 


# 1. Introduction
**The general goal of this assessment and the concepts covered (TCP/IP,
routing, transport, complementary protocols such as DHCP and ARP) is** the analysis and understanding of the fundamentals of communication and data exchange on a computer network. The concepts covered allow you to understand how networks interact with each other, to ensure fast and efficient communication.

**TCP/IP** (Transmission Control Protocol / Internet Protocol):

**TCP/IP** is a set of communication protocols that define how data travels on a network. TCP is responsible for the secure transmission of data, and IP is responsible for routing packets across different networks. Together, they form the basis of communications on the Internet.

**Routing** concerns how packets and frames are sent from one device to another across different networks. Routers are responsible for this task, by defining the best path for data to reach its destination.

**Transport** ensures how data is segmented and transmitted between applications on remote computers. TCP is used for reliable transmissions, while UDP is faster but without guarantee of data reception.
Additional protocols:

**DHCP**: this is the protocol that assigns devices on a network, automatically, an IP address, which facilitates their configuration and organization without manual intervention.

**ARP** the ARP protocol is used to associate an IP address with a MAC address in a local area network, in order to allow effective and secure communication on a local area network (LAN).

The assessment allows you to understand the technical basics of networks and how they work, by covering protocols, address management, data transport and routing. This serves to fully understand the complete process of exchanging information across a computer network.

# 2. List of manipulations performed
Describe each exercise, including:

### 2-1 The commands used (example: configura on of an IP address, simula on of dynamic routing).

**1- Insertion of:**
- Three *routers*: ADMIN - TECH - COMM
- A *switch* and three *servers*
- Six computers *PC*

**2- Cabling and physical connection:** connection of the inserted hardware with the *copper straight through* cable

![insertion.jpg](./_resources/insertion.jpg)


**3- Configuration of network interfaces**
In this step, we will proceed to the configuration of the routers, PCs and servers.

- Admin Router :
*FastEthernet 0/0 interface* :
Configuration IP : 192.168.1.1
Subnet mask : 255.255.255.0

*FastEthernet 0/1 interface* :
Configuration IP : 10.0.0.1
Subnet mask : 255.255.255.0

See the following screenshots :
Admin Router

*FastEthernet 0/0 interface*
![AdmiRouter.jpg](./_resources/AdmiRouter.jpg)

*FastEthernet 0/1 interface*
![AdmiRouter1.jpg](./_resources/AdmiRouter1.jpg)

- Tech Router :
*FastEthernet 0/0 interface* :
Configuration IP : 192.168.2.1
Subnet mask: 255.255.255.0

*FastEthernet 0/1 interface*:
Configuration IP: 10.0.0.2
Subnet mask: 255.255.255.0

*FastEthernet 0/0 interface*:
![tech0.jpg](./_resources/tech0.jpg)

*FastEthernet 0/1 interface*:
![tech1.jpg](./_resources/tech1.jpg)

- Comm Router:
*FastEthernet 0/0 interface*:
Configuration IP: 192.168.3.1
Subnet mask: 255.255.255.0

*FastEthernet 0/1 interface*:
Configuration IP: 10.0.0.3
Subnet mask: 255.255.255.0

*FastEthernet interface 0/0*:
![comm0.jpg](./_resources/comm0.jpg)

*FastEthernet interface 0/1*:
![comm1.jpg](./_resources/comm1.jpg)

**2-3 Activation and backup of the configuration of each network interface** with
**Activation**: *no shutdown*
**Backup**: *write memory*
![noshutdown.jpg](./_resources/noshutdown.jpg)

**2-4 Adding routes:**

- *a -Route Admin*
![routeadmin.jpg](./_resources/routeadmin.jpg)

- *b -Route Tech*
![routetech.jpg](./_resources/routetech.jpg)

- *c -Route Comm*
![routecomm.jpg](./_resources/routecomm.jpg)

**2-5 Servers and Computers (PC) Configuration:**

- Servers:
1. Admin Server:
Server Gateway:
![servadmin.jpg](./_resources/servadmin.jpg)

FastEthernet0
![servadmin1.jpg](./_resources/servadmin1.jpg)

2. Tech Server: pereil for the **TECH** server
*The gateway is: 192.168.2.10*
*The DNS server is: 8.8.8.8*

3. Comm Server: for the **COMM** server
*The gateway is: 192.168.3.10*
*The DNS server is : 8.8.8.8*

- Computers (PC):
 1.PC Admin:
 PC1 Admin:
![Pc1Admin1.jpg](./_resources/Pc1Admin1.jpg)
![Pc2Admin2.jpg](./_resources/Pc2Admin2.jpg)

Pc2 Admin:
*IP: 192.168.1.200*
*Gateway: 192.168.1.1*
*DNS address: 8.8.8.8*

 3. PC Tech:
 PC1 Tech:
![pc1tech1.jpg](./_resources/pc1tech1.jpg)
![pc2tech2.jpg](./_resources/pc2tech2.jpg)

 PC2 Tech:
*IP: 192.168.2.200*
*Gateway: 192.168.2.1*
*DNS address: 8.8.8.8*

 5.PC Comm:
PC1 Comm:
![Pc1comm1.jpg](./_resources/Pc1comm1.jpg)
![Pc1comm2.jpg](./_resources/Pc1comm2.jpg)

Pc2 Comm:
*IP : 192.168.3.200*
*Gateway: 192.168.3.1*
*DNS address: 8.8.8.8*

### 3- The context (connectivity tests, DHCP configuration).

**Connectivity test in each subnet**
1. Admin subnet:
*Pinging to IP 192.168.1.200 from PC1-Admin*
![ping1.200.jpg](./_resources/ping1.200.jpg)
*Pinging to Gateway 192.168.1.100 from PC2-Admin*
![ping1.100.jpg](./_resources/ping1.100.jpg)

3. Tech subnet:
*Pinging to IP 192.168.2.200 from PC1-Tech*
![ping2.200.jpg](./_resources/ping2.200-1.jpg)
*Pinging to Gateway 192.168.2.100 from PC2-Tech*
![ping2100.jpg](./_resources/ping2100.jpg)

5. Comm Subnet:
*Pinging IP 192.168.3.200 from PC1-Comm*
![ping3200.jpg](./_resources/ping3200.jpg)
*Pinging Gateway 192.168.3.100 from PC2-Comm*
![ping3100.jpg](./_resources/ping3100.jpg)

**Connectivity test between subnets**

*Ping Admin to Tech* ping 192.168.1.100 to 192.168.2.200
![ping2.200.jpg](./_resources/ping2.200.jpg)


*Ping Admin to Comm* ping 192.168.1.200 to 192.168.2.100
![ping2100-2.jpg](./_resources/ping2100-2.jpg)

*Ping Tech to Admin* ping 192.168.2.100 to 192.168.1.200
![ping1.200-2.jpg](./_resources/ping1.200-2.jpg)

*Ping Tech to Comm* ping 192.168.2.200 to 192.168.3.100
![ping3100-2.jpg](./_resources/ping3100-2.jpg)

**_Observation: the ping did not work_** : This connectivity test did not work because one of the network interfaces of the router **Comm** is not activated
![probleme.jpg](./_resources/probleme.jpg)

** Following the activation of the FastEthernet0/1 network card: the ping worked**
See the following screenshot:

![problemeresolu.jpg](./_resources/problemeresolu.jpg)
*Ping Comm to Admin* ping 192.168.3.100 to 192.168.1.200
![ping1200-2.jpg](./_resources/ping1200-2.jpg)
*Ping Comm to Tech* ping 192.168.3.200 to 192.168.2.200
![ping2200-2.jpg](./_resources/ping2200-2.jpg)

*Connectivity tests between departments have all been successfully completed*

### Performing a ping by filtering the TCP protocol:
1. Selecting the TCP protocol:
![filtretcp.jpg](./_resources/filtretcp.jpg)
2. Performing a ping from one of the PCs on the network:
![pingtcp1.jpg](./_resources/pingtcp1.jpg)

All packets have been transmitted (none was not lost)
![pingtcp2.jpg](./_resources/pingtcp2.jpg)

### Performing a ping by filtering the UDP protocol:
1. Selecting the UDP protocol:
![filtreudp.jpg](./_resources/filtreudp.jpg)
2. Performing a ping from one of the PCs on the network:
![pingudp1.jpg](./_resources/pingudp1.jpg)

All packets have been transmitted *but there may be losses* because the UDP protocol does not check for packet arrival. When watching a video for example, the video. Server continues to send content despite transmission interruption

*Ping result when selecting UDP port*
![resultatpingudp.jpg](./_resources/resultatpingudp.jpg)

### Checking connectivity with ICMP
1. Ping from Admin to ADMIN router
![ICMP1.jpg](./_resources/ICMP1.jpg)
2. Ping from Tech to TECH router
![ICPM2.PNG](./_resources/ICPM2.PNG)
3. Ping from Comm to COMM router
![ICMP3..PNG](./_resources/ICMP3.PNG)

**Connections between PCs and routers on each subnet are well established and working perfectly without any loss of package**

### 4- The expected results after each manipulation.

The expected results between each manipulation are visible in each manipulation performed.

1. The correct configuration of each element.

2. The connectivity between the PCs of each subnet.

3. The connectivity between the PCs of the different departments.

# 5. Problems encountered and solutions

I encountered a connectivity problem when pinging 192.168.3.100 from the **PC TECH2** because of the non-activation of the FastEthernet0/1 interface of the **COMM router.

See photo:
![probleme.jpg](./_resources/probleme-1.jpg)

The ping had worked well when the activation of this network interface was carried out with the command `no shutdown` then `write memory` after two `exit`

# 6. Theoretical Analysis

**Explanation of the importance of TCP/IP protocols in modern networks:**

TCP/IP protocols are very important in the Internet and modern networks. They ensure reliable communication through TCP, routing and addressing with IP and interoperability between different types of networks and devices. They also provide us with the flexibility to adapt to millions of new devices and services.

*Without TCP/IP, the global network as we know it today would not be possible.*

**The advantage of TCP/IP protocols** is reliability and flow control to ensure the guarantee of delivery of all packets sent. It is used for reliable transmissions, such as sending files, sending emails...

**The advantage of UDP protocols** is the direct and uninterrupted transmission of data that are light. It is used in video, streaming, and gaming because it has low latency.

# 7. Conclusion
TCP/IP protocols are essential for modern network connectivity, providing reliable and efficient communication (with TCP for reliability and UDP for speed),
Accurate routing and globally unique addressing (with IP), and the ability to interconnect diverse networks.

TCP/IP is the foundation of the Internet and modern network infrastructure, facilitating the exchange of data between diverse systems around the world.

# 8. Resources
ChatGPT.com and documentation


# Quiz

**1. The main difference between TCP and UDP is:**

_A. TCP guarantees reliability, UDP is faster._

**2. The layer of the TCP/IP model that handles packet routing is:** the Internet layer

**3. The protocol used to resolve an IP address to a MAC address is: ** _ARP_

**4. The size of an IPv6 address is ** _128 bits_

**5. The tool that allows you to analyze the performance of a network by capturing packets is: ** _Wireshark_