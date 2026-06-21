# 📊 Microsoft Sentinel Workbooks

All right class.

This folder contains free, ready-to-deploy Microsoft Sentinel workbooks. Each one is a full JSON you can paste straight into the Advanced Editor. No Content Hub, no marketplace, no dependencies beyond a Log Analytics workspace.

For the full breakdown on what each workbook does, how it was built, and what to watch out for, head to the blog links below. The guides cover the context that a raw JSON file never will.

---

## How to Install

1. Go to Microsoft Sentinel > Workbooks > New
2. Click the Advanced Editor button
3. Paste the JSON from the workbook file
4. Click Apply
5. Save the workbook

---

## Workbooks

### 🛡️ Diagnostic Settings Manager

A workbook that gives you a single place to view and onboard Azure resources to Microsoft Sentinel by configuring diagnostic settings. Three tabs covering Networking, Storage & Data, and Apps & Other. Select resources, hit a button, and it fires a PUT against the ARM API. No scripting, no portal-hopping.

Storage is split by sub-service (Blob, File, Queue, Table) because that is how Azure actually works, and most people only configure the parent and then wonder why their blob logs never show up.

**📖 Blog Guide:** https://www.itprofessor.cloud/diagnostic-settings-manager-workbook/

**📄 File:** [Diagnostic-Settings-Manager.json](./Diagnostic-Settings-Manager/Diagnostic-Settings-Manager.json)

---

### 🔐 User Audit Investigation Workbook

The workbook you build once instead of recreating the same user activity timeline every time HR or Legal comes knocking. Driven by two parameters: the target user's UPN and a time range.

Eight tabs covering Identity & Profile, Access Footprint, Activity Trail, Data & Communication, Exfiltration Patterns, Sabotage & Destruction, Track Covering, and a risk-scored Timeline. Everything you need to build a clean investigation narrative without jumping between portals.

**📖 Blog Guide:** https://www.itprofessor.cloud/sentinel-user-audit-investigation-workbook/

**📄 File:** [User-Audit-Investigation.json](./User-Audit-Investigation/User-Audit-Investigation.json)

**Before you deploy:**
- You need the right data connected (M365 audit / OfficeActivity, Entra sign-ins, Defender tables). If the connectors are not on, the workbook will not magically invent logs.
- Start with a short range (7d / 14d). Going 90d on a noisy tenant will just DDoS your own eyeballs.
- If a query returns nothing, check ingestion and table availability before touching the KQL.

  ---

### 🏝️ Forsaken Resources

An Azure governance workbook that helps you find the forgotten, abandoned, and neglected resources quietly cluttering your environment. Built on Azure Resource Graph, it surfaces orphaned disks, unused public IPs, unattached NICs, empty resource groups, abandoned networking components, and other resources that are either costing money, increasing operational complexity, or waiting to cause confusion during an outage.

Instead of hunting through subscriptions manually, you get a centralised view of resources that probably should not exist anymore, helping you reduce waste, improve governance, and clean up your Azure estate before the next cost review or security audit.

**📖 Blog Guide:** https://www.itprofessor.cloud/azure-forsaken-resources-workbook/

**📄 File:** [Forsaken Resources.json](./Forsaken-Resources/Forsaken-Resources.json)

**Before you deploy:**
- The workbook uses Azure Resource Graph, so users need permissions to query the subscriptions they want to assess.
- Finding a resource here does not automatically mean it is safe to delete. Always validate ownership and dependencies first.
- Larger environments may return significant numbers of results. Start with a limited subscription scope if you're using it for the first time.

---

---


More workbooks will be added over time. Check back or watch the repo for updates.

For more content, tutorials, and free resources: **https://www.itprofessor.cloud/**
