# Az-900-John Savils youtube+Microsoft Learn 06.05.2026

## Which service best use ,,,

| Workload                                                | Virtual Machine   | Container               | Azure Functions   | Azure App Service |
| ------------------------------------------------------- | ----------------- | ----------------------- | ----------------- | ----------------- |
| Legacy účtovná aplikácia bežiaca na Windows Server 2012 | ✅ Najlepšia voľba | ❌ Zbytočne komplikované | ❌ Nevhodné        | ❌ Nevhodné        |
| Moderný e-shop s mikroservismi                          | ⚠️ Možné          | ✅ Najlepšia voľba       | ⚠️ Niektoré úlohy | ⚠️ Frontend       |
| Spracovanie nahratých obrázkov po uploadnutí            | ❌ Overkill        | ⚠️ Možné                | ✅ Najlepšia voľba | ❌ Nevhodné        |


## veľa ľudí si pletie Availability Set, Availability Zone a Scale Set.
| Feature                          | Chráni pred                             | Hlavný účel            |
| -------------------------------- | --------------------------------------- | ---------------------- |
| Availability Set                 | Zlyhanie servera alebo plánovaná údržba | Vysoká dostupnosť VM   |
| Availability Zone                | Zlyhanie celého datacentra              | Disaster resilience    |
| Virtual Machine Scale Set (VMSS) | Nárast záťaže a zlyhanie VM             | Automatické škálovanie |


<img width="898" height="575" alt="image" src="https://github.com/user-attachments/assets/b4fd90d0-0ed1-4dff-b2c3-1f512eb7af31" />

<img width="908" height="404" alt="image" src="https://github.com/user-attachments/assets/b958b5d7-61d3-4606-9ffa-73368006e572" />

<img width="933" height="558" alt="image" src="https://github.com/user-attachments/assets/1b842904-71da-4b9a-abc4-60cc3490287f" />

# Describe the core architectural components of Azure 

To build a concept map that connects regions, Availability Zones, datacenters, resources, resource groups, subscriptions, and management groups in Azure, consider the following structure:

1. **Regions**: 
   - Azure regions are geographic areas that contain multiple datacenters. Each region is designed to provide high availability and resilience.

2. **Availability Zones**:
   - Within a region, there are Availability Zones, which are physically separate datacenters. These zones provide redundancy and isolation from failures in other zones.

3. **Datacenters**:
   - Datacenters are the physical facilities within Availability Zones where Azure's infrastructure is housed.

4. **Resources**:
   - Resources are the individual services and components you deploy in Azure, such as virtual machines, databases, and storage accounts.

5. **Resource Groups**:
   - Resource groups are containers that hold related resources for an Azure solution. They help manage and organize resources by lifecycle and permissions.

6. **Subscriptions**:
   - Subscriptions are used to manage billing and access to Azure services. They act as a boundary for resource management and policy application.

7. **Management Groups**:
   - Management groups are used to organize subscriptions into a hierarchy for unified policy and access management across multiple subscriptions.

This hierarchy allows for efficient management and organization of Azure resources, ensuring scalability, security, and compliance across your cloud environment.

 # Understand VM size families and names
<img width="982" height="909" alt="image" src="https://github.com/user-attachments/assets/170c0eaf-5de1-4fe0-a6c5-f0ec35c12e6a" />

  
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

💡 Na skúške AZ-104 si zapamätaj jednu jednoduchú otázku pri každom nástroji:

Azure Migrate → Ako dostanem servery do Azure?
Data Box → Čo ak mám obrovské množstvo dát a pomalý internet?
AzCopy → Ako rýchlo prenesiem súbory cez sieť?
Storage Explorer → Ako pohodlne spravujem Azure Storage?
File Sync → Ako prepojím lokálny file server s Azure?

| Tool                 | Remember This                                                     |
| -------------------- | ----------------------------------------------------------------- |
| **Azure Migrate**    | **Analyze and migrate servers**                                   |
| **Azure Data Box**   | **Physical appliance for massive offline data transfers**         |
| **AzCopy**           | **Fast command-line tool for copying data to/from Azure Storage** |
| **Storage Explorer** | **GUI for managing Azure Storage**                                |
| **Azure File Sync**  | **Synchronize on-premises file servers with Azure Files**         |


Toto je výborná AZ-104 úloha. Microsoft chce overiť, či rozumieš **Azure Storage Redundancy** a vieš vybrať správny typ podľa potrieb firmy.

# Azure Storage Redundancy Decision Matrix

| Redundancy                            | Copies                              | Protects Against               | Availability | Cost     | Best For                                  |
| ------------------------------------- | ----------------------------------- | ------------------------------ | ------------ | -------- | ----------------------------------------- |
| **LRS (Locally Redundant Storage)**   | 3 copies in one datacenter          | Disk/server failure            | ⭐⭐⭐          | 💲       | Development, test, non-critical workloads |
| **ZRS (Zone-Redundant Storage)**      | 3 copies across Availability Zones  | Datacenter failure             | ⭐⭐⭐⭐         | 💲💲     | Business-critical apps in one region      |
| **GRS (Geo-Redundant Storage)**       | LRS + replication to another region | Regional disaster              | ⭐⭐⭐⭐⭐        | 💲💲💲   | Disaster recovery, backups                |
| **GZRS (Geo-Zone-Redundant Storage)** | ZRS + replication to another region | Datacenter + regional disaster | ⭐⭐⭐⭐⭐        | 💲💲💲💲 | Mission-critical production systems       |

---

# Scenario

Predstav si slovenskú automobilku.

Aplikácia:

```text
Production Planning System
```

Obsahuje:

* výrobné plány
* objednávky
* logistiku

Ak nefunguje:

```text
Výroba sa zastaví.
```

---

# 1. LRS

### How it works

```text
Datacenter A

Copy 1
Copy 2
Copy 3
```

Všetky kópie sú v jednom datacentre.

### RPO

Veľmi nízke.

Ale:

Ak zhorí celé datacentrum:

```text
❌ Dáta sú nedostupné.
```

### Budget

Najlacnejšie.

### Use case

* Laby
* Vývoj
* Testovanie

---

# 2. ZRS

### How it works

```text
Zone 1
Copy

Zone 2
Copy

Zone 3
Copy
```

Každá kópia je v inom datacentre v rámci rovnakého Azure regiónu.

### RPO

Takmer nulové.

### Availability

Ak Zone 1 vypadne:

```text
Zone 2
Zone 3
```

stále fungujú.

### Budget

Stredná cena.

### Use case

Produkčné aplikácie.

---

# 3. GRS

### How it works

```text
West Europe
↓
North Europe
```

Azure replikuje dáta do druhého regiónu.

### RPO

Nie je nulové.

Pri veľkej katastrofe môžeš prísť o posledných pár minút zmien (replikácia je asynchrónna).

### Availability

Výborná pri regionálnych katastrofách.

### Budget

Vyššia cena.

---

# 4. GZRS

### How it works

```text
West Europe

Zone 1
Zone 2
Zone 3

↓

North Europe
```

Kombinuje:

* ZRS
* GRS

### Chráni proti:

✅ výpadku servera

✅ výpadku datacentra

✅ výpadku celého regiónu

### Budget

Najdrahšie.

---

# Recommendation

### Business-critical workload

Ak firma povedala:

```text
Naša výroba nesmie stáť.
```

Odporučil by som:

## ✅ GZRS

### Why?

### RPO

Veľmi nízke.

### Availability

Najvyššia.

### Disaster Recovery

Áno.

### Budget

Najdrahšie, ale opodstatnené pri kritických systémoch.

---

# Ak by firma mala obmedzený rozpočet

Odporučil by som:

## ✅ ZRS

Prečo?

* chráni proti výpadku jedného datacentra,
* stojí menej než GZRS,
* je vhodná pre väčšinu produkčných aplikácií.

---

# AZ-104 Cheat Sheet

| Requirement                              | Best Choice |
| ---------------------------------------- | ----------- |
| Najnižšia cena                           | **LRS**     |
| Ochrana proti výpadku datacentra         | **ZRS**     |
| Disaster Recovery medzi regiónmi         | **GRS**     |
| Maximálna dostupnosť + Disaster Recovery | **GZRS**    |

---

## Sample Answer (GitHub Notes)

```markdown
# Azure Storage Redundancy Comparison

## LRS (Locally Redundant Storage)
- 3 copies in one datacenter
- Lowest cost
- Protects against disk/server failure
- Not suitable for datacenter disasters

Best for:
- Development
- Testing
- Non-critical workloads

---

## ZRS (Zone-Redundant Storage)
- Replicates data across Availability Zones
- Survives datacenter failures
- Higher availability than LRS
- Moderate cost

Best for:
- Production applications
- Business-critical workloads within one Azure region

---

## GRS (Geo-Redundant Storage)
- Replicates data to a secondary Azure region
- Protects against regional disasters
- Asynchronous replication (RPO is not zero)
- Higher cost

Best for:
- Disaster recovery
- Long-term resilience

---

## GZRS (Geo-Zone-Redundant Storage)
- Combines ZRS and GRS
- Protects against server, datacenter, and regional failures
- Highest availability
- Highest cost

Best for:
- Mission-critical production systems
- Financial services
- Healthcare
- Manufacturing

---

## Recommendation

For a business-critical manufacturing system:

✅ Choose **GZRS**

Reason:
- Highest availability
- Protection against datacenter and regional failures
- Best resilience despite higher cost
```

**Zapamätaj si jednoduchú pomôcku na skúšku:**

* **LRS** = *Local* → jedno datacentrum.
* **ZRS** = *Zones* → viac datacentier v jednom regióne.
* **GRS** = *Geo* → druhý Azure región.
* **GZRS** = *Geo + Zones* → najvyššia úroveň ochrany a dostupnosti.


<img width="1050" height="399" alt="image" src="https://github.com/user-attachments/assets/59c43f61-3a5f-493a-b504-ab45123d2cd9" />

| Workload Pattern           | Azure Storage Service             | Performance | Durability | Access Requirements     | Why?                                                                            |
| -------------------------- | --------------------------------- | ----------- | ---------- | ----------------------- | ------------------------------------------------------------------------------- |
| Backup & Disaster Recovery | Azure Blob Storage (Cool/Archive) | ⭐⭐          | ⭐⭐⭐⭐⭐      | Občasný prístup         | Lacné, extrémne odolné úložisko na zálohy.                                      |
| File Sharing for Employees | Azure Files                       | ⭐⭐⭐         | ⭐⭐⭐⭐       | SMB/NFS z Windows/Linux | Zdieľané sieťové disky bez vlastného file servera.                              |
| Website Images & Videos    | Azure Blob Storage (Hot Tier)     | ⭐⭐⭐⭐        | ⭐⭐⭐⭐⭐      | HTTP/HTTPS z internetu  | Rýchle doručovanie obrázkov, videí a dokumentov.                                |
| Virtual Machine Disks      | Azure Managed Disks               | ⭐⭐⭐⭐⭐       | ⭐⭐⭐⭐⭐      | Pripojené iba k VM      | Optimalizované pre vysoký výkon a nízku latenciu operačných systémov a databáz. |


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


Create a short architecture walkthrough that combines compute hosting with one AI or IoT Edge service and explains why each component was chosen

Sensors on machines
        │
        ▼
Azure IoT Edge
        │
        ▼
Azure IoT Hub
        │
        ▼
Azure Function
        │
        ▼
Azure SQL Database
        │
        ▼
Azure App Service Dashboard

A smart factory solution uses Azure IoT Edge to collect and process sensor data locally, Azure IoT Hub to securely ingest telemetry, Azure Functions to process events and generate alerts, Azure SQL Database to store historical data, and Azure App Service to present dashboards. IoT Edge reduces latency, IoT Hub provides secure device management, Functions offer serverless event processing, SQL Database provides reliable storage, and App Service simplifies web application hosting.


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

| Port | Služba     |
| ---- | ---------- |
| 22   | SSH        |
| 80   | HTTP       |
| 443  | HTTPS      |
| 3389 | RDP        |
| 1433 | SQL Server |
| 445  | SMB        |
| 53   | DNS        |


Toto je veľmi dobrý spôsob učenia na **AZ-104, SC-900 a AZ-500**. Nestačí vedieť číslo portu, ale aj **na čo sa používa, prečo je dôležitý a aké sú bezpečnostné riziká**.

# Najdôležitejšie porty pre Azure a Security

| Port | Protokol        | Použitie                    |
| ---- | --------------- | --------------------------- |
| 22   | SSH             | Linux administrácia         |
| 53   | DNS             | Preklad názvov na IP adresy |
| 80   | HTTP            | Nešifrovaný web             |
| 443  | HTTPS           | Šifrovaný web               |
| 3389 | RDP             | Windows vzdialená plocha    |
| 1433 | SQL             | Microsoft SQL Server        |
| 445  | SMB             | Zdieľanie súborov           |
| 25   | SMTP            | Odosielanie e-mailov        |
| 110  | POP3            | Sťahovanie e-mailov         |
| 143  | IMAP            | Synchronizácia e-mailov     |
| 587  | SMTP TLS        | Moderné odosielanie pošty   |
| 636  | LDAPS           | Šifrovaný LDAP              |
| 389  | LDAP            | Active Directory            |
| 3306 | MySQL           | MySQL databázy              |
| 5432 | PostgreSQL      | PostgreSQL                  |
| 8080 | HTTP Alternate  | Web aplikácie               |
| 8443 | HTTPS Alternate | Web administrácia           |
| 161  | SNMP            | Monitoring zariadení        |

---

# TCP 22 — SSH

Používa sa na správu Linux serverov.

Príklad:

```bash
ssh admin@10.0.0.5
```

V Azure:

* Linux VM
* Ubuntu
* RedHat

Bezpečnosť:

❌ neotvárať celému internetu

✅ povoliť iba svoju IP

✅ používať SSH kľúče

---

# TCP 53 — DNS

Prekladá názvy.

Napríklad:

```text
portal.azure.com

↓

20.190.x.x
```

Bez DNS by si musel poznať IP každej služby.

Používa sa:

* DNS Server
* Azure DNS
* Private DNS

---

# TCP 80 — HTTP

Bežný web.

```text
http://example.com
```

Prenáša údaje otvorene.

Nebezpečenstvo:

```text
heslá
cookies
dáta
```

môžu byť odpočúvané.

Dnes sa odporúča:

✅ HTTPS

---

# TCP 443 — HTTPS

Šifrovaná komunikácia.

Používa:

```text
TLS
SSL
```

Príklady:

* Microsoft 365
* Azure Portal
* Banking
* eShop

Takmer všetko moderné ide cez 443.

---

# TCP 3389 — RDP

Windows vzdialená plocha.

Príklad:

```text
mstsc.exe

↓

Windows Server
```

Azure VM:

```text
Allow TCP 3389
```

Riziká:

* brute force
* ransomware

Odporúčané:

✅ Azure Bastion

✅ VPN

✅ JIT Access

---

# TCP 1433 — SQL Server

Používa:

Microsoft SQL Server

Príklad:

```text
Application

↓

SQL Database

Port 1433
```

Azure SQL:

často používa 1433.

Bezpečnosť:

✅ firewall

✅ private endpoint

---

# TCP 445 — SMB

Zdieľanie súborov.

Používa:

```text
\\SERVER\Documents
```

Azure:

```text
Azure Files
```

Port 445 býva blokovaný niektorými ISP.

---

# TCP 389 — LDAP

Active Directory.

Používa:

* overovanie používateľov
* Group Policy
* Domain Join

Nie je šifrovaný.

---

# TCP 636 — LDAPS

LDAP + TLS.

Bezpečnejší variant.

Používa:

```text
Microsoft Entra Domain Services
```

alebo klasické AD.

---

# TCP 3306 — MySQL

Databáza.

Používajú:

* WordPress
* web aplikácie
* e-commerce

---

# TCP 5432 — PostgreSQL

Veľmi populárna databáza.

Používajú:

* cloud aplikácie
* DevOps
* kontajnery

---

# TCP 25

SMTP.

Posielanie mailov.

Veľa cloud providerov ho obmedzuje.

Azure:

má limity na odosielanie cez port 25.

---

# TCP 587

Moderný SMTP.

Používa:

```text
SMTP + TLS
```

Microsoft 365.

Gmail.

Exchange.

---

# TCP 110

POP3.

Stiahne poštu do počítača.

Staršia technológia.

---

# TCP 143

IMAP.

Synchronizuje poštu.

Mail ostáva na serveri.

Používa ho Outlook.

---

# TCP 8080

Alternatívny HTTP.

Veľa aplikácií:

* Jenkins
* Tomcat
* proxy servery

---

# TCP 8443

Alternatívny HTTPS.

Často:

```text
https://server:8443
```

Používa sa pre:

* management rozhrania
* Kubernetes dashboard

---

# UDP 161

SNMP.

Monitoring.

Používa:

* switche
* routery
* tlačiarne

Napríklad:

```text
CPU Usage

Memory

Temperature
```

---

# SC-900 / AZ-104 Cheat Sheet

| Port | Zapamätaj si |
| ---- | ------------ |
| 22   | Linux        |
| 53   | DNS          |
| 80   | Web          |
| 443  | Secure Web   |
| 3389 | Windows      |
| 1433 | SQL          |
| 445  | Files        |
| 389  | LDAP         |
| 636  | Secure LDAP  |
| 3306 | MySQL        |
| 5432 | PostgreSQL   |
| 25   | SMTP         |
| 587  | Secure SMTP  |

---

### Pamäťová pomôcka

```text
22   → Linux
53   → DNS
80   → HTTP
443  → HTTPS
3389 → Windows
1433 → SQL
445  → File Server
389  → Active Directory
636  → Secure AD
3306 → MySQL
5432 → PostgreSQL
25   → Mail
587  → Secure Mail



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

# video.n.43-Microsoft Entra Overview

# Microsoft Entra Overview (AZ-900)

- **Microsoft Entra** = umbrella suite for identity & access solutions.
- Main portal: `entra.microsoft.com`

## Core Components

### Azure AD (Entra ID)
- Identity provider for users, apps, and devices.
- Supports:
  - Single Sign-On (SSO)
  - Conditional Access
  - Authentication for Azure, Microsoft 365, and 3rd-party apps

### Verified ID
- Decentralized identity system.
- Users control/verifiy credentials using apps like Microsoft Authenticator.
- Uses trusted verification systems (e.g. blockchain-style ledgers).

### Permissions Management
- Manages permissions across:
  - Azure
  - AWS
  - Google Cloud
- Helps enforce **least privilege access**.

### Workload Identities
- Protects non-human identities:
  - Service principals
  - Managed identities
- Includes monitoring, access reviews, and security policies.

### Identity Governance
- Features:
  - Access reviews
  - Entitlement management
  - Privileged Identity Management (PIM)
- Prevents permission sprawl.

### Lifecycle Workflows
- Automates onboarding/offboarding tasks:
  - Welcome emails
  - Access provisioning
  - Account removal after leaving

## Key Takeaway
Microsoft Entra centralizes identity, access management, governance, and automation into one ecosystem.


# video.n.44-Azure Directory Services

# Azure Directory Services (AZ-900 Notes)

## 📌 Core Idea

Microsoft identity services evolved from **traditional on-premises Active Directory** to **cloud-based Microsoft Entra ID** (formerly Azure AD).

Think of it like this:

| Old World                                | Cloud World                      |
| ---------------------------------------- | -------------------------------- |
| Active Directory Domain Services (AD DS) | Microsoft Entra ID               |
| Runs on company servers                  | Runs in Microsoft cloud          |
| Designed for internal networks           | Designed for internet/cloud apps |

---

# 🏢 Traditional Active Directory (On-Premises)

## What is Active Directory Domain Services (AD DS)?

AD DS is a centralized system for managing:

* Users
* Groups
* Computers
* Permissions
* Authentication

It allows users to:

✅ Log in once
✅ Access company resources
✅ Use Single Sign-On (SSO)

---

## 🖥️ Domain Controllers

AD DS runs on special servers called:

```text
Domain Controllers (DCs)
```

These servers:

* Store user accounts
* Handle authentication
* Enforce policies

Most companies use **2 or more** DCs for redundancy.

---

## 📂 Organizational Units (OUs)

OUs help organize resources in a hierarchy.

Example:

```text
Company
 ├── HR
 ├── IT
 └── Sales
