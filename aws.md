# Cloud Computing

Cloud computing is the delivery of computing services—like servers, storage, databases, networking, software—over the internet ("the cloud").

Instead of owning and maintaining physical servers, you can:
- Rent resources on demand
- Pay only for what you use
- Scale up/down easily

There are 3 main types:
- IaaS (Infrastructure as a Service) – e.g., AWS EC2
- PaaS (Platform as a Service) – e.g., Heroku
- SaaS (Software as a Service) – e.g., Gmail, Dropbox

## Advantages of Cloud

1. Cost-Efficient – No need to buy and maintain expensive hardware. Pay-as-you-go model.
2. Scalability – Easily scale resources up or down based on demand.
3. Flexibility & Accessibility – Access data and apps from anywhere via the internet.
4. Disaster Recovery – Built-in backup and recovery options reduce data loss risks.
5. Automatic Updates – Providers handle software and security updates. 
6. High Performance – Global network of servers ensures fast performance and low latency.

## Types of Cloud

1. Private Cloud: Exclusively by one buisness or Organization.
2. Public Cloud: The cloud resources (like servers and storage) are ownder and operated by a third party cloud service Provider and delivered over the internet.
3. Hybrid Cloud: Often call 'the best of both worlds' hybird cloud combine on-premises infrastructure clouds so organisationn can reap the advantage of both.

## Service of Cloud

![Alt text](./assests/services-of-cloud.png)

## Global Infrastructure Layers

### Regions:
Geographic areas (e.g., Mumbai, Sydney). Each region comprises multiple, physically separated Availability Zones (AZs).

### Availability Zones (AZs): 
Essentially data centers within a region, designed to be isolated from failures in other AZs.

### Edge Locations / CDN: 
Servers positioned globally to accelerate content delivery using services like Amazon CloudFront.

## AWS OUTPOST
AWS Outposts lets you run AWS infrastructure and services on-premises (in your own data center or office), while still being fully managed by AWS.

### Key Features

- **On-Prem + AWS Integration**: Run AWS services like EC2, ECS, EBS, and RDS on physical servers installed at your location.

- **Low Latency**: Ideal for workloads needing ultra-low latency or local data processing.

- **Consistent APIs**: Use the same APIs, tools, and services as you do in AWS cloud.

- **Fully Managed**: AWS delivers, installs, manages, and supports the Outposts hardware.


### AWS WaveLength
AWS Wavelength brings AWS services to the edge of 5G networks, allowing developers to build apps that deliver ultra-low latency to mobile and connected devices.

#### 🚀 Key Highlights:

| Feature | Details |
|---------|---------|
| Purpose | Ultra-low latency apps (gaming, AR/VR, live video, IoT, ML) |
| Latency | 5–20 milliseconds (ms), much lower than traditional cloud access |
| Location | Deployed within telecom providers' 5G networks |
| Services Available | Subset of AWS: EC2, EBS, VPC, Load Balancer, etc. |
| Same Tools | Uses familiar AWS APIs & services, just deployed closer to end-users |



## part-2

## what is aws EC2?
EC2 stands for Elastic Compute Cloud, a key IaaS (Infrastructure as a Service) from AWS.

Offers scalable virtual servers (“instances”) that you can launch on-demand in the cloud.

initially, we use hypervisor to run multiple operting system . This is called virtualization.

-Scalability & Elasticity: Easily scale up or down based on workload.

-Pay-as-you-go: Only pay for compute time used.

-Variety of instance types: Options optimized for CPU, memory, storage, or GPU workloads.


## practical on creatig Ec2 remaining-12


## What is AWS AMI?
Amazon Machine Image: An AWS AMI (Amazon Machine Image) is a pre-configured template used to launch EC2 instances (virtual servers) on AWS.

### 🔹 Key Points:

*   **Contains**:
    
    *   OS (e.g., Linux, Windows)
        
    *   System settings
        
    *   Application server (optional)[ microsoft window sql server]
        
    *   Installed software (optional)
        
