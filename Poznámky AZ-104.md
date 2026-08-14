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

## 🧠 One sentence to memorize

> **First understand what you are deploying, then determine the resource size, region and expected usage, and finally use the Azure Pricing Calculator to estimate the cost.**

For **AZ-104**, you don't need to memorize specific VM prices because prices change. You need to understand **what factors determine Azure costs and how to estimate them**.

