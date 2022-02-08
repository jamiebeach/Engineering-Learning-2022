# AZ-104 Microsoft Azure Administrator Certification Cheat Sheet

[Exam Outline](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE4pCWy)


## Manage Azure identities and governance (15–20%)

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

### Azure Blueprint


### Azure Advisor
- 5 pilars : "Azure well-architected framework"
  - Cost optimization, Operational excellence, Performance efficiency, Security, Reliability



### Azure Service Health


### Scopes
Root -> Management Groups -> Subscriptions -> Resource Groups -> Resources

### Resouce Manager
- Handles deployments of resources



## Implement and manage storage (15–20%)

## Deploy and manage Azure compute resources (20–25%)

## Configure and manage virtual networking (25–30%)

## Monitor and back up Azure resources (10–15%)
