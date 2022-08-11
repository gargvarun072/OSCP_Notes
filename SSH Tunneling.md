### SSH Tunneling

1.  Local Port Forwarding
  

![SSH Local Port Forwarding](https://sohvaxus.github.io/images/SSH_localforward.png)

  

The client wants to access a resource on the server in a different subnet, let's say a webserver (port 80), but he's denied by the firewall. The firewall denies all incoming traffic, except for SSH on port 22. The client is allowed to SSH to the server, and we can leverage this with the command below.

  
```bash
# SSH Tunnel to bypass firewall restriction on port 80 
ssh -L 8080:192.168.0.5:80 remoteuser@192.168.0.5 
# Syntax ssh -L <LPORT>:<RHOST>:<RPORT> user@<RHOST>
```

The command will create an SSH tunnel on port 22 and route all traffic through this tunnel to the server. This means that if you execute the command below, then navigate to **http://localhost:8080** in a browser, you will be able to navigate to the webserver on port 80 through the SSH tunnel. The green arrow in the schema above represents the SSH tunnel.