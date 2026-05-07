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




