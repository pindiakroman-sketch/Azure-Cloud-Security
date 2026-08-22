## What is Azure 1 video

00:01–07:40 – Čo je vlastne dátové centrum: John Savill najprv vysvetľuje Azure cez klasické on-premises dátové centrum. Dátové centrum poskytuje výpočtový výkon, storage a sieťovú kapacitu, nad ktorou organizácia vytvára služby ako VM, databázy, kontajnery a aplikácie. Problémom je, že firma musí riešiť hardware, OS, patchovanie, backup, DR, monitoring, bezpečnosť, elektrinu, chladenie a ľudí.
08:19–10:49 – Azure = cloudová kapacita + služby: Azure má pod sebou obrovské množstvo compute, storage a networking kapacity, ale zákazník k nej nepristupuje priamo. Namiesto toho využíva hotové služby, napr. Virtual Machines, Storage Accounts, Managed Disks a Virtual Networks. VM je typický príklad IaaS, kde stále spravuješ OS a časť konfigurácie.
11:39–15:40 – Najväčšia sila Azure je PaaS: Azure ponúka oveľa viac než samotné VM – napr. AKS, App Service, Functions, Logic Apps, SQL, PostgreSQL, MySQL, Cosmos DB, AI/ML a IoT služby. Pri PaaS Azure preberá veľkú časť infraštruktúrnej práce, takže zákazník sa môže sústrediť hlavne na svoju aplikáciu a business logiku. Toto je jeden z najdôležitejších konceptov pre AZ-900. Glasp podobne zdôrazňuje rozdiel medzi IaaS, PaaS a SaaS a to, koľko zodpovednosti preberá cloud provider.
15:03–17:31 – IaaS vs PaaS vs SaaS: Savill vysvetľuje tri základné úrovne: IaaS – napr. VM, kde máš viac kontroly; PaaS – Azure spravuje väčšinu infraštruktúry; SaaS – hotová aplikácia, napr. Microsoft 365 alebo Dynamics 365. Pravidlo je: ak existuje vhodné SaaS, použi ho; ak tvoríš vlastnú aplikáciu, preferuj PaaS; VM/IaaS použi, keď potrebuješ väčšiu kontrolu alebo kompatibilitu.
16:08–17:31 – Consumption-based model a elasticita: On-premises firma musí nakúpiť kapacitu dopredu podľa očakávaného maxima. V Azure platíš podľa využívania a môžeš zdroje škálovať hore alebo dole podľa potreby. To prináša flexibilitu a mení veľkú časť nákladov z CapEx na OpEx. Glasp tento koncept tiež uvádza ako jednu z hlavných výhod cloudu.
17:51–22:48 – Azure Regions a globálna sieť: Azure je rozdelený do regions, ktoré pozostávajú z dátových centier. Regióny sú prepojené globálnou Microsoft sieťou. Výber regiónu ovplyvňuje napríklad latenciu, dostupnosť a umiestnenie dát. Pre pripojenie z vlastnej firmy možno použiť internet/VPN alebo privátne pripojenie cez ExpressRoute. Globálna infraštruktúra a geografická redundancia sú dôležitou súčasťou Azure.
23:15–25:24 – Management, governance a security: Azure poskytuje Azure Portal, PowerShell, CLI a templates na správu zdrojov. Keďže cloud umožňuje self-service, musí existovať governance: Azure Policy určuje, čo je povolené, RBAC určuje, kto čo môže robiť a budgets pomáhajú kontrolovať spotrebu. K tomu patria bezpečnostné a monitoringové služby ako Microsoft Defender, Sentinel a Azure Monitor.
25:24–27:40 – Identity a hybrid cloud: Identita je kľúčová – Azure používa Microsoft Entra ID (predtým Azure AD), ktoré umožňuje MFA, Conditional Access, Identity Protection a ďalšie kontroly. Azure Arc potom umožňuje aplikovať Azure management a governance aj na on-premises prostredia a vytvárať konzistentnejší hybridný model.
27:40–28:27 – Najdôležitejšia definícia Azure: Azure nie je len „cudzí dátový center“. Je to obrovská cloudová infraštruktúra rozdelená do regiónov, nad ktorou Microsoft poskytuje rozsiahly ekosystém managed služieb, nástrojov, governance, security a monitoringu. Najväčšia hodnota je v tom, že nemusíš spravovať všetku základnú infraštruktúru a môžeš sa sústrediť na to, čo potrebuješ vybudovať.

Pre AZ-900 si z tohto videa hlavne zapamätaj:
Azure = cloudová infraštruktúra + služby.
IaaS = viac správy na zákazníkovi.
PaaS = Azure spravuje viac infraštruktúry.
SaaS = hotový softvér.
Cloud = elasticita + pay-as-you-go + globálny rozsah.
Azure = regions + networking + services + governance + security.

## Azure Master Class v3-Part1 video