```

OUs are useful for:

* Delegating admin permissions
* Applying Group Policies
* Organizing users/devices

---

## 🔑 Traditional Authentication Protocols

AD DS uses older enterprise protocols:

| Protocol | Purpose                 |
| -------- | ----------------------- |
| Kerberos | Authentication          |
| NTLM     | Legacy authentication   |
| LDAP     | Directory queries       |
| DNS      | Finding domain services |

These work best on **private internal networks**.

---

# ☁️ Microsoft Entra ID (Formerly Azure AD)

## What is Entra ID?

Entra ID is Microsoft's **cloud identity provider**.

It is designed for:

* Cloud applications
* Internet access
* SaaS services
* Azure resources

---

## 🌐 Modern Authentication

Unlike AD DS, Entra ID uses internet-friendly protocols:

| Protocol       | Purpose                   |
| -------------- | ------------------------- |
| OpenID Connect | Modern authentication     |
| SAML           | Single Sign-On            |
| WS-Fed         | Federation/authentication |

Everything mainly works securely over:

```text
HTTPS (Port 443)
```

---

# 🔗 Federation

Apps can trust Entra ID to authenticate users.

This means:

```text
User logs in once → Entra ID verifies identity
→ Apps trust Entra ID
```

Examples:

* Microsoft 365
* Azure
* Dynamics 365
* Third-party SaaS apps

---

# 🛡️ Conditional Access

One of the MOST important Entra ID features.

Conditional Access checks things like:

* User location
* Device health
* Risk level
* Group membership

Example:

```text
IF user is outside company country
THEN require MFA
```

This improves security significantly.

---

# 💻 Device Management

Devices can be:

| Type       | Meaning                     |
| ---------- | --------------------------- |
| Registered | Known to Entra ID           |
| Joined     | Fully connected to Entra ID |

Microsoft Intune can then manage devices by:

* Applying policies
* Managing apps
* Enforcing compliance

---

# 🔄 Hybrid Identity (Most Common Setup)

Most companies use BOTH:

```text
On-Prem AD DS + Entra ID
```

Why?

Because older systems still exist.

---

## 🔁 Identity Synchronization

Users created in AD DS can sync to Entra ID.

### Two Sync Methods

| Tool               | Description                     |
| ------------------ | ------------------------------- |
| Entra Connect Sync | Traditional on-prem sync server |
| Entra Cloud Sync   | Lightweight cloud-managed sync  |

Goal:

```text
One identity for both on-prem and cloud
```

---

# ☁️ Azure Resources & Legacy Authentication

Some applications still need:

* Kerberos
* NTLM
* LDAP

But Entra ID does NOT fully support traditional domain services behavior.

---

# 🔌 Solution 1: Connect to On-Prem AD

Azure networks can connect to on-premises networks using:

* Site-to-Site VPN
* ExpressRoute

This allows Azure resources to talk directly to existing domain controllers.

---

# 🏗️ Solution 2: Microsoft Entra Domain Services

If you DON'T have on-prem AD DS:

Use:

```text
Microsoft Entra Domain Services
```

This provides:

✅ Managed domain controllers
✅ Kerberos support
✅ NTLM support
✅ LDAP support

WITHOUT managing servers yourself.

---

## Important Limitation

With Entra Domain Services:

❌ You are NOT Domain Admin
❌ No direct access to domain controllers

Microsoft manages them for you.

---

# 🧠 Easy Mental Model

## AD DS

```text
Traditional office building identity system
```

Built for:

* Internal company networks
* Windows environments
* Legacy enterprise apps

---

## Entra ID

```text
Internet/cloud identity system
```

Built for:

* Cloud apps
* SaaS
* Remote work
* Modern authentication

---

## Entra Domain Services

```text
Bridge for legacy apps in Azure
```

Useful when apps still require:

* Kerberos
* LDAP
* NTLM

---

# ✅ Exam Takeaways (AZ-900)

Remember these key points:

| Concept               | Important Detail               |
| --------------------- | ------------------------------ |
| Entra ID              | Formerly Azure AD              |
| AD DS                 | Traditional on-prem directory  |
| Conditional Access    | Security policy engine         |
| Federation            | Apps trust Entra ID            |
| Intune                | Device management              |
| Hybrid Identity       | AD DS + Entra ID together      |
| Entra Domain Services | Managed legacy domain services |

---

# 🚀 Super Short Summary

```text
AD DS = Traditional on-prem identity

Entra ID = Cloud identity platform

Entra Domain Services = Managed legacy authentication in Azure
```

______________________
# video.n.45- Describe Azure external Identities


## 🌍 What Are External Identities?

External identities are **users outside your organization** who still need access to your apps or resources.

Examples:

* Business partners
* Vendors
* Contractors
* Customers using your application

Azure handles these differently from internal employees.

---

# 🏢 Internal vs External Users

## Internal Users

These are employees inside your company.

They can exist:

* Directly in Azure
* Synced from on-premises Active Directory

Example:

```text
Company Employee → Azure AD Account
```

---

## External Users

These are people outside your company.

Two main types:

| Type | Purpose                                  |
| ---- | ---------------------------------------- |
| B2B  | Collaborating with partner organizations |
| B2C  | Serving customers using your apps        |

---

# 🤝 B2B (Business-to-Business)

## What is it?

B2B is used when:

* Another company needs access to your resources
* You collaborate on projects
* You share apps, Teams channels, documents, etc.

Example:

```text
Your Company ↔ Partner Company
```

---

## 🔑 Key Idea

The external user:

* Uses THEIR own company login
* Authenticates with THEIR identity provider
* Still appears in YOUR Azure tenant as a guest identity

Azure creates a lightweight reference called a:

```text
Stub Object
```

---

## ✅ Why B2B is Better Than Creating Accounts Manually

Without B2B:

* You manage their passwords
* Security becomes messy
* Users forget multiple passwords
* Offboarding becomes difficult

With B2B:

* Their company manages their identity
* You only manage permissions

---

## Supported Identity Providers

Azure B2B supports:

* Another Azure tenant
* Microsoft accounts
* Google accounts
* Facebook accounts
* One-time email passcodes

---

## ✉️ One-Time Passcode Feature

If users don't have supported accounts:

* Azure sends a temporary code to their email

Benefits:

* No password management
* More secure
* Access disappears if email access is removed

---

# 👥 B2C (Business-to-Customer)

## What is it?

B2C is for:

* Customers using your applications
* Public-facing apps/websites

Example:

```text
Netflix / Spotify / Shopping App
```

---

## 🚨 Important Difference

With customers:

* You may have millions of users
* You DON'T want them inside your corporate tenant

So Azure uses:

```text
A Separate B2C Tenant
```

---

# 🎨 Why Use B2C?

B2C provides:

* Full branding customization
* Social login support
* Customer onboarding flows
* Signup/signin pages

Microsoft describes this as:

```text
"Customize every pixel"
```

---

# 🌐 Social Login Providers in B2C

B2C supports many identity providers:

* Google
* Facebook
* Apple
* Amazon
* Twitter
* WeChat
* Microsoft Accounts

And also:

```text
Local Accounts
```

---

# 📝 Local Accounts

Some users don't want social login.

So B2C allows:

```text
Create username/password directly in your app
```

Example:

```text
"Sign in with Google"
OR
"Create an account"
```

---

# 🔥 B2B vs B2C (Most Important Exam Concept)

| Feature         | B2B                   | B2C                   |
| --------------- | --------------------- | --------------------- |
| Audience        | Partners & vendors    | Customers             |
| Goal            | Collaboration         | Customer access       |
| Identity Source | External organization | Social/local accounts |
| Tenant Type     | Corporate tenant      | Separate B2C tenant   |
| Custom Branding | Limited               | Extensive             |
| Example         | Teams collaboration   | Shopping app login    |

---

# ⚡ B2B Direct Connect

Special feature mainly for:

```text
Microsoft Teams Shared Channels
```

Allows collaboration:

* Without adding every user manually as a guest

---

# 🧠 Easy Memory Trick

## B2B

```text
Business Partners
→ Collaboration
→ Corporate identities
```

## B2C

```text
Customers
→ Public applications
→ Social logins + branding
```

---

# 🎯 AZ-900 Exam Takeaway

Remember:

* **B2B** = collaborate with external organizations
* **B2C** = authenticate customers in apps
* B2C uses a separate tenant with rich customization
* B2B users authenticate using their own identities

---

# video.n.46.Functionallity of Conditional Access, MFA and SSO
# AZ-900 Notes — Conditional Access, MFA & SSO

> Beginner-friendly notes for understanding authentication and security in Microsoft cloud environments.

---

# 📚 Core Concepts

| Term                                  | Simple Meaning                                 |
| ------------------------------------- | ---------------------------------------------- |
| **Conditional Access**                | Rules that decide *when* users can access apps |
| **MFA (Multi-Factor Authentication)** | Extra security verification                    |
| **SSO (Single Sign-On)**              | Login once, access many apps                   |

---

# 🔐 1. Conditional Access

## What is it?

Conditional Access is like a **security guard** for your cloud apps.

It checks:

* Who you are
* Where you are logging in from
* What device you use
* Which app you want
* Whether the login looks risky

Then it decides:

* ✅ Allow access
* ❌ Block access
* 🔑 Ask for MFA

---

## Simple Logic

```text
IF certain conditions are true
THEN apply security controls
```

---

## Example

```text
If user logs in from outside company network
→ Require MFA
```

---

# 🧩 What Can Conditional Access Check?

## User / Group

```text
Admins only
HR department
Specific users
```

---

## Location

```text
Inside company network
Outside country
Unknown IP address
```

---

## Device

```text
Company laptop
Personal phone
Healthy/compliant device
```

---

## Application

```text
Microsoft 365
Azure Portal
Salesforce
Custom company app
```

---

## Risk Level

```text
Normal login
Suspicious login
High-risk sign-in
```

---

# 🎯 What Actions Can It Take?

| Action                   | Meaning                        |
| ------------------------ | ------------------------------ |
| Allow Access             | User can continue              |
| Block Access             | User denied                    |
| Require MFA              | Ask for extra verification     |
| Require Compliant Device | Device must meet company rules |
| Force Password Change    | User must reset password       |

---

# 🔄 Conditional Access Flow

```text
User signs in
      ↓
Conditional Access checks rules
      ↓
Conditions matched?
      ↓
Apply security requirements
      ↓
Grant or block access
```

---

# 🔑 2. MFA (Multi-Factor Authentication)

## What is MFA?

MFA means:

> Use MORE than one way to prove your identity.

---

# 🧠 The 3 Authentication Factors

## 1. Something You KNOW

```text
Password
PIN
```

---

## 2. Something You HAVE

```text
Phone
Authenticator app
Hardware token
Smart card
```

---

## 3. Something You ARE

```text
Fingerprint
Face scan
Biometrics
```

---

# ✅ MFA Examples

## Example 1

```text
Password + Phone App
```

---

## Example 2

```text
Fingerprint + PIN
```

---

# 🚨 Why MFA Matters

Passwords can be:

* guessed
* leaked
* stolen
* reused

MFA makes attacks MUCH harder.

Even if attacker knows password:

```text
They still need second factor
```

---

# ⚠️ Important AZ-900 Concept

Microsoft recommends:

❌ NOT asking for MFA constantly

Why?

```text
Users get tired
Users approve everything automatically
```

---

# ✅ Better Approach

Use Conditional Access to ask for MFA only when needed:

```text
New location
Unknown device
Sensitive application
Suspicious login
```

---

# 📱 MFA Methods in Microsoft Entra ID

| Method            | Example                 |
| ----------------- | ----------------------- |
| Authenticator App | Microsoft Authenticator |
| SMS Code          | Text message            |
| Phone Call        | Automated call          |
| Hardware Token    | Physical security key   |
| Biometrics        | Fingerprint / Face ID   |

---

# 🔓 3. SSO (Single Sign-On)

## What is SSO?

SSO means:

> Sign in ONCE → use many apps without logging in again.

---

# 🧠 Without SSO

```text
Login to Outlook
Login to Teams
Login to SharePoint
Login to Salesforce
```

Very annoying 😅

---

# ✅ With SSO

```text
Login once in the morning
↓
Access all trusted apps automatically
```

Much easier 👍

---

# 🎫 How SSO Works

After login:

* Entra ID gives user a **token**
* Apps trust that token
* User doesn't need to enter password again

---

# 🔄 SSO Flow

```text
User logs in once
      ↓
Entra ID creates authentication token
      ↓
User opens another app
      ↓
App trusts token
      ↓
No new login required
```

---

# 🏢 Real Example

```text
Morning login to company laptop
↓
Open Teams → No login prompt
↓
Open Outlook → No login prompt
↓
Open SharePoint → No login prompt
```

That's SSO.

---

# 🔗 How ALL 3 Work Together

```text
1. User signs in
        ↓
2. SSO token created
        ↓
3. User opens application
        ↓
4. Conditional Access checks rules
        ↓
5. If risky → Require MFA
        ↓
6. Access granted
```

---

# 📝 Quick Exam Notes

## Conditional Access

* Policy-based security
* Controls app access
* Uses conditions + rules
* Requires Entra ID Premium P1/P2

---

## MFA

* Uses multiple authentication methods
* Stronger security
* Commonly triggered by Conditional Access

---

## SSO

* One login for many apps
* Better user experience
* Uses authentication tokens

---

# 🧠 Easy Memory Tricks

| Term               | Remember This                  |
| ------------------ | ------------------------------ |
| Conditional Access | "Should this user get access?" |
| MFA                | "Prove it's really you"        |
| SSO                | "Login once"                   |

---


# video.n.47.Functionality and usage od RBAC---

# AZ-900 Notes — RBAC (Role-Based Access Control)

> Beginner-friendly notes for understanding authorization in Microsoft Azure.

---

# 🔐 What is RBAC?

RBAC stands for:

```text id="kn9r4v"
Role-Based Access Control
```

It controls:

> **WHO can do WHAT on WHICH resource**

---

# 🧠 Simple Idea

Instead of giving permissions one-by-one to users:

❌ Bad Approach

```text id="29f9li"
Give Alice permission A
Give Alice permission B
Give Alice permission C
```

✅ Better Approach

```text id="5u8v4f"
Assign Alice a ROLE
```

The role already contains permissions.

---

# 🎯 Purpose of RBAC

RBAC helps organizations:

* Manage permissions easily
* Improve security
* Limit unnecessary access
* Follow least privilege principle

---

# 👤 RBAC Components

RBAC has 3 main parts:

| Component          | Meaning              |
| ------------------ | -------------------- |
| Security Principal | WHO gets access      |
| Role Definition    | WHAT they can do     |
| Scope              | WHERE access applies |

---

# 1️⃣ Security Principal

A security principal is:

> The identity receiving permissions

Examples:

```text id="0rj7u8"
User
Group
Application
Service Principal
Managed Identity
```

---

# 2️⃣ Role Definition

A role definition is:

> A collection of permissions

Examples:

* Reader
* Contributor
* Owner

---

# 3️⃣ Scope

Scope defines:

> Where the permissions apply

---

# 📦 Azure Scope Hierarchy

```text id="eclm0o"
Management Group
    ↓
Subscription
    ↓
Resource Group
    ↓
Resource
```

---

# 📌 Important Rule

Permissions inherit downward.

Example:

```text id="8pnkto"
Access at Subscription level
↓
Also applies to all Resource Groups and Resources inside it
```

---

# 🔑 Common Built-in Roles

| Role                      | Permissions                  |
| ------------------------- | ---------------------------- |
| Reader                    | View resources only          |
| Contributor               | Create/manage resources      |
| Owner                     | Full control + manage access |
| User Access Administrator | Manage RBAC permissions      |

---

# 👀 Reader Role

Can:
✅ View resources

Cannot:
❌ Make changes
❌ Delete resources

Example:

```text id="1b85n3"
Auditors
Managers
Monitoring teams
```

---

# 🛠️ Contributor Role

Can:
✅ Create resources
✅ Modify resources
✅ Delete resources

Cannot:
❌ Assign permissions to others

---

# 👑 Owner Role

Can:
✅ Do everything
✅ Manage permissions
✅ Full administrative control

---

# 🔄 RBAC Example

```text id="f2hizj"
Bob = Contributor
Scope = Resource Group A
```

Result:

```text id="ypsqcr"
Bob can manage all resources inside Resource Group A
```

But:

```text id="q0k8tq"
Bob cannot manage resources outside that scope
```

---

# 🧩 Real-World Example

## HR Team

```text id="o0r0ho"
HR Group → Reader Role → Payroll App
```

Meaning:

* HR can view payroll data
* HR cannot modify infrastructure

---

# 🏢 Another Example

## Developer Team

```text id="vy53fk"
Developers → Contributor → Dev Resource Group
```

Meaning:

* Developers can create/test resources
* Only inside development environment

---

# 🚨 Principle of Least Privilege

Very important AZ-900 concept.

Give users:

> ONLY the access they truly need

---

# ❌ Bad Example

```text id="e2t5wm"
Everyone = Owner
```

Very dangerous ⚠️

---

# ✅ Good Example

```text id="1xj8u6"
Managers = Reader
Developers = Contributor
IT Admins = Owner
```

---

# 🔄 How RBAC Works

```text id="j8j6uo"
User tries to access resource
        ↓
Azure checks assigned role
        ↓
Azure checks scope
        ↓
Permissions allowed?
        ↓
Access granted or denied
```

---

# 🔐 RBAC vs Conditional Access

| RBAC                 | Conditional Access          |
| -------------------- | --------------------------- |
| Controls permissions | Controls sign-in conditions |
| Authorization        | Authentication/Security     |
| "What can you do?"   | "Can you sign in?"          |

---

# 🧠 Easy Way to Remember

## RBAC

```text id="3hmfrq"
What are you allowed to do?
```

## Conditional Access

```text id="mec8gd"
Under what conditions can you access?
```

---

# 🔗 RBAC + Entra ID

RBAC commonly works together with:

* Microsoft Entra ID
* Conditional Access
* MFA

---

# 📝 Quick Exam Notes

## RBAC

* Controls authorization
* Uses roles
* Access assigned at scopes
* Supports least privilege

---

# ⭐ Key Terms for AZ-900

| Term            | Meaning                   |
| --------------- | ------------------------- |
| Role Assignment | Linking role to user      |
| Scope           | Where permissions apply   |
| Inheritance     | Permissions flow downward |
| Least Privilege | Minimum required access   |

---

# 🧠 Super Simple Summary

## RBAC

```text id="k3p4qa"
WHO can do WHAT on WHICH resource
```

---

# ✈️ Easy Analogy

Think of a company office building:

| RBAC Part   | Office Example       |
| ----------- | -------------------- |
| User        | Employee             |
| Role        | Job title            |
| Scope       | Which office/floor   |
| Permissions | What they can access |

Example:

```text id="pk3d4s"
Receptionist
↓
Can enter lobby
↓
Cannot enter server room
```


# video.n.48-Functionallity and usage of Resource Locks

# AZ-900 Notes — Resource Locks

> Beginner-friendly notes for understanding Resource Locks in Microsoft Azure.

---

# 🔐 What are Resource Locks?

Resource Locks help prevent:

* accidental deletion
* accidental modification

Think of them as:

> “Extra protection for important Azure resources.”

---

# 🧠 Why Use Resource Locks?

Even admins can accidentally:

* delete a VM
* remove a storage account
* modify critical resources

Resource Locks add:

```text id="x4q0q5"
An extra safety step
```

---

# 🎯 Main Purpose

Resource Locks help protect:

* Production resources
* Critical databases
* Important storage accounts
* Shared infrastructure

---

# 📦 Where Can Locks Be Applied?

Locks can be applied at:

```text id="hzx7q9"
Subscription
Resource Group
Individual Resource
```

---

# 🌳 Azure Hierarchy

```text id="y4o42s"
Subscription
    ↓
