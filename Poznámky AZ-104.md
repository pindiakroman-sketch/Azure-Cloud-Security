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


## 8-video. What are Azure AD External Identities?

## Deeper explanation

### 1. “External Identities” is primarily a product grouping

External Identities is not a completely new directory type replacing B2B or B2C. It is an umbrella that brings the two scenarios under one product family: **B2B collaboration** and **B2C customer identity**. [07:35–08:13]

The important distinction is where the external users live:

- **B2B:** users become guest objects in the organization’s normal Azure AD tenant. [01:31–02:09]
- **B2C:** customers use a separate Azure AD B2C directory rather than being placed in the organization’s main tenant. [04:16–04:45]

### 2. B2B is for known collaborators; B2C is for customers

B2B is intended for partners, vendors, contractors, or other people an organization collaborates with. They may authenticate using Azure AD, Microsoft accounts, Google, federation, or one-time passcodes. [00:54–01:31]

B2C is intended for an application’s customer population. Customers can use numerous social identity providers or create local accounts in the B2C directory. [04:45–05:19]

A useful architectural rule is:

> If the person needs to be treated like a guest in your organization, think B2B. If the person is simply a customer of your application, think B2C. [04:16–04:45]

### 3. The new B2B features reduce dependence on invitation-based onboarding

Traditional B2B onboarding is centered on sending an invitation to an email address and having the recipient redeem it. [01:31–02:09]

External Identities adds **guest self-service sign-up through user flows**, allowing an external person to start onboarding through an application rather than receiving a direct invitation. [08:46–09:15]

This is especially important for identity providers such as Facebook: Facebook cannot simply be invited in the same way as an email-based identity, so the sign-up must occur through a configured application and user flow. [10:24–11:30]

### 4. Facebook is added to regular B2B, but with a limitation

Facebook becomes an available identity provider for B2B users. [10:24–12:05]

However, it is not a general invitation mechanism. The organization must:

1. Create and configure a Facebook developer application. [12:05–12:32]
2. Add the Facebook application ID and secret to Azure AD. [12:05–12:32]
3. Enable self-service sign-up through a custom application and user flow. [11:02–11:30]

After sign-up, the user is still represented as a normal guest in the organization’s Azure AD tenant, with Facebook recorded as the identity issuer and self-service sign-up recorded as the creation method. [12:32–13:03]

### 5. User flows are the mechanism that ties the experience together

A user flow determines:

- Which identity providers are available, such as Google, Facebook, or Microsoft accounts. [16:23–16:57]
- Which built-in attributes the user must provide. [16:23–16:57]
- Which custom attributes should be collected during registration. [16:57–17:28]
- How the registration page is ordered and presented. [17:28–17:57]

For example, the demonstration collects a user’s name, city, and shirt size, then presents shirt size as a single-select radio control rather than a free-text field. [17:28–17:57]

The user flow is then associated with a registered application, so the sign-up experience is launched in the context of that application. [18:26–19:34]

### 6. Custom attributes make B2B identities more application-aware

External Identities allows administrators to define custom user attributes, such as a shirt size or another application-specific value. [13:03–14:10]

These values are stored as extension attributes on the automatically created Azure AD application and can be retrieved through Microsoft Graph. [14:10–15:53]

This means the external identity can carry more than authentication information; it can also contain data used by the application during authorization or personalization. [13:40–15:53]

The page does not describe a complete automatic provisioning workflow after sign-up. It notes that dynamic groups could potentially be used, but there is no built-in flow that automatically adds users to groups or provisions all related resources. [23:48–24:09]

### 7. The licensing model can change significantly

Historically, Azure AD guest access to premium capabilities followed a ratio model: one licensed user could cover five guest users. [02:09–02:44]

External Identities can instead use a **monthly active user** billing model by linking the Azure AD tenant to an Azure subscription. [24:38–25:45]

Under that model:

- The first 50,000 monthly active users are free. [06:54–07:35]
- Billing is based on users who authenticate during the month, rather than simply the number of directory objects. [06:25–06:54]
- MFA usage is billed separately. [06:54–07:35]
- Guests inherit the highest Azure AD licensing level available in the tenant, such as P1 or P2, rather than requiring individual guest licenses. [26:18–27:12]

This can be valuable for organizations with many occasional external users, but the page emphasizes that MFA charges remain additional. [26:18–26:48]

### 8. The practical decision is still B2B versus B2C

Use the enhanced B2B-oriented External Identities capabilities when external users are **partners or collaborators** who need access to resources in the organization’s tenant. [03:45–04:16]

Use B2C when users are **customers**, should remain outside the organization’s primary Azure AD tenant, or when the application needs extensive branding, onboarding customization, local accounts, and a large range of social identity providers. [04:16–05:55]

The central takeaway is that External Identities unifies the branding and management model, while the underlying architectural distinction remains: **B2B extends access into your tenant; B2C provides customer identity for applications in a separate directory.** [27:12–28:19]

Azure

## Azure AD Administrative Units Overview video.9


* **Administrative Unit (AU)** = logické rozdelenie používateľov, skupín alebo zariadení.
* Hlavný účel je **delegovaná administrácia**.
* Napríklad firma má 3 regióny → vytvoríš AU `Slovakia`, `Germany`, `France`.
* Admin pre Slovensko môže dostať napr. **User Administrator** iba v scope `Slovakia`, takže nemá rovnaké oprávnenia nad celým tenantom. ([Microsoft Learn][1])
* AU teda súvisí priamo s **RBAC, least privilege a security** – preto je to relevantné aj pre cloud security. Microsoft ich dokonca uvádza ako mechanizmus pre delegated administration a izoláciu. ([Microsoft Learn][2])
* V roku 2026 sa stále dajú spravovať cez **Entra admin center, PowerShell a Microsoft Graph**. ([Microsoft Learn][3])
* Novšie dokumenty Microsoftu z roku 2026 ich stále aktívne dokumentujú, takže nejde o nejakú zastaranú Azure AD funkciu. ([Microsoft Learn][4])



Stačí, aby si dokonale chápal:

> **Administrative Unit = časť Entra tenantu + scoped admin permissions.**

A vedel rozdiel:

**Group** → organizovanie/prístup používateľov
**Administrative Unit** → **obmedzenie rozsahu administrátorských oprávnení**

- **Administrative units (AUs) provide scoped delegation in Azure AD.** They let administrators assign roles over a subset of users or groups—such as a department or branch—instead of the entire tenant. [02:20–04:40]
- **They address Azure AD’s otherwise flat structure.** Without AUs, roles such as User Administrator generally apply across the whole Azure AD instance. [00:37–02:20]
- **Users can belong to multiple AUs, but AUs cannot be nested.** [03:31–04:07]
- **Only Global Administrators or Privileged Role Administrators can create AUs.** [02:55–03:31]
- **Delegated administrators need an Azure AD Premium P1-or-higher license; AU members do not need additional licensing and may use the free tier.** [04:40–05:22]
- **Adding a group to an AU controls only the group object—not its members.** The delegated administrator can manage the group’s properties and membership, but cannot manage users merely because they belong to that group. [07:51–09:23]
- **This restriction is a security safeguard** that prevents administrators from escalating privileges by adding users to a group they control. [08:24–09:23]
- **Available delegated roles include** Authentication Administrator, Groups Administrator, Helpdesk Administrator, License Administrator, Password Administrator, and User Administrator. [10:47–11:17]
- **AUs support bulk management** through the portal, CSV files, PowerShell, scripting, and REST APIs. [09:47–10:17]
- **The feature applies to regular Azure AD, not Azure AD B2C**, and includes a separate “My Staff” portal for delegated user-management tasks. [04:40–05:22] [07:22–07:51]