*   **UseCase**:
    
    *    Rapdi instance Deployment of EC2 instance
    *    Load Balancing and Sacaling.
    *    Environment Cloning
    *    Diaster Recovery

**Types**:

1.  **AWS-provided AMIs** – Basic OS like Ubuntu, Amazon Linux, etc.
    
2.  **Marketplace AMIs** – Provided by vendors (e.g., WordPress, Red Hat).
    
3.  **Custom AMIs** – Created by you for consistent deployment.



# 🌐 Private IP vs Public IP on AWS EC2 (Day 17)

## 🔹 Private IP
- Used for internal communication within the VPC.
- Static (doesn’t change while instance runs).
- Not accessible from the internet.

## 🔹 Public IP
- Assigned automatically at launch (if enabled).
- Used for internet access.
- Changes if the instance is stopped/started.

we can access the instance with  private ip  via public Ip instance. that means access the public IP instance then access the Private IP instance.

# 🌐 Types of AWS EC2 Instances(part -18)

![Alt text](./assests/Ec2instance-tyype.png)

## what is Nitro instance-
Normal instance access hardware access using hypervisor but nitro instance directly hardware bypassing the hypervisor. 


# 🌐 Networking Setting- 19

Q> what is AWS multi AZ(avaibility zone) in aws?

Multi-AZ (Multi Availability Zone) is a high-availability architecture in AWS where your resources (like EC2, RDS, etc.) are replicated across multiple Availability Zones within a region.


# 🌐 What is EC2 Security group? Day 20/100 :  part-1

An EC2 Security Group acts as a virtual firewall for your EC2 instances to control inbound and outbound traffic.


- **Attached to EC2 instances**.56+
- Works at the **instance level**, not at the subnet level.
- Define rules based on:
  - **Protocol** (e.g., TCP, UDP, ICMP)
  - **Port range** (e.g., 22 for SSH, 80 for HTTP)
  - **Source/Destination**:
    - IP address
    - CIDR block (e.g., 0.0.0.0/0)
    - Another security group

# why security group is statefulAn EC2 Security Group is called stateful because:

If you allow inbound traffic, the response traffic is automatically allowed—without needing an explicit outbound rule, and vice versa.



#  aws User Data Script: day 24
It’s a shell script (or cloud-init directive) you attach to an EC2 instance at launch time to automate setup tasks like installing software, updating packages, or configuring the server.


Your instance will automatically run this script once, on first boot.




# Aws Instance Termination Protection
A feature that prevents accidental termination (deletion) of your EC2 instance.


# Aws ec2 Placement Group:26

# Aws Tenancy: day 27
Determine how the physical hardware on which your instances run is shared with other AWS accounts.

1. Shared(Default)
2. Dedicated Instance (no shared beteen physical host )
3. Dedicated Host(full control)



# AWS Pricing Plan: day 28;

![Alt text](./assests/Pricing_plan.png)


# elastic IP :Day 32

We know every time when we restart the instance then new IP address assign. But If we want to use the same ip,then we can purchase the elastic IP.



# what is instance Store? day:34

In AWS, Instance Store is temporary block-level storage physically attached to the host machine. Here's a quick breakdown:
Also called ephemeral storage.
Provides high-speed, low-latency storage.
Data is lost when the instance stops, terminates, or fails.

## what is Elastic Block Storage (EBS)?

Amazon EBS (Elastic Block Store) is persistent block-level storage for EC2 instances.

Data persists even after instance stops or terminates.
Can attach/detach volums across instance.
Data stored in multiple AZs
![alt text](assests/Instance-store-ebs.png)
## Difference between EC2 instance store and EBS store
![alt text](assests/Instance_ebs_diff.png)

# AWS EBS Volume Types: GP2, GP3, and Provisioned IOPS