Resource Group
    ↓
Resource
```

---

# 📌 Important Rule — Inheritance

Locks inherit downward.

Example:

```text id="2fqzly"
Lock applied to Resource Group
↓
All resources inside also become locked
```

---

# 🔒 Types of Resource Locks

There are ONLY 2 lock types.

---

# 1️⃣ CanNotDelete Lock

Also called:

```text id="z90vcm"
Delete Lock
```

---

## What It Does

✅ Can modify resource
❌ Cannot delete resource

---

## Example

```text id="s0ykkn"
Storage Account protected from accidental deletion
```

You can still:

* change settings
* update configurations

But:

```text id="z8wxyx"
Cannot delete it
```

---

# 2️⃣ ReadOnly Lock

## What It Does

❌ Cannot modify
❌ Cannot delete

Resource becomes:

```text id="35ujcg"
Read-only
```

---

## Example

```text id="obd8k2"
Critical production database
```

Admins can:
✅ View it

But cannot:
❌ Change settings
❌ Delete resource

---

# 🔄 Resource Lock Flow

```text id="n3bhzk"
User tries to modify/delete resource
        ↓
Azure checks for lock
        ↓
Lock exists?
        ↓
Operation blocked
```

---

# 🔑 Who Can Manage Resource Locks?

Usually:

```text id="gk9y2k"
Owner role
```

Owners can:

* Create locks
* Remove locks

---

# ⚠️ Important AZ-900 Concept

To delete a locked resource:

```text id="vj9a9j"
You must remove the lock FIRST
```

This prevents accidental mistakes.

---

# 🧠 Very Important Concept

# Resource Locks Protect the CONTROL PLANE

NOT the DATA PLANE.

---

# 🏗️ Control Plane vs Data Plane

| Plane         | Meaning                        |
| ------------- | ------------------------------ |
| Control Plane | Managing Azure resource itself |
| Data Plane    | Actual data inside resource    |

---

# 📦 Example — Storage Account

## Resource Lock Protects:

✅ Deleting storage account
✅ Modifying storage account settings

---

## Resource Lock DOES NOT Protect:

❌ Files inside storage
❌ Blobs inside storage
❌ Data modifications

---

# Example

Even with a lock:

```text id="0sfb5q"
You can still delete blobs/files inside storage account
```

Because:

```text id="p6ny6v"
That is DATA PLANE activity
```

---

# 🔥 Important Exam Question Area

Many AZ-900 questions test:

```text id="e6p7m9"
Resource Locks protect CONTROL PLANE only
```

NOT the data itself.

---

# 🧩 Real-World Example

## Scenario

Company has:

* critical production database
* shared storage account

They apply:

```text id="ms44q0"
CanNotDelete lock
```

Result:

* admins cannot accidentally delete resources
* resources stay protected

---

# 🛠️ Another Example

## Production VM

Apply:

```text id="n3jny5"
ReadOnly lock
```

Result:

* no accidental changes
* no accidental deletion

---

# 🔄 Example of Inheritance

```text id="8dij8q"
Resource Group locked
↓
VMs inside locked
↓
Storage Accounts inside locked
↓
Databases inside locked
```

---

# ⚠️ Important Limitation

Locks are NOT security permissions.

RBAC controls:

```text id="7kx6ov"
WHO can access resources
```

Locks control:

```text id="s6m5m5"
Preventing accidental changes/deletion
```

---

# 🔐 RBAC vs Resource Locks

| RBAC               | Resource Locks              |
| ------------------ | --------------------------- |
| Permission system  | Protection mechanism        |
| Controls access    | Prevents accidental actions |
| "Who can do this?" | "Should this be blocked?"   |

---

# 🧠 Easy Memory Trick

## RBAC

```text id="mpkjjw"
Controls PEOPLE
```

## Resource Locks

```text id="uijud4"
Protect RESOURCES
```

---

# 📝 Quick Exam Notes

## CanNotDelete

* Prevents deletion
* Allows modification

---

## ReadOnly

* Prevents modification
* Prevents deletion

---

## Inheritance

* Locks apply downward

---

## Important

* Protects CONTROL PLANE only
* Does NOT protect data inside resource

---

# ⭐ Super Simple Summary

## Resource Locks

```text id="x3o6nm"
Extra protection against accidental changes or deletion
```

---

# ✈️ Easy Analogy

Think of a document:

| Lock Type    | Real-Life Example          |
| ------------ | -------------------------- |
| CanNotDelete | Cannot throw document away |
| ReadOnly     | Cannot edit document       |

---


# video.n.49-Functionallity and usage of tags

> Beginner-friendly notes for understanding Tags in Microsoft Azure.

---

# 🏷️ What are Tags?

Tags are:

> Metadata labels added to Azure resources.

A tag is simply:

```text id="n6ml8s"
Key : Value
```

---

# 🧠 Simple Example

```text id="g2c26d"
Environment : Production
Owner : John
Department : HR
CostCenter : Finance
```

---

# 🎯 Purpose of Tags

Tags help organizations:

* organize resources
* search resources
* track costs
* identify ownership
* manage environments

---

# 📦 Where Can Tags Be Applied?

Tags can be added to:

```text id="b1f07l"
Subscription
Resource Group
Resource
```

---

# 🌳 Azure Hierarchy

```text id="9v9m8y"
Subscription
    ↓
Resource Group
    ↓
Resource
```

---

# ⚠️ IMPORTANT EXAM FACT

# Tags are NOT inherited by default

---

# Example

If Resource Group has tag:

```text id="ylt4f1"
Environment : Dev
```

Resources inside:

```text id="3a3y6t"
DO NOT automatically get the tag
```

---

# 🧠 Key AZ-900 Concept

## Resource Locks

✅ Inherited

## Tags

❌ NOT inherited

Very common exam question.

---

# 🔄 How to Auto-Apply Tags?

You can use:

```text id="44ay9i"
Azure Policy
```

Azure Policy can:

* require tags
* copy tags from parent resources
* enforce naming/tagging standards

---

# 🏷️ Common Tag Examples

| Key         | Example Value     |
| ----------- | ----------------- |
| Environment | Dev / Test / Prod |
| Owner       | Alice             |
| Department  | Finance           |
| CostCenter  | CC-100            |
| OS          | Windows 11        |
| Project     | WebsiteUpgrade    |

---

# 💰 Tags for Cost Management

Very common use case.

Example:

```text id="o06w5m"
CostCenter : Marketing
```

Now Azure billing reports can show:

* how much Marketing spends
* how much HR spends
* how much Dev team spends

---

# 🔍 Tags for Searching

Tags make resources easy to find.

Example:

```text id="if0wcc"
Environment : Production
```

You can filter Azure resources using that tag.

---

# 🛠️ Real Example

## Virtual Machine Tags

```text id="4o74hr"
Environment : Dev
Owner : John
OS : Windows 11
Department : IT
```

This helps admins quickly understand:

* who owns VM
* purpose
* environment
* operating system

---

# 🔄 Tag Structure

```text id="r2j6nk"
Tag Key = Category
Tag Value = Specific Information
```

Example:

```text id="j08cl0"
Key = Environment
Value = Production
```

---

# 📌 Important Characteristics

## Tags are:

✅ Metadata
✅ Flexible
✅ Searchable
✅ Useful for billing/reporting

---

## Tags are NOT:

❌ Security controls
❌ Resource locks
❌ Permissions

---

# 🔐 Tags vs RBAC vs Locks

| Feature        | Purpose                       |
| -------------- | ----------------------------- |
| Tags           | Organization/metadata         |
| RBAC           | Permissions/access            |
| Resource Locks | Prevent deletion/modification |

---

# 🧩 Real-World Example

## Company Resources

| Resource    | Tag                 |
| ----------- | ------------------- |
| HR VM       | Department: HR      |
| Finance DB  | CostCenter: Finance |
| Dev Storage | Environment: Dev    |

Now admins can:

* filter resources
* group costs
* identify ownership quickly

---

# ⚠️ Important Azure Policy Note

If Azure Policy requires tags:

```text id="p7av1w"
Resources without required tags may fail deployment
```

---

---

# 🔄 Tags vs Folders

Azure doesn't use folders like Windows.

Instead:

```text id="smjq1q"
Tags help logically organize resources
```

---

# 📝 Quick Exam Notes

## Tags

* Metadata key-value pairs
* Used for organization and billing
* NOT inherited by default
* Can be enforced using Azure Policy

---

# ⭐ Super Simple Summary

## Tags

```text id="s1q99e"
Labels used to organize and track Azure resources
```


---

# 🔥 Common AZ-900 Comparison

| Feature        | Inherited? |
| -------------- | ---------- |
| RBAC           | ✅ Yes      |
| Resource Locks | ✅ Yes      |
| Tags           | ❌ No       |


# video.n.50-Usage of Azure Policy

> Beginner-friendly notes for understanding governance and compliance in Microsoft Azure.

---

# 📘 What is Azure Policy?

Azure Policy is a service that helps enforce:

* company rules
* standards
* compliance requirements
* governance controls

---

# 🧠 Simple Definition

Azure Policy says:

```text id="s4n6na"
"What is allowed in Azure?"
```

It automatically checks resources against rules.

---

# 🎯 Main Goal

In cloud environments:

* users can create resources themselves
* deployments are automated
* there may be no admin manually checking things

Azure Policy acts like:

```text id="x5l7i2"
Automatic governance enforcement
```

---

# 🏢 Old IT vs Cloud

## Traditional IT

```text id="0fxj6r"
User requests server
↓
IT admin reviews request
↓
IT admin creates server
```

Admins manually enforced rules.

---

## Cloud / Azure

```text id="h1g0ho"
User deploys resources directly
↓
Azure Policy checks requirements automatically
```

---

# 🛡️ Why Azure Policy Matters

Organizations still need rules like:

```text id="r31h6i"
Only approved Azure regions
No public IP addresses
Specific VM sizes only
Required tags
Encryption enabled
```

Azure Policy enforces these automatically.

---

# 🔄 Where Azure Policy Works

Azure Policy works at:

```text id="6rqyyg"
Azure Resource Manager (ARM)
```

Every deployment goes through ARM first.

---

# 🌳 Azure Hierarchy

Policies can be applied at multiple scopes:

```text id="s2odto"
Management Group
    ↓
Subscription
    ↓
Resource Group
    ↓
Resource
```

---

# 📌 Important Rule

Azure Policies are:

```text id="jlwm1z"
Inherited downward
```

Example:

```text id="oh6d22"
Policy at Subscription level
↓
Applies to all Resource Groups and Resources inside it
```

---

# 🧩 What is a Policy?

A policy is basically:

```text id="wl38kp"
IF condition is true
THEN apply effect
```

---

# Example

```text id="nvvzmg"
IF storage account type is not approved
THEN deny deployment
```

---

# 📦 What is an Initiative?

An Initiative is:

> A collection of multiple policies

---

# Why Use Initiatives?

Instead of assigning:

```text id="h4yq3x"
100 separate policies
```

You group them into:

```text id="yw4w63"
1 initiative
```

Much easier to manage.

---

# 🏛️ Real Example

Compliance standards often use initiatives:

* HIPAA
* NIST
* ISO
* Microsoft Cloud Security Benchmark

These contain MANY policies together.

---

# 🔥 Common Azure Policy Effects

Policies can perform different actions.

---

# 1️⃣ Audit

## Purpose

Only checks compliance.

✅ Resource still deploys
⚠️ Azure logs warning/non-compliance

---

## Example

```text id="phg2r3"
Audit resources missing tags
```

---

# 2️⃣ Deny

## Purpose

Blocks deployment.

❌ Resource cannot be created

---

## Example

```text id="f3j64f"
Deny storage accounts in unapproved regions
```

---

# 3️⃣ Append

## Purpose

Automatically adds information.

---

## Example

```text id="qhy8vx"
Automatically add required tags
```

---

# 4️⃣ Modify

## Purpose

Changes resource configuration automatically.

---

# 5️⃣ DeployIfNotExists

## Purpose

Automatically deploys required resources/settings.

---

## Example

```text id="yjlwmw"
If monitoring agent missing
→ Automatically install it
```

---

# 🧠 Best Practice

Start with:

```text id="ys1l4e"
Audit mode first
```

Why?

Because a bad policy could:

* break deployments
* stop production systems
* block developers

---

# ✅ Recommended Approach

```text id="d3nfs4"
1. Audit
2. Review impact
3. Fix issues
4. Change to Deny
```

---

# 🏷️ Azure Policy + Tags

Azure Policy is commonly used to:

* require tags
* auto-add tags
* enforce naming standards

---

# Example

```text id="b2h3pw"
Require:
Environment tag
CostCenter tag
Owner tag
```

---

# 🔄 Azure Policy Flow

```text id="s9oh6o"
User deploys resource
        ↓
Azure Resource Manager receives request
        ↓
Azure Policy evaluates rules
        ↓
Compliant?
        ↓
Allow / Audit / Deny / Modify
```

---

# 🧩 Real-World Examples

---

# Example 1 — Allowed Regions

Company policy:

```text id="30mbf8"
Resources allowed only in Europe
```

Azure Policy:

```text id="9tqt8o"
Deny deployments outside approved regions
```

---

# Example 2 — Security

Company requirement:

```text id="q0f6uw"
No public IP addresses allowed
```

Azure Policy:

```text id="e6u90v"
Deny public IP creation
```

---

# Example 3 — Cost Control

Company requirement:

```text id="xg7jws"
Only approved VM sizes allowed
```

Azure Policy:

```text id="pd12mr"
Block expensive VM types
```

---

# 🔐 Azure Policy vs RBAC

| Azure Policy             | RBAC                    |
| ------------------------ | ----------------------- |
| Controls WHAT is allowed | Controls WHO has access |
| Governance/compliance    | Permissions/access      |
| Resource rules           | User permissions        |

---

# 🔐 Azure Policy vs Resource Locks

| Azure Policy            | Resource Locks              |
| ----------------------- | --------------------------- |
| Governance rules        | Prevent accidental deletion |
| Automated enforcement   | Manual protection           |
| Works during deployment | Works after deployment      |

---

# 📊 Compliance Tracking

Azure Policy also tracks:

* compliant resources
* non-compliant resources
* compliance percentage

Very useful for:

* security audits
* governance reporting
* compliance monitoring

---

# 🧠 Easy Memory Trick

## Azure Policy

```text id="3u0y3t"
Company rules for Azure
```

Think:

```text id="2v11md"
"Guard rails"
```

---

# 📝 Quick Exam Notes

## Azure Policy

* Governance service
* Enforces standards and compliance
* Uses policies and initiatives
* Applied at multiple scopes
* Inherited downward

---

# 🔥 Important Exam Concepts

| Concept                         | Important? |
| ------------------------------- | ---------- |
| Policies are inherited          | ✅ YES      |
| Audit mode                      | ✅ YES      |
| Deny effect                     | ✅ YES      |
| Initiatives = group of policies | ✅ YES      |
| Works through ARM               | ✅ YES      |

---

# ⭐ Super Simple Summary

## Azure Policy

```text id="jffv5y"
Automatically enforce company rules in Azure
```

---

# video.n.51-Microsoft Purview OVerview
# AZ-900 Notes — Microsoft Purview

> Beginner-friendly notes for understanding data governance and compliance in Microsoft cloud environments.

---

# 📘 What is Microsoft Purview?

Microsoft Purview is a:

> Data governance, compliance, and data discovery solution.

Its main goal is to help organizations understand:

```text id="76afkq"
What data they have
Where the data is
How sensitive the data is
How the data is being used
```

---

# 🧠 Simple Definition

Microsoft Purview helps companies:

```text id="jls7vo"
Protect and manage their data
```

---

# 🎯 Main Purpose

Organizations store data everywhere:

* Azure
* Microsoft 365
* AWS
* Databases
* On-premises servers
* SaaS apps

Purview gives:

```text id="mvl4lg"
One unified view of all data
```

---

# 🌍 Data Sources Supported

Purview supports MANY data sources.

---

# ☁️ Microsoft Services

Examples:

* Microsoft Azure Blob Storage
* Azure SQL Database
* Data Lake
* Microsoft SharePoint
* Microsoft Teams
* Power BI

---

# 🌐 Other Clouds

Examples:

* Amazon Web Services S3
* Other SaaS platforms

---

# 🏢 On-Premises Data

Purview can also scan:

* local databases
* file systems
* internal company storage

---

# 🔑 Core Goal

The BIG idea is:

```text id="l3up5z"
Prevent data exposure
```

To protect data:

1. Find it
2. Understand it
3. Classify it
4. Secure it

---

# 🗺️ Main Components of Purview

| Component          | Purpose                 |
| ------------------ | ----------------------- |
| Data Map           | Discover and scan data  |
| Classification     | Identify sensitive data |
| Sensitivity Labels | Apply security labels   |
| Data Catalog       | Unified searchable view |
| Data Lineage       | Track data movement     |
| Data Sharing       | Secure sharing          |
| Estate Insights    | Governance dashboards   |

---

# 🗺️ 1. Data Map

The Data Map:

> Scans and discovers data sources.

---

# Important Feature

Purview scans:

```text id="b8ub2m"
Data in place
```

Meaning:

* data stays where it already exists
* no need to move/import all data

---

# Example

Purview can scan:

```text id="m25tb6"
Azure Blob Storage
AWS S3
SQL Databases
Microsoft 365
```

Without copying the data elsewhere.

---

# 🔍 2. Data Classification

Purview can automatically identify:

* credit card numbers
* passport numbers
* social security numbers
* personal information

---

# Example

```text id="w5qlhl"
Detect:
Credit Card Numbers
PII
Confidential Data
```

---

# 🧠 Built-in Classifications

Purview includes:

```text id="znkjs5"
200+ built-in classifiers
```

You can also create custom ones.

---

# 🏷️ 3. Sensitivity Labels

After data is classified:
Purview can apply labels.

---

# Example

```text id="jnpmy3"
Highly Confidential
PII
Public
Internal Only
```

---

# Why Labels Matter

Labels can trigger actions like:

* encryption
* DLP policies
* retention policies
* access restrictions

---

# 🔐 Example

```text id="8r1ijv"
If file contains credit card numbers
↓
Apply "Highly Sensitive" label
↓
Block external sharing
```

---

# 🔄 4. Data Lineage

Data lineage tracks:

> Where data came from and where it moved.

---

# Example

```text id="jlwm06"
Database
↓
Data transformation
↓
Power BI dashboard
↓
Reports
```

Purview shows the full journey.

---

# 📚 5. Data Catalog

The Data Catalog provides:

```text id="vjlwmm"
One searchable view of all data
```

---

# Why Important?

Data may:

* exist in many systems
* be duplicated
* be renamed

Purview normalizes everything into:

```text id="4owmx8"
A single unified catalog
```

---

# 🔍 Example

A customer record may exist in:

* SQL database
* Excel file
* SharePoint
* Power BI

Purview helps identify:

```text id="zqqkq4"
These are all related
```

---

# 🤝 6. Data Sharing

Purview supports secure data sharing.

---

# Important Feature

Data sharing is:

```text id="z48mmk"
In-place
```

Meaning:

* data is NOT copied
* data stays in original location

---

# Example

Company A shares storage with Company B.

Result:

```text id="v57s4z"
Company B sees data
BUT data physically stays with Company A
```

---

# Benefits

✅ Better governance
✅ No unnecessary duplication
✅ Easier control/revocation

---

# 📊 7. Estate Insights

Estate Insights provide:

* dashboards
* compliance reports
* governance analytics

Mostly useful for:

* security teams
* compliance teams
* executives

---

# Example Insights

```text id="w11g4u"
Sensitive data locations
Compliance risks
Data usage patterns
```

---

# 🔐 Purview + Security

Purview often works with:

* DLP (Data Loss Prevention)
* Microsoft 365 Compliance
* Sensitivity Labels
* Retention Policies

---

# 🆓 Free vs Enterprise

Purview has:

* Free version
* Enterprise version

---

# Free Version

Limited features:

* basic catalog
* limited data sources

---

# Enterprise Version

Includes:

* advanced governance
* more data sources
* advanced analytics
* security/compliance tools

---

# 🧠 Easy Memory Trick

## Microsoft Purview

```text id="r2bwrj"
"Know your data"
```

---

# 📝 Quick Exam Notes

## Microsoft Purview

* Data governance solution
* Scans data across environments
* Supports classification and labeling
* Tracks data lineage
* Creates unified data catalog

---

# 🔥 Important AZ-900 Concepts

| Concept               | Important? |
| --------------------- | ---------- |
| Data classification   | ✅ YES      |
| Sensitivity labels    | ✅ YES      |
| Data lineage          | ✅ YES      |
| Unified data catalog  | ✅ YES      |
| Data scanned in place | ✅ YES      |

---

# 🔐 Purview vs Azure Policy

| Microsoft Purview                | Azure Policy            |
| -------------------------------- | ----------------------- |
| Governs DATA                     | Governs AZURE RESOURCES |
| Data discovery/classification    | Resource compliance     |
| Sensitive information protection | Deployment rules        |

---

# ⭐ Super Simple Summary

## Microsoft Purview

```text id="c9u8mn"
Discover, classify, protect, and govern organizational data
```

---

# ✈️ Easy Analogy

Think of Purview like a library management system 📚

| Purview Feature | Library Example        |
| --------------- | ---------------------- |
| Data Catalog    | Library index          |
| Classification  | Book categories        |
| Labels          | "Restricted" stickers  |
| Lineage         | Book borrowing history |
| Insights        | Library reports        |

---

# video.n.52-Governance Hierarchy Constructs


> Beginner-friendly notes for understanding Azure governance hierarchy in Microsoft Azure.

---

# 🌳 Azure Governance Hierarchy

Azure uses a hierarchy structure to organize:

* management
* governance
* permissions
* policies
* budgets

---

# 🏗️ Full Azure Hierarchy

```text id="j6d1oo"
Microsoft Entra ID
        ↓
