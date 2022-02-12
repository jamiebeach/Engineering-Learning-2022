# AZ-104 Microsoft Azure Administrator Certification Cheat Sheet

[Exam Outline](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4pCWy)


## 🔖 Manage Azure identities and governance (15–20%)

### AD (Active Directory) vs AAD (Azure Active Directory)
- Fundamental differences : REST API vs NTLM\Kerberos\LDAP. Also Group Policy Object vs Intune
- Hybrid AD-AAD use **AD Connect** - Hash sync, pass-through auth (PTA), Federation
- [Built-in **AAD Roles**](https://docs.microsoft.com/en-us/azure/active-directory/roles/permissions-reference) : examples: *global admin*, *user admin*, *billing admin*
  - Global Admin: can reset all passwords / elevated access. Can grant admin roles. On root (above Management Groups)
- [Join Types](https://o365blog.com/post/devices/#join-types): 
  - Registered (personal device - non organization account)
  - Joined (organizatino device, sign-in w Azure AD account - cloud only)
  - Hybrid Joined (organization device, Active Directory Domain Services account - both on-prem and cloud)
- [Dynamic Group](https://docs.microsoft.com/en-us/azure/active-directory/enterprise-users/groups-create-rule) : O365 group - When an attribute changes for a user or device, all dynamic group rules in the organization are processed for membership changes.
- [Administrative Units](https://docs.microsoft.com/en-us/azure/active-directory/roles/administrative-units) - AD resource that contains other AD resources (users/groups)
- [Identity Governance](https://docs.microsoft.com/en-us/azure/active-directory/governance/identity-governance-overview)
- SSPR (Self-serve password reset). Administrators have strong 2-gate password reset always, which may differ from configured SSPR policies.


### Azure RBAC (Role-Based Access Control)
- Follow least privileges policy : Grant narrow access for role
- Uses Azure Resource Manager for fine-grained authorization control within set scope (resouces)
- **Security Principal** - like a service account or managed identity for resource access
- **Role Definition** - list of ops that can be performed
- **Scope** - set of resources for access. Follows parent-child relationship in scope hierarchy
- Role assignments can be *Allow* or *Deny*
- RBAC is free with Azure subscriptions
- [Built-in roles](https://docs.microsoft.com/en-us/azure/role-based-access-control/built-in-roles) : *owner*, *contributor*, *reader*, *user access administrator*. Also specialized roles (ex. Network Contributor)

### Azure Policy
- Free. Define\assign\manage standards (like ISO\HIPPA\GDPR) for resources
- Mark actions and setup as non-compliant
- Policy Definition -> Policy Initiative -> Policy\Initiative Assignment
- **Initiative** is a set of policy definitions, grouped together. (ex. all billing policies in an initiative)

### [Azure Blueprints](https://cloudacademy.com/blog/what-are-azure-blueprints/)
- Build and deploy collections of Azure resources adhering to requirements and standards
- Includes role assignments, resource groups, policy assignments, etc..
- Used by admins and architects to design solutions
- Similar to ARM templates, but exist natively on Azure

### Azure Advisor
- 5 pilars : "Azure well-architected framework"
  - Cost optimization, Operational excellence, Performance efficiency, Security, Reliability

### Azure Service Health
- Personalized dashboard for ssubscription - all resources across all subscriptions and regions
- Notifications of issues or upcoming maintenance

### Scopes
Root -> Management Groups -> Subscriptions -> Resource Groups -> Resources

### Resouce Manager
- Handles deployments of resources

### Scaling

| SLA   | Scaling type |
| ----- | ------------------------------------------ |
| 99.9% | Single VM (with Premium SSD or Ultra Disk) |
| 99.95% | Availability Set |
| 99.99% | Availability Zones |

- Scale Sets spread load over multiple fault domains, but have no defined SLA besides the underlying VM SLA's.

### Azure Key Vault
- Integrated into AD - store secrets, keys and certificates (w multiple versions)
- [FIPS 140-2 compliant](https://csrc.nist.gov/publications/detail/fips/140/2/final)
- Set access policies or RBAC for data plane. Management plane RBAC only.

### Locks
- Locks can be put on resources. 
- Delete lock on a resource still allows it be moved.

## 🔖 Implement and manage storage (15–20%)

### Azure Storage

- Azure Import/Export service is used to securely import large amounts of data to Azure Blob storage and Azure Files by shipping disk drives to an Azure datacenter.

#### Azure BLOB Storage
- binary/text data
- [REST API](https://docs.microsoft.com/en-us/rest/api/storageservices/blob-service-rest-api)\CLI\ARM
- Common for backup\restore\largef files\logging
- ADLS (Azure Data Lake) is on Blob Storage
- [Types](https://docs.microsoft.com/en-us/rest/api/storageservices/understanding-block-blobs--append-blobs--and-page-blobs): 
  - Block:  large objects \ optimal for streaming. Up to 190.7 TiB
  - Append: keep updating to files (ex logging)
  - [Page](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-blob-pageblob-overview?tabs=dotnet): collection of 512-byte pages for read/write arbitrary byte ranges. Optimal for data structures like OS and data disk images. ex Azure SQL DB. Up to 8 TiB
- Access levels: Private, Blob (anon read), Container (anon read for container and blob)
- Access tiers: Hot/Cool and Archive (Cool - between 30 and 180 days storage)
- Zone replication: 

| . | **LRS** | **ZRS** | **GRS/RA-GRS** | **GZRS/RA-GZRS** |
| -- | ------ | ------- | -------------- | ---------------- |
| Node outage        | ✅ | ✅ | ✅ | ✅ |
| Data center outage |   | ✅ | ✅ | ✅ |
| Region-wide outage |   |    | ✅ | ✅ |

- **For RA- variants read access for secondary region is available if primary region goes down*
- Lifecycle management: moving between hot\cool\archive

#### Azure File Storage
- File share accessible over [SMB](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831795(v=ws.11)) or [NFS](https://docs.microsoft.com/en-us/windows-server/storage/nfs/nfs-overview)
  - UNC path mounted with File Explorer : \\host-name\share-name\file-name

#### Azure Disk Storage

#### Azure Queue Storage

#### Azure Table Storage

#### Azure Archive Storage


## 🔖 Deploy and manage Azure compute resources (20–25%)

## 🔖 Configure and manage virtual networking (25–30%)

### Load Balancers
- Load balancer works at Layer 4
- Basic LB - underlying VM's need to be in an availability set, Standard LB - no availabilty set required
- Standard LB requires Standard public network interface on VM
- LB's require VM's in same virtual network
- [Availability Sets](https://docs.microsoft.com/en-us/azure/load-balancer/tutorial-multi-availability-sets-portal): only apply to VM's. Takes the virtual machine and configures multiple copies of it. Each copy is isolated within a separate physical server, compute rack, storage units and network switches within a single datacentre within an Azure Region. ([tutorial](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/tutorial-availability-sets))

### Application Gateway
- Layer 7
- Route based on URL and other attributes.

### Network Verification
- IP Flow: checks if a packet is allowed or denied to or from a virtual machine
- Network Watcher Connection Monitor:  provides unified end-to-end connection monitoring in Azure Network Watcher
- Network Configuration Diagnostic Tool: understand which traffic flows will be allowed or denied in your Azure Virtual Network
- Network Watcher Next Hop: Checking if traffic is being directed to the intended destination.

### Point-to-Site VPN

### Site-to-Site VPN
## 🔖 Monitor and back up Azure resources (10–15%)