Toto je presne ten typ veci, ktorý sa ti **oplatí vedieť na AZ-104/AZ-500**, ale nie je to téma, na ktorej by som trávil veľa času oproti napr. **RBAC, Entra ID, Conditional Access, networking, NSG, private endpoints, Azure Policy, Defender for Cloud a Key Vault**.

## Microsoft Azure Managed Identity Deep Dive video.10

# Managed identities: deep explanation and key takeaways

## 1. The problem managed identities solve

An application running inside an Azure resource—such as a VM, Function, or Web App—may need to access another resource, such as Storage or Key Vault. The target resource uses Azure RBAC to decide what an authenticated security principal is allowed to do. Therefore, the application needs an identity and an access token. [00:39] [01:18]

The traditional solution is to create an app registration and its corresponding service principal, then authenticate with either a client secret or certificate. The problem is that the application must store that credential somewhere and handle its expiration, rotation, protection, and deployment. [02:28] [08:44]

Even storing the credential in Key Vault does not fully solve the initial problem: the application must first authenticate to Key Vault in order to retrieve the credential. This creates the “chicken and egg” problem managed identities are designed to avoid. [01:59]

---

## 2. What a managed identity actually is

A managed identity is an Azure-managed identity that appears in Azure AD as a **service principal**. Because it is a service principal, it can receive RBAC role assignments on resources such as Storage accounts, Key Vaults, and other Azure services. [10:23] [11:46]

The important difference is that a managed identity is **not backed by an application registration**. It is managed by Azure’s managed identity resource provider rather than by the application owner directly. [22:19] [25:14]

Although a managed identity has an application ID/client ID-like value, the video explains that this value is randomly generated for consistency with the service-principal model; it does not correspond to a real app registration. [23:56] [25:14]

Managed identities are also tenant-scoped: they exist only in the Azure AD tenant in which they were created and are not multi-tenant identities. [22:19]

---

## 3. System-assigned managed identity

A **system-assigned managed identity** is enabled directly on an Azure resource. Azure creates a service principal representing that resource. [10:23]

For example, if the resource is called `res1`, its system-assigned identity is associated with that resource and can be granted permissions on other resources. [11:01]

Its characteristics are:

- **One-to-one relationship:** one resource can have one system-assigned identity, and that identity belongs to one resource. [13:28]
- **Shared lifecycle:** deleting the Azure resource also deletes its system-assigned identity. [11:01]
- **No application-managed secret or certificate:** the application can request tokens without storing credentials itself. [11:01]
- **Resource-specific permissions:** you grant RBAC roles to that resource’s identity, such as Storage Blob Data Reader or a Key Vault role. [11:46]

### When to use it

Use a system-assigned identity when a single resource needs its own distinct permissions and the identity should naturally disappear with that resource. [46:06]

For example:

```text
Virtual machine A
  └── System-assigned identity A
        └── Storage Blob Data Reader on Storage account X
```

If the VM is deleted, its identity and its associated identity object are also removed. [11:01]

---

## 4. User-assigned managed identity

A **user-assigned managed identity** is created independently as its own Azure resource. It is not automatically tied to the lifecycle of any particular VM, Function, or Web App. [14:18] [17:07]

Its characteristics are:

- It can be assigned to multiple Azure resources. [15:58]
- A single resource can use multiple user-assigned identities. [15:58]
- It has an independent lifecycle. [17:07]
- Its RBAC permissions are defined once and reused by every authorized resource using that identity. [17:07]
- It can coexist with a system-assigned identity on the same resource. [18:13]

For example:

```text
User-assigned identity MI1
  ├── VM A
  ├── VM B
  └── Web App C

MI1
  ├── Storage Blob Data Reader
  └── Key Vault Secrets User
```

Every assigned resource can obtain tokens as `MI1` and use the permissions granted to `MI1`. [17:07] [18:52]

### When to use it

User-assigned identities are particularly useful for a group or fleet of resources that need identical permissions—for example, a farm of web servers or middle-tier servers. Without one, you would need to create many system-assigned identities and repeat the same role assignments for each resource. [16:37] [17:07]

They are also useful when permissions should be prepared before the compute resource is created or when the identity should survive replacement of the resource. [46:33]

---

## 5. System-assigned versus user-assigned

| Characteristic | System-assigned | User-assigned |
|---|---|---|
| Created by | Enabling identity on a resource [10:23] | Creating a separate managed identity resource [14:18] |
| Relationship | One identity to one resource [13:28] | One identity can be assigned to many resources [15:58] |
| Resource can use multiple identities | No additional system-assigned identity, but can also use user-assigned identities [18:13] | Yes, multiple user-assigned identities are possible [15:58] |
| Lifecycle | Tied to the resource [11:01] | Independent lifecycle [17:07] |
| Best fit | One resource with its own permissions [46:06] | Many resources sharing the same permissions [46:06] |
| Permissions | Assigned to the identity [11:46] | Assigned once and reused by assigned resources [17:07] |

A resource may have both a system-assigned identity and one or more user-assigned identities. [18:13]

---

## 6. How authorization works

Managed identity provides **authentication**, not automatic authorization. The identity still needs an appropriate RBAC role assignment on the target resource. [01:18] [11:46]

The general process is:

1. Enable or create the managed identity. [10:23] [14:18]
2. Grant that identity an appropriate role on the target resource. [20:04]
3. The application requests an access token as that identity. [35:52]
4. The application presents the token to the target Azure service. [37:43]
5. The target service evaluates the identity’s RBAC permissions. [20:43]

For example, the video grants a VM’s identity the **Storage Blob Data Reader** role and then successfully copies a file from Blob Storage using the VM’s current identity. [30:13] [31:23]

The same pattern is demonstrated with Key Vault: the VM’s system-assigned identity can read one secret because it has permission for that secret, but it cannot read another secret for which it has no permission. [33:27] [34:10] [38:13]

This demonstrates that merely having a managed identity does not grant broad access. Permissions remain controlled by RBAC and scope. [20:43] [38:13]

---

## 7. How an application obtains a token

The application does not need to know a client secret or certificate. It requests a token through the mechanism exposed by its hosting resource. [27:38] [37:43]

For a VM, the flow uses the **Instance Metadata Service** at the link-local address `169.254.169.254`. [35:52] [41:24]

Conceptually, the flow is:

```text
Application
   │ requests an access token
   ▼
Instance Metadata Service
   │ asks for the resource identity
   ▼
Managed Identity Resource Provider
   │ supplies the service-principal identity and certificate material
   ▼
Azure AD
   │ authenticates the managed identity and issues a token
   ▼
Instance Metadata Service
   │ returns the token
   ▼
Application
```

The certificate used behind the scenes is issued and periodically rolled by the managed identity resource provider. The application does not manage that certificate. [26:01] [26:37]

Other Azure services use different endpoints or mechanisms—for example, Functions and Web Apps expose their own way to request tokens—but the overall pattern is similar. [41:24] [41:55]

---

## 8. Choosing between identities at runtime