Root Management Group
        ↓
Management Groups
        ↓
Subscriptions
        ↓
Resource Groups
        ↓
Resources
```

---

# 🔐 1. Microsoft Entra ID

Previously called:

```text id="7i2ce4"
Azure Active Directory (Azure AD)
```

---

## Purpose

Stores identities like:

* users
* groups
* applications
* devices

---

## Example

```text id="96x6jv"
Employees
Admins
Service Accounts
```

---

# 🌲 2. Root Management Group

Automatically created under Entra ID.

Purpose:

```text id="rnpdkt"
Top-level governance container
```

Everything in Azure belongs under it.

---

# 🧩 3. Management Groups

Management Groups help organize subscriptions.

---

## Why Use Them?

Useful for:

* large companies
* multiple departments
* governance at scale

---

# Example Structure

```text id="o9gtvw"
Company
 ├── Production
 ├── Development
 └── Testing
```

---

# 📌 Important Fact

You can create:

```text id="odnhfu"
Up to 6 levels deep
```

(not counting the root management group)

---

# 💳 4. Subscriptions

A Subscription is:

> A billing and management boundary.

---

## Purpose

Subscriptions help separate:

* billing
* environments
* departments
* workloads

---

# Example

```text id="x6y0ja"
Production Subscription
Development Subscription
HR Subscription
```

---

# 📌 Important Fact

Subscriptions:

```text id="yw3wtx"
CANNOT be nested
```

---

# 📦 5. Resource Groups

Resource Groups contain Azure resources.

---

# Purpose

Resources in same Resource Group should:

```text id="3sv1g9"
Share the same lifecycle
```

Meaning:

* created together
* managed together
* deleted together

---

# Example

```text id="i9i4gv"
Web App
Database
Storage Account
```

All supporting same application.

---

# 📌 Important Fact

Resource Groups:

```text id="0m5e4r"
CANNOT be nested
```

---

# 🖥️ 6. Resources

Resources are actual Azure services.

Examples:

* Virtual Machines
* Storage Accounts
* Databases
* Networks

---

# 🔑 3 Major Governance Features

The lesson focuses on 3 important governance tools:

| Governance Feature | Purpose            |
| ------------------ | ------------------ |
| Azure Policy       | Rules & compliance |
| RBAC               | Permissions        |
| Budgets            | Cost control       |

---

# 🛡️ 1. Azure Policy

Azure Policy creates:

```text id="5vjlwm"
Governance guard rails
```

---

# What Policies Can Do

| Action    | Purpose                  |
| --------- | ------------------------ |
| Deny      | Block actions            |
| Audit     | Track compliance         |
| Remediate | Automatically fix issues |

---

# Example

```text id="jlwmjx"
Require specific tags
Block public IPs
Allow only approved regions
```

---

# 📌 Important Concept

Policies are:

```text id="z65r0h"
Inherited downward
```

---

# Example

```text id="0w45jh"
Policy at Management Group
↓
Applies to all child subscriptions and resources
```

---

# 👥 2. RBAC (Role-Based Access Control)

RBAC controls:

```text id="d8o6m4"
WHO can do WHAT
```

---

# RBAC Formula

```text id="iwcmum"
Identity + Role + Scope
```

---

# Example

```text id="u1v0eh"
Alice = Contributor
Scope = Dev Subscription
```

Alice can manage resources in Dev Subscription.

---

# 📌 Important Concept

RBAC assignments are also:

```text id="7nqjlwm"
Inherited downward
```

---

# 💰 3. Budgets

Budgets help track:

```text id="jlwm4z"
Azure spending
```

---

# Budget Alerts

Azure can alert based on:

* actual spending
* forecasted spending

---

# Example

```text id="4ijcnm"
80% budget reached
Forecast predicts overspending
```

---

# 📌 Budget Scope

Budgets can be assigned at:

* Management Group
* Subscription
* Resource Group

---

# 🔄 Inheritance in Azure

Very important AZ-900 concept.

---

# What Gets Inherited?

| Feature        | Inherited? |
| -------------- | ---------- |
| Azure Policy   | ✅ Yes      |
| RBAC           | ✅ Yes      |
| Resource Locks | ✅ Yes      |
| Tags           | ❌ No       |

---

# 🧠 Governance Best Practice

## Higher Levels

Apply:

```text id="rgjlwm"
Broad company-wide rules
```

Example:

* allowed regions
* security requirements

---

## Lower Levels

Apply:

```text id="jlwmwv"
Specific resource rules
```

Example:

* app-specific permissions
* dev/test policies

---

# 🔥 Common AZ-900 Exam Points

| Concept                         | Important? |
| ------------------------------- | ---------- |
| Management Groups hierarchy     | ✅ YES      |
| Policies inherited downward     | ✅ YES      |
| RBAC inheritance                | ✅ YES      |
| Resource Groups share lifecycle | ✅ YES      |
| Subscriptions cannot be nested  | ✅ YES      |

---

# 🧠 Easy Memory Trick

## Management Groups

```text id="jlwm0q"
Organization
```

## Subscriptions

```text id="bdzjlwm"
Billing boundary
```

## Resource Groups

```text id="jlwm1a"
Lifecycle grouping
```

## Resources

```text id="jlwm2b"
Actual Azure services
```

---

# ⭐ Super Simple Summary

## Azure Governance Hierarchy

```text id="jlwm3c"
Organize → Govern → Secure → Control Costs
```

---

# ✈️ Easy Analogy

Think of a company structure:

| Azure Construct  | Real-Life Example   |
| ---------------- | ------------------- |
| Entra ID         | Company directory   |
| Management Group | Corporate divisions |
| Subscription     | Department budget   |
| Resource Group   | Project team        |
| Resources        | Actual equipment    |

---

# video.n.54-Describe Cloud Adoption Framework

> Beginner-friendly notes for understanding the Microsoft Cloud Adoption Framework for Azure.

---

# ☁️ What is the Cloud Adoption Framework?

The Cloud Adoption Framework (CAF) is:

> A collection of best practices, guidance, and tools for adopting cloud services successfully.

---

# 🧠 Simple Definition

CAF helps organizations answer:

```text id="z7mx6j"
"How do we move to the cloud successfully?"
```

---

# 🎯 Main Goal

The framework helps companies:

* plan cloud adoption
* organize cloud migration
* apply governance
* improve security
* manage cloud environments properly

---

# 📌 Why CAF Exists

Moving to the cloud can feel overwhelming because there are many things to consider:

* governance
* security
* identity
* networking
* migration
* cost management
* operations

CAF provides:

```text id="jlwm7u"
Step-by-step best practices
```

---

# 🔄 Cloud Adoption Lifecycle

CAF is built around a lifecycle approach.

---

# 🌟 Main CAF Stages

```text id="jlwm8v"
Strategy
    ↓
Plan
    ↓
Ready
    ↓
Adopt
    ↓
Govern
    ↓
