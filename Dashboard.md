---
title: Engineering Second Brain & Project Master Map
type: dashboard
status: active
tags: [dashboard, index, master-map, google-apps-script, typescript]
created: 2026-09-18
last-updated: 2026-09-19
---

# 🧠 Engineering Second Brain & Project Master Map

Welcome to your central engineering memory layer! This vault serves as the persistent knowledge base for all your software repositories, Google Apps Script pipelines, and infrastructure architectures.

---

## 📜 Rules & Memory Engine Guidelines
*Standard operating procedures for onboarding new repositories and incrementally patching existing codebase memory.*
* **[[Rules/How-to-Add-New-Codebase-Memory|How to Add New Codebase Memory]]**: Authoritative rules, 19 required sections, monorepo handling, and prompt template for onboarding new codebases.
* **[[Rules/How-to-Update-Codebase-Memory|How to Update Codebase Memory]]**: Surgical, incremental patching standard, section-by-section rules, and prompt template for updating existing codebases.
* **[[Rules/GAS-Architecture-Index|GAS Architecture Index & Agent Router]]**: Fast-triage decision matrix, 6 App Archetypes, 22 granular feature lookups, line-number citations, pre-flight gatekeeper, and official codification of TypeScript (`.ts`) Native Compilation as the enterprise standard.
* **[[Rules/GAS-Webapp-Architecture-Rulebook|GAS Webapp Architecture Rulebook]]**: Complete 21-section authoritative engineering standard establishing Native Clasp TypeScript (`module: "None"`) as the industry standard for high-visibility operations, zero-downtime automated triggers, full `@types/google-apps-script` signature validation, and 1:1 Stackdriver parity.

---

## 🗺️ Architectural Project Suites (Genuine Clusters)

### 1. 📱 Field Agent Operations & Manpower Tracking (`AgentFlow` Monorepo Suite)
*Monorepo suite tracking agent shifts, leave requests, payouts, and attendance.*
* **Monorepo Master Hub:** [[Projects/agent-summary-mechanism|agent-summary-mechanism]]
  * [[Projects/AgentFlow-Android|AgentFlow Android App]] — Native Android client with ML Kit OCR.
  * [[Projects/AgentFlow-Web-Tracker|AgentFlow Web Operations Map]] — Field agent web tracker portal.
  * [[Projects/AgentFlow-Leave-Admin|AgentFlow Leave Administration]] — Administrative leave review dashboard.
  * [[Projects/AgentFlow-GAS-Backend|AgentFlow GAS Payout Backend]] — Google Apps Script financial calculation backend.

---

### 2. 🎥 Warehouse Vision & VMS Hardware Overlays (`Bagging VMS` Workstation Suite)
*Workstation camera overlays recording live packing operations in WebM VP9 with barcode scanner integrations.*
* **Workstation Overlays & Bridges:**
  * [[Projects/Bagging-VMS-overlay|Bagging-VMS-overlay]] — Top-level WebRTC camera host shell.
  * [[Projects/cameraOverlayBridge|cameraOverlayBridge]] — Hardware permission camera bridge interface.
* **Connected Google Apps Script Backend:**
  * [[Projects/bagging-vms-gas-backend|bagging-vms-gas-backend]] — Serverless video capture, archival, and chain-of-custody logging backend.

---

### 3. 📊 Logistics Big-Data & Excel Streaming Engine (`XLSX-STREAM` Suite)
*High-throughput data streaming engine processing 500k+ row supply chain workbooks in constant $O(1)$ memory.*
* **Core Stream Engine Hub:** [[Projects/XLSX-STREAM-REPORT-GENERATOR|XLSX-STREAM-REPORT-GENERATOR (`ei_stream_server`)]]
* **FastAPI Direct Conversion Bridge:**
  * [[Projects/xlsx_to_csv_bridge|xlsx_to_csv_bridge]] — Rust/Calamine and SAX streaming XLSX-to-CSV converter.
* **Connected Stream Trigger Pipelines:**
  * [[Projects/EI-Stream-Trigger|EI-Stream-Trigger (Lake Ingestion Pipeline)]]
  * [[Projects/ei-report-trigger|ei-report-trigger (Render Cloud Trigger Orchestrator)]]