If a resource has a system-assigned identity, requesting a token without specifying an identity uses that system-assigned identity by default. [28:26]

The video describes the following behavior:

- **System-assigned identity exists:** it is selected by default. [28:26]
- **No system-assigned identity and exactly one user-assigned identity:** that user-assigned identity is selected. [28:26]
- **No system-assigned identity and multiple user-assigned identities:** the application must specify which identity to use; otherwise token acquisition fails because Azure cannot choose one automatically. [28:26]

When explicitly selecting a user-assigned identity, the application needs identifying information such as that identity’s client ID. [39:27] [39:57]

This is important when a resource has several identities with different permissions. For example, one identity may read Storage blobs while another may read Key Vault secrets. [38:48] [39:57]

---

## 9. Key Vault’s role in the architecture

Managed identities are preferable when the target Azure service supports Azure AD authentication and RBAC. [12:53]

However, some external or legacy systems may still require a password, signature, API key, or certificate. In that situation, Key Vault can be used as a secondary credential store:

```text
Application
   │ authenticates using managed identity
   ▼
Key Vault
   │ returns a protected secret or certificate
   ▼
Application
   │ uses that credential with a system that lacks Azure AD/RBAC support
```

The managed identity solves authentication to Key Vault, while Key Vault protects the credential needed by the downstream system. [32:11] [32:57]

This is different from using Key Vault to bootstrap the application’s own Azure authentication, which would recreate the original credential-storage problem. [01:59]

---

## 10. Security benefits

Managed identities improve security because:

- Applications do not need embedded client secrets. [08:44]
- Applications do not need to store certificates for Azure authentication. [08:44]
- Credential rotation is handled by Azure’s managed identity infrastructure. [26:01] [26:37]
- Access is governed through Azure RBAC rather than manually distributed credentials. [11:46]
- A compromised application receives only the permissions granted to its selected identity. [33:27] [38:13]

The identity should still be given the minimum role and scope necessary. The video shows that different identities can have different permissions and that access to one Key Vault secret does not imply access to another. [33:27] [38:13]

---

## 11. Reliability benefits

The video presents managed identity as more than a security convenience; it also improves resilience. [45:04]

Managed identity uses a regional version of Azure’s security token service, reducing dependence on global gateways and services. [43:31] [43:57]

The access token is described as having a default lifetime of approximately 24 hours, with proactive renewal around the halfway point. This means the identity service attempts to refresh the token before it becomes near-expiry. [43:57] [44:33]

The practical result is that a short Azure AD disruption may not immediately affect the application, because it can continue using a still-valid token. [44:33] [45:04]

The video contrasts this with a short-lived one-hour token flow, where a longer authentication outage could cause more immediate failures. [44:33]

---

## 12. Managed identity versus a normal service principal

A normal service principal generally comes from an application registration. The application registration is the global application definition, while the service principal is its tenant-specific instance. [03:40] [05:47]

A managed identity is also represented as a service principal, but:

- It is not tied to an application registration. [22:19]
- It is managed by Azure. [23:56] [25:14]
- Its credentials are handled and rotated by the managed identity resource provider. [26:01] [26:37]
- It is associated with Azure resources rather than being independently authenticated using an application secret or certificate. [10:23] [11:46]

So the useful mental model is:

```text
Normal application:
App registration → Service principal → Secret/certificate → Token

Managed identity:
Azure resource → Managed identity service principal → Azure-managed credential → Token
```

---

## 13. Practical decision guide

Use a **system-assigned identity** when:

- One Azure resource needs access to other Azure resources. [46:06]
- The identity should be deleted along with the resource. [11:01]
- There is no need to share the identity with other resources. [13:28]

Use a **user-assigned identity** when:

- Multiple resources need the same permissions. [16:37]
- You want to define RBAC permissions once and reuse them. [17:07]
- The identity must have an independent lifecycle. [17:07]
- You want to provision permissions before attaching the identity to a resource. [46:33]
- A resource must choose between multiple permission sets. [38:48] [39:57]

Use **Key Vault with managed identity** when:

- The application must access a password, API key, certificate, or other secret. [32:11]
- The downstream service does not support Azure AD/RBAC authentication. [47:56]

## Bottom line

Managed identity lets an Azure-hosted application obtain Azure access tokens without managing its own Azure credentials. System-assigned identities are resource-specific and lifecycle-bound; user-assigned identities are reusable and independently managed. After assigning the correct RBAC roles, the application can securely access supported Azure services such as Storage and Key Vault, while Azure handles the underlying credentials and token renewal. [47:29]


## Azure Master Class v3 - Part 3 - Governance-video 11
Azure Master Class v3 - Part 3 - Governance - YouTube
https://www.youtube.com/watch?v=t-i4XrygWCc

Here are the comprehensive, deeply technical, and structured study notes in English, directly mapped to the lifecycle and logical flow of the architectural training document you provided.
------------------------------
## 📑 ADVANCED ARCHITECTURAL NOTES: AZURE GOVERNANCE## 1. Paradigm Shift & Requirement Analysis## 🔄 On-Premises vs. Cloud Governance Models

* On-Premises Infrastructure: An operations team acts as a human proxy between the application owner and physical deployment. They manually interpret organizational guidelines via emails, forms, or calls before provisioning infrastructure.
* Cloud Architecture: Application owners interact directly with the Cloud API/Control Plane via the Azure Portal, CLI, Infrastructure as Code (IaC), or CI/CD pipelines.
* The Governance Mandate: Because there is no human standing in the chain of deployment, governance must be enforced programmatically as automated guardrails directly embedded within the control plane. This mitigates risks concerning data exfiltration, target infiltration, unexpected service interruptions, and catastrophic financial overhead.

## ⚖️ Compliance Tracking Tools

* Shared Responsibility Model: As you move from IaaS to PaaS and SaaS, customer-managed responsibilities decrease, but compliance configuration, identities, and data always remain the customer's burden.
* Microsoft Service Trust Portal: The central repository for downloading regulatory compliance reports, independent third-party audit attestations (e.g., ISO, PCI DSS, FedRAMP), and regional compliance deep dives.
* Microsoft Purview Compliance Manager: A operational portal used to track real-time compliance posture via an aggregated Compliance Score. It categorizes points based on the Shared Responsibility Model: actions managed by Microsoft vs. actions managed by the customer. It functions as an internal audit ledger where you can assign owners, modify implementation statuses, track testing dates, and attach verification notes.

------------------------------
## 2. The Core Azure Hierarchical constructs
Azure Governance operates on a strict Top-Down Inherited Model. Any policy, role assignment, or resource lock applied at a higher scope automatically cascades down through all child entities.

[Microsoft Entra Tenant]
          │
  [Root Management Group]
          │
  [Management Groups] (Up to 6 levels deep below Root)
          │
    [Subscriptions]
          │
   [Resource Groups]
          │
      [Resources]

## 🏢 Management Groups (MGs)

* Definition: Logical containers designed to apply baseline governance, access control, and policies at scale across multiple subscriptions.
* Architectural Boundaries:
* Supports up to 10,000 management groups per Entra ID tenant.
   * The custom hierarchy can extend up to 6 levels deep (excluding the Root Management Group).
   * A Management Group or Subscription can have exactly one parent.