Amazon Elastic Block Store (EBS) provides persistent block storage for EC2 instances. Below are the key general-purpose and performance-oriented EBS volume types.

---

## 1. General Purpose SSD (gp2)

- **Purpose**: Balanced price/performance for a wide variety of workloads.
- **Baseline Performance**:
  - 3 IOPS per GB (e.g., 100 GB = 300 IOPS)
  - Up to 16,000 IOPS per volume
- **Burst Performance**:
  - Volumes under 1 TB can burst to 3,000 IOPS using a credit system.
- **Max Throughput**: 250 MB/s
- **Use Cases**:
  - Boot volumes
  - Small to medium-sized databases
  - Development and test environments
- **Limitation**:
  - Performance tied to volume size.

---

## 2. General Purpose SSD (gp3)

- **Purpose**: Successor to gp2 with better performance at lower cost.
- **Baseline Performance**:
  - 3,000 IOPS baseline regardless of volume size
  - Up to 16,000 IOPS
- **Throughput**:
  - 125 MB/s by default
  - Can be provisioned up to 1,000 MB/s
- **Benefits**:
  - Decoupled IOPS and throughput from volume size
  - 20% lower cost than gp2
- **Use Cases**:
  - Similar to gp2 but more cost-efficient and predictable
  - High-performance web servers
  - Gaming and streaming apps

---

## 3. Provisioned IOPS SSD (io1/io2)

- **Purpose**: High-performance storage for mission-critical applications.
- **Provisioned IOPS**:
  - io1: Up to 64,000 IOPS (Nitro-based EC2)
  - io2: Up to 256,000 IOPS (Nitro-based EC2)
- **Throughput**:
  - io1: Up to 1,000 MB/s
  - io2: Up to 4,000 MB/s
- **Durability**:
  - io2 has 99.999% durability (higher than io1)
- **Use Cases**:
  - Large relational/NoSQL databases (e.g., Oracle, SQL Server, MongoDB)
  - Critical workloads requiring sustained high IOPS

---

## Summary Table

| Volume Type | Max IOPS | Max Throughput | Baseline IOPS | Cost-efficiency | Use Cases |
|-------------|----------|----------------|----------------|------------------|-----------|
| gp2         | 16,000   | 250 MB/s       | 3 IOPS/GB      | Moderate         | General-purpose workloads |
| gp3         | 16,000   | 1,000 MB/s     | 3,000 IOPS     | High             | Cost-effective performance |
| io1/io2     | 64K/256K | 1GB/s–4GB/s    | Provisioned    | Low (premium)    | High IOPS, mission-critical apps |

---

## Choosing the Right Volume Type

- Use **gp3** over gp2 for most general-purpose needs.
- Use **io1/io2** for databases and applications with high IOPS/throughput/durability needs.



# AWS Snapshot: Day 40

## What is a Snapshot?

A **snapshot** in AWS is a point-in-time backup of an Amazon EBS (Elastic Block Store) volume.

## Key Features

- **Backup**: Stores a backup of your EBS volume.
- **Incremental**: Only changes made after the last snapshot are saved.
- **Stored in S3**: Though not directly accessible through the S3 interface.
- **Restoration**: Can be used to create new EBS volumes or restore old ones.
- **Use in AMIs**: Can be used to create Amazon Machine Images (AMIs).

## Use Cases

- **Disaster Recovery**: Restore data after failure.
- **Data Migration**: Move data between regions or accounts.
- **Version Control**: Maintain different states of data over time.

## How to Create a Snapshot

### Using AWS Console:
1. Go to EC2 Dashboard.
2. Click on "Volumes" under Elastic Block Store.
3. Select a volume.
4. Click on **Actions > Create Snapshot**.
5. Provide a name and description, then create.

### Using AWS CLI:
```bash
aws ec2 create-snapshot --volume-id vol-1234567890abcdef0 --description "My snapshot"
```

# Day - 41 : Practical of AWS snapshot and their uses

