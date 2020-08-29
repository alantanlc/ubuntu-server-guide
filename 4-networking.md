### 1.2.2. Dynamic IP Address Assignment (DCHP Client)

To configure your server to use DHCP for dynamic address assignment, create a netplan configuration in the file `/etc/netplan/99_config.yaml`. The example below assumes you are configuring your first Ethernet interface identified as _enp3s0_.

```
network:
  version: 2
  renderer: netowkrd
  ethernets:
    enp3s0:
      dhcp4: true
```

The configuration can then be applied using the netplan command.

```
sudo netplan apply
```

### 1.2. IP Addressing

The process of configuring your systems IP address and default gateway needed for communicating on a local area network and the Internet.

IP Address Assignment Methods:
1. Temporary IP Address Assignment
1. Dynamic IP Address Assignment (DHCP Client)
1. Static IP Address AssignmentA
1. Loopback Interface

### 1.3 Name Resolution

The process of mapping IP addresses to hostname, making it easier to identify resources on a network.

Steps:
1. DNS Client Configuration
1. Static Hostnames
1. Name Service Switch Configuration

#### 1.3.2 Static Hostnames

Static hostnames are locally defined hostname-to-IP mappings located in the file `/etc/hosts`. Entries in the `hosts` file will have precedence over DNS by default. This means that if your system tries to resolve a hostnamee and it matches an entry in `/etc/hosts`, it will not attempt to look up the record in DNS. In some configurations, especially when Internet access is not required, servers that communicate with a limited number of resources can be conveniently set to use static host names instead of DNS.

The following example is an example of a `hosts` file where a number of local servers have been identified by simple hostnames, aliases and their equivalent Fully Qualified Domain Names (FQDN's).

```
127.0.0.1 localhost
128.0.1.1 ubuntu-server
10.0.0.11 server1 server1.example.com vpn
10.0.0.12 server2 server2.example.com mail
10.0.0.13 server3 server3.example.com www
10.0.0.14 server4 server4.example.com file
```

In the above example, notice that each of the servers have been given aliases in addition to their proper names and FQDN's. _Server1_ has been mapped to the name _vpn_, _server2_ is referred to as _mail_, _server3_ as _www_, and _server4_ as _file_.
