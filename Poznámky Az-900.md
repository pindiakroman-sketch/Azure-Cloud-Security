# Az-900-John Savils youtube+Microsoft Learn 06.05.2026

### Kurz Az-900
Video n.:20
https://www.youtube.com/watch?v=jNBcXnMTo9s&list=PLlVtbbG169nED0_vMEniWBQjSoxTsBYS3&index=22

## What is a Storage Account:
<img width="935" height="308" alt="image" src="https://github.com/user-attachments/assets/90316551-fee4-4390-b472-16c390de709e" />

<img width="943" height="602" alt="image" src="https://github.com/user-attachments/assets/3db2ee0d-491e-4bf5-b6e3-08650393d8ec" />

<img width="948" height="479" alt="image" src="https://github.com/user-attachments/assets/ba76aa5a-d491-4561-9def-32edbf6a056e" />

# Account kind
Storage account kind is a set of policies that determine which data services you can include in the account and the pricing of those services. 
There are four kinds of storage accounts:


The core advice is to choose the Resource Manager deployment model and the Standard - StorageV2 (general purpose v2) account kind for all your storage accounts. 
For new resources, there are few reasons to consider the other choices.


<img width="875" height="288" alt="image" src="https://github.com/user-attachments/assets/ff27f5fb-c3f0-4734-9149-c302c01786a1" />


# Excercise:Exercise - Create a storage account using the Azure portal

<img width="889" height="522" alt="image" src="https://github.com/user-attachments/assets/9f6d3f2d-3427-46d9-9c70-414fd04dfc86" />
_____________________________

Performance-I choose standard(premium one is for faster access).
Redundancy-I choose (LRS) There is no need to pay for event of catastrophic scenarios,,, (GRS-Geo redundant Storage).If happens something really catastrophic, i have fresh content from my users.(it is a surf report web app).
Require secure transfer for REST API operations-Better to activate, (enable) → everything goes through HTTPS (šifrované, bezpečné) 🔒
Allow enabling anonymous access on individual containers-Check. Blob containers, by default, don't permit anonymous access to their content. This setting allows authorized users to selectively enable anonymous access on specific containers.
Enable storage account key access-Check. We want to allow clients to access data via SAS-To znamená že povolím dočasný prístup k dátam
Default to Microsoft Entra authorization in the Azure portal-Uncheck. Clients are public, not part of an Active Directory.-nepotrebuješ firemné prihlásenie, ideš klasickým verejným prístupom.
Minimum TLS version-Select Version 1.2 from dropdown list. TLS 1.2 is a secure version of TLS, and Azure Storage uses it on public HTTPS endpoints-najbezpečnejší typ zašifrovanej komunikácie.
Hierarchical Namespace-Uncheck-It is a special funcion for large objets of data.You only work with basic blob storage.
Enable SFTP-Default-nepracuješ s SFTP 
Enable network file system v3-default-je to protokol pre linuxove servery,ty pracuješ len z blobmi, nie s file share cez NFS.
Allow cross-tenant replication-uncheck-Vyžaduje Azure AD-to teraz nevyužívaš...nepotrebuješ posielať dáta do ineho tenant ID.
Access tier-Hot-najlacnejšie pre často používané dáta.V tomto cvičení dôležité hot-rýchly prístup vhodný pr dáta ktoré sa budú často čítať.
Network access-Enable-povolenie internetového prístupu
Routing preference-Microsoft network routing-We want to make use of the Microsoft global network that is optimized for low-latency path selection.
Enable point-in-time restore for containers-Uncheck-Not necessary for this implementation-vráti kontajner do stavu z určitého času, nepotrerebne.
Enable soft delete for blobs-Uncheck-ked omylom zmažeš súbor (blob), vieš h obnoviť, tento prípad to nevyžaduje.
Enable soft delete for containers-Uncheck-umožní obnoviť zmazaný kontajner, nepotrebne,,, idem len základné nastavenia
Enable soft delete for file shares-Uncheck-obnovíš omylom zmazaný súbor alebo celý share vo file share službe... toto cvičenie file shares nepoužíva,
Enable versioning for blobs-Uncheck-ukladá všetky verzie jedného blobu (všetky prechádzajúce úpravy súboru).Nepracujem s historiou súboru.
Enable blob change feed-Uncheck-zaznamenáva všetky zmeny v storage účte-logy zmien.Nepotrebne...nepotrebujem audit
Enable version-level immutability support-Uncheck-Immutability-súbor sa nedá zmeniť ani zmazať počas určenej doby(dôležité pre banky,archívy,compliance).Cvičenie nepracuje s politikami WORM.nechcem blokovať zmeny súborov takže to nechávam vypnuté

# Prečo sú dobré tagy?
project-ak máš 30 Storage účtov, hned vieš ktorý patrí surf appke
Environment-dôležité pre security policies
Owner-Kto to spravuje
Datatype/Data classification/ cloud security must have-firma potrebuje vedieť, aké dáta skladujú.(UserContent)-videá,fotky.Je to klasifikované ako public=nízke riziko.

## Summary

Storage accounts let you create a group of data management rules and apply them all at once to the data stored in the account: blobs, files, tables, and queues.

If you tried to achieve the same thing without storage accounts, the end product would be tedious and error-prone. For example, what are the chances that you could successfully apply the same rules to thousands of blobs?

Instead, you capture the rules in the settings for a storage account, and those rules are automatically applied to every data service in the account.


_____________________________________________________

## Video n.21:-Data Movement and Migration Options-
https://www.youtube.com/watch?v=jNBcXnMTo9s&list=PLlVtbbG169nED0_vMEniWBQjSoxTsBYS3&index=22




| Tool             | Purpose               |
| ---------------- | --------------------- |
| Azure File Sync  | Sync SMB file servers |
| Storage Explorer | GUI upload/download   |
| AZCopy           | Automation + sync     |
| Azure Migrate    | VM/database migration |
| Data Box         | Offline data transfer |


# Azure provides multiple ways to move data:

online over the network
offline using physical devices

# The best option depends on:

data size
available bandwidth
workload type
automation requirements
whether you are migrating files, VMs, or databases

# Azure File Sync
What it is

A service that synchronizes Windows SMB file servers with Azure Files.

Local file servers sync through a central Azure file share.

# When to use it
hybrid file server environments
migration to Azure Files
resiliency scenarios
multiple office locations
Important Notes
file servers do NOT sync directly with each other
all synchronization happens through the Azure file share
supports cloud tiering
Cloud Tiering

Less frequently used files exist only in Azure.

Locally, only a placeholder/link remains.
When a user opens the file, it is automatically downloaded again.

Mental Model-pre predstavu

“Like OneDrive for enterprise file servers.”

# Azure Storage Explorer
What it is

A GUI application for managing Azure Storage resources.

What it can do
upload/download files
manage blob containers
manage file shares
interact with queues
interact with tables

# When to use it
manual operations
smaller data transfers
ad hoc uploads/downloads
Mental Model

“File Explorer for Azure Storage.”

# Storage Browser (Azure Portal)
What it is

A web-based version of Storage Explorer built directly into the Azure Portal.

When to use it

Quick uploads/downloads without installing a desktop application.

# AZCopy
What it is

A command-line tool for automated data copy and synchronization.

When to use it
scripting
automation
large-scale transfers
scheduled jobs
Important Notes

Supports:

local ↔ Azure
Azure ↔ Azure
AWS/GCP → Azure
Major Advantage

Azure-to-Azure transfers are server-side.

Data does not pass through your local machine.


# Azure Migrate
What it is

A migration service for:

virtual machines
databases
physical servers
What it can do
workload assessment
Azure SKU recommendations
replication
cutover/migration
Supported Sources
VMware
Hyper-V
bare-metal servers
Mental Model