Manage
```

---

# 1️⃣ Strategy

## Purpose

Understand:

* business goals
* motivations
* expected outcomes

---

# Questions Asked

```text id="jlwm9w"
Why are we moving to the cloud?
What business problems are we solving?
```

---

# Example

* reduce costs
* improve scalability
* modernize applications
* enable remote work

---

# 2️⃣ Plan

## Purpose

Create cloud adoption plans.

---

# Includes

* skills readiness
* migration planning
* workload prioritization
* team organization

---

# Example

```text id="jlwm0x"
Which applications move first?
What training do teams need?
```

---

# 3️⃣ Ready

## Purpose

Prepare the Azure environment.

---

# Includes

* Azure landing zones
* identity setup
* networking
* governance
* subscriptions

---

# 🛬 What is a Landing Zone?

A Landing Zone is:

> A prepared Azure environment following best practices.

---

# Includes

```text id="jlwm1y"
Networking
Security
Policies
Identity
Management setup
```

---

# 4️⃣ Adopt

## Purpose

Actually move or build workloads in Azure.

---

# Two Main Paths

| Method   | Meaning                     |
| -------- | --------------------------- |
| Migrate  | Move existing systems       |
| Innovate | Build new cloud-native apps |

---

# Example

```text id="jlwm2z"
Move virtual machines to Azure
OR
Build modern apps using Azure services
```

---

# 5️⃣ Govern

## Purpose

Ensure compliance and control.

---

# Includes

* Azure Policy
* RBAC
* tagging
* security standards
* cost control

---

# Goal

```text id="jlwm3a"
Maintain governance guard rails
```

---

# 6️⃣ Manage

## Purpose

Operate and monitor cloud resources.

---

# Includes

* monitoring
* backups
* updates
* cost optimization
* incident response

---

# 🔑 Key Idea of CAF

CAF is NOT:

```text id="jlwm4b"
A single tool
```

It is:

```text id="jlwm5c"
A best-practice framework
```

---

# 🧩 CAF Helps Organizations

| Area            | CAF Helps With          |
| --------------- | ----------------------- |
| Governance      | Policies & compliance   |
| Security        | Best practices          |
| Migration       | Cloud transition        |
| Cost Management | Budgeting               |
| Operations      | Monitoring & management |

---

# 📌 Important AZ-900 Concept

CAF provides:

```text id="jlwm6d"
Guidance for successful cloud adoption
```

---

# 🧠 Easy Memory Trick

## CAF

```text id="jlwm7e"
Plan → Prepare → Move → Govern → Manage
```

---

# 🌍 Real-World Example

A company wants to:

* move apps to Azure
* reduce datacenter costs
* improve scalability

CAF helps them:

1. Define goals
2. Plan migration
3. Prepare Azure
4. Migrate workloads
5. Govern resources
6. Manage operations

---

# ⭐ Super Simple Summary

## Cloud Adoption Framework

```text id="jlwm8f"
Microsoft best practices for successful cloud adoption
```

---

# ✈️ Easy Analogy

Think of CAF like building a house 🏠

| CAF Stage | House Example             |
| --------- | ------------------------- |
| Strategy  | Decide why you need house |
| Plan      | Create blueprint          |
| Ready     | Prepare land/utilities    |
| Adopt     | Build the house           |
| Govern    | Apply safety rules        |
| Manage    | Maintain the house        |

---

# video.n.55-Describe Cloud Adoption Framework
# AZ-900 Notes — Microsoft Privacy Statement, OST, and DPA

> Beginner-friendly notes for understanding important Microsoft privacy and compliance documents.

---

# 📘 Why These Documents Matter

When using cloud services, organizations need to know:

* what data is collected
* how data is protected
* legal responsibilities
* compliance requirements

Microsoft provides official documents explaining these topics.

---

# 🧩 The 3 Important Documents

| Document                       | Purpose                                        |
| ------------------------------ | ---------------------------------------------- |
| Microsoft Privacy Statement    | Explains data collection and usage             |
| Online Services Terms (OST)    | Legal agreement between Microsoft and customer |
| Data Protection Addendum (DPA) | Details data protection and security practices |

---

# 1️⃣ Microsoft Privacy Statement

## Purpose

Explains:

```text id="h1j8s2"
What personal data Microsoft collects
How it is used
Why it is collected
```

---

# 🧠 Simple Definition

Think of it as:

```text id="o2k7v4"
Microsoft's transparency document
```

---

# Example Topics

* diagnostic data
* account information
* usage information
* cookies
* telemetry

---

# Key Focus

```text id="t9m3pq"
Personal data handling
```

---

# 📌 Important AZ-900 Point

If someone asks:

```text id="l5w0nc"
"What data does Microsoft collect?"
```

Answer:

```text id="c6v9xr"
Microsoft Privacy Statement
```

---

# 2️⃣ Online Services Terms (OST)

## Purpose

The OST is:

> The legal agreement between Microsoft and the customer.

---

# Covers Topics Like

* customer obligations
* Microsoft obligations
* service usage terms
* security responsibilities
* acceptable use policies

---

# 🧠 Simple Definition

Think of OST as:

```text id="d8q2ya"
The contract for using Microsoft cloud services
```

---

# Key Focus

```text id="w7u3oe"
Legal terms and service agreements
```

---

# Example

The OST explains:

* what customers are allowed to do
* Microsoft's responsibilities
* service conditions

---

# 📌 Important AZ-900 Point

If someone asks:

```text id="k1r7mb"
"What document defines the legal agreement between Microsoft and customer?"
```

Answer:

```text id="j4t6zs"
Online Services Terms (OST)
```

---

# 3️⃣ Data Protection Addendum (DPA)

## Purpose

The DPA provides:

> Detailed information about data processing and security protections.

---

# Covers Topics Like

* data processing
* encryption
* security practices
* compliance
* data retention
* deletion
* international data transfers

---

# 🧠 Simple Definition

Think of DPA as:

```text id="v3n1fp"
Detailed security and data protection rules
```

---

# Key Focus

```text id="r5x9uk"
How customer data is secured and processed
```

---

# Example Topics

* GDPR compliance
* security controls
* breach handling
* access controls
* retention policies

---

# 📌 Important AZ-900 Point

If someone asks:

```text id="a7p0ye"
"Where can I find details about Microsoft's data security practices?"
```

Answer:

```text id="q9d2wl"
Data Protection Addendum (DPA)
```

---

# 🔄 Easy Comparison Table

| Document          | Main Purpose                       |
| ----------------- | ---------------------------------- |
| Privacy Statement | What Microsoft collects            |
| OST               | Legal agreement                    |
| DPA               | Security & data protection details |

---

# 🧠 Easy Memory Trick

## Privacy Statement

```text id="u2g4mh"
"What data is collected?"
```

---

## OST

```text id="x8k1pr"
"What are the legal terms?"
```

---

## DPA

```text id="z4m7ty"
"How is data protected?"
```

---

# 🔐 Real-World Analogy

| Document          | Real-Life Analogy |
| ----------------- | ----------------- |
| Privacy Statement | Privacy notice    |
| OST               | Service contract  |
| DPA               | Security handbook |

---

# 📌 Important Exam Tip

For AZ-900:

```text id="m1c8eq"
You DO NOT need to memorize the documents word-for-word
```

You only need to know:

* they exist
* their main purpose
* when each one is used

---

# 🔥 Common AZ-900 Questions

| Question                          | Correct Document  |
| --------------------------------- | ----------------- |
| What data does Microsoft collect? | Privacy Statement |
| What are the legal service terms? | OST               |
| How is customer data protected?   | DPA               |

---

# ⭐ Super Simple Summary

## Microsoft Privacy Statement

```text id="g6y3vo"
Explains what data Microsoft collects
```

---

## OST

```text id="y9f1ka"
Legal agreement for online services
```

---

## DPA

```text id="b4u8nx"
Explains data protection and security practices
```

---

# video.n.56-Purpose of Trust center and Azure Compliance Documentation


> Beginner-friendly notes for understanding the Microsoft Trust Center and Azure compliance resources.

---

# 📘 What is the Microsoft Trust Center?

The Microsoft Trust Center is:

> The main hub for security, privacy, compliance, and trust information about Microsoft cloud services.

---

# 🧠 Simple Definition

Think of the Trust Center as:

```text id="a7n3pl"
Microsoft's transparency portal
```

It explains:

* how Microsoft secures data
* how compliance works
* how privacy is protected

---

# 🎯 Why the Trust Center Exists

When companies move to the cloud:

```text id="p5k1wr"
They trust Microsoft with their data
```

So Microsoft must:

* earn trust
* maintain trust
* provide transparency

---

# 🔑 Main Trust Pillars

Microsoft focuses on 3 major trust pillars:

| Pillar     | Meaning                             |
| ---------- | ----------------------------------- |
| Security   | Protect systems and data            |
| Privacy    | Protect customer information        |
| Compliance | Meet legal and regulatory standards |

---

# 🔐 1. Security

Security focuses on:

* defense in depth
* physical security
* encryption
* identity protection
* threat protection

---

# Example Topics

```text id="m9v2xu"
Data center security
Access controls
Disaster protection
Encryption
```

---

# 🔒 2. Privacy

Privacy focuses on:

* how data is collected
* how data is used
* GDPR compliance
* customer control of data

---

# Example Topics

```text id="y6d8fe"
Data handling
Personal information
Data residency
GDPR
```

---

# 📋 3. Compliance

Compliance focuses on:

* regulatory standards
* certifications
* industry requirements

---

# Example Compliance Standards

| Standard  | Industry              |
| --------- | --------------------- |
| GDPR      | Privacy               |
| PCI DSS   | Payment card industry |
| ISO 27001 | Security              |
| HIPAA     | Healthcare            |

---

# 🌐 What Services Are Covered?

The Trust Center covers:

* Microsoft Azure
* Microsoft 365
* Microsoft Dynamics 365
* Power Platform

---

# 🏢 Azure Compliance Documentation

Microsoft provides detailed compliance documents for Azure services.

These explain:

* certifications
* audits
* regulations
* security practices

---

# 📌 Important Concept

The Trust Center is:

```text id="f3o1yt"
The central location for compliance information
```

---

# 🔍 Compliance Offerings

Microsoft provides MANY compliance offerings based on:

* industries
* countries
* government requirements

---

# Example Categories

```text id="u8n7qh"
Healthcare
Finance
Government
Retail
International Regulations
```

---

# 💳 Example — PCI DSS

PCI DSS is important for:

```text id="k5r4mv"
Companies handling payment card data
```

Microsoft documents:

* supported Azure services
* compliance scope
* security requirements

---

# 🏢 Data Center Security

Trust Center also explains:

* physical security
* disaster protection
* external audits
* environmental protections

---

# Examples

```text id="r1x9bz"
Earthquake protection
Hurricane protection
Access controls
Security testing
```

---

# 📜 Certifications & Audits

Microsoft cloud services are regularly checked by:

* external auditors
* regulators
* certification organizations

---

# Purpose

To verify:

```text id="n4v6pa"
Microsoft meets compliance requirements
```

---

# 🔐 Service Assurance

Microsoft also provides:

> Service Assurance documentation

This gives deeper details about:

* security controls
* operational processes
* compliance evidence

---

# 📌 Important AZ-900 Concept

If you need information about:

* compliance
* privacy
* certifications
* security standards

You go to:

```text id="q2z8hj"
Microsoft Trust Center
```


# 🔄 Trust Center vs Compliance Manager

| Trust Center                 | Compliance Manager                |
| ---------------------------- | --------------------------------- |
| Information portal           | Compliance management tool        |
| Documentation & transparency | Compliance tracking               |
| Public information           | Operational compliance activities |

---

# 🌍 Real-World Example

A healthcare company wants to use Azure.

They need to verify:

* HIPAA compliance
* security standards
* data protection

They use:

```text id="d5f0qw"
Microsoft Trust Center
```

to review official compliance documentation.

---

# ⭐ Super Simple Summary

## Microsoft Trust Center

```text id="v1m4rt"
Central hub for Microsoft security, privacy, and compliance information
```

---

# ✈️ Easy Analogy

Think of the Trust Center like a safety inspection office 🏢

| Trust Center Area | Real-Life Equivalent        |
| ----------------- | --------------------------- |
| Security          | Building security systems   |
| Privacy           | Personal privacy rules      |
| Compliance        | Government inspections      |
| Certifications    | Official approvals/licenses |

-

##  video.n.57-Purpose of Azure sovereign Regions


> Beginner-friendly notes for understanding Azure sovereign clouds and sovereign regions in Microsoft Azure.

---

# 🌍 What are Azure Sovereign Regions?

Azure Sovereign Regions are:

> Special isolated Azure cloud environments designed for specific government, legal, or regulatory requirements.

---

# 🧠 Simple Definition

Think of sovereign clouds as:

```text id="d9w2jf"
Separate versions of Azure for special compliance needs
```

---

# 📌 Important Concept

Azure is NOT only:

```text id="h4u8xr"
One global commercial cloud
```

There are multiple Azure environments.

---

# ☁️ Main Azure Cloud Environments

| Azure Environment      | Purpose                         |
| ---------------------- | ------------------------------- |
| Azure Commercial Cloud | Standard public Azure           |
| Azure Government       | US government workloads         |
| Azure China            | Operated in China               |
| Azure Germany (legacy) | German sovereignty requirements |

---

# 🔐 Key Feature of Sovereign Clouds

Sovereign clouds are:

```text id="m1n5vy"
Completely isolated
```

---

# Isolation Includes

* separate data centers
* separate networking
* separate authentication systems
* separate Azure AD/Entra endpoints
* separate infrastructure

---

# 📌 Important AZ-900 Concept

Even though they all run Azure:

```text id="v3k7oe"
They are separate cloud instances
```

---

# 🏛️ Why Sovereign Clouds Exist

Some organizations have strict requirements like:

```text id="y6r0pd"
Data must stay in country
Only local personnel can access systems
Government certifications required
```

Regular Azure commercial cloud may not meet these requirements.

---

# 🇺🇸 Azure Government

Azure Government is designed for:

* US federal agencies
* state/local governments
* approved partners

---

# Key Purpose

Meet additional:

* security
* compliance
* regulatory requirements

---

# 🔐 Example Certifications

Azure Government supports standards like:

| Compliance Standard | Purpose                    |
| ------------------- | -------------------------- |
| CJIS                | Criminal justice security  |
| ITAR                | Defense/export controls    |
| IRS 1075            | Tax information protection |
| DoD Level 4         | US defense requirements    |
| FedRAMP High        | Government cloud security  |

---

# 📌 Important Concept

Azure Government is:

```text id="u8j3ts"
Physically separate from commercial Azure
```

---

# Example Difference

Commercial Azure:

```text id="e5p2lm"
Shared public cloud environment
```

Azure Government:

```text id="t1x9qf"
Restricted government-focused environment
```

---

# 🇨🇳 Azure China

Azure China exists because:

```text id="k7b4nz"
China has strict laws about cloud operations
```

---

# Important Fact

Azure China is:

```text id="c2w6ra"
Operated by 21Vianet
```

NOT directly by Microsoft.

---

# 🧠 Key Idea

Microsoft licenses Azure technology:

```text id="z5n1gh"
21Vianet operates the cloud inside China
```

---

# 🇩🇪 Azure Germany

Azure Germany was created for:

* German data sovereignty requirements

---

# Important Update

The older sovereign German cloud:

```text id="f9m3yb"
Is no longer used for new customers
```

Microsoft now provides:

```text id="g1v8ke"
Regular commercial Azure regions in Germany
```

that meet modern requirements.

---


---

# 🧩 Real-World Example

## Chinese Company

Requirements:

* local cloud operation laws

Solution:

```text id="q4h9du"
Azure China (21Vianet)
```


# 🔥 Common AZ-900 Questions

| Question                                         | Answer           |
| ------------------------------------------------ | ---------------- |
| Which Azure cloud is for US government?          | Azure Government |
| Which cloud is operated by 21Vianet?             | Azure China      |
| Are sovereign clouds isolated?                   | Yes              |
| Do sovereign clouds use separate infrastructure? | Yes              |

---


Think of sovereign clouds like secure government buildings 🏢

| Commercial Azure       | Sovereign Cloud                         |
| ---------------------- | --------------------------------------- |
| Public office building | Restricted military/government facility |
| Shared access          | Controlled access                       |
| Standard rules         | Special security rules                  |

---

# video.n.58-Factors that affect costs

> Beginner-friendly notes for understanding what affects pricing and cost in Microsoft Microsoft Azure.

---

# 💰 Core Idea of Azure Pricing

Azure uses:

```text id="v8p2ma"
Consumption-based pricing
```

Meaning:

> You pay for what you use.

---


# 🔑 Main Factors That Affect Cost

| Factor        | Description                       |
| ------------- | --------------------------------- |
| Resource Type | VM, Storage, Database, etc.       |
| SKU           | Different service levels/features |
| Tier          | Premium vs Standard               |
| Region        | Geographic location               |
| Usage         | Amount consumed                   |
| Runtime       | How long resources run            |
| Transactions  | Number of operations              |
| Licensing     | OS or software licenses           |

---

# 1️⃣ Resource Type

Different Azure resources have different costs.

---

# Examples

| Resource Type | Example          |
| ------------- | ---------------- |
| Compute       | Virtual Machines |
| Storage       | Blob Storage     |
| Database      | Azure SQL        |
| Networking    | Load Balancer    |
| AI/ML         | Machine Learning |

---

# 📌 Important Concept

More powerful services usually:

```text id="r3j7cf"
Cost more
```

---

# 2️⃣ SKU (Service Level)

Many Azure services have multiple SKUs.

---

# Example

## Load Balancer

| SKU      | Cost                       |
| -------- | -------------------------- |
| Basic    | Lower cost                 |
| Standard | More features, higher cost |

---

# Example

## Azure Firewall

| SKU      | Features          |
| -------- | ----------------- |
| Standard | Basic protection  |
| Premium  | Advanced security |

---

# 📌 Important Concept

Higher SKU:

```text id="k1x5ou"
Usually means higher cost and more features
```

---

# 3️⃣ Pricing Tiers

Services often have pricing tiers.

---

# Storage Example

| Tier    | Usage                    |
| ------- | ------------------------ |
| Hot     | Frequently accessed data |
| Cool    | Less frequently used     |
| Archive | Rarely accessed          |

---

# 📌 Important Concept

Different tiers optimize:

* performance
* access frequency
* cost

---

# 4️⃣ Azure Region (Location)

Costs vary by region.

---

# Why?

Different regions have different:

* electricity costs
* operational costs
* networking costs
* infrastructure costs

---

# Example

```text id="t9b4vl"
Network traffic may cost more in some regions
```

---

# 📌 Important AZ-900 Concept

Region selection affects:

```text id="n4m8yw"
Pricing
```

---

# 5️⃣ Provisioned vs Used Resources

This is VERY important.

Some services charge for:

```text id="z6c2er"
What you provision
```

Others charge for:

```text id="q1f7pk"
What you actually use
```

---

# Example — Virtual Machine

You pay compute cost:

```text id="g3h5un"
Only when VM is running
```

If stopped/deallocated:

* compute charges stop
* storage charges continue

---

# Example — Premium Storage

You pay for:

```text id="m7w9ta"
Provisioned storage size
```

Even if unused.

---

# 6️⃣ Number of Instances

Cloud services can scale automatically.

---

# Example

If traffic increases:

* Azure may create more VM instances
* More instances = higher cost

---

# 📌 Important Concept

Auto-scale helps:

```text id="s5e0rd"
Balance performance and cost
```

---

# 7️⃣ Serverless Consumption

Serverless services charge based on:

```text id="j8u1bx"
Actual work performed
```

---

# Examples

| Service         | Billing Method      |
| --------------- | ------------------- |
| Azure Functions | Per execution       |
| Logic Apps      | Per workflow/action |

---

# 🧠 Why Serverless Saves Money

You only pay:

```text id="y2k6oq"
When events happen
```

---

# 8️⃣ Storage Consumption

Storage pricing may depend on:

* total storage used
* provisioned capacity
* redundancy options

---

# Example

| Storage Type     | Billing Style      |
| ---------------- | ------------------ |
| Standard Storage | Amount used        |
| Premium Storage  | Amount provisioned |

---

# 9️⃣ Transactions & Operations

Some services charge per operation.

---

# Examples

| Operation         | Example          |
| ----------------- | ---------------- |
| Read transaction  | Accessing a blob |
| Write transaction | Uploading data   |
| Database queries  | SQL operations   |

---

# 🔟 Licensing Costs

Some resources include software licenses.

---

# Examples

| License          | Example               |
| ---------------- | --------------------- |
| Windows Server   | VM OS cost            |
| SQL Server       | Database licensing    |
| Marketplace Apps | Third-party licensing |

---



# 🔄 Provisioned vs Running

| Resource State                    | Cost?             |
| --------------------------------- | ----------------- |
| VM exists but stopped/deallocated | Storage only      |
| VM running                        | Compute + storage |
| Public IP exists                  | Usually charged   |

---

# 📌 Important Exam Concepts

| Concept                           | Important? |
| --------------------------------- | ---------- |
| Consumption-based pricing         | ✅ YES      |
| SKU affects pricing               | ✅ YES      |
| Region affects pricing            | ✅ YES      |
| Provisioned vs consumed resources | ✅ YES      |
| Serverless billing                | ✅ YES      |
| Licensing costs                   | ✅ YES      |

---

# video.n.59-Factors to reduce cost

# 💰 Main Goal

Azure pricing is:

```text id="x1r7pv"
Pay-as-you-go
```

So the goal is:

> Use only what you need and avoid waste.

---

# 🧠 Core Cost Optimization Strategies

| Strategy                   | Purpose                                |
| -------------------------- | -------------------------------------- |
| Auto-scale                 | Run fewer resources when demand is low |
| Serverless                 | Pay only when code runs                |
| Shut down unused resources | Avoid unnecessary charges              |
| Use correct SKUs           | Prevent overpaying                     |
| Use reservations           | Get long-term discounts                |
| Use Spot VMs               | Use spare Azure capacity cheaply       |
| Use tags                   | Track ownership and costs              |

---

# 1️⃣ Use Auto-Scaling

## What is Auto-Scaling?

Azure automatically:

* adds resources when demand increases
* removes resources when demand decreases

---

# Benefits

```text id="m4z8qo"
Only pay for the capacity you actually need
```

---

# Examples

| Service       | Auto-Scaling Feature         |
| ------------- | ---------------------------- |
| VM Scale Sets | Scale VM count automatically |
| AKS           | Cluster autoscaler           |
| App Service   | Auto-scale plans             |

---

# 📌 Important AZ-900 Concept

Auto-scale helps:

```text id="j9u2cy"
Reduce wasted compute resources
```

---

# 2️⃣ Prefer Serverless & PaaS

## Why?

Traditional VMs run continuously:

```text id="k7x5dr"
Even when idle
```

Serverless runs:

```text id="q2p1lb"
Only when triggered
```

---

# Examples

| Service         | Billing Style       |
| --------------- | ------------------- |
| Azure Functions | Per execution       |
| Logic Apps      | Per workflow/action |

---

# 🧠 Key Benefit

```text id="f6m9vn"
You pay only for actual work performed
```

---

# 3️⃣ Choose the Correct SKU & Size

## Don't Overprovision

Avoid:

* oversized VMs
* unnecessary premium tiers
* excessive memory/CPU

---

# Example

| Bad Choice             | Better Choice |
| ---------------------- | ------------- |
| Large VM for small app | Small VM      |

---

# 📌 Important Concept

```text id="w3n4tb"
Right-size your resources
```

---

# 4️⃣ Shut Down Unused Resources

## Common Beginner Mistake

Leaving dev/test VMs running overnight.

---

# Solution

Use:

```text id="a8q6ej"
Auto-shutdown schedules
```

---

# Example

A VM used only during work hours:

* ON during day
* OFF at night

---

# 🧠 Benefit

```text id="d5k0ry"
Reduce compute charges
```

---

# 5️⃣ Delete Unused Resources

Stopping a VM:

```text id="z1v8pn"
Does NOT always remove all costs
```

---

# Resources That May Still Cost Money

* disks
* storage accounts
* public IPs
* load balancers

---

# 📌 Best Practice

Delete resources completely when no longer needed.

---

# 🧠 Why Resource Groups Help

Resources in the same project:

```text id="n6h3cx"
Can be deleted together
```

---

# 6️⃣ Use Storage Tiers

## Azure Storage Tiers

| Tier    | Best For                   |
| ------- | -------------------------- |
| Hot     | Frequently accessed data   |
| Cool    | Infrequently accessed data |
| Archive | Rarely accessed data       |

---

# 🧠 Cost Optimization Idea

Move older data to cheaper tiers.

---

# 📌 Lifecycle Management

Azure can automatically:

```text id="s9p2wm"
Move data between tiers
```

based on usage.

---

# 7️⃣ Use Tags

## What are Tags?

Metadata labels like:

* owner
* environment
* department
* cost center

---

# Example

| Tag         | Value        |
| ----------- | ------------ |
| Environment | Production   |
| Owner       | Finance Team |
| CostCenter  | CC-100       |

---

# 🧠 Why Tags Matter

Tags help:

* identify resources
* track costs
* avoid forgotten resources

---

# 📌 Important AZ-900 Concept

Use:

```text id="g4t7yk"
Azure Policy
```

to enforce tags.

---

# 8️⃣ Use Azure Advisor

## What is Azure Advisor?

A recommendation tool that helps optimize:

* cost
* security
* performance
* reliability

---

# Example Recommendations

```text id="v7m1ez"
Resize underutilized VMs
Delete unused resources
Buy reservations
```

---

# 9️⃣ Use Azure Reservations

## What are Reservations?

Commit to using resources for:

* 1 year
* 3 years

to get large discounts.

---

# 🧠 Key Idea

Azure rewards predictable usage:

```text id="r2n8lf"
With lower pricing
```

---

# Example Savings

| Pricing Model      | Example Cost |
| ------------------ | ------------ |
| Pay-as-you-go      | ~$1525/month |
| Reserved (3 years) | ~$370/month  |

---

# 📌 Important Concept

Reservations work best for:

```text id="y5c0qa"
Always-running workloads
```

---

# 🔟 Use Azure Hybrid Benefit

## What is it?

Reuse existing:

* Windows Server licenses
* SQL Server licenses

inside Azure.

---

# Benefit

```text id="u3f6tw"
Avoid paying license costs twice
```

---

# Example

Without Hybrid Benefit:

* VM includes Windows license cost

With Hybrid Benefit:

* Use existing license

---

# 1️⃣1️⃣ Use Spot VMs

## What are Spot VMs?

Very cheap VMs using:

```text id="p8k2vd"
Azure's spare capacity
```

---

# ⚠️ Important Tradeoff

Azure can:

```text id="h1z7mu"
Evict (stop) the VM at any time
```

if capacity is needed.

---

# Best Use Cases

| Good For   | Bad For                  |
| ---------- | ------------------------ |
| Batch jobs | Critical production apps |
| Testing    | Always-on services       |
| Rendering  | Databases                |

---

# 🧠 Key Benefit

```text id="c4r9ox"
Massive cost savings
```

---

# 🔄 Cost Optimization Summary

| Technique          | Savings Type          |
| ------------------ | --------------------- |
| Auto-scale         | Reduce idle resources |
| Serverless         | Pay per execution     |
| Shutdown schedules | Reduce runtime        |
| Reservations       | Long-term discounts   |
| Hybrid Benefit     | Reuse licenses        |
| Spot VMs           | Cheap spare capacity  |

---

# 🧠 Easy Memory Trick

## Reduce Azure Costs By:

```text id="e7x3kj"
Scale smart
Shut down unused things
Commit for discounts
Use cheaper tiers
```

---

# ⭐ Super Simple Summary

Azure cost optimization means:

* using fewer resources
* using resources efficiently
* deleting waste
* using discounts
* automating scaling

---

# ✈️ Easy Analogy

Think of Azure like renting apartments 🏢

| Azure Feature     | Apartment Analogy                    |
| ----------------- | ------------------------------------ |
| Auto-scale        | Rent more rooms only when needed     |
| Reservations      | Long-term lease discount             |
| Spot VM           | Cheap unused room that may disappear |
| Shutdown schedule | Turn off lights when leaving         |
| Tags              | Labels on apartment ownership        |

---

# video.n.60-Functionality and usage of pricing and TCO Calculators,,, using web Pricing Calculator,Azure Calculator
# 💰 Functionality and Usage of Pricing & TCO Calculators (AZ-900)


Azure provides **two major calculators** to help estimate cloud costs:

| Calculator                                   | Purpose                                                 |
| -------------------------------------------- | ------------------------------------------------------- |
| **Pricing Calculator**                       | Estimates the cost of Azure resources before deployment |
| **TCO (Total Cost of Ownership) Calculator** | Compares on-premises costs vs Azure cloud costs         |

---

# 🧮 1. Azure Pricing Calculator

## ✅ What It Does

Helps estimate:

* Monthly Azure costs
* Resource pricing
* Infrastructure architecture expenses

Useful before:

* Deploying workloads
* Budget planning
* Cloud migration projects

---

## 🛠️ How It Works

You manually add:

* Services
* Resource sizes
* Usage estimates
* Region/location
* Storage
* Networking
* Licensing

👉 The calculator estimates the total monthly price.

---

## 🧱 Example Inputs

### Virtual Machines

You specify:

| Setting            | Example       |
| ------------------ | ------------- |
| Region             | East US       |
| OS                 | Windows/Linux |
| VM Size            | D2s_v3        |
| Number of VMs      | 10            |
| Hours Running      | 500 hrs/month |
| Reserved Instance? | Yes/No        |

---

## 💾 Disk Costs Matter Too

VMs also require disks:

* OS disk
* Data disks

You choose:

* Standard SSD
* Premium SSD
* Disk size
* Number of disks

⚠️ Premium disks cost more.

---

## 🌐 Networking Costs

Azure also charges for:

* Internet egress (outbound traffic)
* Bandwidth usage

Costs vary by:

* Region
* Amount of data transferred

---

## 📦 Important Pricing Factors

### Cost depends on:

* Resource type
* SKU/size
* Region
* Usage hours
* Storage amount
* Transactions
* Licensing
* Reserved instances

---

## 💡 Reserved Instances

If you commit for:

* **1 year**
* **3 years**

You get major discounts.

### Example

| Option          | Monthly Cost |
| --------------- | ------------ |
| Pay-as-you-go   | ~$1500       |
| 3-Year Reserved | ~$370        |

Huge savings for predictable workloads.

---

## 🪪 Azure Hybrid Benefit

If you already own:

* Windows Server licenses
* SQL Server licenses

You can bring them to Azure and reduce costs.

✅ Especially useful for:

* Existing Microsoft customers
* Hybrid cloud environments

---

## 📤 Extra Features

You can:

* Save estimates
* Export pricing
* Share estimates with others
* Add support plans
* Compare configurations

---

# 🏢 2. Total Cost of Ownership (TCO) Calculator

## ✅ Purpose

Helps organizations compare:

| On-Premises       | Azure Cloud            |
| ----------------- | ---------------------- |
| Hardware          | Azure services         |
| Electricity       | Managed infrastructure |
| Cooling           | Reduced maintenance    |
| Data center costs | Operational savings    |
| Labor costs       | Automation benefits    |

---

## 🛠️ What You Input

### Existing Infrastructure

* Servers
* Databases
* Storage
* Networking
* VMware environments

---

## 📊 Example Inputs

| Resource          | Example       |
| ----------------- | ------------- |
| Number of VMs     | 10            |
| CPU cores         | 8             |
| RAM               | 16 GB         |
| Databases         | SQL           |
| Storage           | NAS/SAN       |
| Network bandwidth | Custom values |

---

## ⚙️ Adjustable Assumptions

You can customize:

* Electricity cost
* Labor cost
* Licensing
* Redundancy
* Azure region
* Time period (e.g., 5 years)

---

## 📈 Final Output

The TCO calculator shows:

* Estimated on-prem costs
* Estimated Azure costs
* Potential savings over time

Example:

> “Moving to Azure could save X dollars over 5 years.”

---

# 🧠 Beginner-Friendly Key Takeaways

## Pricing Calculator

✅ Estimates Azure service costs
✅ Good for architecture planning
✅ Requires accurate usage estimates

---

## TCO Calculator

✅ Compares cloud vs on-premises
✅ Helps justify migration to Azure
✅ Includes operational savings

---

# 🚀 AZ-900 Exam Tips

## Remember:

### Pricing Calculator

= **Estimate Azure resource costs**

### TCO Calculator

= **Compare Azure vs on-premises costs**

---

# video.n.62-Purpose of Service Level Agreements
# 📜 Purpose of Service Level Agreements (SLAs) — AZ-900 Notes

## 🌟 What is an SLA?

A **Service Level Agreement (SLA)** is Microsoft's promise about:

* **Availability**
* **Uptime**
* **Reliability** of an Azure service

It tells customers:

> “How much downtime can we expect?”

---

# 🎯 Why SLAs Matter

In cloud computing:

* Microsoft manages much of the infrastructure
* Customers need guarantees on reliability

SLAs help define:

* Expected uptime
* Financial compensation if targets are missed
* Reliability architecture requirements

---

# 🔢 Understanding “Nines” in SLAs

SLAs are usually shown as percentages.

| SLA               | Downtime Per Week |
| ----------------- | ----------------- |
| 99% (2 nines)     | ~1.68 hours       |
| 99.9% (3 nines)   | ~10 minutes       |
| 99.95%            | ~5 minutes        |
| 99.99% (4 nines)  | ~1 minute         |
| 99.999% (5 nines) | ~6 seconds        |

👉 More “9s” = Higher availability = Less downtime

---

# 🏗️ Azure VM SLA Examples

## ✅ Highest SLA (99.99%)

To get **4 nines**, Azure requires:

* **2 or more VMs**
* Across **2 or more Availability Zones**
* In the **same Azure region**

### Example Architecture

```text
Region
 ├── AZ1 → VM1
 └── AZ2 → VM2