---

## 🛰️ Standalone Satellite Applications (Decoupled Nodes)

### 📦 Standalone Logistics Reporting & Hub ETL Satellites
*Independent Google Apps Script pipelines and microservices executing localized data transformations.*
* [[Projects/EI-Pan-India-Report|EI-Pan-India-Report]] — Daily E2E task ingestion pipeline and weekly partitioner.
* [[Projects/HourlyConversionReport|HourlyConversionReport]] — Real-time hourly conversion tracking engine.
* [[Projects/D-1-SummaryAutomation|D-1-SummaryAutomation]] — Previous-day operational summary ingestion script.
* [[Projects/RVP-Q2-AppendAutomation|RVP-Q2-AppendAutomation]] — Reverse pick-up Q2 append pipeline.
* [[Projects/RTO-Q2-appendAutomation|RTO-Q2-appendAutomation]] — Return-to-origin append pipeline.
* [[Projects/BRSNRAttributesAutomation|BRSNRAttributesAutomation]] — Customer non-receipt attribute tagging pipeline.
* [[Projects/DataConversion|DataConversion (`xlsx-filter-service`)]] — Asynchronous spreadsheet filtering microservice.
* [[Projects/dc-rca-progression|dc-rca-progression (Hub RCA Tracker Dashboard)]] — Distribution center breach resolution tracker.
* [[Projects/spf-final|spf-final (North Loss DB / Cluster Lead View)]] — Seller Protection Fund loss reconciliation engine.
* [[Projects/scm-performance|scm-performance (24-Hr SLA Performance)]] — SCM TAT 24-hour performance tracker.
* [[Projects/shipment_reco|shipment_reco]] — Last-mile hub dispatch and return reconciliation tool.
* [[Projects/shipVerify_BridgeAutomation|shipVerify_BridgeAutomation]] — Inbound scanning and quality audit verification backend.
* [[Projects/pre-alert|pre-alert (Inbound Shipment Pre-Alert & Manifest Dispatcher)]] — Inbound logistics alerting engine.

---

### 🖥️ Operations Consoles & Attendance Monitoring
*Dedicated operational analytics and attendance monitoring consoles.*
* [[Projects/unified-dashboard|unified-dashboard (MRZ Operations Unified Dashboard)]] — Mirzapur hub forward pendency console.
* [[Projects/gas-ops-dashboard|gas-ops-dashboard (Operations Hub Management Suite)]] — Operations hub management dashboard.
* [[Projects/l4d-dashboard|l4d-dashboard (L4D Inactivity Engine & Roster Dashboard)]] — Field agent inactivity and attendance tracker.
* [[Projects/nps|nps (NPS Performance Engine)]] — Net Promoter Score survey feedback tool.

---

### 🚨 Customer Escalations & Grievance Routing
*Automated detection and real-time Telegram dispatch of customer grievance escalations (IMD, delivery disputes, TAT breaches).*
* [[Projects/daily-task-alert-gas|daily-task-alert-gas (Customer Escalation Alert Engine)]]

---

### 💰 Financial Automations & Cash Reconciliation
*Automated tracking of Cash-On-Delivery (COD) remittances, transaction lookups, and account top-ups.*
* [[Projects/cod-automation|cod-automation (Excel Runsheet Bridge & PDF Deposit Slip)]]
* [[Projects/cash-inject|cash-inject (Cash Pickup Transaction Tracker)]]

---

## ⚙️ Core Infrastructure & Services
* [[Services/Myntra-Logistics-Infrastructure|Myntra Logistics Domain Model]]
* [[Services/FastAPI-Render-Bridges|FastAPI Render Streaming Microservices]]
* [[Services/Google-Apps-Script|Google Apps Script Environment & Quotas]]
* [[Services/Cloudflare-DNS|Cloudflare DNS Configuration (1.1.1.1)]]
* [[Services/Network-Optimization|Wi-Fi & Network Adapter Tuning (24 Mbps)]]
