## Design Identity, Governance, and Monitoring Solutions (25-30%)

### Design a solution for logging and monitoring

- [ ] design a log routing solution
- [ ] recommend an appropriate level of logging
  - [Alert Rules](https://docs.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-overview) :
    - Severity : 0-4 (critical, error, warning, info, verbose)
    - action to take on specific condition
    - Rule -> Resource -> Condition (signal and signal logic) -> Action Group
      - [Action Group](https://docs.microsoft.com/en-us/azure/azure-monitor/alerts/action-groups) : notification prefs defined by Azure sub owner.
        - Notification could be email, SMS, etc. Also ITSM (like ServiceNow) connector can be used.
        - Lots of options in Action Group with logical conditions on resources, for example

    - Log Analytics Workspace
    - Logging destination : Log analytics workspace (query and analyze), azure storage (backup, archive, audit), event hubs (can then stream to something like Splunk)
- [ ] recommend monitoring tools for a solution
  - Azure Monitor
    - Collects : 
      - application monitoring data
      - Guest OS monitoring data
      - Azure resource monitoring data
      - Azure subscription monitoring data
      - Azure tenant monitoring data
    - Diagnostics Logs :
      - different for each resource
      - one or more destinations available
        - event hubs, log analytics workspace, storage
      - can alter level of logging - information or critical for example
    - Azure Monitoring
    - Azure Monitor for Containers
    - App Insights

  - **Recomended Tools** :
    - Diagnostics : diagnostic log settings configured and route to destination
    - Health, Availability, Performance Monitoring : Azure Monitor Metrics and Logs routed to Log Analytics Workspace
    - Application Monitoring: Application Insights, 3rd party solutions (ex App Dynamics, DataDog)
    - Security Logs : Security Center (Log Analytics Workspace), 3rd Party Integration via Event hub

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

    - Azure Active Directory Domain Services (Azure AD DS)
      - provides managed domain services (ex. LDAP)
      - An Azure AD DS managed domain lets you run legacy applications in the cloud that can't use modern authentication methods
      - or where you don't want directory lookups to always go back to an on-premises AD DS environment.
      - You can lift and shift those legacy applications from your on-premises environment into a managed domain
      
Azure AD DS integrates with your existing Azure AD tenant. This integration lets users sign in to services and applications connected to the managed domain using their existing credentials. You can also use existing groups and user accounts to secure access to resources. These features provide a smoother lift-and-shift of on-premises resources to Azure.
### Design governance
- [ ] recommend an organizational and hierarchical structure for Azure resources
- [ ] recommend a solution for enforcing and auditing compliance

### Design identities and access for applications
- [ ] recommend solutions to allow applications to access Azure resources
- [ ] recommend a solution that securely stores passwords and secrets
- [ ] recommend a solution for integrating applications into Azure Active Directory (Azure AD)
  - [Manage user access (to applications) with access reviews](https://docs.microsoft.com/en-us/azure/active-directory/governance/manage-user-access-with-access-reviews) - Use AD access reviews.
    - Has list of reviewers
    - Can review Teams+Groups or by Application
    - More info here - [Create Access Review](https://docs.microsoft.com/en-us/azure/active-directory/governance/create-access-review)

  - [Azure AD Application Proxy](https://docs.microsoft.com/en-us/azure/active-directory/app-proxy/application-proxy) : allows access to on-prem applications through AD proxy. Uses an application proxy connector installed on the on-prem server.
    - Part of "Enterprise Application"

  - [Register app for Enterprise Application](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app)


- [ ] recommend a user consent solution for applications

## Design Data Storage Solutions (25-30%)

### Design a data storage solution for relational data
- [ ] recommend database service tier sizing
   
  - **Azure SQL Tiers**
 
   | Tier | Good For | Examples |
   |------|----------|----------|
   | Basic | Small database with single concurrent user | small db, single active operation, dev/test, small apps, 5 DTU, 2GB storage |
   | Standard | Medium-sized database that must support multiple concurrent connections | cloud apps, multiple ops, web apps, 10-100 DTU, 1 TB , 3000 DTU max|
   | Premium | Large db - support large number of concurrent connections/operations | high transaction volumes, large number of users, multiple ops, mission critical apps, 100-800 DTU, 4TB, 4000 DTU max |
 
 - **Third-party db options**
    - Managed :
      - MySQL
      - PostgreSQL
    - Not Managed :
      - Windows or Linux hosted variants of MySQL, or other databases
  
  - **Azure SQL Pricing Models**
    - [Azure Pricing Models](https://docs.microsoft.com/en-us/azure/azure-sql/database/service-tiers-dtu?view=azuresql)
    
    - vCore Pricing : independently scale, optimize price\perforamnce, choose hardware gen (gen4 - 24 logical CPIs; Gen5 - 80 CPUs)
      - General Purpose Tier
      - Business Critical
      - Hyperscale

    - DTU
      - Flexible compute sizes
      - All 99.99 SLA
      - Retention : 7 days for basic, 35 days standard/premium
      - IO : 2.5 IOPS per DTU for Standard/Basic, 48 IOPS for Premium
      - OLTP processing for Premium only

  - Caching 
    - Private caching
    - Shared caching

  - **Cosmos DB**
    - globally distributed
    - supports schema-less data
    - build highly responsive, always on apps with highly changing data
    - Consistency Levels : 5 levels
      - Strong : guaranteed write ops
      - Bounded Stateless : config how stale docs can be within replicas
      - Session : all r/w ops are consistent within user session
      - Consistent PRevix : ensures chnages are read in order
      - Eventual Consistency : Eventual consistency

  - **Big Data Solution**
    - ingest, store, prep\train, model and serve
    - SQL Data Warehouse
    - HDInsight (hadoop, spark, hive, etc)
    - Data Lake Analytics : on demand job service for big data
    - Databricks
      - [Databricks credential passthrough](https://docs.microsoft.com/en-us/azure/databricks/security/credential-passthrough/adls-passthrough)

   - **Azure Data Factory**
    - ETL, integration services
    - Facilitae data-drive workflows\pipelines
    - Connect, collect, transform, publish, monitor


- [ ] recommend a solution for database scalability
- [ ] recommend a solution for encrypting data at rest, data in transmission, and data in use
  - To ensure storage account is envrypted at rest, use Azure Storage Encryption

### Design data integration
- [] recommend a solution for data integration
- [] recommend a solution for data analysis

### Recommend a data storage solution
- [ ] recommend a solution for storing relational data
- [ ] recommend a solution for storing semi-structured data
- [ ] recommend a solution for storing non-relational data

### Design a data storage solution for non-relational data
- [ ] recommend access control solutions to data storage
  - [Shared Access Signatures](https://docs.microsoft.com/en-us/azure/storage/common/storage-sas-overview)
    - Grant limited access to Azure storage with SAS tokens. ie. Solution that allows access to a resource for a limited amount of time.
- [ ] recommend a data storage solution to balance features, performance, and cost
- [ ] design a data solution for protection and durability

## Design Business Continuity Solutions (10-15%)

### Design a solution for backup and disaster recovery
- [ ] recommend a recovery solution for Azure, hybrid, and on-premises workloads that meets
- [ ] recovery objectives (Recovery Time Objective RTO, Recovery Level Objective RLO, Recovery Point Objective RPO)

  | SLA | Downtime/week | Downtime/month | Downtime/year |
  |-----|---------------|----------------|---------------|
  | 90% | 16.8 hrs      | 72 hrs         | 36.5 days     |
  | 99% | 1.68  hrs     | 7.2 hrs        | 3.65 days     |
  | 99.9% | 10.1 min    | 43.2 min       | 8.76 hrs      |
  | 99.99% | 1.01 min   | 4.32 min       | 52.56 min     |
  | 99.999% | 6.05 sec  | 25.9 sec       | 5.26 min      |
  | 99.9999% | 0.605 sec | 2.59 sec      | 31.5 sec      |
  
- [ ] understand the recovery solutions for containers
- [ ] recommend a backup and recovery solution for compute
- [ ] recommend a backup and recovery solution for databases
- [ ] recommend a backup and recovery solution for unstructured data

### Design for high availability
- [ ] identify the availability requirements of Azure resources
- [ ] recommend a high availability solution for compute
- [ ] recommend a high availability solution for non-relational data storage
  - File Shares: https://docs.microsoft.com/en-us/azure/storage/file-sync/file-sync-deployment-guide?tabs=azure-portal%2Cproactive-portal
- [ ] recommend a high availability solution for relational data storage
  - https://docs.microsoft.com/en-us/azure/site-recovery/site-recovery-sql
  


## Design Infrastructure Solutions (25-30%)

### Design a compute solution
- [Decision tree for compute services (link)](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree)

  ![compute choices](https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/images/compute-choices.png)
  
- [ ] Recommend a virtual machine-based compute solution
  - VM Compute Types ([from here](https://azure.microsoft.com/en-us/pricing/details/virtual-machines/series/)):
    - VM (IaaS)
    - App Service (Managed PaaS)
    - Container Service
    - AKS
    - Functions
    - Azure Batch (managed service for running large-scale parallel things)
  
  | Type | Purpose |
  |------|---------|
  | A - Basic | Basic version - dev and test |
  | A - Standard | General-purpose |
  | B - Burstable | Can burst to full capacity when needed |
  | D - General Purpose | Enterprise apps. DS - premium storage |
  | DC - General Purpose Secured | Confidential multiparty data sharing, fraud detection, AML, blockchain, confidential usage analytics, intelligence analytics, confidential ML |
  | E - Memory optimized | High memory-to-CPU ratio. ES - premium storage |
  | F - CPU Optimized | High CPU-to-memory. FS - premium storage |
  | G - Godzilla | Very large instances ideal for large database and big data |
  | H - High Performance Compute | Higher disk throughput and IO |
  | M - Large Memory | Up to 3TB of RAM |
  | N - GPU | GPU-enabled |
  | SAP HANA on Azure | Purposely built instances for [SAP HANA](https://www.ibm.com/topics/sap-hana) |

  - Compute Managed Disk Options : 
    1. **Premium SSD** :
        - Max throughput per disk : 250 MiB/s
        - Max IOPS per disk : 7500 IOPS
          - P4: 32 GiB (managed only)
          - P6: 64 GiB (managed only)
          - P10: 128 GiB
          - P15: 256 GiB (managed only)
          - P20: 512 GiB
          - P30: 1024 GiB
          - P40: 2048 GiB
          - P50: 4095 GiB

    2. **Standard SSD** : 
        - Max throughput: 60 MiB/s
        - Max IOPS: 500 IOPS
        - Sizes (managed only):
          - E10: 126 GiB
          - E15: 256 GiB
          - E20: 512 GiB
          - E30: 1024 GiB
          - E40: 2048 GiB
          - E50: 4095 GiB

    3. **Standard HDD Disk** :
        - Max throughput: 60 MiB/s
        - Max IOPS: 500 IOPS
        - Sizes:
            - 1 GiB - 4 TiB (4095 GiB) - unmanaged
            - S4: 32 GiB
            - S6: 64 GiB
            - S10: 128 GiB
            - S10: 128 GiB
            - S15: 256 GiB
            - S20: 512 GiB
            - S30: 1024 GiB
            - S40: 2048 GiB
            - S50: 4095 GiB
  - Availability Sets:
    - Group 2 or more VM's into a set
    - Fault Domains and Update Domains
    - Fault Domains : up to 3 separate racks in an availabiilty set. If outage to one domain, application unaffected.
    - Update Domains : separation of underlying hosts for updating\maintenance.
    - Use availability set for each tier of the application.
    - Availability Zones : multiple zones per region. Can't have availability sets if zones are available for a region.

  - Scale Sets
    - can configure auto-scale rules
    - can scale based on a variety of metrics (transactions, cpu, scheduled, etc)
    - remember to account for sessions when scaling in on web servers.
    - can set min and max nodes
- [ ] recommend an appropriately sized compute solution based on workload requirements
  - **ACU** [Azure Compute Units](https://docs.microsoft.com/en-us/azure/virtual-machines/acu) : provides a way of comparing compute (CPU) performance across Azure SKUs.
- [ ] recommend a container-based compute solution
- [ ] recommend a serverless-based compute solution

### Design an application architecture
- [] recommend a caching solution for applications
- [] recommend a messaging architecture
- [] recommend an event-driven architecture
- [] recommend an automated deployment solution for your applications
- [] recommend an application configuration management solution
- [] recommend a solution for API integration

### Design migrations
- [ ] evaluate a migration solution that leverages the Cloud Adoption Framework for Azure
- [ ] assess and interpret on-premises servers, data, and applications for migration
- [ ] recommend a solution for migrating applications and virtual machines
  - Azure Migrate _appliance_ : lightweight appliance that the Azure Migrate: Discovery and assessment tool uses.
    - Deployed on-prem as physical or virtual
    - continually sends server metadata to Azure Migrate
    - Connects to Azure through ExpressRoute + microsoft peering.
    - Can connect to multiple vCenter Servers
    - Can discover up to 10k servers in VMWare, 5000 servers in Hyper-V, 1000 phusical servers w single appliance.
  - Azure Migrate:
    - Centralized hub to assess and migrate on-prem servers, infra, apps, data to Azure
    - **Discovery and Assessment**: discover + assess on-prem servers running VMWare, Hyper-V and physical
    - **Server Migration**: migrate vmware, hyper-v and physical servers and public cloud VMs to Azure
    - **Data Migration Assistant**: Assess SQL Server dbs for migration. 
    - **Database Migration Service**: Migrate on-prem dbs to Azure
    - **Movere**: Assess servers, SaaS - presents entire IT environment in single day.
    - **Web migration assistant**: Assess on-prem web apps and migrate to Azure.
    - **Azure Data Box**: Migrate offline data
- [ ] recommend a solution for migrating databases
- [ ] recommend a solution for migrating unstructured data

### Design network solutions
- [ ] recommend a network architecture solution based on workload requirements
  - OSI (Open Source Interconnection) 7 Layer Model
  
  | Layer | Layer Name |  Example | Devices or Protocols |
  |-------|------------|----------|----------------------|
  | 7 | **Application** | End-user layer | User applications, SMTP |
  | 6 | **Presentation** | Character code translation, data encryption or compression | JPEG, ASCII, GIF |
  | 5 | **Session**     | Sync or send to ports: session, name resolution, logging | RCP, SQL, NetBIOS |
  | 4 | **Transport**   | TCP, UDP | TCP, UDP, SPX |
  | 3 | **Network**     | Routing, traffic control, packets, subnets | Routers, IP, ICMP |
  | 2 | **Data Link**   | Frames, MAC address, Switch | Switch \ Bridge|
  | 1 | **Physical**    | Cables, hubs, etc | hub |
  
- [] recommend a connectivity solution that connects Azure resources to the internet
- [] recommend a connectivity solution that connects Azure resources to on-premises
networks
  - Site-to-Site VPN
    - S2S VPN gateway connection : connection over IPsec/IKE (IKEv1 or IKEv2) VPN tunnel
    - requires VPN device in enterprise DC w public ip address assigned to it
    - can't be behind a NAT
    - Can be used for cross-premesis or hybrid configurations
  - Point-toSite VPN
    - Connect individual people to network. Great for remote work situations.
    - No need for a VPN device or public ip address. (Can connect wherever Internet)
    - Supports Windows 7-10, Server 2008 - 2012
    - Throughput is 100Mbps
    - Doesn't scale easily to many workstations.

  - VPN Gateway SKU's
    - https://docs.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways

      | Generation | SKU(s) | Max s2s Tunnels | Max p2s sstp Connections | Max p2s IKEv2/OpenVPN connections | Throughput | Zone-redundant |
      |------------|--------|-------------|--------------------------|-----------------------------------|------------|----------------|
      | Gen 1      | Basic  | 10          | 128                      |  Not supported                    | 100 Mbps    | No   |
      | Gen 1      | gw1 - gw3 | 30       | 128                      | 250, 500, 1000                    | 650 Mbps, 1Gbps, 1.25 Gbps | No |
      | Gen 1      | gw1AZ - gw3AZ |  30  | 128                      | 250, 500, 1000                    | 650 Mbps, 1Gbps, 1.25 Gbps | Yes |
      | Gen 2      | gw2 - gw5 | 30, 100  | 128                      | 500, 1000, 5000, 10000            | 1.25 Gbps, 2.5 Gbps, 5 Gbps, 10 Gbps | No |
      | Gen 2      | gw2 - gw5 | 30, 100  | 128                      | 500, 1000, 5000, 10000            | 1.25 Gbps, 2.5 Gbps, 5 Gbps, 10 Gbps | Yes |
      
    - Gen1 :
      - Basic : max 10 tunnels, max 128 p2s connections
  - ExpressRoute
    - Customer Network -> Partner Edge (with circuit to Azure) -> Azure
    - Layer 3 connectivity between networks
    - Allows connectivity to all regions but can also add on premium addon to get global 
    - Dynamic routing
    - Redundancy along the way
    - Can take many months to procure and setup
    - Azure public/private or Microsoft peering require peering subnet (w public ip address for private\microsoft). 2 paths, each /30 CIDR range.
    - Unlimited vs Metered.
      - Unlimited option has higher cost but unlimited outbound traffic
      - Metered has predetermined fee for outbound traffic
    - Connectivity Models :
      - Cloud Exchange Co-location - equinex
      - Point-to-Point Ethernet Connection - dedicated w partner
      - Any-to-any (IPVPN) connection - over mpls wan type of scenario
    - Peering : 
      - All types require /30 address space on both peered subnets
      - Private Peering
      - Public Peering
      - Microsoft Peering
  - In Logic App: 
    - In multi-tenant Azure Logic Apps, you need the on-premises data gateway installed on a local computer and a data gateway resource in Azure
    - (https://docs.microsoft.com/en-us/azure/connectors/connectors-create-api-sqlazure?tabs=consumption)
    
- [ ] optimize network performance for applications
  - Default routing vs User-Defined routing (UDR)
    - Sometimes may need to route traffic through something else, in which case you can create a UDR and attach to subnet.
  - Default Routing:
    - If address within VNew address prefix : route to local VNet
    - If address within on-prem address prefixes or BGP routes - route to gateway
    - If address not part of VNet or BGP or LSN routes - route to internet via NAT
    - If destination is Azure datacenter address and ExpressRoute public peering enabled - route to gateway
    - If destination is Azure datacenter w S2S/ExpressRoute without public peering -  route to Host NAT for Internet path, but do not leave datacenter.
  - User defined routing :
    - https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-udr-overview
    - You can't create or remove system routes, but you can override some system routes with custom routes.

  - Providing application with inbound internet access :
    - Options :
      - Give service public ip
      - Put service behind LB with PIP
      - Use Virtual network appliance that has a PIP
- [ ] recommend a solution to optimize network security
- [ ] recommend a load balancing and routing solution
  - Basic Load Balancer :
    - Layer 4
    - Scoped to availability sets only
    - Supports up to 100 instances
    - Service monitoring
    - Automated reconfiguration
    - 5 tuple hash-based distribution
    - Internal and public options available
    - Open by default
  - Standard Load Balancer :
    - Layer 4
    - Supports up to 1000 instances
    - Any machine in vnet (vs availability set)
    - https support
    - Supports availability zones
    - Secure by default
  - App Gateway
    - Sticky sessions
    - Layer 7 load balancing
    - SSL offload
    - end-to-end SSL
    - web application firewall
    - URL-based content routing (routing based on decisions based on traffic attributes)
    - Requires own subnet
    - Highly available
    - Small, MEdium, Large
    - Single region (vs Traffic Manager or Front Door)
   
  - Traffic MAnager
    - Region based 

  - Traffic Manager vs Front Door
    - Traffic Manager handles any protocol while Front Door works onyl on HTTP
    - Traffic Manager : on-premis routing vs Front Door