* The Root Management Group: Dynamically generated upon tenant creation. It cannot be deleted or relocated, but its display name can be modified. By default, all newly created subscriptions trust this root.
* Break-Glass Privilege Elevation: A Global Administrator in Microsoft Entra ID can toggle "Access management for Azure resources" to Yes. This injects a special inherited User Access Administrator role assignment at the Root Management Group level. This is used exclusively as an emergency operational backdoor to regain control of subscriptions if local owners leave the organization.
* Design Strategy: Organize custom management group levels logically by Geography (regional compliance laws), Business Units (separate accounting/operational pillars), or Environments (Non-Production vs. Production).

## 💳 Subscriptions

* Definition: The fundamental unit for billing aggregation, security scoping, and resource management.
* Modern Architectural Pattern: The traditional guidance to minimize subscriptions is obsolete. Current best practices dictate using individual subscriptions per workload unit. Because subscriptions act as an isolation barrier for components like Virtual Networks, separating workloads prevents limit exhaustion and resolves service health alert ambiguity (e.g., distinguishing which of 20 apps triggered a localized health event).
* Tenant Alignment Risks: Moving an active subscription to a different Entra ID tenant strips away all local RBAC role assignments, disrupts Managed Identities, and breaks data plane access. It must be avoided in production environments.
* Tenant Policy Controls: Entra administrators can configure advanced subscription joining/leaving rules under "Manage Policies". This can lock down the tenant to permit no one to add or remove subscriptions except explicitly exempted break-glass users.

## 📦 Resource Groups (RGs)

* Definition: Flat, non-nested lifecycle boundaries within a single subscription.
* Operational Constraints:
* Every resource must belong to exactly one Resource Group.
   * Resource Groups cannot be nested inside one another.
   * They cannot be renamed. Remediation requires creating a new target RG and migrating components manually.
   * The Metadata Region: The region specified during RG creation dictates solely where the resource group's metadata is stored. Components placed inside that group can safely reside in entirely different geographical regions.
   * No Network or Functional Isolation: An RG is not a communication barrier. For example, an AKS cluster in App-RG can natively connect to a Core-VNet residing inside a specialized Network-RG managed by a dedicated network team.

------------------------------
## 3. Naming and Tagging Strategy## 🏷️ Naming Standards

* Guided by the Cloud Adoption Framework (CAF), organizations must enforce uniform naming schemas.
* Standard Component Layout: [Resource Type]-[Workload/Application Name]-[Environment]-[Azure Region]-[Instance Number]. This ensures seamless readability across hybrid on-premises and multi-cloud nodes.

## 🏷️ Tagging Architecture

* Tags are metadata pairs comprised of a Key and a Value.
* Supported across resources, resource groups, and subscriptions (not supported on Management Groups).
* Technical Limits: Typically capped at 50 tags per resource (a few legacy skus limit to 15). Tag keys are capped at 512 characters; values are capped at 256 characters.
* The Non-Inheritance Rule: Tags are not naturally inherited by child resources from a parent subscription or resource group. Dedi-inheritance must be programmatically forced via Azure Policy (e.g., using "inherit from resource group if missing" policy rules).
* Advanced Rich Content: To bypass the physical tag count limit, a tag value can contain a minified JSON document. Programmatic code or automation systems can then extract deep telemetry strings such as complex firewall configurations or anti-malware versions.

------------------------------
## 4. Identity and Access Control (RBAC & ABAC)## 🛡️ Role-Based Access Control (RBAC)

* Core Rule: Grant role permissions exclusively to groups, never to individual users, to maintain scale and control role assignment quotas (capped at 4,000 assignments per subscription).
* No Inheritance Blocking: You cannot block inherited permissions from a higher scope. If an identity is a subscription owner, an app owner cannot remove that access at the resource group level; doing so would compromise enterprise governance.
* Control Plane vs. Data Plane Scoping:
* Control Plane (ARM): Handled by standard roles like Owner, Contributor, and Reader. Contributor can change resource properties but cannot manipulate access control or permissions.
   * Data Plane: Modern services (such as Azure Storage or Cosmos DB) expose inner data properties via Entra ID data roles (e.g., Storage Blob Data Contributor). This eliminates the need for hardcoded Access Keys, enabling secure auditing and direct access for Managed Identities.
* Custom Roles: Leveraged when built-in roles violate the Principle of Least Privilege. Limited to 5,000 per tenant. Configured precisely using JSON blocks defining Actions, NotActions, DataActions, and NotDataActions. Broadly scoped custom roles should use high-level AssignableScopes (like Management Groups) to avoid token duplication across individual resource groups.

## 🔐 Privileged Identity Management (PIM)

* Natively integrated within the Azure Portal's role assignment engine.
* Rather than provisioning a user with permanent active roles, PIM configures roles as Eligible. Users must actively elevate their accounts on-demand, satisfy justification rules, and clear timed constraints. Note: Requires an Entra ID P2 license feature set.

## 🧩 Attribute-Based Access Control (ABAC)

* ABAC allows you to inject conditional expressions onto an active RBAC assignment, preventing role inflation.
* The "Clark Kent" Enterprise Use Case:
1. A security group (Justice League) is assigned the Storage Blob Data Reader role on a central Storage Account.
   2. An ABAC conditional expression is appended: The authorization engine verifies that the requester's Custom Security Attribute matches the target file's explicit Blob Index Tag.
   3. Clark Kent holds a custom Entra ID attribute of primary project = Alpha. When he queries the storage container, files tagged with Alpha evaluate successfully and display. Files tagged with Bravo return a hard permission block, despite residing within the exact same blob container.
* Environmental Modifiers: Conditions can also evaluate request contextual parameters, including incoming request private subnets, private endpoints, or explicit UTC time-windows.

------------------------------
## 5. Guardrails via Azure Policy
Azure Policy acts as an intercept engine inside the Azure Resource Manager (ARM) pipeline, inspecting every lifecycle request against specific resource properties.
## 🛠️ Evaluation Engine Mechanics

* Uses Aliases to map internal JSON properties of resource configurations to policy evaluation rules.
* Follows a predictable logical path: IF a resource matches targeted types/conditions, THEN execute a designated Effect.
* Implementation Blueprint: Always begin by assigning custom policies with the Audit effect. Evaluate the compliance footprint and coordinate change-management windows with development teams before shifting the rule to an aggressive Deny enforcement model.

## ⚡ Core Policy Effects

* Audit: Emits a compliance flag in dashboard reports but permits resource deployment.
* Deny: Intercepts the configuration request at the ARM layer and blocks execution, returning a 403 Forbidden API code to the user or pipeline.
* Append / Modify: Alters or adds missing fields, attributes, or tag pairs during execution.
* DeployIfNotExists (DINE): Executes an embedded ARM/Bicep template if a required child component is missing after deployment. Commonly used to automatically inject Log Analytics workspace diagnostic extensions or monitoring agents onto newly provisioned infrastructure.

## 📋 Initiatives, Exclusions, and Exemptions

* Initiatives: Regulatory or organizational wrappers that bundle hundreds of individual policy definitions into a single point of assignment (e.g., the built-in PCI DSS v4 initiative contains 719 policies).
* Not Scopes (Exclusions): Defined directly during the initial assignment of a policy or initiative. It explicitly removes sub-scopes (such as a legacy development resource group) from the policy's evaluation tree. Max 400 per assignment.
* Exemptions: Used on an active deployment to handle exceptional business cases. Rather than changing the overarching policy assignment, an explicit Waiver or Mitigated exception is applied to a specific resource. The component is marked as exempt and will no longer distort the parent initiative's overall compliance percentage. Requires administrative permissions at the initial policy assignment scope.

