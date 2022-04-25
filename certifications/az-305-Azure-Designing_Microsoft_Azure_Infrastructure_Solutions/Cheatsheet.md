## Design Identity, Governance, and Monitoring Solutions (25-30%)

### Design a solution for logging and monitoring

- [ ] design a log routing solution
- [ ] recommend an appropriate level of logging
- [ ] recommend monitoring tools for a solution

### Design authentication and authorization solutions

- [ ] recommend a solution for securing resources with role-based access control
- [ ] recommend an identity management solution
  - **Active Directory**
    - **AD Connect**
      - Synchronization Services - responsible for matching between on-prem and cloud
        - Filtering : limit which objects are sychronized
        - Password Hash Synchronization : user can use same password on-prem and in cloud
        - Password Writeback : change password in cloud and write-back to on-prem
        - Device Writeback : update device in AAD and write-back to on-prem AD
        - Prevent Accidental Deletes : useful to help prevent 
        - Auto Upgrade : ensures AD Connect always up to date

      - Password Sync Options
        - Password Sync : Ensures password same in AD DS and AAD
        - Passthrough Authentication : When user logs into AAD, request forwarded to AD DS - single source
        - AD FS : Use AD Federation Service server to fully federate across AD DS and AAD, along with other services
      - AD Federation Services - hybrid deployment
      - Health Monitoring

    - **Cloud Authentication**
      - Cloud-Only

      - Password Hash Sync + Seamless SSO
        - Every 2 min, AD connect syncs up with On-Prem
        - Least effort required
        - Seamless SSO
        - Highly Availabile, Can deploy additional AD Connect Server in staging mode
        - No immediate enforcement in on-prem : consider running immediate sync if many changes done on-prem

      - Pass-Through Authentication + Seamless SSO
        - validation happens on-prem
        - Agents need to be installed with access to AD
        - More effort
        - Need 1 or more (recommended 3) agents installed on existing servers
        - Must have onprem AD controllers
        - Need outbound access to internet
        - Seemless SSO
        - Recommended to deploy 2 extra pass through agents

      - Federated Authentication
        - On-Prem does authentication
          - Third Party Providers
          - Federation proxies - rediredt to alt sign-in

    - **Single Sign On**
      - Provided by Azure AD Connect for users using Password Hash Sync or Pass-Through
    
    - **MFA**
      - Works by requiring 2 or more of the following verification methods :
        - Something you know (password)
        - Something you have (cellphone)
        - Something you are (biometrics)
      - Available : Phone Call, SMS, Mobile App (authenticator), Mobile app verification code, Third-party tokens

    - Self-Service Password Reset
      - Requires p2 premium license
      - none, selected, all
      - can choose number of methods required (1 or 2)
      - Default 180 days to re-confirm
      - https://aka.ms/sspr

      
- [ ] recommend a solution for securing identities
  - Identity Protection
    - Detect vulnerabilities and risky accounts
    - Investigating risk events
      - sending notifications, contextul info
    - Risk-based conditional access polcies

  - Protection Roles :
    - Global admin - full access, onboard identiy protection
    - Securiety admin - full access
    - Security reader - read-only access to identit protection

  - Privileged Identity Management (PIM)
    - Azure PIM
      - visibility into users with privileged access
        - Azure Resources
        - Azure AD
      - Enable on-demande administratove access
      - View admin history
      - Setup alerts
      - Require approvals

    - PIM process
      - Activiation process (via mfa, approval workflow, time restrictions)

    - Azure AD P2 License required

    - PIM Roles :
      - Pviileged Role Admin
      - Security Admin

### Design governance
- [] recommend an organizational and hierarchical structure for Azure resources
- [] recommend a solution for enforcing and auditing compliance

### Design identities and access for applications
- [] recommend solutions to allow applications to access Azure resources
- [] recommend a solution that securely stores passwords and secrets
- [] recommend a solution for integrating applications into Azure Active Directory (Azure AD)
- [] recommend a user consent solution for applications

## Design Data Storage Solutions (25-30%)

### Design a data storage solution for relational data
- [] recommend database service tier sizing
- [] recommend a solution for database scalability
- [] recommend a solution for encrypting data at rest, data in transmission, and data in use

### Design data integration
- [] recommend a solution for data integration
- [] recommend a solution for data analysis

### Recommend a data storage solution
- [] recommend a solution for storing relational data
- [] recommend a solution for storing semi-structured data
- [] recommend a solution for storing non-relational data

### Design a data storage solution for non-relational data
- [] recommend access control solutions to data storage
- [] recommend a data storage solution to balance features, performance, and cost
- [] design a data solution for protection and durability

## Design Business Continuity Solutions (10-15%)

### Design a solution for backup and disaster recovery
- [] recommend a recovery solution for Azure, hybrid, and on-premises workloads that meets
- [] recovery objectives (Recovery Time Objective [RTO], Recovery Level Objective [RLO],
- [] Recovery Point Objective [RPO])
- [] understand the recovery solutions for containers
- [] recommend a backup and recovery solution for compute
- [] recommend a backup and recovery solution for databases
- [] recommend a backup and recovery solution for unstructured data

### Design for high availability
- [] identify the availability requirements of Azure resources
- [] recommend a high availability solution for compute
- [] recommend a high availability solution for non-relational data storage
- [] recommend a high availability solution for relational data storage


## Design Infrastructure Solutions (25-30%)

### Design a compute solution
- [] recommend a virtual machine-based compute solution
- [] recommend an appropriately sized compute solution based on workload requirements
- [] recommend a container-based compute solution
- [] recommend a serverless-based compute solution

### Design an application architecture
- [] recommend a caching solution for applications
- [] recommend a messaging architecture
- [] recommend an event-driven architecture
- [] recommend an automated deployment solution for your applications
- [] recommend an application configuration management solution
- [] recommend a solution for API integration

### Design migrations
- [] evaluate a migration solution that leverages the Cloud Adoption Framework for Azure
- [] assess and interpret on-premises servers, data, and applications for migration
- [] recommend a solution for migrating applications and virtual machines
- [] recommend a solution for migrating databases
- [] recommend a solution for migrating unstructured data

### Design network solutions
- [] recommend a network architecture solution based on workload requirements
- [] recommend a connectivity solution that connects Azure resources to the internet
- [] recommend a connectivity solution that connects Azure resources to on-premises
networks
- [] optimize network performance for applications
- [] recommend a solution to optimize network security
- [] recommend a load balancing and routing solution