* **00:00–05:52 – Typy cloudov:** John Savill vysvetľuje **private, public, community a hybrid cloud**. Azure je public cloud; hybrid cloud kombinuje cloud s on-premises infraštruktúrou. Pri hybride Azure umožňuje napr. **Azure Arc** spravovať zdroje mimo Azure podobným spôsobom ako Azure zdroje. ([Glasp][1])

* **06:34–11:38 – 5 charakteristík cloudu podľa NIST:** cloud poskytuje **on-demand self-service, broad network access, resource pooling, rapid elasticity a measured service**. Dôležité je, že cloud je založený na zdieľaní zdrojov, automatickom škálovaní a meraní spotreby.

* **12:09–20:24 – IaaS, PaaS, SaaS a shared responsibility:** hlavná myšlienka je **presúvanie zodpovednosti na cloud providera**. Pri IaaS (napr. VM) spravuješ OS a aplikácie; pri PaaS (napr. App Service) sa staráš hlavne o aplikáciu a dáta; pri SaaS (napr. Microsoft 365) provider spravuje takmer všetko. Toto je zároveň jedna z kľúčových oblastí AZ-900. ([Glasp][2])

* **20:24–22:34 – Identita zostáva dôležitá:** bez ohľadu na model služby zákazník stále nesie zodpovednosť za veci ako **identity, účty, MFA, Conditional Access a správne nastavenie prístupov**. Pri Azure sa na identitu používa **Microsoft Entra ID**.

* **22:34–32:50 – Prečo používať public cloud:** hlavné výhody sú **elasticita, škálovateľnosť, globálny dosah, flexibilita, disaster recovery a pay-as-you-go**. Výborným príkladom je pizza počas Super Bowlu: nepotrebuješ obrovskú kapacitu celý rok, ale iba počas špičky. Cloud umožní kapacitu zvýšiť a následne znížiť.

* **30:00–36:43 – Typické scenáre pre Azure:** cloud je vhodný na **predictable/unpredictable bursting, startupy, vývoj a testovanie, disaster recovery, verejne dostupné služby/DMZ, globálne aplikácie a krátkodobé špeciálne projekty**, napríklad AI workloady.

* **37:04–49:47 – Azure služby, účty a náklady:** Azure ponúka obrovské množstvo služieb pre **compute, storage, networking, databázy, AI/ML, security, DevOps a IoT**. Dôležité sú tiež subscriptions, management groups, pay-as-you-go, Enterprise Agreement, CSP, **quotas/limits a SKUs**. Pri učení treba dávať pozor na spotrebu a vypínať nepotrebné resources.

* **50:11–54:39 – Reliability v cloude:** namiesto spoliehania sa na jeden veľmi odolný server sa cloudové aplikácie navrhujú s **viacerými inštanciami distribuovanými cez fault/update domains a availability zones**. Spoľahlivosť teda musí byť súčasťou architektúry aplikácie, nie iba vlastnosťou hardvéru.

* **55:06–59:28 – Prečo Azure:** Savill zdôrazňuje silnú kombináciu **IaaS + PaaS, identity, security, governance a hybridných možností**. Azure Arc umožňuje rozšíriť Azure management mimo samotného Azure. Pri výbere cloudu však odporúča pozerať nielen na jednu konkrétnu funkciu, ale na **integráciu celého ekosystému**. ([Glasp][1])

**Najdôležitejšie pre tvoje AZ-900:** zapamätaj si hlavne **Public/Private/Hybrid + IaaS/PaaS/SaaS + 5 charakteristík cloudu + elasticity + consumption-based pricing + shared responsibility + availability/reliability**. Glasp zhrnutia tiež zdôrazňujú, že pri AZ-900 je lepšie chápať **kategórie, účel a príklady služieb** než memorovať každý SKU. ([Glasp][3])


## Master the Azure Pricing Calculator-video-dôležité
Jasné. Toto si **ulož ako základnú definíciu pre AZ-104**. Keď budeš neskôr vytvárať Azure VM, presne tieto pojmy budeš riešiť.

## 🖥️ Azure VM – základná definícia

Pri vytváraní **virtuálneho počítača (VM)** v Azure vyberáš najmä:

### 1. vCPU → procesorový výkon ⚙️

**vCPU (virtual CPU)** určuje, koľko virtuálneho procesorového výkonu VM dostane.

Napríklad:

> **2 vCPU**

znamená, že VM má pridelené 2 virtuálne CPU.

**Viac vCPU → väčší výpočtový výkon.**

---

### 2. RAM → pracovná pamäť 🧠

RAM je pamäť, ktorú VM používa na **aktuálne spustené programy a operácie**.

Napríklad:

> **8 GiB RAM**

VM má 8 GiB pracovnej pamäte.

**Viac RAM → VM zvládne viac programov/dát naraz.**

RAM sa používa počas behu VM a nie je to miesto určené na trvalé uloženie dát.

---

