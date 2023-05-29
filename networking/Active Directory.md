- Hierarchical organization of directory information
- A directory is hierarchical structure that stores information about objects on the network
- Active Directory Domain Service (AD DS) provides methods for storing directory data and make data available to network users and administrator
- AD DS stores user account information such as name, password, email, phone number and enable authorized user to access those data
- The stored objects are typically includes shared resources such as servers, volumes, printers and network users and computer accounts

Active Directory is used to authenticate and authorize the users, computers, resources which are part of a network

- Active Directory uses DNS as its domain controller location mechanism
- Domain controllers use DNS to locate each other
- For example, when a network user with an Active Directory user account logs on to an Active Directory domain, the user’s computer uses DNS to locate a domain controller for the Active Directory domain to which the user wants to log on.
- To log on to a network that consists of an Active Directory forest, a client workstation must first be able to locate a nearby domain controller. The domain controller is necessary for initial authentication of both the workstation and the user and for subsequent authorization of the user for the files and resources to which the user needs access. The support that is provided to Active Directory by DNS enables a client workstation to locate a domain controller.


AD has following parts:
1. Object: Lowest entity
2. Domain: Collection of all object
3. Organizational Unit:
	- Can be used to denote specific department, location, team, function, etc
	- OUs are unique inside a domain
	- Contains other objects like Users, Groups, Contacts, Computers, Printers, Shared folders, etc
1. Tree:
2. Forest: Multiple domain

- Every domain is associated to the domain controller
- Domain controller
	- Data store (LDAP, Replication RPEL, Messaging API MAPI, Security Accounts Manager SAM) considered as APIs
	- Schema
	- Database
 - Domain controller is responsible for all the authentications, authorizations, additions, deletion, edits, modification inside a domain. 

### Trust
Object in different domain communicates through 'Trusts'
Types:
- Transitive (default): If A has transitive trust with B and B has transitive trust with C then A will trust C
- Non transitive
- Two way
- One way

### Active Directory User
- Part of organization
- Unique identity in the domain
- Accesses the domain's resources
- Authorization based access
- Has unique SID (Security Identifier)
- Account is unique and is secured by a password

### Active Directory Computer 
- Individual workstations, servers which are part of network
- Each computer has unique computer account
- Computer account allows each computer to be authenticated and authorized for access to domain and domain resources
- A server could be a Domain controller or global catalog server  or a member server

### Active Directory Contact
- An individual who is not part of the organization but related to the organization
- Example: Customers, Vendors, Supplier, etc
- Unlike a user, a contact cannot login or access the domain or network

### Active Directory Groups
- Contains Users and computer who are member of group
- All permissions, authorizations and restriction paced on the groups apply to all the members of group
- Two types of group:
	1. Security Groups -> Used for assigning permission
	2. Mail Groups 
 - Group Scopes:
	 1. Domain local: To give access to resources in same domain as a group, users can be from different domain
		 - Resources -> same domain
		 - Users -> different domain
	 2. Global group: To give access to resources that are in different domain, to users in specific domain
		 - Resources -> different domain
		 - Users -> same domain
	 3. Universal group: To give access to resources that are in different domain, to users in different domain
		 - Resources -> different domain
		 - Users -> different domain


## Domain and Forest Components
#### Forest
- A forest is the highest level of the logical structure hierarchy
- An Active Directory forest represents a single self-contained directory
- A forest is a security boundary, which means that administrators in a forest have complete control over all access to information that is stored inside the forest and to the domain controllers that are used to implement the forest

#### Domain
- Domains partition the information that is stored inside the directory into smaller portions so that the information can be more easily stored on various domain controllers and so that administrators have a greater degree of control over replication
- Data that is stored in the directory is replicated throughout the forest from one domain controller to another. Some data that is relevant to the entire forest is replicated to all domain controllers. Other data that is relevant only to a specific domain is replicated only to domain controllers in that particular domain
- A good domain design makes it possible to implement an efficient replication topology. This is important because it enables administrators to manage the flow of data across the network, that is, to control how much data is replicated and where that replication traffic takes place.

#### OU (Organization Units)
- OUs provide a means for administrators to group resources, such as user accounts or computer accounts, so that the resources can be managed as one unit.
- This makes it much easier to apply Group Policy to multiple computers or to control the access of many users to a single resource.
- OUs also make it easier to delegate control over resources to various administrators.


## Global Catalog
- Global Catalog is a search index
- First domain controller in a domain becomes GC by default
- GC holds same information as DC in the same domain
- And also, it stores partial attributes copy of other domains, forest
- A DC knows information about object within domain however GC knows object information in other domain as well
- It helps applications and users to search object from Active Directory database
- User Principle Name Resolution
- It also stores universal group membership
- To add an attribute to the GC, you must select the option Replicate this attribute to Global catalog