“A migration orchestrator for Azure.”

# Azure Data Box
What it is

An offline migration solution using physical devices.

Used when:

internet bandwidth is limited
datasets are extremely large

# Data Box Disk
What it is

Encrypted SSD disks shipped by Microsoft.

Use Case

Importing data into Azure.


# Data Box
What it is

A physical network appliance for large-scale offline transfers.

Capacity

~80 TB usable storage.

Workflow
Microsoft ships the device
Copy data via SMB/NFS
Ship the device back
Microsoft uploads the data into your storage accounts

# Data Box Heavy
What it is

A larger enterprise version of Data Box.

Capacity

~770 TB

Use Case

Massive enterprise-scale migrations.

______________________________________________

Video.n.23
https://www.youtube.com/watch?v=22z9ARaKlbU&list=PLlVtbbG169nED0_vMEniWBQjSoxTsBYS3&index=23
Benefits and Usage of Azure IoT Services

| Service      | Purpose                           |
| ------------ | --------------------------------- |
| IoT Hub      | Custom IoT communication platform |
| IoT Central  | Ready-made IoT SaaS solution      |
| Azure Sphere | IoT security                      |

# What is IoT (Internet of Things)

 IoT = devices with microcontrollers connected to the cloud.

Devices can:

send telemetry/data to the cloud
receive commands/updates
communicate with other devices

Benefits:

remote management
firmware updates
analytics
predictive maintenance

Downside:

larger attack surface → requires strong security and authentication

# Azure IoT Hub
Purpose

Core Azure service for communication with IoT devices.

Features
device-to-cloud telemetry
cloud-to-device commands
file uploads
request/response communication
Device Twin

Virtual representation of a device inside Azure.

Applications communicate with:

the device twin
instead of directly with the physical device.

Use cases:

firmware updates
restart commands
device state tracking

When to Use

Use when:

building a custom IoT solution
writing your own application/code
working directly with SDKs/APIs

IoT Hub = more developer-oriented.

# Azure IoT Central
Purpose

Ready-made SaaS IoT platform built on top of IoT Hub.

Features
dashboards
device templates
starter applications
simulated devices
rules engine
GUI-based management
Example Rule

IF:
temperature > threshold

THEN:

send email
create ITSM ticket
trigger Azure Function
When to Use

Use when:

you want minimal coding
you need fast deployment
you want built-in dashboards/templates

# IoT Central = more managed / low-code solution.

# Azure Sphere
Purpose

Provides end-to-end security for IoT devices.

Components
Azure Sphere MCU
Custom Linux-based OS
Azure Sphere Security Service (AS3)
Security Features
certificate-based authentication
integrity verification
anti-tampering protection
When to Use

Use when:

security is critical
medical devices
industrial systems
financial/sensitive environments

Azure Sphere is typically combined with:

IoT Hub
IoT Central

# Video.n.24-Benefits and Usage of Big Data and Analytics Services

## Basic Flow of Data

Sources → Extract → Store → Transform → Analytics

Modern approach:
- ELT instead of ETL
- Raw data is first stored in Data Lake
- Transformation happens later

Why?
- Storage is cheap
- Keeps original data
- Future reprocessing is possible

---

# Important Concepts

## ETL
Extract → Transform → Load

Traditional model:
1. Extract data
2. Transform immediately
3. Load into database

Problem:
- Some useful data may be lost during transformation

---

## ELT
Extract → Load → Transform

Modern cloud approach:
- Store raw data first
- Transform later when needed

Benefit:
- More flexibility for future analytics

---

# Azure Services

## Azure Data Lake Storage Gen2
Cheap, scalable storage for raw/unstructured data.

Used for:
- keeping original data
- near infinite scale
- analytics pipelines

Think:
"Raw storage for everything"

---

## Data Transformation

Transformation includes:
- cleaning missing values
- removing duplicates
- formatting data
- reshaping data ("wrangling")

Goal:
Prepare data for analytics.

---

## Azure Data Factory
Orchestration service.

Responsible for:
- connecting to sources
- moving data
- triggering transformations
- loading data into destination systems

Think:
"Pipeline manager"

---

## HDInsight
Managed open-source analytics frameworks.

Includes:
- Hadoop
- Spark
- Kafka
- Hive
- Storm
- HBase

Goal:
Run big data tools without manually managing infrastructure.

---

## Hadoop
Disk-based distributed processing using MapReduce.

Good for:
- very large datasets
- distributed computation

---

## Spark
Memory-based analytics engine.

Faster than Hadoop because processing happens in RAM.

Supports:
- Python
- Scala
- SQL
- Java
- R

Used for:
- batch processing
- transformations
- analytics

---

## Kafka
Streaming ingestion platform.

Used when:
- continuous data arrives constantly
- IoT / sensors / live systems

Think:
"Massive real-time data pipe"

---

## Azure Databricks
Managed Databricks service built on Apache Spark.

Features:
- collaborative analytics
- notebooks
- Delta Lake
- scalable processing

Think:
"Advanced Spark analytics platform"

---

## Delta Lake
Layer on top of Data Lake.

Adds:
- versioning
- transactions
- auditing

---

## Azure Synapse Analytics
Unified analytics workspace.

Combines:
- data integration
- big data analytics
- BI
- machine learning

Think:
"All-in-one analytics platform"


# video.25-Benefits and Usage of AI Services
Azure AI Services Overview
# 1. Why use AI services?


identify patterns in data,predict future outcomes,understand language, speech, images,Approaches

Machine learning → train your own model


AI services → use ready-made AI APIs


# 2. Azure Machine Learning (AML) – custom platform 

Use AML when:you need a custom model,you want full control,you need advanced customization



# 3. Azure Cognitive Services – prebuilt AI
No need to build your own models.
Just call APIs.
Key point
fast setup
low-code
ready-made AI



# 4. Azure Bot Service – conversational AI
Build chatbots and virtual assistants.
Workflow
user sends message/speech,bot understands intent,bot checks knowledge base,bot sends response


Can use:


Language services


Speech services


other Cognitive Services


Deployment:web apps,Teams,mobile apps

# 5. Three main Azure AI offerings

Take-away


AML → build your own AI


Cognitive Services → use Microsoft AI APIs


Bot Service → create conversational assistants


All can be exposed as APIs/endpoints for applications.


# video n.26 Benefits and Usage of Serverless Technologies:

