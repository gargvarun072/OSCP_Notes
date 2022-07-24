Access Control List

# Access Control List
An access control list (ACL) contains rules that ***grant or deny access to certain digital environments***. There are two types of ACLs:

- **Filesystem ACLs** - filter access to files and/or directories. Filesystem ACLs tell operating systems which users can access the system, and what privileges the users are allowed.
- **Networking ACLs** - filter access to the network. Networking ACLs tell routers and switches which type of traffic can access the network, and which activity is allowed.

* * *
### Reasons to use an ACL:

1. Traffic flow control
2. Restricted network traffic for better network performance
3. A level of security for network access specifying which areas of the server/network/service can be accessed by a user and which cannot
4. Granular monitoring of the traffic exiting and entering the system

* * *
### Types of Access Control Lists
Access control lists can be approached in relation to two main categories:

**Standard ACL**
An access-list that is developed solely using the source IP address. These access control lists allow or block the entire protocol suite. They don’t differentiate between IP traffic such as UDP, TCP, and HTTPS. They use numbers 1-99 or 1300-1999 so the router can recognize the address as the source IP address.

**Extended ACL**
An access-list that is widely used as it can differentiate IP traffic. It uses both source and destination IP addresses and port numbers to make sense of IP traffic. You can also specify which IP traffic should be allowed or denied. They use the numbers 100-199 and 2000-2699.

* * *
### Linux ACL vs. Windows ACL
Linux provides the flexibility to make kernel modifications, which cannot be done with Windows. However, because you can make kernel modifications to Linux, you may need specialized expertise to maintain the production environment.

Windows offers the advantage of a stable platform, but it is not as flexible as Linux. In relation to application integration, Windows is easier than Linux.

A user can set access control mechanisms in a Windows box without adding software.

In terms of patching, Microsoft is the only source to issue Windows patches. With Linux, you can choose to wait until a commercial Linux provider releases a patch or you can go with an open-source entity for patches.