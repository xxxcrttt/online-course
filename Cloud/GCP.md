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