### 3. OS Disk → úložisko 💾

**OS disk** je virtuálny disk, na ktorom je uložený operačný systém VM.

Napríklad:

> **128 GiB OS disk**

Na ňom môže byť napríklad:

* Windows Server
* Linux
* systémové súbory
* nainštalované aplikácie

Po vypnutí VM **dáta na disku zostávajú**.

---

### 4. Data Disk → ďalšie úložisko 📦

Ak potrebuješ viac priestoru, môžeš k VM pridať **data disks**.

Napríklad:

```text
Azure VM
│
├── 4 vCPU        → výkon CPU
├── 16 GiB RAM    → pracovná pamäť
│
├── OS Disk       → Windows/Linux
│   └── 128 GiB
│
└── Data Disk     → dáta aplikácie
    └── 512 GiB
```

---

## 🧠 Zapamätaj si toto

> **CPU = ako rýchlo VM počíta**
> **RAM = koľko môže VM naraz pracovať**
> **Disk = koľko môže VM uložiť**

### Príklad

Ak v Azure vyberieš:

**4 vCPU + 16 GiB RAM + 128 GiB OS disk**

znamená to:

> VM dostane **4 virtuálne CPU**, **16 GiB pracovnej pamäte** a **128 GiB trvalého úložiska pre operačný systém**.

A toto je presne ten základ, ktorý budeš potrebovať, keď začneš v **AZ-104** riešiť vytváranie a konfiguráciu virtuálnych strojov.

# Azure Pricing Calculator — AZ-104 Notes

## 1. Azure Pricing Calculator

**Azure Pricing Calculator** is a tool used to **estimate the cost of Azure resources** before deploying them or when planning an Azure architecture.

> **Pricing Calculator = estimate how much your Azure solution may cost.**

⚠️ It provides an **estimate**, not a guaranteed final bill.

---

## 2. Understand the architecture first

Before using the calculator, you should know:

* What **resources** you need
* How many resources you need
* The **size/SKU** of each resource
* The **Azure region**
* How long the resources will run
* How much data they will process/store
* How the resources communicate with each other

### Example

```text
Users
   ↓
Web App
   ↓
Virtual Machine
   ↓
Database
   ↓
Storage
```

You cannot accurately estimate the cost just by saying:

> "I need an Azure VM."

You need details such as the VM size, region, number of VMs, operating hours, disks, etc.

---

# 3. What affects Azure cost?

### Region

The price of a service can vary between Azure regions.

> **Region can affect the price.**

### Size / SKU

For example:

**2 vCPU + 8 GiB RAM**

will generally cost less than:

**8 vCPU + 32 GiB RAM**

> More resources/performance → generally higher cost.

### Usage

How much and how long you use a resource affects the cost.

For example:

> VM running 24/7

will generally cost more than:

> VM running only 8 hours per day.

---

# 4. Storage costs

Storage costs can depend on things such as:

* Capacity
* Storage type
* Performance
* Number of operations
* Redundancy

For example, Azure Storage redundancy options include:

* **LRS** — Locally Redundant Storage
* **ZRS** — Zone-Redundant Storage
* **GRS** — Geo-Redundant Storage
* **GZRS** — Geo-Zone-Redundant Storage

Different redundancy options can have different costs.

---

# 5. Networking and data transfer

An important AZ-104 concept:

> **The cost is not always just the cost of the resource itself.**

Data transfer/networking can also generate charges.

For example:

```text
VM
 ↓
Database
```

or:

```text
VM
 ↓
Storage
```

The amount and type of data transferred can affect costs.

Therefore, when estimating costs, consider:

> **Network / data transfer costs**

---

# 6. VM and disks

This is particularly important for AZ-104.

A VM can have:

```text
Azure VM
│
├── Compute
│
└── OS Disk
```

**Compute and storage are separate components.**

For example, if you stop or delete a VM, you need to understand what happens to its associated disks and other resources.

> **Stopping/deallocating a VM does not mean that every associated resource disappears.**

Persistent resources such as disks can continue to exist and incur charges.

---

# 7. Free services and free tiers

Some Azure services have:

* Free tiers
* Free amounts of usage
* Limited free services

Therefore, when estimating costs, check:

> **What is free and what is billable?**

Don't assume that an Azure service is always free simply because it has a free tier.

---

# 8. Correct cost-estimation process

Remember this sequence:

```text
1. Design the architecture
          ↓
2. Identify all resources
          ↓
3. Choose sizes / SKUs
          ↓
4. Choose the region
          ↓
5. Estimate usage
          ↓
6. Consider storage
          ↓
7. Consider networking / data transfer
          ↓
8. Use the Pricing Calculator
          ↓
9. Review the estimated cost
```

---

# 9. Pricing Calculator = estimate, not a bill

The calculator gives you an:

> **Estimated cost**

It is **not a guaranteed final Azure bill**.

Actual costs can be different because real usage can change.