```md
# Serverless Technologies (AZ-900)

## Serverless
- no server management
- pay only when code runs
- event-driven

Examples:
- file upload
- queue message
- HTTP request
- scheduled task

---

# Azure Functions
Run custom code on events.

Use when:
- you need backend logic
- you want automation with code
- you need scalable compute

Features:
- supports .NET, Python, JavaScript, Java...
- usually stateless
- auto scaling

Durable Functions:
- stateful workflows
- long-running processes

---

# Azure Logic Apps
Low-code workflow automation.

Use when:
- connecting services
- automating business processes
- minimal coding required

Features:
- visual designer
- many connectors
- fast integrations

Examples:
- Outlook
- SQL
- SharePoint
- Salesforce

---

# Functions vs Logic Apps

| Functions | Logic Apps |
|---|---|
| write code | visual workflows |
| developer-focused | low-code |
| custom logic | integrations |

---

# Practical Rule
- Need custom code → Azure Functions
- Need workflow automation/integration → Logic Apps

____________________________________________


# video.n.27 Benefits and Usage of DevOps Technologies (AZ-900)

## DevOps
DevOps = development + operations

Goal:
- faster deployments
- automation
- better collaboration
- continuous delivery

---

# Main Benefits
- faster software releases
- fewer deployment errors
- automated testing/deployment
- easier monitoring
- better scalability

---

# Important DevOps Practices

## CI (Continuous Integration)
- developers merge code frequently
- automatic build + testing

## CD (Continuous Delivery/Deployment)
- automatic release pipeline
- faster deployments

## Infrastructure as Code (IaC)
- infrastructure defined in code
- repeatable deployments

Tools:
- ARM Templates
- Bicep
- Terraform

---

# Azure DevOps Services

## Azure Repos
- Git repositories
- source control

## Azure Pipelines
- CI/CD pipelines
- automate build and deployment

## Azure Boards
- task/project tracking

## Azure Test Plans
- testing management

## Azure Artifacts
- package management

---

# GitHub in DevOps
Used for:
- source control
- collaboration
- CI/CD with GitHub Actions

---

# Practical Rule
- CI = build + test automatically
- CD = deploy automatically
- DevOps = automate everything possible


___________________________

# video.n.28-Azure Management Solutions – AZ-900 Notes

# Azure Management Solutions (AZ-900)

## Azure Resource Manager (ARM)
- Central management layer in Azure
- All management tools communicate through ARM
- Enforces:
  - RBAC permissions
  - Azure Policies
  - Security and resource management rules

---

## Azure Portal
- Graphical web interface
- Best for:
  - Viewing resources
  - Monitoring
  - Troubleshooting
  - Basic configuration
- Not ideal for:
  - Large-scale deployments
  - Consistent provisioning
  - Automation

### Pros
- Easy to use
- Intuitive UI

### Cons
- Slow for repetitive tasks
- Hard to standardize deployments

---

## Azure Mobile App
- Available for iOS and Android
- Used for:
  - Viewing alerts
  - Checking resource status
  - Simple actions (start/stop VM)

### Limitation
- Not suitable for resource creation

---

## Azure PowerShell
- Automation and scripting tool
- Cross-platform:
  - Windows
  - Linux
  - macOS

# video.n.29-Functionality and usage of Azure Advisor

# Important Notes for AZ-900
- Azure Advisor is a recommendation service
- It focuses on:
  - Reliability
  - Security
  - Performance
  - Cost
  - Operational Excellence
- Advisor does NOT automatically fix issues
- Users choose whether to apply recommendations

_________________________________________

# video. 30. ARM Templates – Benefits for Azure Management Solutions

This document explains the benefits of using **Azure Resource Manager (ARM) templates** as part of an Azure management and infrastructure-as-code strategy.

---

## Overview

ARM templates are a declarative way to define and deploy Azure infrastructure using JSON (or Bicep). Instead of describing *how* to create resources, you define *what the final state should be*, and Azure handles the rest.

---

## Key Benefits

### 1. Consistent and Repeatable Deployments
ARM templates ensure that every environment (development, testing, production) is deployed in the same way.

- Eliminates configuration drift  
- Guarantees identical infrastructure across environments  
- Improves reliability of deployments  

---

### 2. Idempotent Deployments (Safe Re-runs)
You can deploy the same template multiple times safely.

- If resources already match the desired state → no changes  
- If changes exist → only required updates are applied  
- Prevents accidental duplication or failures  

---

### 3. CI/CD Pipeline Integration
ARM templates integrate seamlessly with modern DevOps workflows.

- Works with Azure DevOps and GitHub Actions  
- Enables automated infrastructure deployment  
- Supports version-controlled infrastructure changes  
- Allows promotion across environments (dev → test → prod)  

---

### 4. Governance and Compliance
ARM templates help enforce organizational standards.

- Standardized naming conventions  
- Controlled resource configurations  
- Easier auditing and compliance tracking  
- Infrastructure defined as code in source control  

---

### 5. Reusability and Modularity
Templates can be parameterized and reused.

- Same template used for multiple environments  
- Supports parameters and variables  
- Encourages modular infrastructure design  

---

### 6. Reduced Human Error
Automation reduces reliance on manual configuration.

- No manual portal setup  
- Fewer misconfigurations  
- Less risk of inconsistent environments  

---

### 7. Built-in Dependency Management
Azure automatically handles resource dependencies.

- Resources deployed in correct order  
- No need for manual sequencing  
- Supports complex multi-resource deployments  

---

### 8. Foundation for Modern Infrastructure as Code
ARM templates are the core Azure-native IaC approach.

- Can be extended using **Bicep (recommended modern syntax)**  
- Can integrate with tools like Terraform  
- Supports scalable cloud architecture practices  

---

## Summary

ARM templates transform infrastructure from manual processes into **automated, repeatable, and version-controlled deployments**. They are essential for building scalable and reliable Azure solutions.

---_____________________________

# video.n.31:  Azure Monitor – Functionality and Usage (AZ-900)

## Overview

Azure Monitor is the **central observability platform in Azure**. It collects, analyzes, and acts on telemetry data from across your entire Azure environment, including subscriptions, services, and applications.

It unifies:
- Metrics (performance data)
- Logs (detailed event data)
- Alerts (automation triggers)

---

## Key Data Sources in Azure Monitor

### 1. Azure Active Directory Logs
- Sign-in logs  
- Audit logs  
- Risk-based identity logs  

These help track identity and access activity.

---

### 2. Azure Subscription Activity Logs
- Records control-plane actions (via Azure Resource Manager)
- Example: creating, deleting, or modifying resources
- Typically retained for ~90 days

---

### 3. Resource Telemetry
Azure resources generate two types of signals:

- **Metrics** → numerical, time-series data (enabled by default)
- **Logs** → detailed diagnostic data (requires configuration)

---

## Diagnostic Settings

Logs are **not collected automatically** from resources. You must configure diagnostic settings to send them to a destination:

### Supported Destinations

- 📦 **Azure Storage**
  - Low-cost long-term retention
  - Limited querying capability

- 🌐 **Event Hub**
  - Streams logs to external systems (e.g., SIEM tools)

- 📊 **Log Analytics Workspace**
  - Primary analytics engine in Azure Monitor
  - Supports querying, dashboards, and insights
  - Retention up to ~2 years (based on configuration)

---

## Azure Monitor Capabilities

### 1. Metrics Monitoring
- Real-time performance data
- Example: CPU usage, storage capacity, network traffic
- Time-series visualization in Azure Portal

---

### 2. Log Analytics
- Centralized log analysis platform
- Supports queries and correlation across resources
- Used by advanced tools like Azure Sentinel and Insights

---

### 3. Alerts

Azure Monitor allows you to define **alert rules** based on:

- Metrics (e.g., CPU > 80%)
- Activity logs
- Log Analytics queries

When conditions are met → an alert is triggered.

---

## Action Groups

Alerts can trigger automated actions using **action groups**, such as:

- Email or SMS notifications
- Webhooks
- Azure Functions
- Logic Apps
- IT Service Management (ITSM) integration
- Automation Runbooks
- Event Hub streaming

---

## Alert Processing Flow

1. Data is collected (metrics/logs/activity logs)
2. Alert rule evaluates conditions
3. Alert is generated if condition is met
4. Action group executes response (notification or automation)

---

## Azure Monitor Portal Features

- View metrics for any resource
- Analyze performance trends over time
- Create and manage alert rules
- Configure diagnostic settings

Example:
- Monitor VM CPU usage
- Trigger alert when threshold is exceeded

---

## Key Concepts to Remember

- Azure Monitor is the **central monitoring hub for Azure**
- Metrics are available by default; logs require configuration
- Log Analytics Workspace is the core analysis engine
- Alerts + Action Groups enable automation and response
- Supports full-stack observability across Azure services

---

## Summary

Azure Monitor provides a **unified observability platform** that enables:
- Real-time monitoring (metrics)
- Deep diagnostics (logs)
- Automated response (alerts + actions)

It is essential for managing performance, availability, and reliability in Azure environments.
____________________________________

# video.n.32:Azure Service Health
Azure Service Health is basically a **dashboard that tells you what’s going on in Azure and whether it affects you**.

### Simple explanation:

* It shows if **Azure services are down or having issues**
* It informs you about **planned maintenance** that might temporarily affect services
* It notifies you about **changes or deprecations** in Azure services
* It tells you if a **specific resource (like your VM or database) has a problem**

### Why it matters:

* You can quickly see if the problem is **on your side or Microsoft’s side**
* You don’t need to guess or check multiple places
* You can set up **alerts (email, SMS, etc.)** so you get notified automatically

### Quick difference:

* **Azure Status** → global Azure health (everyone)
* **Service Health** → issues affecting *your subscription*
* **Resource Health** → health of a specific resource

### Bottom line:

👉 It’s a tool that tells you: *“Is Azure broken, and does it affect me?”*

# video.n.33.
# Microsoft Defender for Cloud (AZ-900 Notes)

## What is Microsoft Defender for Cloud?

Microsoft Defender for Cloud is a cloud security service in Azure that helps protect:

- Azure resources
- On-premises servers
- Other cloud platforms like AWS

It helps organizations:

- Improve security posture
- Detect threats
- Find vulnerabilities
- Meet compliance requirements

---

# Main Features

## 1. Secure Score

Secure Score measures how secure your Azure environment is.

It:

- Checks resources against security best practices
- Gives a security score
- Provides recommendations to improve security

### Examples

- Enable MFA
- Install system updates
- Close unnecessary ports
- Fix vulnerabilities

> Higher score = better security posture

---

## 2. Security Recommendations

Defender for Cloud continuously scans Azure resources and suggests ways to improve security.

Some recommendations can be fixed automatically using **Quick Fix**.

Recommendations can also be marked as **Exempt** if they do not apply.

---

## 3. Regulatory Compliance

Defender for Cloud checks whether resources follow security standards and compliance frameworks.

Example:

- Azure Security Benchmark

It shows:

- Compliant resources
- Non-compliant resources
- Overall compliance status

---

# Free Tier vs Paid Tier

## Free Features

Included by default:

- Secure Score
- Security recommendations
- Basic security monitoring

## Paid Features (Microsoft Defender Plans)

Advanced protection features include:

- Threat detection
- Endpoint protection
- Regulatory compliance dashboards
- Just-In-Time VM access
- Adaptive application controls

---

# Important Security Features

## Just-In-Time (JIT) VM Access

JIT helps protect virtual machines by opening management ports only when needed.

Examples:

- RDP port (3389)
- SSH port (22)

Access is:

- Temporary
- Limited to specific IP addresses

> This reduces the risk of attacks.

---

## Adaptive Application Controls

Uses machine learning to:

- Learn normal application behavior
- Detect suspicious software
- Help block malicious applications

---

## Threat Protection

Provides advanced threat detection for:

- Virtual machines
- Servers
- Azure services

Uses analytics and machine learning to detect attacks and suspicious activity.

---

# Integration

Defender for Cloud integrates with:

- Azure Policy
- Azure Monitor
- Other security tools

This allows automated monitoring and centralized security management.


# video.n.34.

# Azure Key Vault (AZ-900 Notes)

## What is Azure Key Vault?

Azure Key Vault is a service used to securely store and manage:

- Secrets
- Encryption keys
- Certificates

Instead of storing sensitive information inside application code, it is stored securely in Key Vault.

---

# Main Types

| Type | Example |
|---|---|
| Secrets | Passwords, API keys, connection strings |
| Keys | Encryption and decryption keys |
| Certificates | SSL/TLS certificates for HTTPS |

---

# Practical Example

A web application needs a database password.

### Without Key Vault
```python
password = "Admin123!"

