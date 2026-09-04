# Topic 11: The Microsoft Defender Portal & Microsoft Purview Portal

> Topic 10 explained the *architecture* (which product owns which signal, how it all correlates). This topic is the actual **workspace tour** — where you'll physically spend most of your time as a SOC analyst: the unified **Microsoft Defender portal** (security operations) and **Microsoft Purview** (data governance/compliance, the M365 E5 sibling to Defender).

---

## 1. Microsoft Defender Portal — Home

![Microsoft Defender portal home page - SIEM and XDR in one place](defender-portal-home.png)

Path: `security.microsoft.com`

The banner says it plainly: **"Get your SIEM and XDR in one place."** This is the unified portal Topic 10 referenced — Sentinel (SIEM) and Defender XDR now share this single interface, so you're not context-switching between separate tools to investigate an incident.

### Left navigation — what each section is for

| Section | Purpose |
|---|---|
| **Home** | Overview dashboard (what you're looking at now) |
| **Incidents** | Correlated, cross-domain security incidents — the XDR output from Topic 10's architecture |
| **Exposure management** | Attack surface / exposure score — proactive risk visibility before an incident happens |
| **Investigation & response** | Tools for digging into and remediating specific alerts/incidents |
| **Advanced hunting** | KQL-based hunting across all connected data — this is where your future KQL skills get used directly |
| **Threat intelligence** | Indicators of compromise (IOCs), threat actor profiles, campaign data |
| **Assets** | Devices, identities, and other inventoried objects XDR is protecting |
| **Microsoft Sentinel** | Sentinel-specific features (analytics rules, workbooks, playbooks) — nested *inside* this same portal, confirming the unification |
| **Email & collaboration** | Defender for Office 365 — email/Teams/SharePoint threat protection |
| **Cloud security** | Defender for Cloud Apps / Defender for Cloud surface |
| **SOC optimization** | Recommendations to tune your SOC's coverage and detection quality |
| **Reports / Learning hub / Trials** | Reporting, training content, and feature trials |
| **System** | Settings — this is exactly the "Endpoints / Identities / Cloud Apps / Sentinel" settings page from Topic 8 |

### Home page cards (fresh/unconfigured tenant state)

| Card | What it tracks |
|---|---|
| **SOC optimization** | Active / In progress / Completed / Dismissed optimization recommendations (all `0` — nothing configured yet) |
| **Entity Behavior Analytics (UEBA)** | *"Enable UEBA — gain insights into user and entity behaviors... detect anomalies that may indicate compromised accounts or insider threats"* — not yet enabled |
| **Microsoft Sentinel automation** | `0 automation rules` — playbooks/auto-response not yet configured |
| **Microsoft Sentinel data connectors** | `0 data connectors` — **nothing is flowing into Sentinel yet** |

⚠️ **This is the exact state you'd expect right after Topic 5's tenant setup, before any Sentinel workspace or data connectors exist.** The `0`s across every card are the signal that the next major task in your course is: **connect a workspace** (the big blue button in the banner) and start wiring up data connectors — which is almost certainly your next topic after this one.

---

## 2. Microsoft Purview Portal — Home

![Microsoft Purview portal home page - Data Security Investigations](purview-portal-home.png)

Path: `purview.microsoft.com`

Purview is Microsoft's **data governance, compliance, and information protection** platform — the sibling portal to Defender. Where Defender focuses on **threats**, Purview focuses on **data**: what data exists, who can access it, whether it's being handled compliantly, and investigating data-centric risks.

### Left navigation

| Section | Purpose |
|---|---|
| **Home** | Overview / featured solutions |
| **Solutions** | The full catalog of Purview capabilities |
| **Agents** | AI agent management (newer addition) |
| **Learn** | Training content |
| **Usage center** | Adoption/usage metrics |
| **Settings** | Tenant-wide Purview configuration |

### Featured solutions shown

| Solution | Purpose |
|---|---|
| **Data Security Investigations** *(New)* | *"Accelerate data security investigations with AI-powered deep content analysis"* — the newest capability, headlining this home page |
| **Data Catalog** | Discover and classify data across the organization |
| **Settings** | Purview-wide configuration |
| **Compliance Manager** | Track regulatory/compliance posture and improvement actions |
| **eDiscovery** | Legal hold, search, and export of content for litigation/investigations |
| **Information Barriers** | Restrict communication/collaboration between specific groups (e.g., conflict-of-interest walls) |

⚠️ **Portal migration note visible on this page:** *"Some features and solutions from the classic portals either have a new home or were retired."* Microsoft has been consolidating separate compliance/security portals into Purview and Defender — expect some SC-200 material (and real-world screenshots you find online) to reference older portal layouts (e.g., the old `compliance.microsoft.com` or `security.microsoft.com` layouts) that have since moved.

---

## 3. Defender vs. Purview — Why Both Exist

| | Microsoft Defender | Microsoft Purview |
|---|---|---|
| **Core question** | "Are we under attack, and how do we respond?" | "Where is our data, and is it being handled properly?" |
| **Primary users** | SOC analysts (your SC-200 role) | Compliance officers, legal, data governance teams |
| **Feeds Sentinel?** | Yes — direct signal source | Indirectly — DLP/compliance alerts can also surface as Sentinel incidents |
| **SC-200 relevance** | Primary — this is where you'll live day-to-day | Secondary but tested — e.g., insider risk, eDiscovery-driven incident response |

**Why this matters for SC-200:** the exam does test Purview-adjacent scenarios (Insider Risk Management, DLP alerts triggering an incident) *specifically because* data-security incidents (data exfiltration, insider threats) are increasingly investigated jointly by SOC and compliance teams. Recognizing when an incident needs to cross from Defender into Purview (or vice versa) is itself a tested skill.

---

## Key Terms to Know

- **Unified Defender portal** (`security.microsoft.com`) — single pane combining SIEM (Sentinel) and XDR
- **Advanced hunting** — KQL-based cross-data hunting inside the Defender portal
- **Data connectors** (Sentinel) — the mechanism for ingesting log sources into Sentinel; currently `0` in a fresh tenant
- **UEBA (User and Entity Behavior Analytics)** — Sentinel/Defender feature detecting anomalous behavior patterns
- **Microsoft Purview** — the data governance/compliance platform (`purview.microsoft.com`)
- **Data Security Investigations** — Purview's newest AI-powered deep content analysis capability
- **eDiscovery** — legal hold, search, and export workflows inside Purview
- **Information Barriers** — Purview feature restricting communication between defined groups

---

## Quick Self-Check

- [ ] Can you name at least five sections in the Defender portal's left navigation and what each does?
- [ ] Do you understand why "0 data connectors" and "0 automation rules" on the home page signal that Sentinel onboarding hasn't happened yet?
- [ ] Can you explain the core difference in purpose between Microsoft Defender and Microsoft Purview?
- [ ] Do you know where UEBA lives and what kind of threat it's designed to catch (hint: insider/compromised-account behavior, not just external attacks)?
- [ ] Can you think of a scenario where an incident would need to involve both Defender (threat response) and Purview (data governance/eDiscovery)?

---

*Keep `defender-portal-home.png` and `purview-portal-home.png` in this same folder as this README so the image links resolve correctly on GitHub.*
