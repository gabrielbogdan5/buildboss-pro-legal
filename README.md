# BuildBoss PRO — Construction Manager App

> **Professional construction site management — offline, no account required, runs anywhere.**

![BuildBoss PRO](https://img.shields.io/badge/version-2.0.0-gold?style=flat-square&labelColor=1a1c22&color=f7c53b)
![Platform](https://img.shields.io/badge/platform-Android%20%7C%20iOS%20%7C%20Web-blue?style=flat-square&labelColor=1a1c22)
![Storage](https://img.shields.io/badge/storage-IndexedDB%20(unlimited)-green?style=flat-square&labelColor=1a1c22)
![License](https://img.shields.io/badge/license-All%20Rights%20Reserved-red?style=flat-square&labelColor=1a1c22)

---

## 📱 Screenshots

| Settings & Dark Mode | Incident Report |
|:---:|:---:|
| ![Settings](screenshots/settings-dark.jpg) | ![Incident](screenshots/incident-details.jpg) |

---

## 🔍 Overview

**BuildBoss PRO** is a standalone HTML5 construction management application designed for site managers, supervisors and inspectors. It runs entirely in the browser — no installation, no account, no internet connection required after the first load.

All data is stored locally on the device using **IndexedDB**, providing virtually unlimited storage for photos, reports and job history.

---

## ✨ Features

### 🔍 Audit — Job Inspection Report
- Multi-step job audit workflow (Job Info → Add Issue → Issues → Summary → Preview)
- Log unlimited issues with severity levels: **High**, **Medium**, **Low**
- Attach up to 3 photos per issue (gallery or camera)
- Action tracking: assigned person, deadline, status (Open / In Progress / Closed)
- Professional **Site Inspection Report** PDF — clean monochrome design, no branding
- Auto-generated reference number per report
- Live PDF preview before export

### 💬 Talk — Toolbox Talk
- 20 pre-built safety topics (working at height, PPE, manual handling, COSHH, fire safety, and more)
- Topic content viewer with key points and discussion questions
- Digital attendance & signature collection (up to 20 workers)
- Optional date field — schedule talks in advance or leave undated
- Export as professional PDF with full attendance register

### 📅 DAB — Daily Activity Briefing
- 8-step briefing workflow: Project → Review → Tasks → SIMOPS → H&S → Checks → Sign → Export
- Weather conditions, work area, SIMOPS conflict checks
- Health & Safety pre-start checklist
- Team sign-off with digital signatures
- Full PDF export and native share sheet

### 🚨 Incident — Incident Report
- 4 incident types: **Accident**, **Near Miss**, **Dangerous Occurrence**, **Property Damage**
- RIDDOR (UK) reminder with link to HSE guidance
- Injured person details, witnesses, actions taken
- Photo evidence attachment (gallery or camera)
- Digital signature for reporting officer
- PDF report export with all details

---

## 🗃️ Jobs History

All completed reports (audits, talks, DABs, incidents) are saved to a searchable **Jobs History** with full snapshot data including photos. Stored in IndexedDB — no size limit.

---

## ⚙️ Technical Stack

| Component | Technology |
|-----------|-----------|
| **Frontend** | Vanilla HTML5 / CSS3 / JavaScript (ES2020+) |
| **Storage** | IndexedDB (primary) + localStorage (settings only) |
| **PDF Export** | Native `window.open` + `print()` — no external library |
| **Photo Handling** | FileReader API + Canvas compression (800×800px, 0.75 quality) |
| **Share** | Web Share API (`navigator.share`) — native Android/iOS share sheet |
| **Offline** | Fully offline after download — zero network dependencies |
| **Architecture** | Single HTML file — no build tools, no frameworks, no dependencies |

---

## 📦 Storage Architecture

Previous versions used `localStorage` (5MB limit). **v2.0.0** migrates all large data to **IndexedDB**:

```
IndexedDB: buildboss_pro
├── audit      — current audit state (with full photo data)
├── talk       — current toolbox talk state
├── jobs       — jobs history (all types, with photos)
└── kv         — key-value store (migration flags)

localStorage (settings only, <50KB)
├── bb_lang    — language preference
├── bb_theme   — dark/light mode
├── bb_company — company name for PDF footer
└── bb_pdf_*   — PDF display preferences
```

Auto-migration from localStorage → IndexedDB runs transparently on first launch of v2.0.0.

---

## 📄 PDF Export System

All modules generate PDFs using the **native browser print dialog** (no jsPDF or external libraries):

- **Audit** → "Site Inspection Report" — professional monochrome, A4, with issues table and photos
- **Talk** → Toolbox Talk report + Attendance & Signatures register (2 pages)
- **DAB** → Daily Activity Briefing — full 8-section report
- **Incident** → Incident Report with RIDDOR flag, photos, and signatures

---

## 🔒 Privacy & Data

- ✅ **No data leaves the device** — everything stored locally
- ✅ **No analytics, no tracking, no ads**
- ✅ **No account required**
- ✅ **No internet connection required** after initial load
- ✅ **GDPR compliant by design** — zero server-side data processing

---

## 🚀 Getting Started

1. Download `BuildBoss-PRO.html`
2. Open in any modern browser (Chrome, Samsung Browser, Safari)
3. Use directly — no installation required
4. For best experience on Android: open in Samsung Browser or Chrome, tap **Add to Home Screen**

---

## 📋 Changelog

### v2.0.0 (2026-05-31)
- ✅ Migrated storage from localStorage → IndexedDB (unlimited photo storage)
- ✅ Professional "Site Inspection Report" PDF (replaced jsPDF)
- ✅ Live PDF preview in Audit (matches export exactly)
- ✅ Gallery + Camera photo selection (no forced camera capture)
- ✅ Talk date field made optional with clear/now buttons
- ✅ Removed Romanian language option
- ✅ Hamburger menu (☰) with yellow active state
- ✅ Native share sheet (`navigator.share`) across all modules
- ✅ IDB status indicator in topbar (🟢 IDB / 🟡 LS)
- ✅ Disclaimer uses `sessionStorage` — shows on every fresh open
- ✅ Consistent export pages across all 4 modules

### v1.0.0
- Initial release

---

## 📬 Contact

**Email:** buildbosspro@gmail.com

---

## ⚖️ Legal

© 2026 BuildBoss PRO. All rights reserved.

This software is proprietary. No part of this codebase may be reproduced, distributed, or transmitted in any form without prior written permission from the author.

See [Terms & Conditions](terms-and-conditions.html) · [Privacy Policy](privacy-policy.html) · [Legal Disclaimer](legal-disclaimer.html)