[link](https://www.youtube.com/watch?v=y3ORzlAqTIU&list=PLIm9KY-ideOsCuwMRoX1ltMZGuNZeBrRp&index=41)

# DAY - 42: AWS Fast Snapshot Restore (FSR)

## 🚀 What is Fast Snapshot Restore?

**Fast Snapshot Restore (FSR)** is an AWS feature that enables **low-latency, fully-initialized EBS volumes** from snapshots. Without FSR, volumes created from snapshots may experience **initial I/O latency** as data is loaded lazily from Amazon S3.

## 🧠 Why Use FSR?

- Avoid performance hit during initial read operations.
- Ideal for **production workloads**, **disaster recovery**, and **automated scaling**.
- Speeds up instance launch time from snapshots (especially for large EBS volumes).

## ✅ Key Features

- Supported on **EBS General Purpose SSD (gp2, gp3)** and **Provisioned IOPS SSD (io1, io2)**.
- Enabled **per Availability Zone**, **per snapshot**.
- Charges **per AZ per hour** while FSR is enabled.

## 💸 Pricing

You are charged **per snapshot per Availability Zone per hour** where FSR is enabled.  
Refer to official pricing: [AWS EBS Pricing](https://aws.amazon.com/ebs/pricing/)

## ⚙️ Enabling FSR (CLI Example)

```bash
aws ec2 enable-fast-snapshot-restores \
  --source-snapshot-ids snap-1234567890abcdef0 \
  --availability-zones us-east-1a
  ```

# Day 43: EBS Lifecycle Manager (DLM) – Automated Snapshots and Backup

## 🔹 What is EBS Lifecycle Manager (DLM)?

[EBS Lifecycle Manager](w) is an AWS feature that **automates the creation, retention, and deletion of Amazon EBS snapshots**. It helps enforce backup policies without manual intervention.

---

## 🔹 Key Features

- ✅ **Automated Backups**: Schedule snapshot creation based on policies.
- ♻️ **Retention Rules**: Automatically delete old snapshots after a specified time.
- 🔒 **Cross-account Copy**: Share and copy snapshots to another AWS account.
- 📅 **Daily, Weekly, Hourly** schedule support.
- 🔁 **Fast Snapshot Restore (FSR)** integration.

---

## 🔹 How It Works

1. **Create a Lifecycle Policy**
   - Define target resources (via **tags**).
   - Set schedule frequency (e.g., daily at 5 AM).
   - Configure retention (e.g., keep 7 days of backups).
2. **DLM runs automatically** based on your rules.
3. **Snapshots are created and deleted** without manual effort.

---
# What is EFS? | AWS Elastic File System DAY:44

## 🔹 Overview

[Amazon Elastic File System (EFS)](w) is a **fully managed, scalable, NFS-based cloud file storage** system. It allows multiple [EC2 instances](w) to access the **same file system simultaneously**, making it ideal for **shared storage** use cases.

---

## 🔹 Key Features

- 📂 **Shared Storage**: Multiple EC2 instances across **Availability Zones** can mount the same EFS.
- 📈 **Elastic**: Automatically scales up/down as files are added or removed.
- 🔒 **Secure**: Integrated with [IAM](w), [VPC](w), [KMS](w) for access control and encryption.
- 🌐 **Highly Available**: Data is stored redundantly across multiple [AZs](w).
- 🏷️ **POSIX-compliant**: Supports standard Linux file permissions.

---

## 🔹 Use Cases

- 🖥️ **Web server farms** (e.g., Apache, Nginx)
- 📊 **Big data analytics**
- 📁 **Content management systems**
- 🤝 **Home directories and user file storage**
- 🧠 **Machine learning workloads**

---

## 🔹 EFS vs Other Storage Options

| Feature          | EFS                         | EBS                        | S3                      |
|------------------|------------------------------|-----------------------------|--------------------------|
| Access           | Shared (multi-AZ)            | Single EC2 instance         | Web/App access           |
| Protocol         | NFS                          | Block storage               | HTTP-based (object)      |
| Use Case         | Shared file system           | Boot volumes, databases     | Static content, backup   |
| Scaling          | Auto                         | Manual                      | Auto                     |

---

## 🔹 Mounting EFS

1. **Create EFS file system** in the AWS Console.
2. **Attach to EC2** via mount targets in VPC subnets.
3. **Mount using NFS** from EC2:
```bash
sudo mkdir /mnt/efs
sudo mount -t nfs4 -o nfsvers=4.1 fs-12345678.efs.us-east-1.amazonaws.com:/ /mnt/efs
```
# AWS EFS: Day - 45 
![alt text](/assests/efs.png)

When we create a EFS file system then we can customized it based on our requirment.

## Option Avilable for customization:

Storage Class
  - standar: Storage data redundant.
  - One Zone: stores data redundancy within a single AZ.

LifeCycle Management- 
   - Transition into IA - It will keep our cold data  in infrequent access and give you. 
   - Transition out ot IA - if you access your data then automatically keep that in standard storage.


## Performance Setting:
 Through Mode- How much data you can store in your strage. 
 Enhanced-
 Burstinng - if you store 1 GiB data then performance will be 1kiB that means how much data you store that much performance is you get.

 Enhanced 
  >elastic- how much need ? \
  >provisioned- you can enter your requirement.



# 46 -labs

# what is  amazon FSX?                                 
>It is a fully managed file storage service provided by AWS. \
> launch and run feature and highly optimize third party file system
> You can access FSX file system from 
   - EC2 instance
   - Amazon ECS
   - EKS
  - On premises
  > The services is designed to support various workloads , such as 
    - Amazon fsx for NetApp ONTAP.
    - amazon fsx for openzf.
    - amazon fsx for windows file server.
    - amazon fsx for lustre

## amazon fsx Benefits;
 - fully managed
 - scalable
- performance
- secure
- cost-effective

## use cases for Amazon FSX 
 - list and shift of windows based application
 - file sharing and collaboration
 - High Performance computing(HPC) workloads
 - Backup and disaster recovery

# What is NetApp ONTAP?
1. NetApp is MNC company known for its data management storage,formallt known as netwok appliance.
2.Netapp provides know for NAS(Network attached stroage) product and services and holding a resputation for reliabilty and services.\
3. NetApp provides these data management services.
  - Data Storage
  - Data Protectionj
  - Data Management
  - Data Sharing

4. NetApp one of the most significant and well known flagship storage operating system is NetApp ONTAP.



## subtopic -ONTAP 
1. ONTAP is essentially a operating system for data management.
2. Just like the operating system on your computer handles all your files and runs your program , ONTAP managest all the data storage tasks for large buisness.
3. NetApp ONTAP  comes in various form, designed to suit different deployment methods and buisness needs.
4. Each product under the ONTAP umberalla maintains the core functionalities of ONTAP but is is tailed for specfic sceario.
5. Here is the list 
 - ONTAP-9: This is flagship ONTAP software.Operated on dedicated netapp hardware.
 - ONTAP select : ONTAP select is software defined storage solution.Deployed as a virtual appliances on a company existing hardware.
  - Cloud Volume ONTAP ( CVO): specially designed for cloud environement. Cloud Volume ONTAP is the ONTAP softwar used in cloud services like aws, google cloud, Azure.it provied same ONTAP experience in the cloud. 
### ONTAP Feature :
 - latency < 1ms
  - Max throughput per file system 4-6GB
  - cliet compability: Window , linux , macos,
  - Protocol support : SMB , NFS,  ISCSI(shared block storage)
  - AWS computer:EC2, ECS, EKS
  - Active directory support
  - Deployment OPtions: single AZ, Multi AZ
  - Avaiblity SLA : single Ax, multi AZ


  