------------------------------
## 6. Financial Operations (FinOps) & Budget Management## 📈 Cost Analytics & Allocation

* Machine Learning Smart Views: Automatically process tenant consumption patterns to spot deviations and unexpected daily spend anomalies (e.g., a sudden 72% run-rate spike).
* Cost Allocation Architecture: Solves the challenge of shared common operational resources (e.g., an ExpressRoute circuit or active directory domain controller cluster). FinOps teams can designate a shared resource group as a Source, and distribute its expenses across targeted business unit subscriptions as an Allocated Cost. This distribution can be executed via an even split, a fixed custom percentage, or a proportional split based on the target scopes' compute, storage, or network consumption profiles.

## 💰 Budget Automation

* Budgets can be applied at any scope and narrowed down via custom tag filters.
* Thresholds can evaluate Actual or Forecasted spend trajectories. This lets you trigger reactive steps before an over-budget event actually happens.
* Action Groups: When a financial threshold is breached, the budget engine moves beyond simple email alerts. It passes telemetry payloads to automated Action Groups capable of firing Webhooks, triggering Azure Functions, invoking Logic Apps, or instantly opening operational tickets in an external ITSM system.

------------------------------
## 7. Compute Financial optimization & Capacity Guardrails

| Financial Instrument | Flexibility Profile | Execution Mechanics |
|---|---|---|
| Azure Reservations | Low Flexibility (Highly Specific) | A 1- or 3-year financial commitment tied to a hyper-specific VM family instance size (e.g., D2 v5) within a designated geographic region (e.g., West US 3). The billing engine applies deep discounts every hour. Unused hours cannot be recovered. |
| Azure Compute Savings Plan | High Flexibility (Broad Coverage) | A 1- or 3-year commitment based on a fixed hourly monetary spend. It automatically covers multiple compute engines (including VMs, Azure Container Instances, Dedicated Hosts, and Container Apps) across any global region. It provides lower baseline discounts than reservations but handles dynamic architecture shifts seamlessly. |
| Azure Hybrid Benefit (AHUB) | Licensing Optimization | Allows organizations to bring pre-existing on-premises Windows Server or SQL Server licenses into Azure. This strips the operating system licensing fee out of the consumption matrix, reducing the billing charge down to the raw compute hardware rate. |

⚠️ CRITICAL ARCHITECTURAL WARNING: An Azure Reservation does NOT guarantee or reserve physical hardware capacity inside an Azure Datacenter. It is strictly an accounting mechanism. During regional high-demand anomalies, a VM can still throw a Capacity Failure error on startup even if it is fully backed by a valid reservation.
## 🔒 On-Demand Capacity Reservations

* To secure a legally backed SLA guarantee that physical compute capacity will always be available for critical workloads, you must deploy an On-Demand Capacity Reservation.
* You are billed for the hardware slot the moment the capacity reservation is initialized, regardless of whether a VM is actively deployed inside it.
* The FinOps Pattern: Layer an On-Demand Capacity Reservation directly over a hyper-specific Azure Billing Reservation. This strategy locks in the maximum possible pricing discount while simultaneously ensuring the physical compute hardware is physically allocated to you at the hypervisor layer.

------------------------------
## 8. Enterprise Observability Nastavenia## 🔒 Control Plane Resource Locks

* Implemented at the ARM layer; has zero visibility or enforcement power over internal Data Plane actions.
* CanNotDelete: Allows configurations to be modified or updated but blocks any API command to drop or delete the resource block.
* ReadOnly: Halts any configuration state change or deletion request.
* Operational Catch: Placing a CanNotDelete lock on a Storage Account prevents an administrator from accidentally dropping the Azure Storage resource from the portal. However, a database user or application using valid connection strings can still completely purge files, drop rows, and wipe data structures from inside that storage plane.

## 🥞 Deployment Stacks

* Fully replaces the legacy Azure Blueprints engine.
* Manages an active collection of resources across multiple resource groups or subscriptions as a cohesive lifecycle boundary.
* Built using native template formats (such as Bicep or ARM) but deployed via specialized stack arguments (az stack group).
* Native Deny Assignments: Includes granular lock settings that override traditional subscription Owner permissions. These block unauthorized out-of-band updates and can cascade down to child structures while explicitly exempting automation or break-glass identities.
* When a stack is deleted, it offers a cleanup mechanism: it can either permanently purge every managed resource across all subscriptions or cleanly detach them as unmanaged components without interrupting their runtime states.

## 🔍 Azure Resource Graph (ARG)

* A high-performance lookup system operating on a separate, optimized tracking database that exposes current Azure Control Plane states.
* Programmed via the Kusto Query Language (KQL).
* Bypasses traditional ARM throttling limits (which are capped around 12,000 reads per hour). It handles multi-tenant, complex queries (e.g., counting resources across all enterprise subscriptions) in milliseconds while validating user access rights.

## 🕒 Change Analysis

* Built directly on the Azure Resource Graph engine to track configuration drift across a rolling 14-day history window.
* Exposes the precise Change Actor, the client footprint utilized (e.g., Azure Portal vs. CLI), and the exact API transaction invoked.
* Provides an interactive "Before/After" side-by-side JSON property diff. This allows operators to quickly pinpoint why a service failed by isolating exactly what changed at a specific timestamp.

## 💡 Azure Advisor

* An automated scanning system that evaluates cloud infrastructure across five pillars: Cost, Security, Reliability, Operational Excellence, and Performance.
* Scores your tenant (Advisor Score) and flags actionable optimizations, such as right-sizing idle VMs or restructuring local storage accounts to Zone-Redundant Storage (ZRS).
* Supports automated digest distribution schedules and maps directly into Action Groups to automatically alert operations teams or open tickets when new optimization risks are found.

------------------------------
To proceed with tailoring these architectural notes to your specific project needs, please let me know:

* Do you want to see a complete JSON template example for an advanced Azure Policy definition?
* Do you need a Bicep template example illustrating how to deploy a Deployment Stack with native Deny Settings?


## Azure Master Class v3 - Part 4 - Resiliency-video 13

Jasné — teraz **to isté ako predtým, ale celé v angličtine**. Spravím to **prakticky, jednoducho a tak, aby si rozumel, čo by si reálne riešil v Azure**, nie len definície na skúšku.

# Azure Resiliency – Practical Notes

## 1. What does resiliency mean?

**Resiliency means that your application can continue working, or recover quickly, when something fails.**

In Azure, failures can happen at different levels:

* a VM can fail
* a physical server can fail
* a rack can fail
* an Availability Zone can fail
* an entire Azure region can fail
* data can be accidentally deleted
* an application update can break the system

The goal is not necessarily to prevent every failure.

The goal is:

> **Assume that failures will happen and design the system so that the business can continue operating.**

The module focuses on disaster recovery, Availability Zones, redundancy, replication, multi-region architectures, backups, and protection against destructive actions. 

---

# 2. Disaster Recovery: Planned vs Unplanned

## Planned failover

You know that something bad may happen.

Example:

> A major storm is approaching the region where your datacenter or infrastructure is located.

You can move your workload to another location **before the disaster happens**.

Because you have time to prepare:

* data can be replicated
* services can be shut down cleanly
* failover can be controlled
* data loss should be minimal or zero

