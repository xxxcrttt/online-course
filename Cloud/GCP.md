# [Understanding Google Cloud Fundamentals](https://www.linkedin.com/learning/paths/understanding-google-cloud-fundamentals)

## Google Cloud Fundamentals 

### 1. Google Cloud Compliance Requirements (合约、规定)
[Compliance resource center](https://cloud.google.com/security/compliance) --    
find information, download reports if you are working with the legal department. 

### 2. Google Cloud Resource Hierarchy 
[资源层次结构](https://cloud.google.com/resource-manager/docs/cloud-platform-resource-hierarchy?hl=zh_cn)

![image](https://user-images.githubusercontent.com/56160038/171853877-d38b9aeb-cb70-4698-bcb1-615b8735968b.png)

#### Managing Identity and access 
-- who can do what on which resource? [link](https://cloud.google.com/resource-manager/docs/creating-managing-projects?hl=zh_cn)

**Q1.** A general recommendation is to have one PROJECT per application per environment. 

**Q2.** You can assign IAM policies to any of the accounts, Google workspace / Google Group... 

### 3. Controlling and Optimizing Google Cloud Costs 
[billing](https://cloud.google.com/pricing?hl=zh-cn)

#### Optimization strategies
1. **Rightsizing** -- Optimize workloads by reducing hardware or using cloud-native services. 
2. **Discounts** -- Commit to specific machine types to lower overall cost for Google Cloud resources.
3. **Enable Guardrails** --Implement billing alerts and limits so you dont hav surprises!

### 4. Google Cloud Geographical Segmentation Strategy 
1. Zone resources -- Computer Engine VM instances, Persistent disks
2. Regional and global resources -- Static external IP addresses(regional), VPC network(global)

**Q1.** A multi-region / standard bucket provides the largest availability, there's no minimum storage duration. 

### 5. Support Options 
**SLA**: Service Level Agreement    
An agreement on a monthly uptime percentage on a covered Google Cloud service. 
[SLA](https://cloud.google.com/terms/sla)

**Premium Support**    
It offers unlimited 1:1 technical support for outages and defects, unexpected product behaviour, product usage questions, billing issues, 
feature questions, and more. You also have Customer Aware Support and are assigned a Technical Account Manager. 

## Learning Google Cloud Security 

### Introduction
9 catagories: Compute, Data Transfer, Internet of Things, Management Tools, Big Data, Cloud AI, 
Identity and Security, Networking, Storage and Database; 

**Zone**: Single deployment area for resources that are within a region. A single point of failure within a region -- US-East1, Europe-West4, etc.     
**Regions**: Large, independent geographic area that is a collection of zones. Low latency, fault-tolerant(故障容许) -- Las Vegas, Finland, etc. 

**Multi-Regions**: deploying resources in more than one region -- Asia, Europe, US etc. 

* Not every resource / all services can be expanded outsizde of a zone or a region; 
* Resources can be zonal, regional, or across multiple regions. 

Interact with seervices: Console, Command line interface or Client libraries. 

#### Shared Security Responsibility Model 
A cloud security framework that dictates the level of security responsibilities 
of both you and your chosen cloud services provider. 

Responsibility Chart: On-Prem(User), IaaS, PaaS, SaaS    
Google manages its infrastructure security, while you are responsible for your data's security.  

Cloud Service models: 
* **IaaS**: Infrastructure as a service -- need to access a wide range of computing infrastructure -- storage, networking and servers. 
* **PaaS**: Platform as a service -- need a base for the developers to test code and build applications
* **SaaS**: Software as a service -- remove the management of nay underlying infrastructure, want quick access to applications for their data. 

**Q1.** Who is responsible for protecting the data that is stored in physical disk?   
A: the user -- Although GCP ensure the avalability of physical disks, it is ultimately the users responsibility to protect the actual data stored on those disks. GCP has no responsibility for lost, deleted or unsecured customer data. 

**Q2.** Requirement -- The data must be fault tolerant, and the data cannot leave the origin country   
A: Deploy the resource in a single region, of the country of origin, across multiple availability zones.   
Regions provide fault tolerance as you can have your data redundancy across multiple zones without your data leaving the country. 

### Identity and Access Management(IAM)

#### How to build a resource hierarchy? 
**IAM**: Collective term that covers technologies, processes, and policies used to manage user identities. 

**Research Hierarchy**: A logical concept in which you set up how you rCG resources are organized.     
It consists of Orgainizational node and Folders, projects, resources; 

1. Easy management of the cloud resource
2. Enforce access restrictions on the cloud resource through policies.  

**Transitive inheritance**: Underlying resources inhent policy permissions from parent resources.    

1. Root Node: represents the organization, not required to have an organization node, but best practice to create one to keep track of prjects. 
2. Folder: children of the organization node, allow to logically isolate the projects, best practice to map and categorize folder structure. Folders can contain other folder. 
3. Project: children of folder, first step in creating a cloud resource, projects contains the underlying Google Cloud resources. 
Multiple prjects can be housed under individual folders or organization nodes. 
4. Resources: Actual Google Cloud services(Compute engine VM, Cloud storage, BigQuery DB), must be associated with a project, 
Each resource can only be assigned to one project at a time. 


#### Define and apply IAM policies
A **policy** is a collection of **bindings** that specify access controls for GC resources.    
A **bingding** specifies how **access** should be granted on a resource.    
You can create **policies** to apply on **resources** to **control access**.    

1. Members: User account, service account, google group, domain -- indentity or principal 
2. Roles: Collection of permissions that allow you to perform specific actions on GC resources. 
3. Conditions: Logical expressions that add constraints, in addition to a binding 

Apply policies:    
1. Transitive inheritance: the resources will always inherit the policy of their parent node. 
2. Direct Assignment

#### Choose the right role for your users 
* Who: refers to an identity associated with members in the cloud environment. Members include Google Account, service account, Google group,  Workspace(G Suite), or cloud identity domain. 
* What access: roles -- a collections of permissions that determine what operations a member can do on a resource. 
* Which resource: GC resources 

**Roles:**    
* Basic roles(primitive roles):  Existed prior to creation of GC IAM service.     
1. Owner: broad permissions to edit, manage, and set up billing for all resources. 
2. Editor: broad permissions to read and edit most resources.
3. Viewer: read-onlt permission to existing resources or data.

* Predefined role: preset roles that have fine-grained access control to the cloud resources.    
Compute Admin, App Engine Creator, Web Security Scanner Viewer.    
Predefined Roles provide the security principle of least privilege. 
* Custome Role: tailor a set of permissions in a role that better suits your business needs. 

New Google IAM features are automatically applied to basic and predefined roles only, and using custom roles requires high level of maintenance.

#### Service Accounts. 
-- special accounts for automated tasks.  
1. Default or Google-managed service accounts -- create when **first** utilize a GC service. Both service account and ket pair are created by GC. Google is tasked with rotating keys **regularly**. Automatically granted the primitive role of editor. **NOT** recommended for production workloads. 
2. User-managed service accounts -- created by user, can be created using Cloud console, gcloud command-line, IAM API, user own public and private portions of a key pair. Up to 100 service accounts can be created per project. 

#### IAM best practices
1. Always implement the principle of least privilege 
2. Create separate service accounts 
3. Roatet user-manafed service account keys regularly 
4. Manage resources by using projects 
5. Utilize Google Groups insteand of individual roles 
6. Limit the use of primitive roles by using predifined roles 

**Q1.** What type of resources can a Service Account Role be applied to?    
A: Virtual Machine -- A service account is a special kind of account used by an application or a VM instance, not a person. 

**Q2.** What provides access control to GC resources?   
A: Policies -- it is managed by IAM policies, which are attached to resources. 

### Infrasctructure Security 
#### Different computing services 
Compute Service offer multiple infrastructure and plat form services to handle the traffic and workload for all Google users.     
1. Compute Engine -- Virtual Machines 
2. App Engine -- Scalable web and mobile back end
3. Kubernetes Engine -- Container services 
4. Cloud Functions -- Lightweight compute solutions 

**Google Compute Engine(GCE)**     
Infrastructure as a service, create and manage virtual machines. Instances = Virtual Machine.     
Customer is responsible for full configuration lifecycle: ```creating instance, pick operating system, processors, RAM, Install and manage applications, update security patches```.   
Use preemptible(抢占式多任务处理 multi-task, 操作系统完全决定进程的调度方案) instances for cost savings.     

**Google App Engine**   
Platform as a services. Build, develop and host web applications. Great option for high-reliability, high-performance applications.   
Support multiple languages: ```Go, PHP, Java, Python```. Environment: standard and flexible. 

#### Compute service best practices 
**Defence-in-Depth Approach** (Information strategy)     
* Series of defense mechanisms and controls are layered throughout the network to protect data. 
* Securing services using identity and access management policies. 
* Secure network, use firewalls, load balance or encrypt. 

1. Isolate your production resources from the internet. 
2. Disable default service accounts. 
3. Apply the principle of least privilege. -- IAM recommander 
4. Enable log collection and monitor your systems. 

**Q1.** What service is the customer responsible for configuring, administering, and monitoring?    
A: Google Compute Engine -- GCE falls under the IaaS category, customers are responsible for the full configuration lifecycle of the service.

### Network Security 
#### Create a network using virtual private clouds(VPCs)
VPC: a virtual version of a physical network; offers same services as a physical network but virtualized for cloud environment.

VPC Benefits:   
* Considered a global resource, an instance with an IP address in any zone or region can communicate privately with each other within the same project, creating a global wide area network.
* Flexible and scalable.
* Shareable and provide isolation, can build an entire virtual network for the organization but still enforce isolation for teams.

1. In order to create a VPC, you must create a project -- logical control for billing and organization within the nevironment. Each project created has its own VPC. 
2. VPC are made up subnets -- logical subdivisions of an IP network. Subnets are a regional resource -- can only span within the same region. It is defined by a range of IP addresses. 
3. Firewall rules control network traffic flow. Firewall rules are enforced at the instance level. 
4. VPC peering -- allows internet resources to connect to other VPC networks; regardless if in the same project or organization.  Great option for organizations with multiple networks that need to communicate privately. 

#### How to build firewall rules
Firewall rules take action on the network traffic attemping to flow in and out of the network.    
Rules take the form of **allow** or **deny**. Rules can apply different types of ```traffic, protocal, port , services, or destinations.```

1. Firewall rules are stateful and always enforced, regardless the operating system or the VM is trun on or off. 
2. Rules are enforced at Instance, or virtual machine level. Serve as an isolation mechanism between virtual machines and other networks. Enforce isolation between one or more virtual machines. 
3. Google has predefined rules. 
* Your default network has 2 implied firewall rules: 
```
Outgoing connections = Allowed 
Incoming connections = Blocked
```
* Default rules can be overriden with higher priority firewall rules. A rule set with priority 0 is highest firewall rule. 
* SMTP(Simple Mail Transfer Protocol), associated with port 25, is always blocked. 
* DHCP(Dynamic Host Control Protocol), associated with port 67, is always allowed. 

#### Networking Best Practice 
* Ensure your environment is **manageable, reliable, and well understood** by everyone. 
* Use clear naming conventions for network resources. (Abbreviation and familiar terminology; Company name, business units, application code, region, status;)
* Utilize custom networks instead of default ones for production environments. 
* Segment and isolate sensitive data in separate VPC networks. 
* Utilize Google Cloud VPC FLow Logs for networking monitoring. -- Flow Logs are a networking service that records a sample of network flows sent to and from VMs.
* **Load balancer**: high-performance, scalable load balancing
* **Cloud Security Command Center**: security and risk management 
* **Cloud Armor**: network security service to defend against DDoS and app attacks. 
* **Cloud Identity Aware Procy**: uses identity and context to guard against apps and Vms. 

**Q1.** VPCs are a global resource, meaning an instance with an IP address, in any zone or region, can communicate privately with each other within the same project. Subnets are only regional resources.

**Q2.** How can you control the traffic coming into instances in your Google Cloud Network?   
A: Use firewall rules. -- Firewall Rules enable you to either allow or deny network traffic connections, to and from, your virtual machine resources based on your specific needs.

### Data Security

#### Understanding cloud storage
```Objects, Buckets, Projects, Organizations.``` 
* Objects -- An immutable(cannot be changed, only replayed with a new version) piece of data consisting of a file of any format. Any data uploaded to Cloud Storage. 
* Buckets -- Containers that store your objects. 

#### Encryption 
-- prevent harm to your data when stored in a public cloud.    
The process of converting information(plaintext) into an unrecognizable form(cipertext), especially to prevent unauthorized acces.. 
* CGP Service-Side Encryption:     
By default, data is encrypted on the server side before written to disk.    
Encryption that occurs after Google receives the data, but before the data is stored to Google's servers. 
* Additional Cloud Storage Encryption:    
1. Customer-supplied encryption keys(CSEK) -- Customer is responsible for encryption lifecycle, create and manage encryption keys. Google does not store keys on server. Only cryptographic hash is stored.       
2. Customer-managed encryption keys(CMEK) -- Google creates and managed encryption keys using Cloud Key Management Service(KMS), KMS is a cloud-hosted key management service.    
* Google does **NOT** handle client-side encryption. Client-side encryption is when your data is encrypted prior to being received by Google.   

#### Best Practices
* Do not use useer IDs, emails, project numbers, or names, or any personally identifiable information (PII) in the name of your cloud buckest or cloud projects. 
* Store your data in a region closest to your application users. 
* Never share credentials with anyone else. 
* Always use TLS(HTTPS) protocol to transport your data. 
* Protect against Accidental or Malicious Deletion -- Place retention policies on your buckets. Create object holds to prevent deletion until hold is removed. Use object versioning. 


**Q1.** The IT term for a university is moving documents and database to GCP, they want ot ensure maximum control over the encryption process of data stored at rest in Cloud Storage.   
A: Customer-supplied encryption keys(CSEK) -- it provides more control of the security of the encryption keys. 

**Q2.** making changes to an object stored in Cloud Storage:   
A: Objects are immutable(they can not be changed once upload) and therefore you must upload a new version to overwrite the existing one.

### Security Operations
#### Security Command Center
```Gather data, identify threates, Act on threats in the platform, Build-in services for full visibility```
* It enables enterprises to gain holistic views of your assets(GCP resources and security risks) with a focus on assets inventory, discovery search and management. 
* Key features: ```Assets discovery and inventory, sensitive data identification, application vulnerability detection, access control monitoring, anomaly detection```
* You can integrate third-party security tool with Security Command Center ro centralize your security management. 
* Security Command Center girves a centralized security managed to improve security posture. 

#### Security Operations Suite 
-- Combining operational processes from different business units.    
Cloud Operations: ```Full visibility, Loggings, Monitoring```    
* Use Google Cloud operations suite to monitor and log your data. 
* GCOS: formerly known as Stackdriver, it is a set of tools designed to help businesses -- Monitor, Troubleshoot, improve application performance/ 
* Logging: Fully managed service, collects all of the events into a single location. Data sources include Compute Engine instances, custom logs, and API; can expoprt logs to other services or third parties. 
* Monitoring: Fullt managed service, collects metrics, envents, and metadata to provide insight into the applications. Services include GCP, other Cloud service providers, and on-premises. 
* APM(Application Performance Monitoring): Offers advanced ovservability, includes ```Cloud Trace, Cloud Debugger, Cloud Profiler.```
1. Trace: Find bottlenecks occuring in environment and identify root cause. 
2. Debugger: Inspect state of running application without impacting user experience. 
3. Profiler: Gather usage to identify application performance issues. 