Example:

You estimate:

> VM = 100 hours/month

But in reality:

> VM = 400 hours/month

Your actual cost will be higher.

---

# 10. Saving and sharing estimates

You can use the Pricing Calculator to:

* Create estimates
* Save estimates
* Share estimates
* Export estimates, such as to **Excel**

Signing in is useful when you want to save and manage your estimates.

---

# 🎯 What you should remember for AZ-104

If you want the **exam-focused version**, remember these:

### Azure Pricing Calculator

> A tool used to **estimate Azure costs**.

### Azure cost can depend on:

> **Region + Size/SKU + Usage + Storage + Data Transfer + service-specific factors**

### Before calculating:

> **Understand the architecture and identify all resources.**

### Pricing Calculator:

> **Provides an estimate, not a guaranteed final bill.**

### VM:

> **Compute and storage are separate cost components.**

### Networking:

> **Data transfer can generate additional costs.**

### Free tier:

> Some services or amounts of usage may be free, but always check the applicable limits.

---

## Key takeaways

- **Use Cost Management for existing deployments:** Azure Cost Analysis shows spending by subscription, resource, service, region, resource group, and over time. Budgets can trigger alerts based on actual or projected costs. [00:26–02:26]

- **Start with a well-defined architecture:** The pricing calculator is only as accurate as its inputs—identify all resources, SKUs, sizes, quantities, usage patterns, and interactions before estimating costs. [02:26–02:50]

- **Include indirect costs:** Some resources are free, such as virtual networks and resource groups, but their use can create costs through peering, private endpoints, data transfer, or related services. [02:50–03:49]

- **Account for usage rather than just resource count:** Auto-scaling services may run different numbers of instances for different durations, so estimate total instance-hours instead of assuming everything runs continuously. [04:48–06:16]

- **Consider supporting services:** Disks, snapshots, backups, security tools, monitoring, networking, load balancers, public IPs, databases, and disaster recovery can significantly affect the total cost. [06:16–12:36]

- **Pay attention to data-related charges:** Costs may depend on storage transactions, data churn, retention, replication, bandwidth, and egress—especially for monitoring, backups, disks, ExpressRoute, and internet traffic. [06:16–10:17]

- **Azure AD licensing is generally separate:** Licenses such as P1/P2, Conditional Access, Identity Protection, PIM, and MFA are tenant-level costs and are not typically included in a project estimate from the calculator. [12:36–13:03]

- **Sign in to save and manage estimates:** The calculator supports multiple estimates, saved estimates, sharing through a URL, and exporting to Excel. [13:03–14:03] [26:53–28:31]

- **Use example scenarios when helpful:** Prebuilt scenarios can suggest the products commonly needed for architectures such as container CI/CD, modern data warehouses, and web apps. [14:03–14:57]

- **Apply pricing options accurately:** Region, operating system, licensing, reserved instances, Azure Hybrid Benefit, Dev/Test pricing, and agreement type can materially change the estimate. [15:25–17:21] [27:23–27:57]

- **Treat the result as an estimate:** A good architecture can usually produce a reasonable initial range—roughly within 10–20%—which should be refined after observing real workloads. [12:11–12:36]


## Azure Master Class v3 - Part 2 - Identity -6 video-veľa vecí setup v platených verziách--- preto odporučam vrátiť sa k tomu neskôr.


# Deeper explanation of the key takeaways

## 1. Identity replaces the traditional network perimeter

In a traditional data center, organizations often relied on the internal network and firewalls as the primary security boundary. In the cloud, users, applications, devices, and services access resources from many locations and networks, so being “inside the network” no longer proves trust. Identity becomes the control point for deciding who or what may access each resource. [00:00]

This means an identity strategy must include:

- Reliable authentication
- Precise authorization
- Conditional access policies
- Protection of privileged accounts
- User education against phishing and other attacks [00:33]

The broader principle is **“never trust simply because of network location.”** Access should be evaluated using identity, device state, location, application, risk, and authentication strength. [02:00:08] [02:03:22]

---

## 2. Least privilege should guide the entire design

The goal is not merely to make access work. The goal is to give every identity the **minimum permissions required for its specific function**. [02:12]

Excessive permissions create two types of risk:

1. **Accidental risk:** A user or automation makes a mistake, and its broad permissions allow the mistake to affect many resources.
2. **Malicious risk:** An attacker compromises the identity and uses its excessive permissions to cause greater damage. [02:12]

Least privilege applies at multiple levels:

- Which actions the identity can perform
- Which resources it can access
- The scope of those resources
- How long the permissions remain active
- Whether permissions are granted directly or through groups [01:18:17]

For example, a help-desk administrator who only supports one office should not automatically receive tenant-wide administrative permissions. Administrative units allow the role to be scoped to a defined subset of users or objects. [01:19:48]

---

## 3. Treat every identity type differently

An identity is not necessarily a person. It can represent:

- A human user
- An application
- An automation script
- A service
- A device
- A workload running in Azure [04:42]

Each identity should be uniquely identifiable. Shared accounts are problematic because different people or processes may perform actions under the same name, making accountability and auditing difficult. [05:45] [06:49]

Human identities and workload identities also have different security requirements. For example, a human can respond to an MFA prompt, but an unattended automation usually cannot. Using a normal user account for automation therefore creates operational and security problems, especially as MFA enforcement increases. [39:23] [05:12:09]

---

## 4. Separate authentication from authorization

The module emphasizes two different questions:

### Authentication

Authentication answers:

> “Who are you, or what identity are you allowed to use?”

Examples include:

- Passwords
- MFA
- Authenticator applications
- Certificates
- Biometrics
- Hardware tokens
- Passkeys [01:04:39] [01:41:28]

### Authorization

Authorization answers:

> “What is this identity allowed to do?”

Authorization is implemented through roles, permissions, group membership, application assignments, and resource scopes. [08:59] [01:15:52]

This distinction is important because successfully signing in does not mean the identity should have access to every resource. A user may authenticate successfully but still be denied access because they do not have the required role, device compliance, authentication strength, or application assignment. [02:03:22]

---

## 5. Understand the difference between Entra ID and AD DS

### Traditional Active Directory Domain Services

AD DS is primarily designed for a controlled, domain-based network. It commonly uses:

- Domain controllers
- Kerberos and NTLM
- Organizational Units
- Group Policy
- Domain joining
- Hierarchical object structures [22:40] [23:53]

### Microsoft Entra ID

Entra ID is designed for cloud identity and application access. It uses cloud protocols and services such as:

- OAuth
- OpenID Connect
- SAML
- Microsoft Graph
- REST APIs
- Cloud-based authentication and authorization [25:53] [27:01]

Entra ID is not simply “Active Directory running in Azure.” The older Azure AD name was changed partly because it caused people to confuse the two services. [19:13]

The practical consequence is that organizations often need both systems:

- AD DS for legacy domain-dependent workloads
- Entra ID for cloud applications, Microsoft 365, Azure, SaaS applications, and modern authentication [55:16]

---

## 6. The Entra tenant is the central identity boundary

An organization’s Entra tenant contains its identity objects and configuration, including:

- Users
- Groups
- Devices
- Applications
- Service principals
- Tenant-level policies
- Domain names [20:11]

Microsoft services such as Azure, Microsoft 365, and Dynamics 365 rely on the organization’s Entra tenant. Microsoft 365 does not have a completely separate directory; its administrative experiences use the organization’s Entra tenant and Microsoft Graph. [35:03]

An Azure subscription trusts a specific Entra tenant. Although the directory associated with a subscription can technically be changed, doing so after resources are deployed can disrupt access and service configuration. It should not be treated as a casual or routine change. [31:37]

Organizations can have multiple tenants, for example for:

- Separate business entities
- Development or testing
- Customer-facing applications
- Lab environments [36:13] [37:16]

However, unnecessary tenants increase complexity because identities, policies, applications, and administration become distributed across multiple boundaries. [37:16]

---

## 7. Use groups instead of assigning permissions directly to users

Directly assigning permissions to users creates “permission creep.” As users change roles, old permissions may remain attached to their accounts, resulting in an ever-growing set of access rights. [44:32]

A better model is:

1. Assign permissions to a group.
2. Add users to the group when they need the access.
3. Remove users from the group when their role changes.
4. Use group membership as the source of authorization. [44:32]

Groups can be:

- **Assigned:** Membership is managed manually.
- **Dynamic user groups:** Membership is calculated from user attributes.
- **Dynamic device groups:** Membership is calculated from device attributes.
- **Microsoft 365 groups:** Useful for collaboration services such as Teams and SharePoint.
- **Security groups:** Used primarily for access control. [45:28]

Dynamic groups can automatically add or remove people based on attributes such as job title or location. This can reduce manual administration, but the quality of access depends on the accuracy and timeliness of those attributes. [46:30]

---

## 8. Administrative units provide delegated, scoped administration

A tenant-wide administrative role may be too powerful for local or departmental administrators. Administrative units allow administration to be scoped to a subset of users or devices. [01:19:48]

For example:

- A regional help-desk team can manage users in its region.
- An office administrator can reset passwords for one office.
- A department administrator can manage users in a particular department. [01:19:48]

Administrative units can use dynamic membership, such as including users whose city attribute equals a particular location. A role can then be assigned only within that administrative unit. [01:22:08]

Important limitations include:

- Administrative units are for administrative scope, not general resource permissions.
- They cannot be nested.
- Adding a group to an administrative unit does not automatically give management rights over all users in that group.
- Special restricted-management administrative units can protect highly sensitive users or devices from ordinary administrators. [01:20:52] [01:23:15] [01:24:36]

---

