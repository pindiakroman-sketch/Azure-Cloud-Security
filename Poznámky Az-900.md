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

#video.n.28-Azure Management Solutions – AZ-900 Notes

All Azure management tools communicate through Azure Resource Manager (ARM).
Azure Portal
graphical interface
good for monitoring, viewing, and basic management
not ideal for large-scale or consistent deployments
Azure Mobile App
quick access to alerts and resource status
supports simple actions like start/stop VM
Azure PowerShell
used for scripting and automation
cross-platform (Windows/Linux/macOS)
ideal for PowerShell-based environments
Azure CLI
command-line management tool
similar capabilities to PowerShell
commonly used in Bash/Linux workflows
Azure Cloud Shell
browser-based shell inside Azure Portal
supports both Bash and PowerShell
no local installation required
All management tools enforce:
RBAC permissions
Azure Policies
ARM security controls
GUI tools are useful for management and troubleshooting, but:
not the best option for consistent provisioning
ARM Templates
recommended deployment method
Infrastructure as Code (IaC)
repeatable and consistent deployments
