
- Authenticate using Kerberos ticket.  
- Non-Windows devices such as Linux Machine, firewalls, etc. can use RADIUS or LDAP to authenticate.  

→ **Domain Controller** 
	- Hosts a copy of the AD DS Directory store.  
	- Provides authentication and authorization services.  
	- Replicates updates to other domain controllers in the domain and forest.  
	- Allows administrative access to manage user accounts and network resources.  

→ **AD DS Data Store**  
	  - Contains the database files/user/ services/application
	  - Consists of the ntds.dit file.  
	  - Is stored by default in the %systemroot%/NTDS folder on all DCs.  
	  - Is accessible only through the DC process and protocols.

→ **AD DS Schema**  
	- Defines every type of object that can be stored in the directory.  
	- Enforces rules regarding object creation and configuration. 

→ **Class object**  
	  - Uses  
	  - Computer 
  
→ **Attribute object**  
	Information that can be attached to an object.  
	- Display name.  

→ **Domains** 
	Domain used to group and manage objects in an organization.  
	- An administrative boundary for applying policies to groups of objects.  
	- A replication boundary for replicating data b/w DC  
	- An authentication and authorization boundary that provides a way to limit the scope of access to resources.

→ **Trees**
	A domain trees is hierarchy of domains in AD DS
	- share a contiguous namespace with the parent domain.  
	- can have additional child domains  
	- By default create a two-way transitive trust with other domains  

→ **Forests**
	A Forest is a collection of  a 1 or more trees.  
	- Share a  common scheme
	- Share a common configuration partition.  
	- Share a  common global catalog  to enable  searching
	- Enable trusts below all domains in the forest
	- Share the enterprise admins and schema   Admin groups

→ **Organizational Units (OUs)**  
	OUs are active directory containers that can contain users, groups, computers, and other OUs.  
	
	OUs are used to
	- Represent your organization logically.
	- Manage a collection of objects in a consistent way.
	- Delegate permissions to administer groups  of objects.
	- Apply policies.

→ **Trusts**  
	Trusts provide a mechanism for users to gain access to resources in another domain.
	
	Types of trusts:
	- Directional: Trusting domain to trusting domain
	- Transitive: Relations domain to domain.