The password is exposed inside the code.

### With Key Vault
- Password is stored securely in Key Vault
- The application retrieves it when needed
- Access is controlled using permissions

---

# Access Control

Azure Key Vault supports:

- Access Policies (older method)
- Azure RBAC (recommended)

RBAC provides granular access control.

Example:
- User A can access Secret 1
- User B can access Secret 2

---

# Managed Identity

Managed Identity allows Azure services to access Key Vault securely without storing credentials.

Example:
- An Azure VM can access secrets using its built-in identity

---

# Important Features

- Secure secret storage
- Encryption key management
- Certificate lifecycle management
- Hardware Security Module (HSM) support
- Bring Your Own Key (BYOK)

---

# Simple Definition

> Azure Key Vault is a secure Azure service used to store and manage secrets, encryption keys, and certificates.

_______________________________________________

# video.n.35 Microsoft Sentinel 

## What It Is
Microsoft Sentinel is a cloud-native:
- SIEM → collects/analyzes security logs
- SOAR → automates security responses

Main purpose:
- detect threats
- investigate incidents
- automate reactions

---

# Core Architecture

## Required Components
- Log Analytics Workspace
- Microsoft Sentinel

Sentinel runs on top of Log Analytics.

---

# Most Important Thing = Data Connectors

No logs = no detection.

## Common Connectors
- Entra ID (Azure AD)
- Microsoft Defender
- AWS CloudTrail
- Google Cloud
- Cisco / Palo Alto / Fortinet
- Microsoft 365

More data sources = better detection.

---

# Key Concept: Correlation

Sentinel combines logs from multiple systems.

Example:
```text
Failed login
+ impossible travel
+ suspicious mailbox rule
= possible account compromise
```

Single logs usually mean little.

---

# KQL (Very Important)

Kusto Query Language is used for:
- investigations
- hunting
- analytics rules

Example:
```kql
SigninLogs
| where ResultType != 0
| summarize count() by UserPrincipalName
```

---

# Alerts vs Incidents

## Alert
Single suspicious event.

## Incident
Collection of related alerts.

Workflow:
```text
Alert → Incident → Investigation → Response
```

---

# Automation (SOAR)

Sentinel can automate responses using:
- Playbooks
- Logic Apps

Examples:
- block malicious IP
- disable compromised account
- trigger MFA reset

---

# Threat Hunting

Manual search for hidden threats.

Common hunting targets:
- PowerShell abuse
- privilege escalation
- credential theft
- lateral movement

---

# Workbooks

Dashboards for visualization.

Examples:
- attack maps
- failed logins
- risky users
- malware detections

---

# UEBA

User and Entity Behavior Analytics.

Detects abnormal behavior:
```text
User normally logs in from Slovakia
Suddenly logs in from another country
= suspicious
```

---

# Threat Intelligence

Supports external threat feeds:
- malicious IPs
- domains
- file hashes
- IOCs

---

# Biggest Real-World Problem = Cost

Pricing is mostly based on:
```text
GB/day ingested
```

More logs:
- better visibility
- higher cost

---

# Real SOC Workflow

```text
1. Collect logs
2. Correlate events
3. Detect threats
4. Generate alerts
5. Investigate incidents
6. Hunt threats
7. Automate response
```

---

# Most Important Practical Point

Sentinel does NOT secure systems itself.

It:
- provides visibility
- detects suspicious activity
- helps analysts respond faster

Good detections depend on:
```text
Good data + good rules
```

# Simple Definition

> Microsoft Defender for Cloud is a cloud security service that helps protect Azure, hybrid, and multi-cloud environments by providing security recommendations, compliance monitoring, and threat protection.
> 
______________________

# video.n.36-Functionality and Usage of Azure Dedicated Hosts

## What Problem Does Azure Dedicated Host Solve?

Normally in Azure:

* Your VM runs on a **shared physical server**
* Other companies’ VMs may run on the same hardware
* Microsoft isolates everyone securely

Think of it like:

