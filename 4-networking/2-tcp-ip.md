# 2. TCP/IP

The Transmission Control Protocol and Internet Protocol (TCP/IP) is a standard set of protocols developed in the late 1970s by the Defense Advanced Research Projects Agency (DARPA) as a means of communication between different types of computers and computer networks. TCP/IP is the driving force of the Internet, and thus it is the most popular set of network protocols on Earth.

### 2.1. TCP/IP Introduction

_Internet Protocol_:
- Connectionless protocol
- Deals with network packet routing using the _IP Datagram_ as the basic unit of networking information.
- IP Datagram consists of a __header__ followed by a __message__

_Transmission Control Protocol_:
- Enables network hosts to establish connections which may be used to exchange data streams
- Guarantees that data between connections is delivered and arrives at one network host in the same order as sent from another network

### 2.2. TCP/IP Configuration

TCP/IP protocol configuration consists of several __elements__ which must be set by editing the appropriate configuration files, or deploying solutions such as the Dynamic Host Configuration Protocol (DHCP) server which in turn, can be configured to provide the proper TCP/IP configuration settings to network clients automatically. These configuration values must be set correctly in order to facilitate the proper network operation of your Ubuntu system.

The common configuration elements of TCP/IP and their purposes are as follows:
1. IP address
1. Netmask (Subnet mask)
1. Network Address
1. Broadcast Address
1. Gateway Address
1. Nameserver Address

> The IP address, Netmask, Network Address, Broadcast Address, Gateway Address, and Nameserver Addresses are typically specified via the appropriate directives in the file `/etc/network/interfaces`.
