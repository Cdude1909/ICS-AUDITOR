<div align="center">

# 🛡️ ICS Auditor `(Beta)`

### Next-Generation Industrial Control Systems (ICS/SCADA) & Operational Technology (OT) Cybersecurity Assessment and Compliance Platform

[![Version](https://img.shields.io/badge/Version-1.0--beta-amber.svg?style=for-the-badge&logo=git)](https://github.com/)
[![Tauri](https://img.shields.io/badge/Tauri-v2.0-FFC131?style=for-the-badge&logo=tauri&logoColor=black)](https://tauri.app/)
[![License](https://img.shields.io/badge/License-MIT-emerald.svg?style=for-the-badge)](LICENSE)

<br />

**Tailored for Critical Infrastructure Security Engineers, OT Auditors, Plant Managers, and CISO Offices**
<br />
*Compliant with IEC 62443, NIST SP 800-82 r3, CISA CSET, NCIIPC, CERT-In, and BIS IS 16335*

</div>

---

> ###  Public Beta Notice
> **ICS Auditor 1.0 is currently in Public Beta.** While the core assessment engine, offline encryption vaults, Gemini Vision diagram analyzer, and PDF generation suites are fully operational, the project is actively undergoing user-experience refinements, performance tuning, and expanding its regulatory library. See [Future Scope & Framework Development](#-future-scope--framework-development) for our architectural roadmap.

---

##  Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [System Architecture & Visual Figures](#-system-architecture--visual-figures)
  - [Figure 1: High-Level Platform Architecture](#figure-1-high-level-platform-architecture)
  - [Figure 2: AI workflow overview](#figure-2-AI-workflow-overview)
  - [Figure 3: Live Runtime Screenshot and working](#figure-3Live-Runtime-Screenshot-and-working)
- [Supported Standards & Regulatory Frameworks](#-supported-standards--regulatory-frameworks)
- [Prerequisites & Requirements](#-prerequisites--requirements)
- [Installation & Quickstart Guide](#-installation--quickstart-guide)
  - [Running the Web Application (Vite SPA)](#1-running-the-web-application-vite-spa)
  - [Running as a Native Desktop App (Tauri v2)](#2-running-as-a-native-desktop-app-tauri-v2)
  - [Environment Variables Configuration](#3-environment-variables-configuration)
  - [Air-Gapped & Offline Deployment](#4-air-gapped--offline-deployment)
- [Detailed Module Walkthrough](#-detailed-module-walkthrough)
- [Future Scope: Framework Development](#-future-scope--framework-development)
- [Project Directory Structure](#-project-directory-structure)
- [Security & Air-Gap Compliance](#-security--air-gap-compliance)
- [Contributing](#-contributing)
- [License](#-license)

---

##  Overview

Industrial Control Systems (ICS) and Operational Technology (OT) networks power critical national infrastructure: **power grids, nuclear plants, oil & gas refineries, chemical manufacturing, water treatment facilities, and pharmaceutical plants**.

Conducting cybersecurity assessments in OT environments has traditionally been hindered by:
-  **Disjointed spreadsheets** with high human error and static checklists.
-  **Lack of OT topology context**, ignoring the Purdue Model and zone/conduit segmentation.
-  **Lengthy reporting turnaround**, taking weeks to correlate findings into executive summaries and technical roadmaps.
-  **Security risks with sensitive plant data**, exposing architecture diagrams to untrusted public cloud services.

**ICS Auditor 1.0** transforms this paradigm. It provides a specialized, local-first assessment platform with **computer vision-based diagram inspection**, **dynamic question synthesis based on Security Assurance Levels (SAL)**, **real-time visual analytics**, and **automated executive & technical PDF generation** all protected by client-side **AES-256 encryption** and designed for air-gapped plant operation.

---

##  Key Features

-  **AI-Powered Visual Diagram Inspection**: Upload architectural schematics or photos of network topologies. Powered by Google Gemini Vision to automatically detect 30+ ICS components (PLCs, RTUs, HMIs, SIS safety controllers, DCS, firewalls, jump hosts, historians, data diodes, and IIoT gateways).
-  **Security Assurance Level (SAL) Calibration**: Tailor question depth according to consequence severity (`Low`, `Medium`, `High`, `Very High`) following IEC 62443 guidance.
-  **Purdue Model & Zone-Conduit Mapping**: Built-in reference templates (Purdue Standard, Flat Network, Converged IIoT/Cloud Edge, Air-Gapped Island, SIS Safety, Distributed RTU/WAN, Micro-Grid).
-  **Paper Checklist & Evidence Digitization**: Scan physical paper audit forms via camera OCR into digital questions. Capture and attach cryptographic image proofs and justifications for partial compliance.
-  **Real-Time Visual Analytics**: Interactive domain compliance bar charts, answer distribution pie charts, and domain radar metrics powered by Recharts.
-  **CSET-Grade PDF Report Engine**: One-click generation of professional executive reports with executive summaries, radar compliance metrics, gap analysis, Purdue topology risk assessments, and prioritized remediation roadmaps.
-  **Defense-in-Depth Cryptography**:
  - AES-256 local encrypted storage for in-progress assessments.
  - Quick 4-digit PIN lock for screen-privacy during walk-through plant inspections.
  - Password-protected encrypted export/import of `.icsaudit` bundles.
- **Dual Deployment (Web + Native Desktop)**:
  - Responsive **Vite + React 19 PWA** with offline capabilities.
  - Ultra-lightweight native **Desktop App** packaged with **Tauri v2** (Rust core).
- **Optional Cloud Collaboration**: Firebase Auth (Google OAuth & Email/Password) and Firestore sync with fine-grained access rules when working in hybrid/IT environments.

---

##  System Architecture & Visual Figures

### Figure 1: High-Level Platform Architecture

<img width="1542" height="757" alt="image_17" src="https://github.com/user-attachments/assets/ab0cc5bc-74b3-425b-883f-b2b733dcd2eb" />

---


### Figure 2: AI workflow overview

<img width="635" height="831" alt="image_9" src="https://github.com/user-attachments/assets/e2f90071-bb1c-4219-b978-40813817ed3d" />

---

### Figure 3: Live Runtime Screenshots and working

<img width="1263" height="777" alt="image_10" src="https://github.com/user-attachments/assets/1fd824ed-94d4-4e2e-a1ae-6ada5a5d0c10" />
<img width="825" height="622" alt="Screenshot 2026-04-15 161306" src="https://github.com/user-attachments/assets/b10e0354-7182-4647-a965-375043c78ca2" />
<img width="3000" height="3000" alt="MixCollage-15-Apr-2026-04-22-PM-7282" src="https://github.com/user-attachments/assets/76e17fd3-66e4-4624-a977-9aeaf037cb2e" />
<img width="1080" height="1080" alt="image_11" src="https://github.com/user-attachments/assets/c8e59f46-aaa3-4462-a3fe-2854b8db319d" />

---

##  Supported Standards & Regulatory Frameworks

ICS Auditor 1.0 maps questionnaires and generates gap analyses directly aligned with globally recognized critical infrastructure standards:

| Standard / Framework | Issuing Body | Primary Scope in ICS Auditor |
| :--- | :--- | :--- |
| **IEC 62443-3-3** | ISA / IEC | System security requirements, Security Assurance Levels (SAL 1-4), Zone and Conduit segmentation |
| **NIST SP 800-82 Rev 3** | NIST | Guide to Operational Technology (OT) Security, Defense-in-Depth, Incident Response for ICS |
| **CISA CSET** | US CISA / DHS | Cross-sector baseline, asset classification, supply-chain validation |
| **NCIIPC Guidelines** | Govt. of India | Critical Information Infrastructure (CII) protection mandates |
| **CERT-In OT/ICS Advisory** | CERT-In | Industrial network hardening, remote access isolation, vulnerability remediation |
| **BIS IS 16335** | BIS | Power system cybersecurity, substation automation, IEC 61850 compliance |
| **ISO/IEC 27001** | ISO / IEC | Information Security Management System (ISMS) baseline alignment |

---

## Prerequisites & Requirements

### For Running the Web Application
- **Node.js**: `v18.0.0` or higher (Node 20+ recommended)
- **Package Manager**: `npm` (v9+), `bun`, or `pnpm`
- **Modern Web Browser**: Chrome, Edge, Firefox, or Safari (WebCrypto and Canvas API support required)
- **Google Gemini API Key**: Free or paid key from [Google AI Studio](https://aistudio.google.com/) for AI vision diagram analysis and automated report generation.

### For Building the Desktop Application (Tauri v2)
- **Rust Toolchain**: `rustc` and `cargo` (1.77+ recommended)
- **Platform Dependencies**:
  - *Windows*: Visual Studio C++ Build Tools & WebView2
  - *macOS*: Xcode Command Line Tools
  - *Linux*: `libwebkit2gtk-4.1-dev`, `build-essential`, `curl`, `wget`, `file`, `libssl-dev`, `libgtk-3-dev`, `libayatana-appindicator3-dev`, `librsvg2-dev`

---

##  Installation & Quickstart Guide

### 1. Running the Web Application (Vite SPA)

```bash
# 1. Clone the repository
git clone https://github.com/your-username/ics-auditor-1.0.git
cd ics-auditor-1.0

# 2. Install dependencies
npm install

# 3. Configure environment variables
cp .env.example .env.local
# Open .env.local and insert your GEMINI_API_KEY

# 4. Start the Vite development server
npm run dev
```

The application will be live at: **`http://localhost:3000`** (or `http://localhost:5173`).

To build for production:
```bash
npm run build
npm run preview
```

---

### 2. Running as a Native Desktop App (Tauri v2)

The desktop edition provides a sandboxed, standalone binary ideal for offline laptops carried by auditors onto plant floors:

```bash
# 1. Ensure Rust is installed
rustc --version

# 2. Run in Tauri desktop development mode
npm run tauri dev

# 3. Build a release desktop installer (.exe, .dmg, or .deb/.AppImage)
npm run tauri build
```

The compiled binaries will be output into `src-tauri/target/release/bundle/`.

---

### 3. Environment Variables Configuration

Create a `.env.local` file in the project root:

```env
# Google Gemini API Key for Vision diagram analysis & AI Report generation
# Obtain a key at: https://aistudio.google.com/app/apikey
GEMINI_API_KEY=your_google_gemini_api_key_here

# Optional: Firebase config overrides (if not using local default config)
# VITE_FIREBASE_API_KEY=your_firebase_api_key
# VITE_FIREBASE_PROJECT_ID=your_firebase_project_id
```

---

### 4. Air-Gapped & Offline Deployment

ICS Auditor 1.0 was intentionally engineered to work seamlessly in **air-gapped industrial environments**:

1. **Local-First Caching**: The core questionnaire engine, scoring metrics, and PDF generation run entirely in client-side WebAssembly / JavaScript. No outbound internet connection is required for manual auditing.
2. **Encrypted File Transfer**: Assessments can be exported to `.icsaudit` encrypted files, copied to a secure USB drive, and imported onto another auditor's workstation.
3. **Graceful AI Fallback**: If an internet connection is unavailable, the application gracefully skips cloud vision analysis and uses manual component selectors and pre-packaged IEC 62443 question catalogs.

---

##  Detailed Module Walkthrough

```
+--------------------------------------------------------------------------------------------------+
|                                    WORKFLOW STEPS                                                |
+--------------------------------------------------------------------------------------------------+
| [1. PREPARE]   -->   [2. DIAGRAM]   -->   [3. QUESTIONS]   -->   [4. RESULTS]   --> [5. REPORT]  |
+--------------------------------------------------------------------------------------------------+
```

### 1. Assessment Preparation (`/prepare`)
- Define facility metadata: Facility Name, Facility Type (Oil & Gas, Power Generation, Chemical, Water Treatment, Manufacturing, Nuclear, Rail).
- Configure **Security Assurance Level (SAL)**: Low, Medium, High, or Very High.
- Select applicable regulatory frameworks (NCIIPC, CERT-In, IEC 62443, NIST SP 800-82, BIS IS 16335, CSET, ISO 27001).
- Assemble the audit team with specific roles (Lead Auditor, OT Specialist, Safety Engineer, Network Architect).

### 2. Network Diagram & Topology (`/diagram`)
- Choose an architectural template or upload a plant network diagram image (PNG, JPG, WebP).
- Trigger **Gemini Vision Analysis** to automatically detect firewalls, PLCs, HMIs, SIS controllers, engineering stations, historians, and jump hosts.
- Manually tag or fine-tune detected equipment across Network, Control, IIoT, and Supporting Infrastructure categories.

### 3. Dynamic Audit Questionnaire (`/questions`)
- Questions adapt dynamically to the facility's SAL level, detected components, and selected standards.
- Evaluate controls with standard responses: **Yes**, **No**, **Partial** (requires justification note), or **Alternative (ALT)**.
- Flag critical items for follow-up review.
- Upload photo evidence and documents for audit verification.
- Use **OCR Camera Scan** to convert paper notes or clipboard checklists into structured digital answers.

### 4. Real-Time Results & Analytics (`/results`)
- Instant domain-by-domain compliance scores (0 - 100%).
- Response distribution breakdown (Compliance vs. Non-Compliance vs. Compensating Controls).
- High-level Purdue Model risk segmentation indicator.

### 5. Report & Remediations (`/report`)
- Generate an AI-synthesized **Executive Summary**, **Compliance Strengths**, **Weaknesses**, and **Purdue Model Gap Analysis**.
- Formulate a prioritized remediation roadmap (Immediate 0-30 days, Mid-Term 30-90 days, Strategic 90+ days).
- Export professional, branded PDF reports ready for boardrooms and regulatory filings.
- Save encrypted backup files with password protection.

---

## Future Scope & Framework Development

ICS Auditor 1.0 is currently evolving from a standalone assessment tool into a **comprehensive, open-source ICS/OT Security Framework**:

<img width="2239" height="566" alt="c" src="https://github.com/user-attachments/assets/335996a9-4d84-40a1-9026-638fd205d60e" />


### Key Framework Roadmap Initiatives:

1. **Industrial Schema Definition Language (ISDL)**:
   - A standardized, declarative schema format (in YAML/JSON) enabling security teams, regulators, and OEMs to author and share custom compliance modules, sector-specific rule packs, and vendor-specific hardening baselines (e.g., Siemens TIA Portal, Rockwell Studio 5000, Schneider EcoStruxure).

2. **Modular Protocol Probe Plugin Architecture**:
   - An extensible plugin interface allowing safe, read-only passive discovery and validation of OT communication protocols (Modbus TCP, DNP3, OPC UA, EtherNet/IP, IEC 60870-5-104, Siemens S7comm).

3. **MITRE ATT&CK for ICS Grounding**:
   - Direct cross-referencing between identified audit non-conformances and MITRE ATT&CK for ICS techniques (e.g., *T0814: Denial of Service*, *T0855: Unauthorized Command Message*, *T0886: Remote Services*), helping teams visualize adversary kill chains.

4. **Headless Audit CLI & CI/CD Pipeline Automation**:
   - A command-line interface (`ics-audit-cli`) to enable continuous compliance checking for digital twins, PLC logic source code repositories, and Infrastructure-as-Code (Terraform / Ansible) OT network definitions.

5. **Multi-Site Enterprise Fleet Management**:
   - Centralized multi-tenant dashboard allowing CISOs to compare compliance posture and risk indexes across dozens of geographically distributed power substations, offshore platforms, or manufacturing plants.

---

## Project Directory Structure

```
ics-auditor-1.0/
├── .env.example                    # Sample environment variables template
├── firebase-applet-config.json     # Firebase project configuration
├── firebase-blueprint.json         # Firestore collections schema blueprint
├── firestore.rules                 # Granular Firestore security access rules
├── index.html                      # Single-page application entry HTML
├── metadata.json                   # Applet metadata & permissions manifest
├── package.json                    # Project dependencies and script definitions
├── tsconfig.json                   # TypeScript compiler options
├── vite.config.ts                  # Vite build tool and Tailwind CSS plugins
│
├── public/                         # Static assets and Web App icons
│   ├── favicon.svg
│   └── pwa-192x192.png
│
├── src-tauri/                      # Tauri v2 Desktop Engine
│   ├── Cargo.toml                  # Rust dependencies & metadata
│   ├── tauri.conf.json             # Desktop window, bundle, and security settings
│   └── src/                        # Rust backend entrypoints
│
└── src/                            # Frontend Application Source Code
    ├── App.tsx                     # Main application orchestrator & wizard views
    ├── index.tsx                   # React root mount point
    ├── index.css                   # Global styles & Tailwind v4 imports
    ├── types.ts                    # TypeScript types (SAL, Question, Report, etc.)
    ├── data.ts                     # Regulatory standards & Purdue templates
    │
    ├── components/                 # Reusable UI & Visualization Components
    │   ├── Dashboard.tsx           # Recharts compliance domain bar & pie charts
    │   └── NetworkDiagram.tsx      # OT topology selector & AI vision uploader
    │
    ├── lib/                        # Utility & Integration Libraries
    │   ├── firebase.ts             # Firebase Auth & Firestore client SDK
    │   └── imageUtils.ts           # Client-side image compression & format conversion
    │
    └── services/                   # Application Services
        ├── geminiService.ts        # Google Gemini Vision & LLM report synthesis
        └── pdfGenerator.ts         # High-resolution PDF document export engine
```

---

##  Security & Air-Gap Compliance

- **No Secret Leakage**: API keys and credentials are not hardcoded. Encryption is performed in-memory using client-side WebCrypto and CryptoJS.
- **Strict Content Security**: When running as a Tauri desktop app, external network calls can be completely disabled or locked down to trusted corporate endpoints.
- **Zero Involuntary Telemetry**: No tracking beacons, analytics cookies, or behavioral telemetry are embedded in the application.


---

##  License

This project is licensed under the **MIT License**, see the [LICENSE](LICENSE) file for details.

---

<div align="center">
  <sub>Engineered for Industrial Control Systems, Critical Infrastructure, and Cyber-Physical Safety.</sub>
</div>