### Practical example

You have an application running in:

```text
West Europe
```

You know there will be a major planned maintenance or a serious external risk.

You manually fail over the application to:

```text
North Europe
```

Users are redirected to the secondary environment.

---

## Unplanned failover

Something suddenly fails.

Example:

```text
Azure region becomes unavailable
```

You did not have time to prepare.

This can result in:

* data loss
* unexpected downtime
* longer recovery time

The important difference is:

> **In a planned failover, you control the switch. In an unplanned failover, the failure controls when you need to switch.**



---

# 3. Disaster Recovery must be tested

Having a DR plan on paper is not enough.

Imagine this:

```text
Production
    ↓
Everything works
```

You have a secondary environment:

```text
Disaster Recovery Site
```

But you never test it.

Then one day production fails.

You try to fail over and discover:

```text
❌ Database replication is broken
❌ DNS configuration is wrong
❌ Application configuration is missing
❌ Required permissions do not exist
```

Now you are discovering problems during a real disaster.

That is exactly what you want to avoid.

### Better approach

Test the DR process regularly.

Some organizations even switch production between locations periodically.

Example:

```text
Month 1:
West Europe = Active

Month 2:
North Europe = Active
```

This gives you confidence that both environments actually work.

> **A Disaster Recovery plan that has never been tested is not a reliable Disaster Recovery plan.**

Also, the DR plan must change when production changes. If you add a new application, resource, or configuration to production, you must consider its impact on DR as part of change control. 

---

# 4. SLA – Don't look at one resource only

Imagine you have:

```text
Web Application
```

with:

```text
99% SLA
```

That sounds okay.

But your application also depends on:

```text
Web App
   ↓
Database
   ↓
Key Vault
   ↓
Load Balancer
   ↓
Microsoft Entra ID
```

Your application only works if the required dependencies are available.

This is called a **composite SLA**.

---

## AND relationship

Imagine:

```text
Web Tier = 99%
Database = 99%
```

Both must work.

So:

```text
0.99 × 0.99 = 0.9801
```

Overall availability:

```text
98.01%
```

Adding dependencies can actually reduce your overall SLA.

The practical lesson:

> **Every dependency matters.**

You cannot look only at the SLA of your main application. You must consider everything the application depends on. 

---

# 5. OR relationship – redundancy improves availability

Now imagine:

```text
VM 1 = 99%
VM 2 = 99%
```

But your application only needs **one VM to be available**.

Architecture:

```text
          ┌── VM 1 ──┐
Users ────┤          ├── Application
          └── VM 2 ──┘
```

If VM 1 fails:

```text
Users → VM 2
```

If VM 2 fails:

```text
Users → VM 1
```

Both VMs would need to fail at the same time for the service to become unavailable.

This is why redundancy improves resiliency.

The general principle is:

> **Avoid single points of failure.**

If one component fails and your entire application stops working, that component is a single point of failure. 

---

# 6. Don't build unnecessary complexity

More redundancy usually means:

```text
More resources
+
More complexity
+
More cost
```

So you should not automatically make everything highly redundant.

Instead ask:

> **What level of availability does the business actually need?**

For example:

### Internal test application

Maybe this is acceptable:

```text
Single region
Single instance
Backup available
```

### Online banking application

You may need:

```text
Multiple instances
Availability Zones
Load balancing
Multi-region architecture
Database replication
Automated failover
Backups
```

The architecture should match the business requirements and required SLA. 

---

# 7. Regional vs Zonal vs Zone-Redundant

This is very important in Azure.

## Regional resource

The resource exists somewhere inside an Azure region.

Example:

```text
West Europe
```

But you may not control which Availability Zone it is placed in.

Conceptually:

```text
West Europe

[Azure infrastructure]

Your resource is somewhere here
```

---

## Zonal resource

You explicitly choose an Availability Zone.

Example:

```text
West Europe

Availability Zone 1 → VM 1
Availability Zone 2 → VM 2
Availability Zone 3 → VM 3
```

You control where individual resources are placed.

---

## Zone-redundant resource

Azure distributes the resource across multiple Availability Zones.

Example:

```text
                Azure Region

      Zone 1        Zone 2        Zone 3
        │             │             │
      Instance      Instance      Instance
```

If one zone fails, the service can continue operating in another zone.

A single instance cannot provide real zone redundancy by itself—you need the architecture and instance placement to survive the loss of a zone. 

---

# 8. Practical example: Storage redundancy

Azure Storage can use different redundancy models.

For example:

### Locally Redundant Storage

Copies of data exist within a local infrastructure boundary.

Conceptually:

```text
Region
 └── Storage infrastructure
      ├── Copy 1
      ├── Copy 2
      └── Copy 3
```

### Zone-Redundant Storage

Copies are distributed across Availability Zones.

```text
Region

Zone 1 → Data Copy
Zone 2 → Data Copy
Zone 3 → Data Copy
```

This protects you against the failure of an individual Availability Zone. 

---

# 9. The weakest dependency can break your resilient architecture

Imagine this architecture:

```text
        Zone 1          Zone 2          Zone 3

        AKS             AKS             AKS
         │               │               │
         └─────── Network dependency ───┘
                        │
                   Single resource
```

Your AKS deployment may be highly resilient.

But if all instances depend on one non-redundant resource, that resource becomes a:

> **Single Point of Failure**

Example from the practical architecture discussion: a zone-redundant workload can still lose network connectivity if it relies on a dependency that exists only in one zone.

The lesson:

> **Your entire architecture must be designed at a consistent resiliency level.**

Do not build:

```text
Highly resilient application
        +
Single non-redundant dependency
```

because the weakest dependency can determine the resilience of the whole system. 

---

# 10. Synchronous vs Asynchronous Replication

## Synchronous replication

When data is written:

```text
Application
      ↓
Primary Database
      ↓
Replica
      ↓
Success returned
```

The system waits until both locations have the data before confirming success.

### Advantage

```text
Very low or no data loss
```

### Disadvantage

```text
Potentially slower performance
```

This approach is typically suitable where the replica is close enough to avoid excessive latency.

---

## Asynchronous replication

The primary system confirms the operation first:

```text
Application
      ↓
Primary Database
      ↓
Success returned
```

Replication happens afterwards:

```text
Primary Database
       ↓
Secondary Region
```

### Advantage

```text
Better performance
Long-distance replication is possible
```

### Disadvantage

If the primary suddenly fails before replication finishes:

```text
Possible data loss
```

A key practical point is that synchronous replication prioritizes consistency, while asynchronous replication accepts some possible data loss in exchange for lower latency and easier cross-region replication. 

---

# 11. Availability Zones vs Multiple Regions

These protect you against different types of failures.

## Availability Zones

```text
West Europe

Zone 1
Zone 2
Zone 3
```

Protect against failures affecting part of a region.

---

## Multiple Regions

```text
West Europe
      +
North Europe
```

Protect against a larger regional failure.

Example:

```text
                Global Users
                     │
             Traffic Management
                /          \
               /            \
       West Europe       North Europe
          Active            Standby
```

For stronger disaster recovery against regional outages, the architecture needs resources in more than one region. 

---

# 12. Active-Passive Architecture

Example:

```text
West Europe
   ACTIVE
      │
      │ Replication
      ▼
North Europe
   PASSIVE
```

Normally:

```text
Users → West Europe
```

If West Europe fails:

```text
Users → North Europe
```

### Advantages

* easier to manage
* simpler architecture
* easier data consistency

### Disadvantages

* secondary environment may sit mostly unused
* failover may take time
* you still need to keep the secondary environment ready

---

# 13. Active-Active Architecture

Both regions are actively serving users.

```text
                Users
                  │
          Global Load Balancing
              /           \
             /             \
     West Europe      North Europe
        ACTIVE            ACTIVE
```

Both regions process traffic.

### Advantages

* higher availability
* better geographic performance
* potentially faster recovery

### Disadvantages

* much more complex
* data synchronization is harder
* conflicts can happen if data is modified in multiple places

The choice between active-passive and active-active is strongly influenced by the application's data model and the complexity of replication. 

---

# 14. Global Azure services

Some Azure services are global rather than tied to one specific region.

Examples discussed include:

* Microsoft Entra ID
* Azure Front Door
* Azure Traffic Manager
* Azure DNS zones

These services handle certain aspects of global availability differently from ordinary regional resources.

This is important when designing your architecture because you need to understand:

> **Which resources are regional, which are zonal, and which are global.**



---

# 15. Application-level resiliency patterns

Resiliency is not only about Azure infrastructure.

Your application can also help itself survive failures.

## Retry logic

If a request fails temporarily:

```text
Request
   ↓
❌ Temporary failure
   ↓
Retry
   ↓
✅ Success
```

But retries must be controlled.

You don't want:

```text
Failure
 ↓
Retry × 1,000,000
```

because that could make the outage worse.

---

## Circuit Breaker

Imagine a backend service is failing repeatedly.

Instead of constantly sending requests:

```text
Application
     ↓
Broken Service
     ❌
     ❌
     ❌
```

The application detects repeated failures and temporarily stops sending requests.

```text
Application
     │
     X
Circuit Open
```

Later it can test whether the service has recovered.

---

## Bulkhead pattern

Separate parts of the application so one failure does not destroy everything.

Example:

```text
Payment System ❌

Customer Portal ✅
Product Search  ✅
```

The goal is to prevent one overloaded or failed component from causing a chain reaction throughout the entire application.

These are examples of client and application-side techniques that complement infrastructure redundancy. 

---

# 16. Backup protection: Assume an attacker can have permissions

A very important security concept.

Imagine an attacker compromises:

```text
Backup Administrator
```

If that administrator can:

```text
Delete backups
Disable protection
Change retention
```

the attacker could destroy your recovery capability.

So Azure can use additional protection mechanisms where critical operations require authorization involving another identity or privileged workflow.

Conceptually:

```text
Backup Admin
     │
     │ Requests critical action
     ▼
Additional protection / authorization
     │
     ▼
Critical operation allowed
```

This helps prevent one compromised administrator account from being enough to destroy the backup environment. 

---

# 17. Immutable backups

Immutable means:

> **Once the backup protection and retention are locked, the data cannot simply be deleted before the retention period expires.**

Conceptually:

```text
Backup Created
      │
      ▼
Immutable Lock
      │
      ▼
Cannot be deleted before retention expires
```

This is very useful against ransomware.

Even if someone gains high-level permissions, the goal is to prevent backups from being immediately destroyed.

But there is an important warning:

```text
Immutable + long retention
        =
More storage cost
```

And once certain settings are locked, they cannot simply be undone.

So:

> **Test the configuration before permanently locking immutability settings.**



---

# Practical Azure Resiliency Checklist

When designing an Azure workload, ask yourself:

### 1. What can fail?

```text
VM?
Zone?
Region?
Database?
Network?
Identity service?
Application update?
Human error?
Ransomware?
```

### 2. Do I have a single point of failure?

```text
One VM?
One database?
One zone?
One network dependency?
One administrator?
```

### 3. What level of availability does the business need?

```text
99%?
99.9%?
99.99%?
```

### 4. What happens if one Availability Zone fails?

```text
Does the application continue working?
```

### 5. What happens if the entire region fails?

```text
Can I fail over to another region?
```

### 6. How much data can I lose?

This determines your replication strategy.

```text
Near-zero data loss → synchronous / stronger consistency requirements

Some acceptable data loss → asynchronous replication may be acceptable
```

### 7. How quickly must the application recover?

This affects your:

* RTO
* automation
* failover architecture
* active-active vs active-passive design

### 8. Are backups protected?

Ask:

```text
Can one compromised admin delete everything?
```

### 9. Have we tested Disaster Recovery?

If not:

```text
You don't really know if it works.
```

---

# The Most Important Idea

The biggest lesson from this module is:

> **Resiliency is not something you add to one Azure resource. It is something you design across the entire architecture.**

You can have:

```text
3 Availability Zones
+
Multiple VMs
+
Load Balancer
+
Database Replication
```

But if everything depends on:

```text
ONE non-redundant component
```

then that component can still bring down the entire application.

Think of an Azure architecture as a chain:

```text
User
 ↓
DNS
 ↓
Load Balancer
 ↓
Application
 ↓
Database
 ↓
Storage
 ↓
Identity
```

**The resilience of the entire solution depends on how all of these components work together—not just on the strongest component.** 


Understanding Microsoft Azure Availability Zones! 14.video

## 1. What is an Azure Region?

**Region = a geographical area of Azure** that contains multiple physical facilities/data centers.

For example, you can choose:

> **East US**

Within a region, there are multiple physical environments that provide compute, storage, networking, and other resources.

Important:

**Region ≠ a single data center.**

---

# 2. What is an Availability Zone?

**Availability Zone (AZ) = an isolated physical environment/data center within a single Azure region.**

The main purpose of an AZ is:

> **ISOLATION – separation from other zones.**

Azure aims to isolate Availability Zones mainly in terms of:

* ⚡ **Power** – power supply
* ❄️ **Cooling** – cooling systems
* 🌐 **Networking** – network infrastructure

If a local power failure occurs in one zone, the goal is for the other zones to continue operating.

---

# 3. How can you visualize it?

Imagine a single Azure region:

```text
                 AZURE REGION
        ┌────────────────────────────┐
        │                            │
        │   AZ1       AZ2       AZ3  │
        │   🏢        🏢        🏢   │
        │                            │
        └────────────────────────────┘
```

Each zone is a physically isolated environment.

If:

```text
AZ1 💥
```

then:

```text
AZ2 ✅
AZ3 ✅
```

can continue operating.

---

# 4. Why do Availability Zones exist?

Before Availability Zones, there were **Availability Sets**.

An Availability Set allows you to distribute VMs across different:

> **racks / fault domains**

So if one rack fails:

```text
Rack 1 💥

Rack 2 ✅
Rack 3 ✅
```

VMs in the other racks can continue operating.

However, they are still located **within the same data center/physical environment**.

Availability Zones take this one level higher:

```text
Availability Set
       ↓
different racks / fault domains

Availability Zones
       ↓
different isolated physical environments
```

---

# 5. AZ1, AZ2, and AZ3 do not mean specific buildings

This is **very important**.

It is not:

```text
AZ1 = Building 1
AZ2 = Building 2
AZ3 = Building 3
```

Instead, they are logical labels for isolated physical environments.

Also:

> **AZ1 in one subscription does not necessarily represent the same physical location as AZ1 in another subscription.**

Azure uses consistent zone mapping **within a specific subscription**, but the mapping does not necessarily correspond between different subscriptions.