| Scenario        | Real World Example                                   |
| --------------- | ---------------------------------------------------- |
| Normal Azure VM | Renting an apartment in a big building               |
| Dedicated Host  | Renting the entire building                          |
| Isolated VM     | Renting a huge mansion that occupies all land itself |

---

# Normal Azure VM (Shared Infrastructure)

## Real World Analogy

You book a room in a hotel.

* You have privacy
* Other guests are nearby
* Same building/resources are shared

This is how Azure usually works.

---

## In Practice

When you create:

* Virtual Machine
* AKS node
* VM Scale Set

Azure places it on a physical server with workloads from other customers.

Example:

```text
Physical Server
├── Your VM
├── Company A VM
├── Company B VM
└── Company C VM
```

This is called:

```text
Multi-Tenant Infrastructure
```

---

# Why Some Companies DON'T Want Shared Hardware

Some industries require:

* Strict compliance
* Hardware isolation
* License optimization
* Security auditing

Examples:

| Industry                        | Reason                           |
| ------------------------------- | -------------------------------- |
| Banks                           | Regulatory compliance            |
| Government                      | Sensitive workloads              |
| Healthcare                      | Patient data isolation           |
| Enterprise Oracle/SQL licensing | CPU licensing benefits           |
| Defense                         | Physical separation requirements |

---

# Azure Dedicated Host

## What It Actually Means

Microsoft gives you:

```text
An entire physical server ONLY for your company
```

No other customer can use it.

---

# Real World Example

Imagine Netflix infrastructure.

They may want:

* Full hardware control
* Predictable performance
* Compliance
* Licensing efficiency

Instead of:

```text
Shared apartment
```

They rent:

```text
Entire building
```

---

# Architecture Flow

```text
Azure Region
    ↓
Host Group
    ↓
Dedicated Hosts
    ↓
Your VMs
```

---

# Step-by-Step Practical Workflow

## 1. Create Host Group

Example:

```text
Region: East US
Availability Zone: AZ1
```

Purpose:

* Logical grouping
* Organize hosts
* Define fault domains

---

## 2. Add Dedicated Hosts

Example:

```text
Host 1 → Rack A
Host 2 → Rack B
```

Why?

If one rack fails:

* Other rack still works

This improves:

```text
High Availability
```

---

## 3. Deploy VMs Onto Hosts

Now your VMs are deployed ONLY on your hardware.

Example:

```text
Dedicated Host
├── App VM
├── Database VM
├── API VM
└── Monitoring VM
```

No outsiders.

---

# Important Concept: VM Family Restriction

A Dedicated Host supports specific VM families.

Example:

```text
DASv4 host
```

Can only run:

```text
DASv4 VMs
```

But sizes can vary:

```text
D2s_v4
D4s_v4
D8s_v4
```

---

# Practical Enterprise Example

## Company Scenario

A large bank runs:

* SQL Server
* Core banking apps
* Sensitive customer workloads

They choose Dedicated Hosts because:

### 1. Compliance

Auditors require:

```text
No shared hardware
```

---

### 2. Licensing Savings

Instead of licensing every VM separately:

They license:

```text
Entire physical CPU
```

This can save millions.

---

### 3. Predictable Performance

No noisy neighbors.

Example problem in shared environments:

```text
Another tenant spikes CPU usage
```

Dedicated host avoids this.

---

# Isolated VM Sizes

## Difference From Dedicated Host

With isolated VMs:

* You DO NOT manage hosts
* The VM itself is so massive it occupies the whole server

---

# Real World Analogy

Instead of renting:

```text
Entire apartment building
```

You rent:

```text
A giant private estate
```

because the house itself consumes everything.

---

# Practical Use Cases for Isolated VMs

Used for:

* SAP HANA
* Massive databases
* AI workloads
* HPC (High Performance Computing)

Examples:

```text
128 CPU
512 GB RAM
2 TB RAM
```

Huge workloads.

---

# Dedicated Host vs Isolated VM

| Feature                   | Dedicated Host       | Isolated VM       |
| ------------------------- | -------------------- | ----------------- |
| You manage host placement | Yes                  | No                |
| Physical isolation        | Yes                  | Yes               |
| Multiple VMs allowed      | Yes                  | Usually one       |
| Best for                  | Compliance/licensing | Massive workloads |
| More control              | High                 | Medium            |

---

# Maintenance Window Advantage

Normally Azure decides maintenance timing.

With Dedicated Hosts:

You get scheduling control.

Example:

```text
Patch servers Sunday 2 AM
```

instead of:

```text
Random weekday outage
```

Huge benefit for enterprises.

---

# Key Exam-Friendly Memory Trick

## Shared Azure VM

```text
Apartment
```

---

## Dedicated Host

```text
Entire Building
```

---

## Isolated VM

```text
Massive Mansion occupying whole property
```

---

# What You Should Remember for AZ-900

## Dedicated Host

* Single tenant physical server
* Compliance/security benefits
* Licensing optimization
* Control over maintenance
* Multiple VMs on one dedicated server

---

## Isolated VM

* One huge VM consumes whole hardware
* Automatic physical isolation
* Used for very large workloads

---

# Short Practical Summary

## Use Normal Azure VM When

* Regular apps
* Cheap scaling
* No compliance concerns

---

## Use Dedicated Host When

* Compliance matters
* Need hardware isolation
* Want licensing benefits
* Need predictable infrastructure

---

## Use Isolated VM When

* Workload is extremely large
* Single VM needs entire machine
* SAP/HPC/AI/database workloads

---

# video.n.38-Concept of Defense in Depth

<img width="1130" height="628" alt="image" src="https://github.com/user-attachments/assets/480a0d28-3868-410c-b062-499eb4e3a4c7" />

## Overview
Defense in Depth is a layered security strategy where multiple security controls protect systems and data. If one layer fails, another layer continues protection.

---

## Key Concept
- Never rely on a single security mechanism.
- Multiple defensive layers reduce risk and improve detection/response.
- The most valuable asset is usually **data**.

---

# Defense in Depth Layers

## 1. Data Layer
**Goal:** Protect sensitive information.

### Security Measures
- Data encryption
- Data classification
- Access controls

### Important Idea
Data is the “core pearl” that all other layers protect.

---

## 2. Application Layer
**Goal:** Secure applications from vulnerabilities and attacks.

### Best Practices
- Write secure code
- Avoid storing secrets in code
- Use Azure Key Vault
- Deploy Web Application Firewalls (WAF)

### Purpose
Protect against common web attacks and application exploits.

---

## 3. Compute Layer
**Goal:** Secure servers, VMs, and workloads.

### Security Measures
- Firewalls
- Patching
- Anti-malware
- Threat detection

### Shared Responsibility
- In PaaS, Azure manages more of this layer.
- In IaaS, customers manage most compute security.

---

## 4. Network Layer
**Goal:** Restrict and secure communication.

### Core Principles
- Least privilege access
- Deny by default
- Zero Trust
- Restrict unnecessary ports

### Recommended Connectivity
- Private endpoints
- VPN tunnels
- ExpressRoute

### Important Idea
Never trust traffic simply because it exists on the network.

---

## 5. Perimeter Layer
**Goal:** Stop attacks before they reach services.

### Security Tools
- DDoS Protection
- Edge firewalls
- Traffic filtering

### Purpose
Mitigate large-scale attacks before impacting workloads.

---

## 6. Identity & Access Layer
**Goal:** Verify users and control access.

### Security Measures
- Multi-factor authentication (MFA)
- Passwordless authentication
- Auditing sign-ins and changes
- Continuous verification

### Important Idea
In cloud environments, **identity becomes the security perimeter**.

---

## 7. Physical Security Layer
**Goal:** Protect datacenter infrastructure.

### Responsibility
Managed by the cloud provider (e.g., Microsoft Azure).

---