```

Usually combined with:

* Standard Load Balancer
* Zone redundancy

---

# 🌍 Availability Zones Improve SLA

## Why?

Availability Zones are:

* Separate physical datacenters
* Independent:

  * Power
  * Cooling
  * Networking

If one zone fails:
✅ Another zone can continue running.

---

# 🧱 Availability Set SLA (99.95%)

If you don't use Availability Zones:

You can still improve uptime using:

* **Availability Sets**

### What they do:

Spread VMs across:

* Different racks
* Different fault domains
* Different update domains

### Example

```text
Datacenter
 ├── Rack 1 → VM1
 └── Rack 2 → VM2
```

Better than single VM, but not as resilient as Availability Zones.

---

# 💻 Single VM SLA

If you only deploy:

* **One VM**

Then SLA depends on:

* Disk type

| Disk Type                | SLA   |
| ------------------------ | ----- |
| Premium SSD / Ultra Disk | 99.9% |
| Standard SSD             | 99.5% |
| Standard HDD             | 95%   |

⚠️ Single VMs have lower reliability.

---

# 💰 Financial Backing

Azure SLAs are:
✅ Financially backed

If Microsoft fails the SLA:

* You may receive service credits

Example:

* Partial refund
* Account credit

---

# 📊 Azure Status & Monitoring

## Azure Status Page

Shows:

* Current outages
* Service availability
* Regional incidents

## Service Health Dashboard

Inside your subscription:

* Personalized alerts
* Resource-specific issues

---

# 🧮 Composite SLA

## What Happens When Multiple Services Work Together?

Example:

```text
Web App + SQL Database
```

If BOTH are required:

* Overall SLA becomes LOWER

---

## Example Formula

If:

* Web App = 99.95%
* SQL = 99.99%

Then:

```text
0.9995 × 0.9999
= 99.94%
```

👉 Composite SLA decreases because BOTH services must work.

---

# 🔄 Improving Composite SLA

## Add Redundancy ("OR" Relationship)

Example:

```text
Web App
   ├── SQL DB
   └── Queue Backup
```

Now:

* Either backend can work
* Failure chance becomes much smaller

This improves overall availability.

---

# ⚠️ Important SLA Concepts

## AND Relationship

More required components =
❌ Lower SLA

```text
Service A AND Service B
```

---

## OR Relationship

Alternative services =
✅ Higher SLA

```text
Service A OR Service B
```

---

# 🚧 Reality of High Availability

## 5 Nines is VERY Difficult

Why?
Because many Azure services themselves are:

* 99.99% max

Example:

* Azure AD = 99.99%

You cannot easily exceed dependencies.

---

# 🧠 Beginner-Friendly Key Takeaways

## SLA

= Microsoft's uptime guarantee

---

## Availability Zones

✅ Highest resiliency
✅ Better SLA

---

## Availability Sets

✅ Good resiliency
❌ Less isolated than AZs

---

## Single VM

❌ Lowest SLA
⚠️ Depends on disk type

---

## Composite SLA

* Multiple required services lower uptime
* Redundancy improves uptime

---

# 📝 Quick Summary

* SLA = uptime guarantee from Microsoft
* More “9s” = less downtime
* Availability Zones provide highest VM SLA
* Availability Sets improve resiliency within a datacenter
* Single VMs have lower SLA
* Composite SLAs decrease when services depend on each other
* Redundancy improves overall availability


____________________________________
prešiel som všetko na 80% ale ešte musím preopakovať praktikum
## SC-900 - Začiatok druhého kurzu na ktorom budem stavať dva hlavné AZ-104-AZ-500

# Introduction to Security,Compliance and indentity concepts
# SC-900 — 1 - Security, Compliance & Identity Concepts

## 1. Shared Responsibility Model

### Main idea
In cloud computing, security responsibilities are shared between:
- Cloud Provider
- Customer

### What YOU always own
- Data
- User identities
- Devices
- Access management

### Service Models

| Model | Provider Manages | Customer Manages |
|---|---|---|
| On-Prem | Nothing | Everything |
| IaaS | Hardware, networking | OS, apps, data |
| PaaS | Infrastructure + OS/runtime | Apps, data |
| SaaS | Almost everything | Users, data access |

### Easy Memory Trick
Cloud = less infrastructure work, NOT less security responsibility.

<img width="3858" height="2475" alt="image" src="https://github.com/user-attachments/assets/bad72547-4a3b-4ddc-9f37-dba36905bea0" />



Diagram showing the AI shared responsibility model, with responsibility divided across AI platform, AI application, and AI usage layers for IaaS, PaaS, and SaaS service types.

---

# 2. Defense in Depth

## Never rely on one protection layer

Security should have multiple layers:
- Physical security
- MFA
- Firewalls
- Network segmentation
- Device security
- Encryption
- Monitoring
- Backups

## Goal
If one layer fails, another stops the attack.

---

# 3. CIA Triad

## Core Security Goals

### Confidentiality
Only authorized users can access data.

Examples:
- Encryption
- Permissions
- MFA

---

### Integrity
Data should remain accurate and unchanged.

Examples:
- Hashing
- Auditing
- Validation

---

### Availability
Systems and data must stay accessible.

Examples:
- Backups
- Redundancy
- Disaster recovery

---


# Balancing the CIA triad
In practice, confidentiality, integrity, and availability can sometimes pull in different directions. For example, encrypting everything strongly protects confidentiality, but if encryption keys are lost, data becomes permanently inaccessible—hurting availability. Requiring complex authentication protects confidentiality and integrity but adds friction that can affect productivity.

Security teams work to find the right balance based on the sensitivity of the data, the potential impact of a breach, and the operational requirements of the business. Understanding the tradeoffs between these three properties helps organizations make informed, risk-based security decisions.

The CIA triad also helps frame the impact of attacks: attackers who steal data are targeting confidentiality, attackers who modify records are targeting integrity, and attackers who take systems offline are targeting availability. Keeping the CIA triad in mind helps organizations think about the full range of threats they need to defend against.



# 4. Zero Trust

## Main Principle
> Never Trust, Always Verify

Do NOT automatically trust:
- Users
- Devices
- Networks
- Internal systems

Always verify:
- Identity
- Device health
- Access level
- Risk signals

---

## 3 Core Principles

### Verify Explicitly
Validate every request.

### Least Privilege Access
Give minimum required permissions.

### Assume Breach
Design systems as if attackers already entered.

---

# 5. Encryption

## Purpose
Makes data unreadable without the correct key.

## Protects Data:
- At Rest
- In Transit
- In Use

---

## Types of Encryption

### Symmetric Encryption
- Same key encrypts & decrypts
- Faster
- Used for large data

### Asymmetric Encryption
- Public + private key pair
- Used in HTTPS/TLS

<img width="554" height="418" alt="image" src="https://github.com/user-attachments/assets/131baeed-e6ee-43ed-8714-d5593d763b9b" />


---

# 6. Hashing

## Purpose
Used mainly for password protection.

## Important Facts
- One-way process
- Cannot be reversed
- Same input = same hash

---

## Password Security
Systems should:
- Store hashed passwords
- Add salts to prevent rainbow-table attacks


Salting
To defend against precomputed attacks, passwords are typically salted before hashing. A salt is a unique, randomly generated value created for each individual password and added to it before hashing. Because every password gets a different salt, two users with the same password produce different hashes in the database. This makes precomputed rainbow tables ineffective, because the attacker would need a separate lookup table for every possible salt value.

Salting is a standard best practice in secure password storage and is required for any properly implemented authentication system.




<img width="508" height="116" alt="image" src="https://github.com/user-attachments/assets/cde18882-1080-48cd-be25-37ed065d468c" />


---

# 7. Governance, Risk & Compliance (GRC)

## Governance
Rules and policies.

Examples:
- Access policies
- Security standards
- Accountability

---

## Risk Management
Identify and reduce threats.

Examples:
- Data leaks
- Cyberattacks
- Insider threats

---

## Compliance
Follow laws and regulations.

Examples:
- GDPR
- HIPAA
- ISO standards

---

# 8. Authentication vs Authorization

## Authentication
### "Who are you?"

Examples:
- Password
- MFA
- Biometrics

---

## Authorization
### "What can you access?"

Examples:
- Roles
- Permissions
- RBAC

Authorization can only happen after successful authentication. You can't determine what someone is permitted to do without first confirming their identity. And confirming identity alone—without checking permissions—leaves resources exposed. Together, authentication and authorization ensure that the right identities get the right access, and nothing more.
---

# 9. Identity = New Security Perimeter

Modern security is no longer based on office networks.

Security now focuses on:
- User identity
- Device trust
- Context
- Access behavior

<img width="1430" height="975" alt="image" src="https://github.com/user-attachments/assets/43f99d0c-36c5-4b19-b4df-181d0d732bad" />

---

# 10. Identity Infrastructure Pillars

## Administration
Manage users/devices.

## Authentication
Verify identity.

## Authorization
Control permissions.

## Auditing
Track activities and logs.

---

# 11. Identity Providers (IDP)

## Purpose
Centralized authentication system.

Examples:
- Microsoft Entra ID
- Okta
- Google Identity

---

## Benefits
- Single Sign-On (SSO)
- MFA
- Centralized policies
- Better monitoring

---

# 12. Directory Services

## Active Directory (AD)
Traditional on-prem identity management.

## Microsoft Entra ID
Cloud identity platform supporting:
- Cloud apps
- Hybrid environments
- Modern authentication

---

# 13. Federation

## Purpose
Allows different organizations to trust each other's authentication.

### Example
Login to another company's app using your company account.

## Benefits
- No duplicate accounts
- Better user experience
- Stronger security
- Easier collaboration

- <img width="949" height="568" alt="image" src="https://github.com/user-attachments/assets/caf3cb14-d678-49ae-a054-5f9c77e3c5ac" />



---

# Everyday Security Takeaways

- Use MFA everywhere
- Apply least privilege
- Encrypt sensitive data
- Monitor login activity
- Never trust devices/users automatically
- Keep backups
- Assume breaches can happen
- Identity security is critical in cloud environments

---

# Quick Exam Memory Lines

- CIA = Confidentiality, Integrity, Availability
- Zero Trust = Never Trust, Always Verify
- Authentication = Who you are
- Authorization = What you can do
- Hashing = One-way password protection
- Encryption = Reversible with key
- Least Privilege = Minimum necessary access


You learned how authentication proves who you are—through credentials, multifactor authentication, and passwordless methods—while authorization determines what you're allowed to do. You explored why identity is the new security perimeter and how organizations manage it through four pillars: administration, authentication, authorization, and auditing.

You learned how identity providers centralize authentication, issue security tokens, and enable single sign-on. You explored directory services—from on-premises Active Directory Domain Services to Microsoft Entra ID as its cloud-native evolution. Finally, you learned how federation uses trust relationships so users can access resources across organizational boundaries using the identities they already have.

<img width="1100" height="580" alt="image" src="https://github.com/user-attachments/assets/6bc9775b-753b-4c5d-8784-589ceff802dc" />


## Introduction to Microsoft entra -SC900

# SC-900 — 2 - Introduction to Microsoft Entra 

# 1. What is Microsoft Entra ID?

## Definition
Microsoft Entra ID is Microsoft's cloud-based:
- Identity Management
- Access Management
- Authentication platform

It controls:
- Who can sign in
- What they can access
- Under what conditions

<img width="1227" height="748" alt="image" src="https://github.com/user-attachments/assets/0da2a233-49b3-4ccc-80ad-38e6cd9598e1" />

<img width="1116" height="630" alt="image" src="https://github.com/user-attachments/assets/48337974-5d18-4439-9e0e-800cb049ddce" />

---

## Main Purpose
Provide one secure identity across:
- Cloud apps
- Microsoft 365
- Azure
- On-prem systems
- Devices

---

## Key Benefits
- Single Sign-On (SSO)
- Centralized identity management
- Better security
- Hybrid identity support
- Zero Trust integration

---

# 2. Entra Tenant / Directory

## Tenant
A tenant = your organization's identity container.

Stores:
- Users
- Groups
- Devices
- Applications
- Policies

---

## Important Concept
One organization can have:
- Single tenant
- Multiple tenants
- Multi-tenant environments

Used for:
- Subsidiaries
- Different regions
- Regulatory separation

---

# 3. Identity Types in Entra

# Human Identities

## Members
Internal employees.

Examples:
- Staff
- IT admins
- HR employees

Usually get:
- Full company access
- Long-term permissions

---

## Guests
External users.

Examples:
- Vendors
- Consultants
- Business partners

Usually get:
- Limited access
- Temporary/project-based permissions

---

# Device Identities

Examples:
- Laptops
- Phones
- Tablets

Purpose:
- Verify trusted devices
- Enable BYOD
- Apply security policies

---

# Workload Identities

## Service Principals
Identity for applications.

Used when apps need secure access to:
- Microsoft Graph
- APIs
- Azure resources

---

## Managed Identities
Identity automatically managed by Azure.

Purpose:
- Remove stored credentials
- Secure service-to-service authentication

Example:
- VM accessing Azure Key Vault securely

---

# 4. Hybrid Identity

## Definition
Single identity across:
- On-prem Active Directory
- Cloud services

---

## How it Works
Synchronization between:
- Active Directory
- Microsoft Entra ID

Using:
- Entra Connect
- Cloud Sync

---

## Benefits
- One login everywhere
- Reduced identity sprawl
- Consistent security policies
- Easier migration to cloud

---

# 5. Authentication in Entra

## Authentication = Verify Identity

Traditional:
- Username/password

Modern:
- MFA
- Biometrics
- Passkeys
- Authenticator apps

<img width="1639" height="768" alt="image" src="https://github.com/user-attachments/assets/36cd910e-a3dc-4c58-bc5e-d65c5077cc76" />

---

# Authentication Methods

<img width="891" height="433" alt="image" src="https://github.com/user-attachments/assets/b7bf4ec4-180e-4751-8f2f-63f542f19e78" />



## Password-Based
- Weakest option
- Still supported

---

## Phone-Based
- SMS
- Voice calls

---

## One-Time Passcodes
- OATH tokens
- Temporary codes

---

## Passwordless Authentication

### Windows Hello
- Face scan
- Fingerprint
- PIN

### Microsoft Authenticator
- Push approval

### FIDO2 Security Keys
- Hardware security keys

### Certificate-Based Authentication
- Trusted certificates

---

## Why Passwordless?
Reduces:
- Phishing
- Password spray attacks
- Credential theft

Improves:
- User experience
- Security

---

# 6. Multifactor Authentication (MFA)

## Definition
Requires multiple verification factors.

---

## Three Factor Types

### Something You Know
- Password
- PIN

### Something You Have
- Phone
- Security key

### Something You Are
- Fingerprint
- Face scan

---

## Why MFA Matters
Even if passwords leak:
- Attackers still cannot log in easily

---

## Security Defaults
Microsoft baseline protections include:
- MFA for admins
- Risk-based MFA prompts

Good for:
- Small organizations
- Simpler deployments

---

# 7. Password Protection

## Purpose
Block weak passwords automatically.

---

## Global Banned Password List
Microsoft blocks:
- Common passwords
- Predictable variations

Examples:
- Password123
- CompanyName2025

---

## Custom Password Lists
Organizations can block:
- Company names
- Product names
- Internal terminology

---

## Protection Against
- Password spray attacks
- Weak credential usage

---

# 8. Conditional Access

# Core Idea
Conditional Access = smart IF-THEN security rules.

---

## Example

IF:
- User logs in from unknown country
- Device is non-compliant
- Risk is high

THEN:
- Require MFA
- Block access
- Force password reset

---

# Signals Used

## User
Who is signing in?

## Device
Trusted or compliant?

## Location
Known or risky location?

## Risk Level
Suspicious activity detected?

## Application
Which app is being accessed?

---

# Access Outcomes

## Allow Access

## Block Access

## Allow with Conditions
Examples:
- Require MFA
- Require compliant device
- Limit session actions

---

# Benefits
- Adaptive security
- Lower friction for safe users
- Stronger Zero Trust enforcement

---

# 9. Global Secure Access

## Purpose
Secure access to:
- Internet apps
- Private corporate apps

Without relying on VPNs.

---

# Components

## Entra Internet Access
Protects:
- SaaS apps
- Web traffic

---

## Entra Private Access
Secure access to:
- Internal corporate resources

Can replace:
- Traditional VPNs

---

# Benefits
- Better visibility
- Identity-driven security
- Reduced lateral movement
- Remote work support

---

# 10. Role-Based Access Control (RBAC)

## Main Principle
Give users only the permissions they need.

---

# Built-In Roles

## Global Administrator
Full control.

## User Administrator
Manage users/groups.

## Billing Administrator
Manage subscriptions/billing.

---

# Benefits
- Least privilege
- Reduced risk
- Easier auditing
- Better control

---

# Important Difference

## Entra RBAC
Controls:
- Identity resources

---

## Azure RBAC
Controls:
- Azure infrastructure
- VMs
- Storage
- Networking

---

# 11. Identity Governance

## Goal
Ensure:
- Right people
- Right access
- Right time
- Right duration

---

# Join-Move-Leave Model

## Join
Create account + grant access.

## Move
Adjust permissions.

## Leave
Remove access.

---

# Governance Features

## Dynamic Groups
Automatic group membership based on attributes.

## Access Reviews
Periodic review of:
- Group access
- App access
- Roles

---

# Why Access Reviews Matter
Prevent:
- Old permissions
- Forgotten guest accounts
- Overprivileged users

---

# 12. Privileged Identity Management (PIM)

## Purpose
Protect admin roles.

---

# Problem
Permanent admin access = dangerous.

---

# PIM Solution
Use:
- Just-In-Time access
- MFA
- Approval workflows
- Time-limited admin access

---

## Example
Admin activates Global Admin role:
- Only when needed
- For limited time
- Fully audited

---

# Benefits
- Reduced attack surface
- Better auditing
- Stronger admin security

---

# 13. Identity Protection

## Purpose
Detect risky identities and sign-ins.

---

# Detects
- Leaked credentials
- Suspicious sign-ins
- Impossible travel
- Risky users
- Risky workload identities

---

# Automated Responses

## Require MFA

## Force Password Reset

## Block Access

---

# Integration
Works with:
- Conditional Access
- Microsoft Security Copilot

---

# 14. Microsoft Security Copilot + Entra

## Purpose
Help security analysts investigate faster.

---

# Capabilities
- Natural language analysis
- Risk summaries
- Investigation guidance
- Threat explanations

---

# Benefits
- Faster incident response
- Easier investigations
- Better visibility

---

# Everyday Practical Takeaways

- MFA should always be enabled
- Passwordless > passwords
- Use Conditional Access for adaptive security
- Apply least privilege everywhere
- Avoid permanent admin access
- Review guest access regularly
- Monitor risky sign-ins continuously
- Identity is the new security perimeter

---

# Quick Memory Notes

- Entra ID = Cloud identity platform
- MFA = Multiple verification factors
- Conditional Access = IF-THEN access rules
- RBAC = Permission control by role
- PIM = Just-In-Time admin access
- Identity Protection = Detect/respond to identity threats
- Passwordless = Stronger + easier authentication


# Introduction to Microsoft security solutions: Part 1

# SC-900 Notes — Microsoft Security Solutions (Part 1)

> Video: [Introduction to Microsoft Security Solutions: Part 1 | SC-900 | Episode 4](https://www.youtube.com/watch?v=wpOwHKL5DpQ&utm_source=chatgpt.com)

---

# 🤖 Microsoft Security Copilot

## What is it?

Microsoft Security Copilot is an AI-powered security assistant.

It combines:

* Large Language Models (LLMs)
* Microsoft security data
* Threat intelligence
* Security tools (Defender, Sentinel, Entra, etc.)

Goal:

> Help security teams investigate threats faster and make better decisions.

---

## Main Use Cases

### Incident Summarization

Instead of reading hundreds of alerts:

* summarizes incidents
* highlights affected users
* identifies impacted devices

### Impact Analysis

Shows:

* affected users
* affected systems
* affected data

Helps prioritize response efforts.

### Script Analysis

Can explain:

* PowerShell scripts
* Bash scripts
* Malware commands

In plain English.

### Guided Response

Provides:

* investigation steps
* containment recommendations
* remediation guidance

---

# Security Copilot Concepts

| Term         | Meaning                          |
| ------------ | -------------------------------- |
| Session      | One conversation                 |
| Prompt       | Question or instruction          |
| Plugin       | Connection to security tools     |
| Workspace    | Separate environment for teams   |
| Orchestrator | AI engine coordinating responses |
| Agent        | Autonomous AI assistant          |

---

# Workspaces

A workspace is an isolated Copilot environment.

Useful for:

* Security teams
* SOC teams
* Compliance teams
* Different departments

Benefits:

* Separate permissions
* Separate plugins
* Separate billing/capacity
* Data residency control

---

# Agents

Agents automate repetitive tasks.

Examples:

* Phishing investigations
* Threat analysis
* Identity investigations
* Data security tasks

Agents:

✅ Can work automatically

✅ Use plugins

✅ Follow permissions

✅ Learn from feedback

---

# Good Prompt Structure

A strong prompt should include:

### 1. Goal

What do you want?

Example:

> Summarize this incident.

---

### 2. Context

Why do you need it?

Example:

> Create a report for management.

---

### 3. Expectations

Desired output.

Example:

> Give me 5 bullet points.

---

### 4. Source

Where should Copilot look?

Example:

> Use Defender XDR alerts.

---

# ☁️ Azure Security Services

---

# Azure DDoS Protection

Protects internet-facing applications from:

* Volumetric attacks
* Protocol attacks
* Resource exhaustion attacks

Features:

* Always-on monitoring
* Automatic mitigation
* Traffic analysis
* Azure Monitor alerts

Best practices for DDoS protection
A multi-layered approach to DDoS protection is most effective:

Combine DDoS Protection with WAF: 
Use Azure DDoS Protection for network-layer (layers 3 and 4) protection and 
a WAF for application-layer (layer 7) protection. 
Neither service alone covers all attack vectors.
Design for resilience:Build applications with redundancy so that if one component is temporarily impacted, the overall application can continue serving users.
Enable telemetry and alerting: Configure Azure Monitor alerts for DDoS metrics so that your security team is notified immediately when an attack is detected.
Plan for incidents: Have an incident response plan in place before an attack occurs, so your team knows how to respond quickly and coordinate effectively.

Common attacks WAF protects against
WAF defends against a wide range of threats defined in the Open Web Application 
Security Project (OWASP) core rule set—a set of generic attack detection rules designed as a baseline for any WAF. 


Common attacks WAF protects against include:

SQL injection: Attackers insert malicious SQL code into input fields to manipulate or extract data from the application's backend database. SQL injection can expose sensitive data or allow attackers to modify or delete database records.
Cross-site scripting (XSS): Attackers inject malicious scripts into web pages that other users view. The scripts can steal session tokens, credentials, or sensitive data from the affected user's browser.
HTTP floods: High volumes of HTTP requests overwhelm a web application at the application layer. This type of distributed denial of service (DDoS) attack targets layer 7 (the application layer), which Azure DDoS Protection alone doesn't cover. Azure WAF detects and blocks abnormal traffic patterns at this layer.
Remote file inclusion: Attackers trick a web application into including a malicious remote file, which then executes on the server and can give the attacker unauthorized access.
By using a centralized WAF, you can patch newly discovered vulnerabilities in one place rather than updating protection on every individual web application. This simplifies security management and reduces the window of exposure when new threats emerge.
---

## Protection Types

### Basic

Free.

Basic platform protection.

### Network Protection

Advanced protection for VNets.

### IP Protection

Protection for specific public IP addresses.

---

# Azure Firewall

Managed cloud firewall.

Provides:

### Layer 3/4 Protection

* IP filtering
* TCP/UDP filtering

### Layer 7 Protection

* Application filtering
* URL filtering
* Threat intelligence filtering

---

## Common Deployment

Hub-and-Spoke Architecture

```text
Internet
    |