## 9. Use workload identities instead of user accounts

Applications and automation should not normally run as a human user. The module describes several workload identity approaches.

### Service principals and app registrations

An application registration defines the application, while its service principal represents that application within a particular tenant. It can be assigned the permissions needed to access resources. [47:42] [50:56]

### Federated credentials

Federation allows an external workload, such as a GitHub Actions workflow, to exchange an identity token from GitHub for an Entra token. This avoids placing a long-lived client secret in the pipeline. [48:49] [49:53]

The trust can be constrained to details such as:

- A particular repository
- A particular workflow
- A particular environment
- A particular external identity [49:53]

### Managed identities

A managed identity gives an Azure resource an automatically managed identity. The application can request a token and access another resource, such as a database, without storing a password, certificate, or secret in configuration. [51:51]

This reduces secret-management risk and is especially useful for Azure Functions, virtual machines, and other Azure workloads. [51:51]

---

## 10. Hybrid identity requires careful synchronization and authentication choices

Many organizations still maintain on-premises AD DS while adopting Entra ID. Synchronization tools copy selected identities and attributes between the environments. [55:16]

The main synchronization approaches discussed are:

### Entra Connect Sync

This is the traditional synchronization architecture. It maintains connector spaces for on-premises Active Directory and Entra ID, then combines and synchronizes the objects. [01:00:18]

A tenant can generally synchronize through one active Entra Connect Sync instance, although staging can be used for disaster recovery. One instance can connect to multiple domains or forests, but the topology has important limitations. [58:16] [59:18]

### Cloud Sync

Cloud Sync uses lightweight provisioning agents and can support synchronization from multiple disconnected AD forests. It may not yet provide every capability of Entra Connect Sync, so the feature requirements must be evaluated before choosing it. [01:01:34] [01:02:29]

### Authentication options

- **Password hash synchronization:** A transformed version of the password hash is synchronized, allowing authentication to occur in the cloud. This is generally the preferred baseline and also supports cloud security analysis such as leaked-password detection. [01:06:54] [01:08:09]
- **Pass-through authentication:** Authentication is validated against on-premises domain controllers, creating a dependency on the on-premises environment. [01:09:12]
- **Federation:** Entra redirects authentication to an external identity provider. This may be appropriate for specialized requirements but introduces additional infrastructure and operational dependency. [01:10:24] [01:11:36]

The module recommends password hash synchronization even when another authentication method is used, because it provides resilience and enables additional Entra security capabilities. [01:08:09]

---

## 11. Strong authentication is more than simply enabling MFA

MFA combines two or more authentication factors:

- Something the user knows, such as a password or PIN
- Something the user has, such as a phone or token
- Something the user is, such as a fingerprint or facial biometric [01:41:28]

Basic MFA significantly reduces many attacks, but not all authentication methods offer the same protection. SMS and voice calls are weaker because attacks can involve SIM cloning, social engineering, or targeted interception. [01:42:51]

Authenticator number matching improves awareness by showing information such as:

- A number the user must match
- The application requesting access
- The approximate location of the request [01:44:07]

However, users can still be tricked into approving a fraudulent request. This is why phishing-resistant methods are preferred for sensitive operations. [01:48:48]

Examples of stronger methods include:

- Windows Hello for Business
- Passkeys
- FIDO2 security keys
- Certificate-based authentication
- Biometric or PIN-protected device credentials [01:45:24] [01:49:48]

These methods are phishing-resistant because the authentication is bound to the legitimate device, key, or proximity requirement rather than being a code that an attacker can persuade the user to disclose. [01:46:32]

---

## 12. Conditional Access is the main policy engine

Conditional Access evaluates a sign-in or access request and applies requirements based on context. It can consider:

- User or group
- Cloud application
- Device platform
- Device compliance
- Location
- Risk
- Authentication context
- Authentication strength [02:02:19] [02:03:22]

Possible decisions include:

- Block access
- Grant access
- Require MFA
- Require a particular authentication strength
- Require a compliant device
- Require acceptance of terms of use
- Force a password change
- Apply session restrictions [02:04:26]

Authentication strength is especially important. Instead of requiring generic “MFA,” a policy can require passwordless MFA or phishing-resistant MFA for sensitive applications. [01:49:48] [01:51:00]

Conditional Access is evaluated as part of the token issuance process. Access tokens are short-lived—roughly 60 to 90 minutes—while refresh tokens can be used to request new access tokens, subject to further policy evaluation. [01:58:58] [02:00:08] [02:01:15]

---

## 13. Privileged access should be temporary and monitored

Permanent administrative access increases the damage that can occur if an administrator’s account is compromised. Privileged Identity Management allows users to be **eligible** for a role rather than permanently active in it. [01:29:03]

When the role is needed, the user can activate it for a limited period. Activation can require:

- MFA
- Stronger authentication
- Justification
- A ticket number
- Approval
- A specific authentication context
- A maximum activation duration [01:30:16] [01:31:27]

