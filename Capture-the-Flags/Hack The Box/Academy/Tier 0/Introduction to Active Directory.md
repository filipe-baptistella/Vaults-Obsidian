-----
- [[#Active Diretory Overview|Active Diretory Overview]]
	- [[#Active Diretory Overview#<span style="color:red">Why Active Diretory ?</span>|Why Active Diretory ?]]
- [[#Active Diretory Fundamentals|Active Diretory Fundamentals]]
	- [[#Active Diretory Fundamentals#<span style="color:red">Active Directory Structure</span>|Active Directory Structure]]
	- [[#Active Diretory Fundamentals#<span style="color:red">Active Directory Terminology </span>|Active Directory Terminology]]
		- [[#<span style="color:red">Active Directory Terminology </span>#<span style="color:yellow">Object </span>|Object ]]
			- [[#<span style="color:yellow">Object </span>#<span style="color:green">Domain </span>|Domain ]]
			- [[#<span style="color:yellow">Object </span>#<span style="color:green">Forest </span>|Forest ]]
			- [[#<span style="color:yellow">Object </span>#<span style="color:green">Tree </span>|Tree ]]
			- [[#<span style="color:yellow">Object </span>#<span style="color:green">Conatainer </span>|Conatainer ]]
			- [[#<span style="color:yellow">Object </span>#<span style="color:green">Leaf </span>|Leaf ]]
		- [[#<span style="color:red">Active Directory Terminology </span>#<span style="color:yellow">Global Unique Identifier (GUID) </span>|Global Unique Identifier (GUID) ]]
			- [[#<span style="color:yellow">Global Unique Identifier (GUID) </span>#<span style="color:green">Security principals </span>|Security principals >]]
			- [[#<span style="color:yellow">Global Unique Identifier (GUID) </span>#<span style="color:green">Security Identifier (SID) </span>|Security Identifier (SID) ]]
		- [[#<span style="color:red">Active Directory Terminology </span>#<span style="color:yellow">Distinguished Name (DN) </span>|Distinguished Name (DN)]]
		- [[#<span style="color:red">Active Directory Terminology </span>#<span style="color:yellow">Relative Distinguished Name</span>|Relative Distinguished Name]]
		- [[#<span style="color:red">Active Directory Terminology </span>#<span style="color:yellow">sAMAccountName</span>|sAMAccountName]]
		- [[#<span style="color:red">Active Directory Terminology </span>#<span style="color:yellow">userPrincipalName</span>|userPrincipalName]]
		- [[#<span style="color:red">Active Directory Terminology </span>#<span style="color:yellow">FSMO Roles</span>|FSMO Roles]]
		- [[#<span style="color:red">Active Directory Terminology </span>#<span style="color:yellow">Global Catalog</span>|Global Catalog]]
	- [[#Active Diretory Fundamentals#<span style="color:red">Active Diretory objects </span>|Active Diretory objects ]]

## Active Diretory Overview
------

### <span style="color:red">Why Active Diretory ?</span>

Active diretory is a service for Windows network which allows a centralize management  of organization's resources, like users, computers, shres, group policies, trusts and etc.

The AD provides authentication and authorization within a Windows domain environment.

But this service has an weakness, many features are arguably not secure by default, and it can be easily misconfigured.


## Active Diretory Fundamentals

-----
### <span style="color:red">Active Directory Structure</span>

Well, a basic AD user account with no added privileges can be used to enumerate the majority of objects contained within AD, including but not limited to:
- Domain Computers, Domain Users;
- Domain Group information, Organizational Units (OUs);
- Default Domain Policy, Functional Domain Levels;
- Password Policy, Group Policy Objects;
- Domain Trusts, Access Control Lists (ACLs)

So, we know that florests can contain one or more doamin, and is common to see multiple domain linked together byu trust relantionships.

### <span style="color:red">Active Directory Terminology </span>
So, befero we go further, it's important define some key terminology that will be used.

#### <span style="color:yellow">Object </span>
An Object is literaly ANY resource present within an Active Directory environment such as OUs, printers, users, domain controllers etc.

Objects has must to be associated with a set of attributes used to define characteristics of the given object. For example:
A computer object contain attributes such as the hostname and DNS name.

##### <span style="color:green">Domain </span>
A domain is a logical group of objects. Domains can operate entirely independently of one another or be connected via trust relationships.

##### <span style="color:green">Forest </span>
A _forest_ is a collection of one or more domain trees.

##### <span style="color:green">Tree </span>
A _domain tree_ is simply a collection of one or more domains that share a common namespace. Each domain in a tree shares a boundary with the other domains. 
A parent-child trust relationship is formed when a domain is added under another domain in a tree. Two trees in the same forest cannot share a name (namespace).

##### <span style="color:green">Conatainer </span>
Container objects hold other objects and have a defined place in the diretory subtree hierarchy.

##### <span style="color:green">Leaf </span>
Lead objects don't contain other objects and are found at the end of the subtree hierarchy.

#### <span style="color:yellow">Global Unique Identifier (GUID) </span>
Every single object created by Active Directory is assigned a GUID, that is a unique 128-bit value, used across all the enterprise AD, similar to a MAC Address.

The GUID is stored in the `ObjectGUID` Atributte. When querying for an AD object, we can query for its value using PowerShell.

The `ObjectGUID` property `never` changes and is associated with the object for as long as that object exists in the domain.

##### <span style="color:green">Security principals </span>
Security principals are domain objects that can manage access to other resources within the domain. Basicly anything that the operating system can authenticate, including users, computer accounts etc.

##### <span style="color:green">Security Identifier  </span>(SID)
SID is a unique identifier for a security principal or security group. Every account, group or process has its own unique SID. Each SID is issued by the domain controller and stored in a secure database. SID can only be used once. This Token is used to check rigts whenever the user perform an action on the computer. 


#### <span style="color:yellow">Distinguished Name  </span>(DN)
A DN describes the full path to an object in AD. (i.e. cn=bjones, ou=IT, ou=Employes, dc=inlanefreight, ds=local). In this example, the user bjones works in the IT department of the company inlanefreight. The Comoon name, bjones is jut one way the user  object could be searched.
DN IS UNIQUE.

#### <span style="color:yellow">Relative Distinguished Name</span>
RDN is a single componant of the DN. Each component identifies the object as unique from other objects at the current level in the naming hierarchy. 
AD does'nt allow two object with the sanem name under the same parent container, but there can be two objects with the same RDNs that are still unique in the domain because they have different DNs.

#### <span style="color:yellow">sAMAccountName</span>
Is the user's logon name. It must be a unique value.

#### <span style="color:yellow">userPrincipalName</span>
It is an attribute, is another way to identify users in AD. Format (user account name)@(domain name), like bjones@inlanefreight.local.

#### <span style="color:yellow">FSMO Roles</span>
There is five roles of FSMO . In the ealy days of AD, there was a problem with the domain controlers. If you have more than 1 domain controllers making changes, which change will be still up? So, they try to fix this assuming just 1 master domain controller, but when he went down, all the change not work and just authentication and authorization still works with the others DC's. So they create FSMO(Flexible Single Master Operation), with five roles. 
`Schema Master` and `Domain Naming Master` (one of each per forest), `Relative ID (RID) Master` (one per domain), `Primary Domain Controller (PDC) Emulator` (one per domain), and `Infrastructure Master` (one per domain). All five roles are assigned to the first DC in the forest root domain in a new AD forest.

#### <span style="color:yellow">Global Catalog</span>
GC is a domain controller that stores copies of ALL objects in an Active Directory Forest. 
GC is a feature that is enabled on a domain controller and performs the following functions:
- Authentication
- Object Search

#### <span style="color:yellow">Read-Only Domain controller</span>
RODC has just read AD database. No AD account passwords are acached on an RODC. No changes are pushed out via SYSVOL, or DNS. RODCs also incluyde a read-only DNS server, allow for administrator role separation, reduce replication traffic in the environment.

#### <span style="color:yellow">Replication</span>
Replication happens in AD when AD objects are updated and transferred from one Domain Controller to another. Whenever a DC is added, connection objects are created to manage replication between them.

#### <span style="color:yellow">Service Principal Name</span> (SPN)
A SPN uniquely identifies a service instance. They are used by Kerberos authentication to associate an instance of service with a logon account, allowing a client applicaiton to request the service to authenticate an account without needing to know the ccount name.

#### <span style="color:yellow">Group Policy Object </span>(GPO)
GPOs are virtual collections of policy settings, each GPO has too a unique GUID. They can be applied to all users and computers within the domain or defined more granularly at the OU Level.

#### <span style="color:yellow">Access Control List</span> (ACLS)
Is the ordered collection of access control entites that apply to an object.

#### <span style="color:yellow">Access Control Entities </span>(ACEs)
Each ACE in an ACL identifies a trustee (User account, logon session, group account), na dlist the access rights that are allowed denied or audited for the given trustee.

#### <span style="color:yellow">Discretionaty Access Control List </span>(DACL)
DACLs define which security principles are granted or denied access to an object; it contains a list of ACEs.

#### <span style="color:yellow">Fully Qualified Domain Name </span>(FQDN)
An FQDN is the complete name for a specific computer or host. It is written with the hostname and domain name in the format [host name].[domain name].[tld].
. An example would be the host `DC01` in the domain `INLANEFREIGHT.LOCAL`.  `DC01.INLANEFREIGHT.LOCAL`

#### <span style="color:yellow">Tombstone </span>
A [tombstone](https://ldapwiki.com/wiki/Tombstone) is a container object in AD that holds deleted AD objects.
If an object is deleted in a domain that does not have an AD Recycle Bin, it will become a tombstone object. When this happens, the object is stripped of most of its attributes and placed in the `Deleted Objects` container for the duration of the `tombstoneLifetime`. It can be recovered, but any attributes that were lost can no longer be recovered.

#### <span style="color:yellow">AD Recycle Bin </span>
When the AD Recycle Bin is enabled, any deleted objects are preserved for a period of time, facilitating restoration if needed.

#### <span style="color:yellow">SYSVOL </span>
The [SYSVOL](https://social.technet.microsoft.com/wiki/contents/articles/8548.active-directory-sysvol-and-netlogon.aspx) folder, or share, stores copies of public files in the domain such as system policies, Group Policy settings, logon/logoff scripts, and often contains other types of scripts that are executed to perform various tasks in the AD environmen

#### <span style="color:yellow">AdminSDHolder</span>
The [AdminSDHolder](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-c--protected-accounts-and-groups-in-active-directory) object is used to manage ACLs for members of built-in groups in AD marked as privileged. The SDProp (SD Propagator) process runs on a schedule on the PDC Emulator Domain Controller. When this process runs, it checks members of protected groups to ensure that the correct ACL is applied to them. It runs every hour by default.
#### <span style="color:green">adminCount</span>
The [adminCount](https://docs.microsoft.com/en-us/windows/win32/adschema/a-admincount) attribute determines whether or not the SDProp process protects a user. If the value is set to `0` or not specified, the user is not protected. If the attribute value is set to `value`, the user is protected.

#### <span style="color:yellow">NTDS.DIT</span>
The NTDS.DIT file can be considered the heart of Active Directory. It is stored on a Domain Controller at `C:\Windows\NTDS\` and is a database that stores AD data such as information about user and group objects, group membership, and, most important to attackers and penetration testers, the password hashes for all users in the domain.

### <span style="color:red">Active Diretory objects </span>
An object can be defined as ANY resource present within an Active Directory environment such as OUs, printers, users, domain controllers.

#### <span style="color:yellow">Computers</span>