Azure Firewall
    |
-----------------
|       |       |
VNet1 VNet2 VNet3
```

Benefits:

* Centralized security
* Easier management
* Better visibility

---

# Azure Web Application Firewall (WAF)

Protects web applications.

Defends against:

* SQL Injection
* Cross-Site Scripting (XSS)
* Application-layer DDoS attacks

Can be used with:

* Azure Application Gateway
* Azure Front Door
* Azure CDN

---

# 🌐 Azure Virtual Network (VNet)

A VNet is your private network in Azure.

Provides:

* Isolation
* Connectivity
* Segmentation

Think of it as:

> Your company's private network inside Azure.

---

# Network Segmentation

Purpose:

* Reduce attack surface
* Limit lateral movement
* Support Zero Trust

Example:

```text
VNet
 ├── Web Subnet
 ├── App Subnet
 └── Database Subnet
```

---

# Network Security Groups (NSGs)

Traffic filtering inside a VNet.

Rules evaluate:

* Source IP
* Destination IP
* Port
* Protocol
* Direction

---

## Example

Allow:

```text
TCP 443
Internet → Web Server
```

Block:

```text
All other inbound traffic
```

---

## Key Exam Fact

Rules are processed:

> Lowest number = Highest priority

Example:

```text
100 Allow RDP
65000 Deny All
```

Rule 100 wins.

---

# Azure Bastion

Secure remote access to VMs.

Supports:

* RDP
* SSH

Without:

❌ Public IPs

❌ Opening ports to the Internet

---

## Benefits

* Reduced attack surface
* Protection from port scanning
* Browser-based access

---

# 🔑 Azure Key Vault

Secure storage for:

* Secrets
* Passwords
* API keys
* Certificates
* Cryptographic keys

---

## Why Use It?

Bad:

```text
Password inside source code
```

Good:

```text
Password stored in Key Vault
```

---

## Key Vault Tiers

### Standard

Software-based encryption.

### Premium

Hardware Security Module (HSM)

Higher security.

---

# SC-900 Exam Takeaways

Remember:

### Security Copilot

* AI-powered security assistant
* Uses prompts
* Works with plugins
* Supports agents

### Azure DDoS Protection

* Protects against DDoS attacks

### Azure Firewall

* Layer 3/4 + Layer 7 protection

### WAF

* Protects web applications

### VNet

* Private Azure network

### NSG

* Traffic filtering rules

### Bastion

* Secure VM access

### Key Vault

* Secure secret management

---

# Introduction to Microsoft security solutions: Part 2 | SC-900 | Episode 5 - YouTube

## 📘 GitHub Notes — SC-900 (Microsoft Security Solutions Part 2)

---

# 🛡️ Microsoft Defender for Cloud

## 🔍 Purpose

* Cloud security management platform for Azure, hybrid, and multi-cloud
* Helps you **improve security posture + protect workloads**

---

## 🧠 Core pillars

### 1. CSPM (Cloud Security Posture Management)

* Continuously scans environment for misconfigurations
* Shows **Secure Score**
* Uses **Microsoft Cloud Security Benchmark (MCSB)**
* Provides recommendations (fixes to improve security)

### 2. CWPP (Cloud Workload Protection Platform)

* Protects running workloads:

  * Virtual Machines
  * Databases
  * Containers
* Detects vulnerabilities + threats in real time
* Uses Defender plans per workload type

### 3. DevSecOps

* Security in development pipelines (CI/CD)
* Integrates with GitHub / Azure DevOps
* Finds:

  * insecure code
  * exposed secrets
  * misconfigurations in infrastructure-as-code
* Helps fix issues before production

---

## 📊 Security Initiatives

* Collection of policies applied to resources
* Default: **Microsoft Cloud Security Benchmark (MCSB)**
* Evaluates compliance across subscriptions/resources
* Generates **recommendations automatically**

---

## 📈 Secure Score

* Overall security rating of environment
* Improves by fixing recommendations
* Helps prioritize security work

---

## 🧾 Example issues detected

* Unencrypted SQL databases
* Public storage access enabled
* Open management ports on VMs

---

## 🧩 Key capabilities in Defender for Cloud

* Asset discovery
* Continuous security assessment
* Regulatory compliance tracking
* Threat recommendations
* Integration with Microsoft Security Copilot

---

## 🖥️ Workload protection examples

* VM endpoint protection
* Vulnerability scanning
* Container security
* Database protection
* Multi-cloud (AWS / GCP support)

---

## ⚙️ Environment settings

* Enable/disable security plans per resource type
* Control coverage per subscription
* Choose between:

  * Free CSPM features
  * Paid advanced protection plans

---

# 📊 Microsoft Sentinel (SIEM + SOAR)

## 🧠 What it is

* Cloud-native **SIEM + SOAR platform**
* Used for:

  * threat detection
  * investigation
  * automated response

---

## 🔍 SIEM (Security Information & Event Management)

* Collects logs from:

  * Azure resources
  * on-prem systems
  * multi-cloud
* Correlates events into alerts/incidents
* Detects anomalies and suspicious behavior

---

## ⚙️ SOAR (Security Orchestration & Automated Response)

* Automates response actions:

  * disable user accounts
  * block IP addresses
  * create tickets (e.g., ServiceNow)
* Reduces manual work + response time

---

## 🔄 Sentinel workflow

### 1. Collect

* Ingest logs from many sources:

  * Entra ID
  * Azure Activity Logs
  * firewalls, endpoints, etc.

### 2. Detect

* Analytics rules find threats
* Uses:

  * threat intelligence
  * MITRE ATT&CK mapping
* Groups alerts into **incidents**

### 3. Investigate

* Incident = full case file
* Tools:

  * Hunting (manual investigation)
  * KQL queries
  * Notebooks
  * Workbooks (visual dashboards)

### 4. Respond

* Automation rules + playbooks
* Actions:

  * isolate machines
  * disable accounts
  * send alerts
* Built using Azure Logic Apps

---

## 🔎 Key features

### 🧪 Hunting

* Manual threat investigation
* Uses KQL queries
* Hypothesis-based security search

### 📊 Workbooks

* Dashboards for visualization
* Show trends, anomalies, activity

### ⚡ Analytics rules

* Detect suspicious behavior
* Trigger alerts/incidents

### 🤖 Automation

* Runs playbooks automatically on incidents
* Improves response speed

---

## 🧠 Example attack scenario

* Impossible travel login detected
* Privileged role assigned from unknown IP
* Sentinel:

  * correlates events
  * creates incident
  * triggers playbook:

    * disable account
    * revoke sessions
    * notify security team

---

## 🧩 MITRE ATT&CK integration

* Maps detections to attacker techniques
* Helps understand:

  * attack type
  * stage of attack
  * behavior patterns

---

## 🤖 Security Copilot integration

* Natural language queries in Sentinel
* Can:

  * summarize incidents
  * generate KQL queries
  * explain alerts in plain English

---

## 🔌 Data connectors

* Connect Sentinel to:

  * Microsoft Defender
  * Azure services
  * external tools (Syslog, APIs)

---

## 📌 Key takeaway

* **Defender for Cloud = prevent + harden**
* **Sentinel = detect + respond**
* Together they provide full security lifecycle coverage

---

# Azure provides a range of interconnected infrastructure security services that protect your resources at multiple layers—from network-level DDoS mitigation to application-layer firewall protection, secure remote access, and cryptographic key management.

In this module, you explored the following services:

Azure DDoS Protection protects applications and servers from distributed denial of service attacks at layers 3 and 4. 
It offers two tiers—DDoS Network Protection and DDoS IP Protection—that provide dedicated monitoring, telemetry, alerting, and, for Network Protection, rapid response support.

Azure Firewall is a managed, cloud-based, stateful network security service. 
It's available in Basic, Standard, and Premium SKUs to match different organizational needs, and supports centralized management through Azure Firewall Manager.

Web Application Firewall (WAF) provides centralized protection for web applications against common exploits like SQL injection and cross-site scripting. 
WAF can be deployed with Azure Application Gateway, Azure Front Door, or Azure CDN.
Azure Virtual Networks are the fundamental building block for private networking in Azure. Subnets, VNet peering, and traffic filtering through NSGs and Azure Firewall enable network segmentation that supports defense-in-depth and the Zero Trust principle of assume breach.

Network Security Groups (NSGs) filter inbound and outbound network traffic using configurable rules based on IP address, port, and protocol. 

Application security groups (ASGs) let you group VMs and manage security policies based on your application’s structure.
Azure Bastion is a fully managed PaaS service that provides secure RDP and SSH connectivity to virtual machines directly from the Azure portal, over TLS, without requiring public IP addresses or open management ports. It’s available in Developer, Basic, Standard, and Premium SKUs.

Azure Key Vault centralizes the storage and management of secrets, keys, and certificates. It enforces the Zero Trust principle of least privilege access through Microsoft Entra ID authentication and Azure RBAC, and integrates with a wide range of Azure services.

Together, these services support a defense-in-depth strategy that layers multiple security controls to reduce the risk and impact of security breaches.


# SC-900 — Microsoft Security Solutions (Part 3)

*GitHub Notes | Exam-focused + Practical*

---

# Microsoft Defender XDR

## What is it?

**Microsoft Defender XDR** is a unified security platform that:

* Prevents attacks
* Detects threats
* Investigates incidents
* Responds automatically

It correlates signals from multiple Defender products and presents them in a **single incident view**.

### Integrated Products

| Product                           | Protects              |
| --------------------------------- | --------------------- |
| Defender for Endpoint             | Devices               |
| Defender for Office 365           | Email & collaboration |
| Defender for Identity             | Identities            |
| Defender for Cloud Apps           | SaaS applications     |
| Defender Vulnerability Management | Vulnerabilities       |
| Microsoft Sentinel                | SIEM/SOAR integration |

---

## Key Benefit

Instead of seeing:

* Email alert
* Identity alert
* Endpoint alert

You see:

✅ **One correlated incident**

This provides the complete attack story.

---

## Example Attack Chain

```text
Phishing Email
      ↓
Credential Theft
      ↓
Suspicious Sign-in
      ↓
Malware on Device
```

Defender XDR automatically correlates all activities into one incident.

---

# Microsoft Defender for Office 365

## Purpose

Protects against:

* Phishing
* Malware
* Malicious links
* Malicious attachments
* Teams threats
* SharePoint threats

---

## Key Features

### Safe Attachments

* Opens attachment in sandbox
* Checks for malicious behavior
* Blocks dangerous files

### Safe Links

* Checks URLs before opening

### Anti-Phishing

* Detects spoofed emails
* Detects impersonation attacks

### Anti-Malware

* Blocks malicious files

---

## Investigation Tools

### Explorer

Used to:

* Investigate emails
* Find affected users
* Track campaigns

### Message Trace

Track email delivery.

### Audit Log Search

Review user/admin actions.

---

## Exam Example

```text
User receives malicious invoice.

Safe Attachments detonates file.

File identified as malware.

Email quarantined.
```

Result:

✅ User never opens malware

---

## ZAP

### Zero-hour Auto Purge

Automatically removes malicious emails already delivered to mailboxes.

---

# Microsoft Defender for Endpoint

## Purpose

Protects:

* Laptops
* Workstations
* Servers
* Endpoints

---

## How it Works

Uses:

* Behavioral sensors
* Cloud analytics
* Threat intelligence

to detect suspicious activity.

---

## Capabilities

### Prevention

Blocks attacks before execution.

### Detection

Detects suspicious behavior.

### Investigation

Automatically investigates incidents.

### Response

Supports remediation actions.

---

## Example

```text
User downloads malware
      ↓
Defender detects exploit attempt
      ↓
Attack blocked
      ↓
Investigation starts automatically
```

---

# Microsoft Defender for Cloud Apps

## Purpose

Protect SaaS applications.

Examples:

* Microsoft 365
* Salesforce
* Dropbox
* Google Workspace

---

## Main Goals

### Cloud Discovery

Discover applications used by employees.

### Shadow IT Detection

Find unauthorized apps.

### Data Protection

Protect sensitive data.

### Threat Detection

Detect risky activities.

---

## Example

```text
Employee uploads customer data
to unauthorized cloud storage.
```

Defender for Cloud Apps:

1. Discovers app
2. Classifies app as risky
3. Blocks access
4. Alerts security team

---

## Cloud Discovery

Analyzes network traffic and identifies:

* Apps in use
* Risk level
* Compliance status

---

## Cloud App Catalog

Database of ~37,000 cloud applications.

Provides:

* Security score
* Compliance score
* Risk assessment

---

## Policy Management

Used to create policies such as:

```text
Alert when terminated employee logs in
```

or

```text
Block risky downloads
```

---

# Microsoft Defender for Identity

## Purpose

Protect on-premises Active Directory environments.

---

## Detects

* Credential theft
* Lateral movement
* Privilege escalation
* Suspicious authentication

---

## How it Works

Sensors installed on:

```text
Domain Controllers
```

collect signals and send them to Defender.

---

## Example

```text
Attacker steals credentials
      ↓