This creates a better operational model:

1. The administrator is eligible for the role.
2. The administrator activates it only when necessary.
3. The activation expires automatically.
4. The activation can be reviewed and audited. [01:33:40] [01:34:46]

The same concept can apply to group membership and Azure resource roles, where the scope may be a management group, subscription, resource group, or another defined boundary. [01:32:41]

---

## 14. Access should be reviewed continuously

Permissions tend to accumulate over time. People change jobs, join projects, leave teams, or stop using applications, but their access may remain. Access reviews help validate whether access is still required. [01:36:49]

Reviews can cover:

- Group membership
- Application assignments
- Entra roles
- Azure resource roles
- Access package assignments [01:36:49]

Reviews may be performed by:

- Administrators
- Managers
- Designated reviewers
- The users themselves through self-review [01:36:49]

Entra Permissions Management can also analyze permissions usage. It may identify permissions that have not been used for an extended period and recommend a more restrictive custom role. [01:34:46] [01:35:56]

---

## 15. External users should authenticate with their existing identity

For business-to-business collaboration, external users should generally not receive a completely separate username and password in the resource-owning organization. Instead, they can authenticate through their home organization or another supported identity provider. [02:06:34]

The two responsibilities are separate:

- The external organization authenticates the person.
- The resource-owning tenant decides what that person may access. [02:08:54]

The resource-owning tenant can still apply its own:

- Conditional Access policies
- MFA or authentication-strength requirements
- Device trust requirements
- Application and resource permissions
- Domain restrictions [02:08:54] [02:12:12]

External identities appear as objects in the local tenant, but the actual account remains owned by the external identity provider. [02:09:56]

Customer-facing applications are a different scenario from workforce collaboration. Customer identities should generally be managed through external/customer identity capabilities rather than being mixed into the organization’s workforce tenant. [02:14:21] [02:15:29]

---

## 16. Automate the identity lifecycle

Identity governance should cover the full lifecycle:

- Before a person joins
- When they start
- When they change roles
- When they need temporary access
- When they leave [02:18:50]

Access packages can bundle several types of access, such as:

- Group memberships
- Applications
- SharePoint sites
- Entra roles

Policies can define who may request access, how approval works, and how long access remains valid. [02:17:54]

Lifecycle workflows can automate tasks such as:

- Adding a new employee to groups
- Disabling an account
- Removing access
- Preparing resources before a user starts [02:18:50]

HR integrations and provisioning APIs can connect identity management to the organization’s source-of-truth HR system, reducing manual joiner, mover, and leaver processes. [01:56:21] [01:57:13]

---

## 17. Choose the right solution for legacy applications

Entra ID does not automatically replace every AD DS dependency. Legacy applications may still require domain protocols, LDAP, Kerberos, or domain joining. [02:24:03]

Two common approaches are:

### Entra Domain Services

This provides managed domain services in Azure for applications that require traditional domain capabilities but do not need direct access to on-premises domain controllers. [02:24:03]

### Extending on-premises AD DS into Azure

An organization can connect Azure networks to its existing domain controllers using options such as:

- Site-to-site VPN
- ExpressRoute
- Private network connectivity [02:26:20]

Azure virtual machines can then use the existing domain, DNS, and domain controllers. A JSON AD domain extension can automate the process of joining virtual machines to the domain, with sensitive configuration values preferably stored in Key Vault rather than plain configuration files. [02:27:26]

---

## Overall design principle

The module’s central message is that identity is the foundation for cloud security. A mature design should therefore:

