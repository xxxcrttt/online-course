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