Attempts lateral movement
      ↓
Defender detects activity
      ↓
Account disabled
```

---

# Microsoft Defender Vulnerability Management

## Purpose

Find and reduce vulnerabilities before attackers exploit them.

---

## Discovers

* Devices
* Applications
* Operating systems
* Configurations

---

## Detects

* Missing patches
* Outdated software
* Weak configurations
* Security misconfigurations

---

## Key Concept

### Risk-Based Prioritization

Not all vulnerabilities are equally important.

Microsoft prioritizes:

* Actively exploited vulnerabilities
* High-risk vulnerabilities
* Critical assets

---

## Supported Platforms

* Windows
* Linux
* macOS
* Mobile devices
* Network devices

---

## Benefits

✅ Reduce attack surface

✅ Prioritize remediation

✅ Track remediation progress

---

# Microsoft Defender Threat Intelligence

## Purpose

Provide intelligence about:

* Threat actors
* Campaigns
* Indicators of compromise (IoCs)
* Vulnerabilities

---

## Main Components

### Threat Analytics

Analyze current attack campaigns.

### Intel Explorer

Search:

* Threat actors
* CVEs
* Indicators

### Projects

Organize investigations.

---

## Security Copilot Integration

Can:

* Summarize threats
* Prioritize vulnerabilities
* Assist investigations

---

# Microsoft Defender Portal

## Purpose

Single pane of glass for Microsoft Security.

Portal:

```text
security.microsoft.com
```

---

## What You Can Manage

### Identities

Defender for Identity

### Devices

Defender for Endpoint

### Email

Defender for Office 365

### Cloud Apps

Defender for Cloud Apps

### Threat Intelligence

Threat Analytics

### Sentinel

SIEM/SOAR

---

# Secure Score

Measures overall security posture.

Higher score = better security.

Used to:

* Track improvements
* Prioritize actions
* Reduce risk

---

# Exposure Management

Provides visibility into:

* Attack paths
* Assets
* Risks
* Weaknesses

---

# Advanced Hunting

Used for:

* Custom investigations
* KQL queries
* Threat hunting

---

## Example

Security analyst suspects:

```text
Suspicious sign-ins
```

Uses:

```text
Advanced Hunting
```

to search logs with KQL.

---

# Microsoft Security Copilot

## Purpose

AI assistant for security operations.

---

## What It Can Do

### Incident Summaries

Explain:

* What happened
* Why it matters
* Affected assets

### Guided Response

Suggest:

* Investigation steps
* Containment actions
* Remediation actions

### Generate KQL

Convert natural language into KQL queries.

Example:

```text
Show suspicious sign-ins today
```

→ Generates KQL automatically

---

# SC-900 Exam Essentials

## Defender XDR

**Correlates alerts into one incident.**

---

## Defender for Office 365

Protects:

* Email
* Links
* Attachments
* Teams
* SharePoint

---

## Safe Attachments

Sandbox for email attachments.

---

## ZAP

Zero-hour Auto Purge removes malicious emails after delivery.

---

## Defender for Endpoint

Protects devices and endpoints.

---

## Defender for Cloud Apps

Protects SaaS applications and detects Shadow IT.

---

## Defender for Identity

Protects Active Directory identities.

---

## Defender Vulnerability Management

Discovers and prioritizes vulnerabilities.

---

## Defender Threat Intelligence

Provides intelligence about threats and attackers.

---

## Security Copilot

Uses AI to:

* Summarize incidents
* Generate KQL
* Assist investigations

---

## Microsoft Defender Portal

```text
security.microsoft.com
```

Unified portal for all Defender solutions.

_______________________________________________________

# Microsoft Purview — GitHub Notes (SC-900 / Real-World Practical Use)

> **Goal:** Understand what Microsoft Purview does, when to use it, and what is important for exams and real-world cloud security roles.

---

# What is Microsoft Purview?

Microsoft Purview is Microsoft's **data governance, compliance, and data protection platform**.

Think of it as:

> **"Microsoft Purview protects and manages data wherever it lives."**

It helps organizations:

* Discover data
* Classify data
* Protect sensitive information
* Meet compliance requirements
* Prevent data leaks

---

# Why Does It Exist?

Companies store sensitive data everywhere:

* Emails
* Teams chats
* SharePoint
* OneDrive
* Databases
* Cloud applications

Purview helps answer:

* Where is our sensitive data?
* Who has access to it?
* Is it being shared improperly?
* Are we compliant with regulations?

---

# Core Capabilities

## 1. Data Discovery

Automatically finds:

* Credit card numbers
* Personal information (PII)
* Health records
* Financial data

### Example

Purview scans SharePoint and finds:

```text
Customer_List.xlsx
Contains:
- Names
- Emails
- Credit card numbers
```

Purview identifies it as sensitive data.

---

## 2. Sensitivity Labels

Allows organizations to classify information.

### Examples

```text
Public
Internal
Confidential
Highly Confidential
```

---

### Example

A document is labeled:

```text
Highly Confidential
```

Purview can:

* Encrypt it
* Restrict sharing
* Prevent downloads
* Prevent printing

---

# 3. Data Loss Prevention (DLP)

Prevents sensitive information from leaving the organization.

---

### Example

User tries to send:

```text
Credit Card Number
```

through:

* Outlook
* Teams
* SharePoint

Purview can:

* Block it
* Warn the user
* Alert administrators

---

### Exam Keyword

```text
DLP = Prevent data leakage
```

---

# 4. Insider Risk Management

Detects risky user behavior.

---

### Example

Employee:

* Downloads thousands of files
* Copies data to USB
* Sends confidential files externally

Purview can generate alerts.

---

### Exam Keyword

```text
Insider Risk = Risk from trusted users
```

---

# 5. eDiscovery

Used during:

* Investigations
* Audits
* Legal cases

---

### Example

Legal team requests:

```text
All emails from John Doe
between Jan and March
```

Purview can locate and export them.

---

### Exam Keyword

```text
eDiscovery = Search and collect evidence
```

---

# 6. Records Management

Controls:

* Retention
* Deletion
* Archiving

---

### Example

Policy:

```text
Keep invoices for 7 years
```

Purview automatically enforces it.

---

# Compliance Manager

Provides compliance tracking against standards such as:

* GDPR
* ISO 27001
* NIST
* HIPAA

---

### Helps Answer

```text
Are we compliant?
What still needs improvement?
```

---

# Purview vs Defender for Cloud Apps

| Service                 | Purpose                                  |
| ----------------------- | ---------------------------------------- |
| Defender for Cloud Apps | Monitor and secure cloud app usage       |
| Purview                 | Protect and govern data                  |
| Defender for Cloud      | Secure cloud resources and workloads     |
| Sentinel                | SIEM/SOAR, threat detection and response |

---

# SC-900 Exam Focus

Know these terms:

```text
Sensitivity Labels
Data Loss Prevention (DLP)
eDiscovery
Insider Risk Management
Compliance Manager
Information Protection
```

---

# Real-World Use Cases

## Financial Company

Purview:

* Finds credit card data
* Labels sensitive files
* Blocks sharing outside company

---

## Healthcare Organization

Purview:

* Protects patient records
* Enforces retention policies
* Supports HIPAA compliance

---

## Legal Investigation

Purview:

* Searches emails
* Collects evidence
* Supports litigation requests

---

# Does Purview Matter for AZ-104?

Not much.

AZ-104 focuses on:

* Virtual Machines
* Networking
* Storage
* RBAC
* Entra ID
* Monitoring

Purview is more important for:

* SC-900
* SC-400
* Security/Compliance roles

---

# For Your Learning Path

### Learn Deeply

✅ Entra ID
✅ RBAC
✅ Conditional Access
✅ Defender for Cloud
✅ Defender for Cloud Apps
✅ Sentinel

### Learn Basic Concepts

✅ Purview
✅ DLP
✅ Sensitivity Labels
✅ eDiscovery

You don't need to become a Purview expert for AZ-104, but you should understand the concepts because they appear frequently in Microsoft security certifications.



<img width="1195" height="761" alt="image" src="https://github.com/user-attachments/assets/01910286-6130-438c-b2bc-324bfda7568a" />


Insider risk levels
At the center of adaptive protection are insider risk levels, which are calculated by Insider Risk Management based on each user's behavior and the risk indicators defined in the organization's policies. Adaptive protection uses three risk levels:

# Elevated risk level: Assigned to users with high severity alerts or users with multiple high-severity activity sequences. The strongest protective controls apply to users at this level.
# Moderate risk level: Assigned to users with medium severity alerts or users with multiple high-severity data exfiltration activities. Moderate controls help balance security with productivity.
# Minor risk level: Assigned to users with low severity alerts or users with at least one high-severity exfiltration activity. Light controls such as policy tips and educational reminders apply to influence positive behavior without disrupting work.
Insider risk levels update continuously and automatically based on users' ongoing activity. When a user's risk level decreases, the protective controls applied to them also relax. When risk increases, controls tighten automatically—without any manual action from an admin.


# Adaptive protection integrates with Microsoft Entra Conditional Access to restrict application access based on insider risk levels. Organizations configure Conditional Access policies that respond automatically to a user's current risk level. For example:

Users with a Minor risk level might be required to acknowledge a Terms of Use agreement before accessing certain applications.
Users with a Moderate risk level might be blocked from accessing specific high-sensitivity applications.
Users with an Elevated risk level might be completely blocked from accessing organizational applications until their risk level is resolved.
Because Conditional Access policies and DLP policies both respond dynamically to the insider risk levels managed by Insider Risk Management, the organization achieves a layered, coordinated response to insider risk—without needing to manually update multiple policies whenever a user's behavior changes.



# SC-900 Exam Cheat Sheet (GitHub Notes)

> Goal: Pass SC-900 and understand Microsoft's security ecosystem at a high level.

---

# 1. Microsoft Security, Compliance & Identity

Microsoft's security portfolio is built around 3 pillars:

| Area                    | Product            |
| ----------------------- | ------------------ |
| Identity & Access       | Microsoft Entra    |
| Security                | Microsoft Defender |
| Compliance & Governance | Microsoft Purview  |

Remember:

```text
Who are you?      -> Entra
Are you safe?     -> Defender
Is your data compliant? -> Purview
```

---

# 2. Microsoft Entra

Formerly Azure AD.

Used for:

* Authentication
* Authorization
* Identity Management

Examples:

* User signs into Microsoft 365
* MFA verification
* Conditional Access
* SSO

---

## Authentication vs Authorization

### Authentication

```text
Who are you?
```

Examples:

* Password
* MFA
* Windows Hello

### Authorization

```text
What can you access?
```

Examples:

* Files
* Applications
* Azure resources

---

## Multi-Factor Authentication (MFA)

Requires:

```text
Something you know
+ Something you have
OR
Something you are
```

Examples:

* Password + Authenticator App
* Password + Fingerprint

---

## Conditional Access

```text
IF conditions are met
THEN allow access
```

Example:

```text
User outside company network
→ Require MFA
```

---

## Zero Trust

Never trust.

Always verify.

Principles:

```text
Verify Explicitly
Least Privilege
Assume Breach
```

---

# 3. Microsoft Defender

Security platform protecting identities, endpoints, cloud workloads, apps and email.

---

## Microsoft Defender XDR

Extended Detection & Response.

Combines signals from:

* Endpoints
* Identity
* Email
* Applications

Goal:

```text
Detect attacks faster
```

---

## Defender Products

### Defender for Endpoint

Protects:

* PCs
* Laptops
* Servers

Detects:

* Malware
* Ransomware
* Suspicious behavior

---

### Defender for Office 365

Protects:

* Email
* Teams
* SharePoint

Detects:

* Phishing
* Malicious links
* Malicious attachments

---

### Defender for Identity

Protects:

* Active Directory
* Identity infrastructure

Detects:

* Credential theft
* Lateral movement

---

### Defender for Cloud Apps

Cloud Access Security Broker (CASB)

Provides:

* Visibility
* Data Security
* Threat Protection
* Compliance

---

### SC-900 Question

**Which CASB area identifies and controls sensitive information?**

✅ **Data Security**

---

# 4. Microsoft Defender for Cloud

Protects Azure, Hybrid and Multi-Cloud resources.

---

## Three Main Capabilities

### CSPM

Cloud Security Posture Management

Focus:

```text
Misconfigurations
Security posture
Recommendations
```

Examples:

* Open management ports
* Public storage accounts
* Missing encryption

---

### CWPP

Cloud Workload Protection Platform

Focus:

```text
Protect workloads
```

Examples:

* Virtual Machines
* Containers
* Databases

---

### DevSecOps

Integrates security into development.

Examples:

* GitHub scanning
* Secret detection
* IaC scanning

---

## Secure Score

Measures security posture.

Higher score:

```text
More secure environment
```

---

## Security Recommendations

Defender for Cloud continuously checks:

* Resources
* Subscriptions
* Configurations

Then provides:

```text
Recommendations
```

---

# 5. Microsoft Sentinel

Cloud-native:

```text
SIEM + SOAR
```

---

## SIEM

Security Information and Event Management

Purpose:

```text
Collect
Analyze
Detect
```

Examples:

* Sign-in logs
* Firewall logs
* Azure logs

---

## SOAR

Security Orchestration Automation and Response

Purpose:

```text
Automate responses
```

Examples:

* Disable account
* Create ticket
* Block IP

---

## Sentinel Workflow

```text
Collect
↓
Detect
↓
Investigate
↓
Respond
```

---

## Incident Investigation

Contains:

* Alerts
* Users
* Devices
* Evidence

---

### Exam Question

Security analyst wants:

* Incident summary
* Related alerts
* Reputation scores
* Users
* Devices

Answer:

✅ **Incident Page / Incident Investigation Experience**

(Security Copilot can enhance summaries)

---

## Hunting

Used when:

```text
You suspect something happened
```

Uses:

```text
KQL Queries
```

---

## MITRE ATT&CK

Sentinel maps detections to:

```text
MITRE ATT&CK Framework
```

Used to understand attacker tactics.

---

# 6. Microsoft Purview

Compliance & Governance platform.

---

## Purpose

Govern:

* Data
* Compliance
* Privacy
* Risk

---

## Sensitive Information Types

Can detect:

* Credit Card Numbers
* Passport Numbers
* IBAN
* National IDs

---

### SC-900 Question

How to identify credit card numbers?

✅ **Sensitive Information Types (SITs)**

---

## Data Loss Prevention (DLP)

Prevents:

```text
Sensitive data leaving organization
```

Examples:

* Emailing credit card numbers
* Uploading confidential documents

---

## Information Protection

Uses:

* Labels
* Encryption

Examples:

```text
Public
Internal
Confidential
Highly Confidential
```

---

## Data Governance

### What is Data Governance?

Organizing, annotating and publishing data so it can be:

* Found
* Reused
* Protected

Answer:

✅ **Data Governance**

---

# 7. Azure Security Basics

---

## Azure Bastion

Provides secure RDP/SSH access through Azure Portal.

Benefits:

* No Public IP required
* No exposed RDP
* No exposed SSH

Remember:

```text
Bastion = Secure VM Access
```

---

# 8. Security Copilot

AI-powered security assistant.

Helps:

* Summarize incidents
* Generate KQL
* Explain alerts
* Investigate faster

---

# 9. Shared Responsibility Model

Who secures what?

---

## SaaS

Microsoft manages almost everything.

Examples:

* Microsoft 365

Customer mainly manages:

* Users
* Data

---

## PaaS

Microsoft manages:

* Infrastructure

Customer manages:

* Data
* Applications

---

## IaaS

Customer manages:

* Operating Systems
* Applications
* Data

Microsoft manages:

* Physical infrastructure

---

# 10. Exam Memorization Sheet

```text
Entra = Identity

MFA = Strong Authentication

Conditional Access = IF/THEN access control

Zero Trust = Verify Explicitly

Defender = Threat Protection

Defender for Endpoint = Devices

Defender for Identity = Active Directory

Defender for Office 365 = Email

Defender for Cloud Apps = CASB

CASB Data Security = Sensitive Data Protection

Defender for Cloud = Azure Security

CSPM = Posture Management

CWPP = Workload Protection

Secure Score = Security Health

Sentinel = SIEM + SOAR

SIEM = Detect

SOAR = Respond

KQL = Hunting Queries

MITRE ATT&CK = Attack Mapping

Purview = Compliance

DLP = Prevent Data Leaks

SIT = Detect Credit Cards

Labels = Protect Documents

Data Governance = Organize & Publish Data

Azure Bastion = Secure RDP/SSH
```

---

# Last-Minute Exam Strategy

For SC-900, focus on understanding **what each product does**, not deep configuration.

If you can answer:

```text
Entra = Identity
Defender = Security
Purview = Compliance
Sentinel = SIEM/SOAR
Defender for Cloud = Azure Security
```

you already cover a large portion of the exam.



Toto mätie skoro každého začiatočníka v Azure. 😄

V skutočnosti existujú **3 hlavné spôsoby**, ako používať Azure CLI:

# 1. Azure Portal (GUI)

To je klasika:

```text
portal.azure.com
```

Klikáš:

```text
Create VM
Create Storage
Create VNet
```

### Kedy?

* keď sa učíš Azure prvýkrát,
* keď chceš vidieť, kde sa čo nachádza,
* na AZ-104 úplný základ.

---

# 2. Azure CLI na svojom PC

Nainštaluješ si Azure CLI:

```bash
az login
az group list
az vm list
```

Beží:

* CMD
* PowerShell
* Windows Terminal

### Výhody

✅ vieš robiť skripty

✅ automatizácia

✅ používaš vlastný počítač

### Nevýhody

❌ musíš inštalovať

❌ musíš sa prihlasovať

---

# 3. Azure Cloud Shell

Toto je to, čo si videl v Azure portáli.

Vpravo hore:

```text
>_
Cloud Shell
```

Keď ho otvoríš, Microsoft ti vytvorí malý Linux kontajner v Azure.

Už obsahuje:

* Azure CLI
* PowerShell
* Git
* kubectl
* Terraform

---

### Cloud Shell CLI

Príkazy sú rovnaké:

```bash
az vm list
az group list
az storage account list
```

Len bežia priamo v Azure.

---

# Rozdiel

### Azure CLI na PC

```text
Tvoj notebook
↓
Internet
↓
Azure
```

### Cloud Shell

```text
Azure
↓
Azure
```

Preto nemusíš nič inštalovať.

---

# Čo používajú admini v práci?

Najčastejšie:

```text
Portal + CLI + PowerShell
```

kombinovane.

Príklad:

1. vytvoria VM cez Portal
2. spravia konfiguráciu cez CLI
3. automatizujú cez PowerShell

---

# Čo je lepšie pre AZ-104?

Pre teba:

### 70 %

Azure Portal

Musíš vedieť:

* VNET
* NSG
* Storage
* VM
* RBAC

v GUI.

---

### 20 %

Cloud Shell

Keď bude Microsoft Learn hovoriť:

```bash
az group create
```

otvoríš Cloud Shell a skúšaš.

Nemusíš nič inštalovať.

---

### 10 %

Lokálne Azure CLI

To rieš až neskôr.

---

# Čo by som robil na tvojom mieste

Keďže:

* učíš sa AZ-104,
* máš vlastný Azure účet,
* nechceš platiť veľa,

rob toto:

```text
Azure Portal
+
Cloud Shell
```

To je presne kombinácia, ktorú Microsoft používa v laboch a Microsoft Learn.

Keď vytvoríš napríklad VM cez Portal, potom si otvor Cloud Shell a skús:

```bash
az vm list --output table
```

Keď vytvoríš Storage Account:

```bash
az storage account list --output table
```

Takto sa najrýchlejšie naučíš Azure aj CLI naraz bez inštalácií a bez ďalších nákladov.
