# AZ-104 Microsoft Azure Administrator Certification Cheat Sheet

[Exam Outline](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4pCWy)


## 🔖 Manage Azure identities and governance (15–20%)

### AD (Active Directory) vs AAD (Azure Active Directory)
- Fundamental differences : REST API vs NTLM\Kerberos\LDAP. Also Group Policy Object vs Intune
- Hybrid AD-AAD use **AD Connect** - Hash sync, pass-through auth (PTA), Federation
- Built-in **AAD Roles** : *global admin*, *user admin*, *billing admin*
  - Global Admin: can reset all passwords / elevated access. Can grant admin roles. On root (above Management Groups)
- [Administrative Units](https://docs.microsoft.com/en-us/azure/active-directory/roles/administrative-units) - AD resource that contains other AD resources (users/groups)
- [Identity Governance](https://docs.microsoft.com/en-us/azure/active-directory/governance/identity-governance-overview)

### Azure RBAC (Role-Based Access Control)
- Follow least privileges policy : Grant narrow access for role
- Uses Azure Resource Manager for fine-grained authorization control within set scope (resouces)
- **Security Principal** - like a service account or managed identity for resource access
- **Role Definition** - list of ops that can be performed
- **Scope** - set of resources for access. Follows parent-child relationship in scope hierarchy
- Role assignments can be *Allow* or *Deny*
- RBAC is free with Azure subscriptions
- Built-in roles : *owner*, *contributor*, *reader*, *user access administrator*

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

### Azure Key Vault
- Integrated into AD - store secrets, keys and certificates (w multiple versions)
- [FIPS 140-2 compliant](https://csrc.nist.gov/publications/detail/fips/140/2/final)
- Set access policies or RBAC for data plane. Management plane RBAC only.

## 🔖 Implement and manage storage (15–20%)

### Azure Storage

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
| | **LRS** | **ZRS** | **GRS/RA-GRS** | **GZRS/RA-GZRS**|
|--|--|--|--|--|--|--|
|Node outage|✅|✅|✅|✅|
|Data center outage| |✅|✅|✅|
|Region-wide outage| | |✅|✅|

**For RA- variants read access for secondary region is available if primary region goes down*
- Lifecycle management: moving between hot\cool\archive

#### Azure File Storage
- File share accessible over [SMB](https://docs.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh831795(v=ws.11)) or [NFS](https://docs.microsoft.com/en-us/windows-server/storage/nfs/nfs-overview)

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

### Application Gateway
- Layer 7
- Route based on URL and other attributes.

### Point-to-Site VPN

### Site-to-Site VPN
## 🔖 Monitor and back up Azure resources (10–15%)