# Shared Responsibility Model

## SaaS
Provider manages most security responsibilities.

## PaaS
Customer focuses mainly on:
- Applications
- Data
- Identity

## IaaS
Customer manages:
- Networks
- Compute
- Applications
- Data
- Identity

Provider mainly manages:
- Physical infrastructure

---

# CIA Triad

## Confidentiality
Ensure only authorized users access data.

### Methods
- Least privilege access
- Strong authentication

---

## Integrity
Ensure data is not altered improperly.

### Methods
- Digital signatures
- Validation checks
- Secure transmission

---

## Availability
Ensure systems and services remain accessible.

### Threat Example
- Distributed Denial of Service (DDoS)

---

# Key Takeaways
- Defense in Depth uses multiple security layers.
- Identity is critical in cloud security.
- Zero Trust assumes no implicit trust.
- Least privilege reduces attack surface.
- Security responsibilities vary across SaaS, PaaS, and IaaS.
- The CIA Triad remains foundational:
  - Confidentiality
  - Integrity
  - Availability

---

# Additional Insight
Microsoft guidance emphasizes that layered security:
> “Slows down attacks and provides alert information for response teams.”

video.n.38-# Concept of Defense in Depth - AZ-900 Certification Course

## Overview
Defense in Depth is a layered security strategy where multiple security controls protect systems and data. If one layer fails, another layer continues protection.

---

## Key Concept
- Never rely on a single security mechanism.
- Multiple defensive layers reduce risk and improve detection/response.
- The most valuable asset is usually **data**.

---

# Defense in Depth Layers

## 1. Data Layer
**Goal:** Protect sensitive information.

### Security Measures
- Data encryption
- Data classification
- Access controls

### Important Idea
Data is the “core pearl” that all other layers protect.

---

## 2. Application Layer
**Goal:** Secure applications from vulnerabilities and attacks.

### Best Practices
- Write secure code
- Avoid storing secrets in code
- Use Azure Key Vault
- Deploy Web Application Firewalls (WAF)

### Purpose
Protect against common web attacks and application exploits.

---

## 3. Compute Layer
**Goal:** Secure servers, VMs, and workloads.

### Security Measures
- Firewalls
- Patching
- Anti-malware
- Threat detection

### Shared Responsibility
- In PaaS, Azure manages more of this layer.
- In IaaS, customers manage most compute security.

---

## 4. Network Layer
**Goal:** Restrict and secure communication.

### Core Principles
- Least privilege access
- Deny by default
- Zero Trust
- Restrict unnecessary ports

### Recommended Connectivity
- Private endpoints
- VPN tunnels
- ExpressRoute

### Important Idea
Never trust traffic simply because it exists on the network.

---

## 5. Perimeter Layer
**Goal:** Stop attacks before they reach services.

### Security Tools
- DDoS Protection
- Edge firewalls
- Traffic filtering

### Purpose
Mitigate large-scale attacks before impacting workloads.

---

## 6. Identity & Access Layer
**Goal:** Verify users and control access.

### Security Measures
- Multi-factor authentication (MFA)
- Passwordless authentication
- Auditing sign-ins and changes
- Continuous verification

### Important Idea
In cloud environments, **identity becomes the security perimeter**.

---

## 7. Physical Security Layer
**Goal:** Protect datacenter infrastructure.

### Responsibility
Managed by the cloud provider (e.g., Microsoft Azure).

---

# Shared Responsibility Model

## SaaS
Provider manages most security responsibilities.

## PaaS
Customer focuses mainly on:
- Applications
- Data
- Identity

## IaaS
Customer manages:
- Networks
- Compute
- Applications
- Data
- Identity

Provider mainly manages:
- Physical infrastructure

---

# CIA Triad

## Confidentiality
Ensure only authorized users access data.

### Methods
- Least privilege access
- Strong authentication

---

## Integrity
Ensure data is not altered improperly.

### Methods
- Digital signatures
- Validation checks
- Secure transmission

---

## Availability
Ensure systems and services remain accessible.

### Threat Example
- Distributed Denial of Service (DDoS)

---

# Key Takeaways
- Defense in Depth uses multiple security layers.
- Identity is critical in cloud security.
- Zero Trust assumes no implicit trust.
- Least privilege reduces attack surface.
- Security responsibilities vary across SaaS, PaaS, and IaaS.
- The CIA Triad remains foundational:
  - Confidentiality
  - Integrity
  - Availability

__________________________________
# video.n.38 Describe the Concept of Zero Trust

## Overview
Zero Trust is a modern security model based on the principle:

> **"Never trust, always verify."**

Unlike traditional security models that automatically trust users and devices inside a network, Zero Trust assumes that every request could be a threat.

---

# Core Principles of Zero Trust

## 1. Verify Explicitly
Always authenticate and authorize every request.

### Verification Includes
- User identity
- Device health
- Location
- Application
- Data sensitivity
- Risk level

### Common Security Methods
- Multi-factor authentication (MFA)
- Passwordless authentication
- Conditional access policies

---

## 2. Use Least Privilege Access
Users and applications should only have the minimum permissions required.

### Goals
- Reduce attack surface
- Prevent unauthorized access
- Limit damage from compromised accounts

### Techniques
- Just-in-time (JIT) access
- Role-based access control (RBAC)
- Privileged identity management (PIM)

---

## 3. Assume Breach
Operate as if attackers are already inside the environment.

### Security Strategies
- Continuous monitoring
- Threat detection
- Network segmentation
- Encryption
- Logging and auditing

### Important Idea
Limit lateral movement across systems.

---

# Key Components of Zero Trust

## Identity Security
Identity becomes the new security perimeter.

### Protection Methods
- MFA
- Strong authentication
- Identity monitoring
- Risk-based sign-ins

---

## Device Security
Only trusted and compliant devices should access resources.

### Device Checks
- OS updates
- Antivirus status
- Compliance policies
- Endpoint protection

---

## Network Security
Do not automatically trust internal network traffic.

### Security Measures
- Micro-segmentation
- Private access
- Encrypted communication
- Firewall controls

---

## Application Security
Applications should enforce secure access controls.

### Best Practices
- Secure APIs
- Web Application Firewalls (WAF)
- Application monitoring
- Secret management using Azure Key Vault

---

## Data Security
Protect sensitive information everywhere.

### Protection Methods
- Encryption at rest
- Encryption in transit
- Data classification
- Data loss prevention (DLP)

---

# Benefits of Zero Trust

## Improved Security
Reduces risk of:
- Data breaches
- Credential theft
- Insider threats

---

## Better Visibility
Provides continuous monitoring and auditing.

---

## Reduced Lateral Movement
Attackers cannot easily move across systems.

---

## Cloud-Friendly Security
Works well in:
- Hybrid environments
- Remote work
- Multi-cloud systems

---

# Traditional Security vs Zero Trust

| Traditional Security | Zero Trust |
|---|---|
| Trust inside network | Trust nobody automatically |
| Perimeter-based security | Identity-based security |
| One-time authentication | Continuous verification |
| Broad network access | Least privilege access |
| Assume safe internal traffic | Assume breach |

---

# Zero Trust in Azure

## Microsoft Security Recommendations
Azure Zero Trust commonly includes:
- Microsoft Entra ID
- Conditional Access
- MFA
- Microsoft Defender
- Azure Firewall
- Network segmentation

---

# Example Scenario

## Traditional Model
A user inside the company network may automatically gain access to internal systems.

## Zero Trust Model
The user must continuously verify:
- Identity
- Device compliance
- Access permissions
- Risk level

before accessing resources.

---

# Key Takeaways

- Zero Trust means:
  > **Never trust, always verify**