---

# 6. Availability Zone ≠ Distance

This is a common mistake.

Do not think:

> "AZ1 and AZ2 are always, for example, 10 miles apart."

❌ No.

Azure **does not guarantee a specific distance** between Availability Zones.

They may be relatively close to each other.

The main idea is:

> **Isolation of power, cooling, and networking.**

Not:

> "A large geographical distance."

---

# 7. Availability Zone ≠ Proximity Placement Group

Remember this:

### Availability Zone

I want:

> **resilience / isolation**

### Proximity Placement Group

I want:

> **resources to be as close to each other as possible / low latency**

So:

```text
Availability Zone
       ↓
resilience

Proximity Placement Group
       ↓
physical proximity / low latency
```

An Availability Zone does **not guarantee** that two VMs will be physically very close to each other.

---

# 8. Biggest mistake: One VM in one AZ

Imagine:

```text
AZ1
└── VM1
```

You might say:

> "I'm using an Availability Zone, so I'm resilient."

❌ No.

If you have only **one VM**, you still have only one VM.

If that VM fails:

```text
VM1 💥
```

your application may become unavailable.

An Availability Zone by itself **is not magic that automatically increases resilience**.

---

# 9. How should you use Availability Zones correctly?

Use **multiple instances** and distribute them across zones.

For example:

```text
AZ1          AZ2          AZ3
 │            │            │
VM1           VM2          VM3
```

If:

```text
AZ1 💥
```

you have:

```text
VM1 💥
VM2 ✅
VM3 ✅
```

Your services can therefore continue operating.

This is the main reason Availability Zones exist.

---

# 10. VM Scale Sets can handle this automatically

You do not have to do everything manually.

For example, you can use:

**Virtual Machine Scale Sets**

and configure them to be zone-redundant.

Azure can then distribute VMs across Availability Zones.

A similar principle can be used with services/workloads such as:

* VM Scale Sets
* AKS worker nodes
* App Service Plans

---

# 11. What if I need only one VM?

Here is something interesting.

Suppose you have:

```text
AZ1
└── VM1
```

A VM itself cannot exist in three AZs simultaneously.

However, you can make its **storage** more resilient.

---

# 12. ZRS Managed Disk

Normally, you can have a disk using **LRS**.

LRS:

> copies of the data are kept within the same physical environment/AZ.

But you can use:

**ZRS – Zone-Redundant Storage**

With ZRS, copies of the data are distributed across Availability Zones.

Simplified:

```text
AZ1       AZ2       AZ3
 │         │         │
Disk      Disk      Disk
copy      copy      copy
```

If AZ1 fails:

```text
VM → ❌
Disk data → ✅
```

You can then create a new VM and attach the existing disk.

---

# 13. Azure Site Recovery

Another option is:

**Azure Site Recovery**

It is typically used to replicate VMs between regions for **Disaster Recovery**.

According to the video, it can also be used to replicate a VM to another Availability Zone within the same region.

For example:

```text
AZ1
VM1
 │
 │ replication
 ↓
AZ2
VM replica
```

If AZ1 fails, you can recover/start the VM in the other zone.

---

# 14. Think about the entire system

This is **one of the most important things for AZ-104/AZ-500**.

It is not enough to simply create:

```text
AZ1 → VM
AZ2 → VM
AZ3 → VM
```

and say:

> "Done, the application is resilient."

You need to look at the **entire architecture**.

For example:

```text
             Load Balancer
                  │
        ┌─────────┼─────────┐
        ↓         ↓         ↓
       AZ1       AZ2       AZ3
       VM1       VM2       VM3
        │         │         │
        └─────────┼─────────┘
                  ↓
              Database
```

Every important component should have the **same or better level of resilience**.

---

# 15. Single Point of Failure

This is a very important concept:

> **Single Point of Failure (SPOF)**

It is a component whose failure can bring down the entire service.

For example:

```text
AZ1 → VM1
AZ2 → VM2
AZ3 → VM3

       ↓
   Load Balancer
       ↓
     Database
```

If you have resilient VMs but:

```text
Database 💥
```

and the database is a single instance without protection against failure, the entire system may still have a problem.

Therefore:

> **Resilience must be handled end-to-end.**

---

# 16. Zone-redundant vs Zonal

You should definitely remember this.

### Zone-redundant service

The service is designed to operate across multiple AZs.

```text
AZ1 ─┐
AZ2 ─┼── Service
AZ3 ─┘
```

### Zonal service

You deploy the service into a **specific AZ**.

For example, the video mentions:

> **NAT Gateway**

It can be zonal.

Therefore, you need to be careful that its placement does not create a **Single Point of Failure**.

---

# 17. VNet and Subnet

Important:

**A Virtual Network and subnet are not automatically tied to a single Availability Zone.**

A subnet can span an entire region.

So:

```text
Region
│
├── AZ1
│    └── VM
│
├── AZ2
│    └── VM
│
└── AZ3
     └── VM

        ↑
     one VNet/subnet
```

Therefore, with zonal services, you need to think about how your resources are distributed.

---

# 18. Availability Zones ≠ Disaster Recovery

🔥 **This is one of the most important things to remember.**

### Availability Zones

You mainly use them for:

> **High Availability**

within **a single region**.

### Multiple Azure Regions

You use them for:

> **Disaster Recovery**

If, for example, an entire region is affected by:

* a major natural disaster
* flooding
* a large-scale regional outage

Availability Zones within that same region may not be enough.

Therefore, you can have:

```text
Region A
├── AZ1
├── AZ2
└── AZ3

        ↓ DR

Region B
├── AZ1
├── AZ2
└── AZ3
```

Regions can be hundreds of miles apart.

---

# 🧠 The easiest way to remember it

Think of **baskets of eggs**:

```text
          REGION
             │
     ┌───────┼───────┐
     ↓       ↓       ↓
   AZ1      AZ2      AZ3
   🧺       🧺       🧺
   🥚       🥚       🥚
```

If one basket falls:

```text
AZ1 💥

AZ2 🥚
AZ3 🥚
```

You still have two-thirds of your workload.

But if you have only:

```text
AZ1
🧺
🥚
```

then having three baskets does not help because you only have **one egg**.

➡️ **You need multiple instances and distribute them across AZs.**

---

# 🎯 AZ-104 / AZ-500 – What you should take away

| Term                          | Remember                                                |
| ----------------------------- | ------------------------------------------------------- |
| **Region**                    | A geographical Azure area                               |
| **Availability Zone**         | An isolated physical environment within a region        |
| **Main purpose of AZ**        | Isolation / High Availability                           |
| **What it isolates**          | Power, cooling, networking                              |
| **AZ ≠ DR**                   | DR is typically handled using another region            |
| **AZ ≠ proximity**            | AZ does not guarantee physical proximity                |
| **Proximity Placement Group** | Low latency / resources close together                  |
| **Availability Set**          | Fault domains/racks within a physical environment       |
| **Zone-redundant**            | Redundancy across AZs                                   |
| **Zonal**                     | Resource is placed in a specific AZ                     |
| **LRS disk**                  | Local replication                                       |
| **ZRS disk**                  | Replication across AZs                                  |
| **Multiple VMs across AZs**   | The real benefit of AZs                                 |
| **Single VM in one AZ**       | The AZ alone does not automatically increase resilience |
| **SPOF**                      | A component whose failure can bring down the service    |




