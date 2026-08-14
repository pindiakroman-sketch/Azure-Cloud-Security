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