1. Give every user, application, device, and workload a distinct identity. [04:42]
2. Authenticate identities with strong, preferably phishing-resistant methods. [01:45:24]
3. Authorize through groups, roles, and narrowly defined scopes. [01:15:52]
4. Use Conditional Access to evaluate context on every access request. [02:01:15]
5. Keep privileged access temporary and reviewable. [01:28:00]
6. Automate onboarding, role changes, and offboarding. [02:18:50]
7. Separate workforce, partner, and customer identity scenarios. [02:14:21]
8. Use managed identities and federation instead of storing workload secrets. [48





## video 7.The Line Between AD and Azure AD!-veľa vecí setup v platených verziách--- preto odporučam vrátiť sa k tomu neskôr.


## Deeper explanation

### 1. They solve different identity problems

**Active Directory (AD DS)** is primarily a directory and authentication system for a controlled corporate network. Devices join a domain, receive computer accounts, and establish shared secrets with domain controllers. Those relationships support Kerberos authentication and access to internal resources. [01:21–02:36]

**Azure AD** is a cloud identity provider and application-access broker. It is built to authenticate users to web and SaaS applications over HTTPS using modern protocols rather than to provide traditional domain services. [12:30–13:45]

### 2. The protocol difference is fundamental

Traditional AD communicates using protocols such as:

- Kerberos
- NTLM
- LDAP
- DNS-based domain discovery [01:21–02:36]

Azure AD instead focuses on:

- OAuth 2.0 for delegated authorization
- OpenID Connect for authentication
- SAML and WS-Federation for federation
- SCIM for user and group provisioning [13:10–14:17]

Therefore, Azure AD cannot simply replace a domain controller for a server that expects LDAP queries or Kerberos tickets. [14:17–14:50]

### 3. AD authenticates to the domain; Azure AD issues application tokens

In AD, a domain-joined computer has a corresponding computer object and shared secret. A domain controller can issue tokens that internal servers trust. [02:05–04:06]

In Azure AD, applications request tokens for particular resources. Access tokens are short-lived—about 60 minutes by default—while refresh tokens provide a longer-lived rolling session. Libraries such as MSAL handle token acquisition and renewal for applications. [15:30–16:25]

This means Azure AD authorization is generally **application- and resource-oriented**, rather than based on a user simply being inside the corporate network. [11:29–12:30]

### 4. Federation moves trust between organizations

Before cloud identity providers became common, companies often deployed AD FS or another federation service. The cloud application and the company’s federation service exchanged configuration, certificates, claims, and token-format information. [07:34–08:34]

During sign-in, the user was redirected to the company’s federation service, authenticated—often using Kerberos—and then sent back to the cloud application with a signed SAML token. [08:34–09:30]

Azure AD reduces this operational burden by providing many application integrations directly, so organizations do not need to deploy and maintain federation infrastructure for every application. [09:56–10:56] [16:25–18:41]

### 5. Azure AD is more than single sign-on

Its major value is not just “one login.” Azure AD can evaluate context before granting access, including:

- User, group, or role
- Application
- Location
- Device platform and compliance
- Sign-in or user risk
- MFA requirements
- Terms of use
- Session duration [23:38–26:50]

For example, access can be blocked, or the user can be required to perform MFA and use an Intune-compliant device. [26:24–27:16]

### 6. Security decisions can happen after the initial login

The presenter distinguishes the initial authentication from ongoing access decisions. Once a user receives a token, Azure AD’s Conditional Access policies and related security features help determine whether access should be allowed under current conditions. [36:44–37:09]

Identity Protection can detect signals such as leaked credentials, impossible travel, unusual locations, abnormal working times, and suspicious IP behavior. [25:32–25:57] [27:45–28:18]

### 7. Synchronization does not merge the directories

With Azure AD Connect or Cloud Sync, an on-premises AD user is synchronized to a corresponding but separate object in Azure AD. The identity appears consistent to the user, but the two directories remain different systems. [34:07–35:10]

The normal direction of authority is:

```text
Active Directory → synchronization → Azure AD → cloud applications
```

AD remains the source of truth in the normal hybrid design; Azure AD generally does not write ordinary directory objects back into AD. [44:56–45:30]

### 8. Seamless SSO is a special bridge, not proof that Azure AD is AD

Seamless sign-on can make a domain-connected user appear automatically authenticated to Azure AD. Behind the scenes, Azure AD uses a special computer account in AD to obtain a Kerberos token. [35:10–36:44]

This is a carefully limited integration mechanism. It does not mean Azure AD generally supports Kerberos, NTLM, or LDAP. [14:17–14:50] [35:38–36:44]

### 9. Device identity is also changing

A traditional AD-joined device depends on the corporate domain and commonly uses Group Policy and related management systems. [37:35–38:05]

An Azure AD–joined device authenticates directly with the cloud identity and can be managed through Intune, including policy, application deployment, and updates from Microsoft services. [37:35–38:33]

Hybrid join allows organizations to retain traditional AD relationships while also registering devices with Azure AD to use cloud-based controls. [39:04–40:02]

### 10. “AD in Azure” means something different

If an Azure virtual machine needs LDAP, Kerberos, or NTLM, there are two main approaches:

1. **Extend existing AD into Azure** using network connectivity, custom DNS, VPN, ExpressRoute, or domain controllers deployed as Azure virtual machines. [42:41–44:56]
2. **Use Azure AD Domain Services**, which provides Microsoft-managed domain controllers that replicate selected identities from Azure AD and support legacy protocols. [45:30–47:48]

Azure AD Domain Services is therefore the service that more closely resembles traditional AD domain functionality in Azure—not Azure AD itself. [46:04–46:40]

### Bottom line

- **AD DS:** domain controllers, internal servers, domain-joined machines, Kerberos, NTLM, LDAP, and Group Policy. [03:06–04:06]
- **Azure AD:** cloud identities, SaaS applications, modern authentication, tokens, SSO, Conditional Access, MFA, and external identities. [13:10–14:17] [21:36–27:16]
- **Hybrid architecture:** keep AD for legacy and on-premises requirements, synchronize identities to Azure AD, and use Azure AD for cloud access and modern security controls. [33:08–35:10] [48:19–49:20]