- Identity is the new security perimeter.
- Every request must be authenticated and authorized.
- Least privilege access reduces risk.
- Continuous monitoring is essential.
- Zero Trust assumes breaches can happen at any time.

_________________________________________________________

# video.n.39-  Azure NSGs (Network Security Groups) — Beginner Notes

## 📌 What is an NSG?

A **Network Security Group (NSG)** is Azure’s way of controlling **network traffic**.

Think of it like a **firewall for your Azure network**.

It lets you decide:

* What traffic is allowed
* What traffic is blocked
* Where traffic can come from
* Which ports/protocols can be used

---

# 🌐 Azure Virtual Network (VNet) Basics

A **Virtual Network (VNet)** is your private network inside Azure.

Inside a VNet, you usually create **subnets**.

Example:

```text
VNet
├── Subnet A
├── Subnet B
└── Subnet C
```

By default:

✅ Subnets can communicate with each other freely.

✅ Peered VNets can also communicate freely.

✅ Connected on-premises networks (VPN / ExpressRoute) are treated as part of the network.

---

# 🔥 Default Azure Network Behavior

Azure already includes a built-in **stateful firewall**.

This means:

## Outbound Traffic

Your VM can:

* Access the internet
* Access Azure services

And the response is automatically allowed back.

Example:

```text
VM → Internet ✅
Internet Response → VM ✅
```

---

## Inbound Traffic

Random traffic from the internet is blocked by default.

Example:

```text
Internet → VM ❌
```

---

# 🚨 Why Do We Need NSGs?

Without NSGs:

* Everything inside the VNet can talk to everything else.
* There is little granular control.

NSGs solve this by letting you:

✅ Restrict subnet communication
✅ Allow specific internet traffic
✅ Block unwanted traffic
✅ Control communication with peered VNets or on-premises networks

---

# 🧩 NSG Rules

An NSG contains **rules**.

Each rule defines:

| Property    | Meaning                       |
| ----------- | ----------------------------- |
| Source      | Where traffic comes from      |
| Destination | Where traffic goes            |
| Port        | Which port is used            |
| Protocol    | TCP / UDP                     |
| Action      | Allow or Deny                 |
| Priority    | Which rule is evaluated first |

---

# 🧠 Important: Priority

Lower number = Higher priority

Example:

```text
100 → Checked first
200 → Checked later
65000 → Very low priority
```

---

# ✅ Example Rule

Allow HTTPS traffic from the internet:

```text
Source: Internet
Destination: VM/Subnet
Port: 443
Protocol: TCP
Action: Allow
```

This allows users to access a secure website hosted on your VM.

---

# 📦 Default NSG Rules

Azure automatically adds some rules.

## Default Inbound Rules

| Rule                      | Action |
| ------------------------- | ------ |
| Allow VNet traffic        | ✅      |
| Allow Azure Load Balancer | ✅      |
| Deny everything else      | ❌      |

---

## Default Outbound Rules

| Rule                    | Action |
| ----------------------- | ------ |
| Allow VNet outbound     | ✅      |
| Allow Internet outbound | ✅      |
| Deny everything else    | ❌      |

---

# 🏷️ Service Tags

Azure services have many IP addresses.

Managing them manually would be difficult.

Instead, Azure provides **Service Tags**.

Examples:

* `VirtualNetwork`
* `Internet`
* `AzureLoadBalancer`
* `AzureKeyVault`

---

## Example

Instead of:

```text
Allow 20 different Azure IP addresses
```

You can simply use:

```text
Allow AzureKeyVault
```

Much easier 👍

---

# 🖥️ Where Can You Apply an NSG?

## Recommended: Subnet Level

```text
Subnet → NSG
```

This is easier to manage.

---

## Possible but Not Recommended: NIC Level

```text
VM Network Interface (NIC) → NSG
```

Technically possible, but:

❌ Harder to manage
❌ Adds complexity
❌ No extra security benefit

---

# ⚙️ How NSGs Actually Work

NSGs are **not physical firewall devices**.

Azure enforces NSG rules at the:

```text
VM Host / Virtual Switch Level
```

This happens behind the scenes automatically.

---

# 🎯 Common Use Cases

## Restrict Communication Between Subnets

```text
Frontend Subnet → Backend Subnet ✅
Backend Subnet → Frontend Subnet ❌
```

---

## Allow Web Traffic

Allow users to access a website:

```text
Port 80 (HTTP)
Port 443 (HTTPS)
```

---

## Protect Internal Services

Block direct internet access to databases:

```text
Internet → Database ❌
```

---

# 📝 Key Exam Takeaways (AZ-900)

Remember these points:

✅ NSGs control inbound and outbound traffic
✅ NSGs use Allow/Deny rules
✅ Rules use priorities
✅ Lower priority number = evaluated first
✅ NSGs are usually attached to subnets
✅ Azure blocks inbound internet traffic by default
✅ Azure allows outbound internet traffic by default
✅ Service Tags simplify Azure service access management

---

# 🧠 Simple Mental Model

Think of NSGs like:

```text
Security guards for your Azure network
```

They decide:

* Who can enter
* Who can leave
* Which doors (ports) they can use


# video.n.40-# Azure Firewall — Beginner Notes (AZ-900)

## 🔥 What is Azure Firewall?

Azure Firewall is a **fully managed security service** in Microsoft Azure that protects your network traffic.

Think of it like a **smart security guard** sitting at the edge of your Azure network.

Unlike Network Security Groups (NSGs), Azure Firewall understands both:

* **Layer 4 traffic** → IPs, Ports, TCP/UDP
* **Layer 7 traffic** → Websites, URLs, HTTP/HTTPS, categories

---

# 🧠 Why NSGs Are Not Enough

## NSGs Understand Only Basic Networking

NSGs can filter traffic using:

* IP addresses
* Ports
* TCP / UDP protocols

Example:

```text
Allow TCP port 443
Block port 22
```

But NSGs **cannot understand**:

* URLs
* Website categories
* HTTP/HTTPS traffic
* Domain names

So NSGs cannot block things like:

* Gambling websites
* Social media
* Specific URLs

---

# 🚀 What Makes Azure Firewall Powerful

Azure Firewall understands **application-level traffic**.

This means it can inspect:

* URLs
* Domain names (FQDNs)
* HTTPS traffic
* Website categories

Example:

```text
Allow: microsoft.com
Block: gambling websites
```

---

# 🏗️ How Azure Firewall Works

Azure Firewall is deployed into its **own subnet** inside a Virtual Network.

Required subnet name:

```text
AzureFirewallSubnet
```

Traffic is redirected to the firewall using:

## User-Defined Routes (UDRs)

UDRs tell Azure:

> "Send traffic through the firewall first."

---

# 📌 Types of Rules in Azure Firewall

## 1. Application Rules (Layer 7)

Used for:

* URLs
* Websites
* Domain names
* Web categories

Example:

```text
Allow github.com
Block facebook.com
```

---

## 2. Network Rules (Layer 4)

Used for:

* IP addresses
* Ports
* Protocols

Example:

```text
Allow TCP 443
Block TCP 22
```

---

# 🔒 Azure Firewall Premium (TLS Inspection)

Normally HTTPS traffic is encrypted.

That means regular firewalls cannot see:

* URLs
* Web paths
* Actual website content

## Premium SKU solves this

Azure Firewall Premium can perform:

# TLS Inspection

It temporarily decrypts traffic so it can inspect it.

This allows Azure Firewall to:

* See encrypted URLs
* Detect risky websites
* Apply filtering rules on HTTPS traffic

---

# 🌐 DNAT (Destination NAT)

Azure Firewall can expose internal VMs securely to the internet.

Example:

```text
Public IP:3389 → Internal VM:3389
```

Useful for:

* RDP
* SSH
* Remote administration

The firewall still controls who can access it.

---

# ⚙️ Managed & Auto-Scaling

Azure Firewall is:

* Fully managed by Microsoft
* Automatically scales
* Uses VM Scale Sets internally
* No manual maintenance required

You only configure the rules.

---

# 🛡️ Azure Firewall + NSGs = Best Practice

Do NOT choose one over the other.

Use BOTH together.

## Recommended Strategy

| Service        | Purpose                        |
| -------------- | ------------------------------ |
| NSGs           | Internal subnet/VM protection  |
| Azure Firewall | Perimeter & advanced filtering |

This is called:

# Defense in Depth

Multiple security layers = better protection.

---

# 🧾 Quick Summary

## Azure Firewall

✅ Layer 4 + Layer 7 filtering
✅ URL & website filtering
✅ HTTPS/TLS inspection (Premium)
✅ DNAT support
✅ Auto-scaling & managed
✅ Perimeter security solution

## NSGs

✅ Basic port/IP filtering
❌ No URL awareness
❌ No HTTPS inspection

---

# 💡 Easy Analogy

| Service        | Real-World Analogy        |
| -------------- | ------------------------- |
| NSG            | Door lock                 |
| Azure Firewall | Smart security checkpoint |

NSG checks:

```text
"Which port are you using?"
```

Azure Firewall checks:

```text
"Which website are you visiting?"
"What category is it?"
"Should you be allowed?"
```

---

# video.n.41- Azure DDoS Protection — Beginner Notes (AZ-900)

## 🌐 What is a DDoS Attack?

DDoS stands for:

# Distributed Denial of Service

A DDoS attack happens when attackers flood a service with massive amounts of traffic to make it unavailable.

Think of it like:

> Thousands or millions of fake users trying to enter a store at the same time so real customers can't get in.

---

# 🧠 Goal of a DDoS Attack

Attackers try to:

* Crash websites
* Slow down applications
* Exhaust server/network resources
* Make services unavailable

---

# 📌 Common Types of DDoS Attacks

## 1. Volumetric Attacks

Flood the network with huge traffic volumes.

Example:

```text id="t8pn4v"
Sending billions of packets to overload bandwidth
```

Goal:

```text id="mjlwmj"
Consume all network capacity
```

---

## 2. Protocol Attacks

Exploit weaknesses in network protocols.

Example:

```text id="7c4x9m"
SYN Flood attacks
```

Goal:

```text id="w1tqkh"
Exhaust server/network resources
```

---

## 3. Application Layer Attacks

Target applications directly.

Example:

```text id="q85h34"
Flooding a website with fake HTTP requests
```

Goal:

```text id="jfwx1g"
Crash the web application
```

---

# ☁️ Azure DDoS Protection

Microsoft Azure provides built-in protection against DDoS attacks.

There are **2 tiers**:

| Tier     | Purpose                              |
| -------- | ------------------------------------ |
| Basic    | Protects Azure infrastructure        |
| Standard | Protects your applications/resources |

---

# 🟦 Azure DDoS Protection Basic

## Included Automatically

Every Azure public-facing service gets basic DDoS protection for free.

You do NOT need to enable it.

---

## What Basic Protection Does

It protects:

* Azure datacenter infrastructure
* Azure network fabric

Main goal:

```text id="sph8ow"
Keep Azure itself running during huge attacks
```

---

## Limitations of Basic Protection

❌ No detailed metrics
❌ No attack reports
❌ No custom tuning
❌ No alerts
❌ Limited visibility

It mainly protects Azure — not specifically YOUR app.

---

# 🛡️ Azure DDoS Protection Standard

This is the advanced paid version.

You create:

```text id="7p2x2o"
DDoS Protection Plan
```

Then attach it to:

* Virtual Networks (VNets)

---

# 🔗 How Standard Protection Works

## Step 1 — Create DDoS Plan

```text id="vwql1j"
Azure DDoS Protection Plan
```

## Step 2 — Link to VNets

The plan protects resources inside those VNets that use:

* Public IP addresses

---

# 🚀 Features of Standard Protection

## ✅ Adaptive Tuning

Azure learns your application's normal traffic behavior using machine learning.

Then it can better detect unusual spikes.

---

## ✅ Attack Analytics & Reports

You get visibility into:

* Attack size
* Attack type
* Mitigation details
* Traffic metrics

---

## ✅ Azure Monitor Alerts

Azure can automatically alert you during attacks.

Example:

```text id="5y2nm7"
Email notifications
Azure Monitor alerts
Automation triggers
```

---

## ✅ Rapid Response Team

During large attacks, Microsoft security experts can assist.

---

## ✅ Cost Protection

If a DDoS attack causes unexpected scaling costs:

Microsoft may provide service credits.

---

# 📍 Important Requirement

## Standard Protection ONLY works for resources:

✅ Inside a Virtual Network
✅ Using Public IPs

If a resource is NOT in a VNet:

❌ It cannot use Standard protection.

Only Basic protection applies.

---

# 🔄 One Plan Can Protect Multiple VNets

A single DDoS Standard plan can protect:

* Multiple virtual networks
* Multiple subscriptions

Very useful for large organizations.

---

# ⚙️ Behind the Scenes

Azure automatically:

* Detects attacks
* Filters malicious traffic
* Allows legitimate traffic
* Mitigates attacks in real time

No manual intervention needed.

---

# 🧾 Quick Comparison

| Feature                      | Basic | Standard |
| ---------------------------- | ----- | -------- |
| Included Free                | ✅     | ❌        |
| Protect Azure Infrastructure | ✅     | ✅        |
| Protect Your Applications    | ❌     | ✅        |
| Metrics & Reports            | ❌     | ✅        |
| Alerts                       | ❌     | ✅        |
| Adaptive Tuning              | ❌     | ✅        |
| Rapid Response Support       | ❌     | ✅        |

---

# 💡 Easy Analogy

| Service             | Analogy                                     |
| ------------------- | ------------------------------------------- |
| Basic Protection    | City police protecting the city             |
| Standard Protection | Personal bodyguard protecting YOUR building |

---

# 🛡️ Best Practice

Use Azure DDoS Protection Standard for:

* Public web apps
* APIs
* Internet-facing workloads
* Mission-critical applications

Especially when downtime is expensive.

---

# 🧠 Exam Tip (AZ-900)

Remember:

```text id="y7ig5n"
Basic = protects Azure
Standard = protects your workloads
```

And:

```text id="w5eg77"
Standard protection requires VNets + Public IPs
```

---

# video.n.42 Authentication vs Authorization — Quick Notes

| Concept        | Meaning                            |
| -------------- | ---------------------------------- |
| Authentication | Verifies **who you are**           |
| Authorization  | Determines **what you can access** |

---

# 🔐 Authentication (AuthN)

Checks your identity.

Examples:

* Password
* MFA
* Fingerprint
* Smart card

Example:

```text id="8qd3ji"
Login with email + password
```

Real-world analogy:

```text id="x7xqtx"
Showing your ID card at a building entrance
```

---

# 🔓 Authorization (AuthZ)

Determines permissions after login.

Examples:

* Can read files
* Can delete resources
* Can access admin panel

Real-world analogy:

```text id="xq0jgl"
Determining which rooms you can enter
```

---

# 🔄 Order Matters

## Step 1

Authentication

```text id="6mfr6z"
"Who are you?"
```

## Step 2

Authorization

```text id="4qx6qy"
"What are you allowed to do?"
```

---

# ☁️ In Azure

| Service            | Purpose        |
| ------------------ | -------------- |
| Microsoft Entra ID | Authentication |
| RBAC               | Authorization  |

---

# 🧠 Easy Memory Trick

```text id="7y8x5v"
AuthN = Identity
AuthZ = Permissions
```

---
