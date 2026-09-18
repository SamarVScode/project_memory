---
title: GAS Architecture Index & Agent Router
type: rules
status: active
tags: [rules, google-apps-script, architecture-index, triage-matrix, agent-router, typescript]
created: 2026-09-18
last-updated: 2026-09-18
---

# ⚡ GAS Architecture Index & Agent Router

> **Authoritative Rulebook:** [[GAS-Webapp-Architecture-Rulebook]] | **Dashboard:** [[Dashboard]]


> **AI Coding Agent Fast-Triage Router & Quick-Reference Index**  
> Read this index first. Match the task to an **Archetype** or **Feature**, read **ONLY** the designated sections in [[GAS-Webapp-Architecture-Rulebook|`GAS-Webapp-Architecture-Rulebook.md`]], and verify code against [[GAS-Webapp-Architecture-Rulebook#21. The Master AI Pre-Flight Verification Checklist|Section 21 `L1411–1435`]].

---

## 🤖 System Prompt Directive for AI Agents

```text
You are an expert Google Apps Script Software Architect. Before generating or modifying any GAS code, inspect GAS_ARCHITECTURE_INDEX.md to triage the user's task to its corresponding App Archetype or Feature Sections.
Read ONLY the targeted sections in GAS-Webapp-Architecture-Rulebook.md to conserve context and eliminate hallucinations.
TypeScript (.ts) with Clasp Native Compilation (module: "None") is the Industry-Grade Standard for enterprise visibility, crash prevention, and zero-downtime automated triggers.
You must strictly follow the 4 Non-Negotiable Core Laws (Flat Scope, Dynamic Headers, Safe Serialization, Client-Side Compute) alongside the Enterprise TypeScript Standard, and pass all verification checks in Section 21 before writing final code.
```

---

## ⚖️ The 4 Non-Negotiable Core Laws (Applies to EVERY App)

| # | Core Law | Rulebook Citation | Mandatory Engineering Constraint |
|:-:|:---|:---|:---|
| **1** | **Flat Scope & Controller Gateways** | [[GAS-Webapp-Architecture-Rulebook#1. The 12 Fatal AI Pitfalls in GAS (Negative Constraints)|Sec 1.1 `L44–62`]] & [[GAS-Webapp-Architecture-Rulebook#3. The `.gs` Global Scope & Namespacing Rules|Sec 3 `L166–235`]] | Zero `import`/`export`. Encapsulate logic in frozen objects (`const Svc = Object.freeze({...})`) or TS namespaces. Expose RPC endpoints as top-level globals in `Controller.gs`. Zero top-level `SpreadsheetApp`/`DriveApp` calls. |
| **2** | **The Header Map Law** | [[GAS-Webapp-Architecture-Rulebook#Rule 5.4: The Header Map Law (Zero Hardcoded Column Numbers)|Sec 5.4 `L343–387`]] | **Zero hardcoded column array indices** (`row[0]`, `row[2]`). Always map headers dynamically from Row 1 using `HeaderResolver.createColumnMap(headers, schemaAliases)` with candidate aliases. |
| **3** | **Safe Serialization Matrix** | [[GAS-Webapp-Architecture-Rulebook#4. HtmlService, Scriptlets & The Client Template Literal Rule|Sec 4 `L236–279`]] & [[GAS-Webapp-Architecture-Rulebook#7. Client-Server Bridge (`google.script.run`) & Serialization Matrix|Sec 7 `L425–455`]] | **Zero raw `Date` objects** (convert to ISO string). Zero server `Blob` objects (use Base64 or Drive URLs). Zero `Map`/`Set` across RPC. Standard response: `{ success, data, error }`. Client script avoids unescaped regex/slashes/HTML in backticks. |
| **4** | **Client-Side Heavy Compute** | [[GAS-Webapp-Architecture-Rulebook#8. Client-Side Compute, DOM & Virtualized Batch Chunking|Sec 8 `L456–509`]] | Treat GAS backend as a dumb data pipe. Filter, sort, aggregate in browser memory (<10ms). For >100 rows, enforce 50-row batch chunking (`requestAnimationFrame`) to eliminate UI freeze. |

> [!IMPORTANT] Enterprise Standard Mandate
> **TypeScript (.ts) with Clasp Native Compilation (`module: "None"`) is the Industry-Grade Standard** for enterprise visibility, crash prevention, and zero-downtime automated triggers. All mission-critical backend logic, schema registries, and RPC bridges must enforce strict ambient `types.ts` interface contracts and full `@types/google-apps-script` signature validation.

---

## 🧭 App Archetype Recipes (Instant Selection Matrix)

| App Archetype | Target Sections to Read | Core Stack & Implementation Focus |
|:---|:---|:---|
| **Archetype A: Read-Only Operations Dashboard & Metric Cockpit** | [[GAS-Webapp-Architecture-Rulebook#1. The 12 Fatal AI Pitfalls in GAS (Negative Constraints)|Sec 1 `L44–62`]], [[GAS-Webapp-Architecture-Rulebook#2. Universal Project Scaffolding & Multi-File Architecture|2 `L63–165`]], [[GAS-Webapp-Architecture-Rulebook#3. The `.gs` Global Scope & Namespacing Rules|3 `L166–235`]], [[GAS-Webapp-Architecture-Rulebook#4. HtmlService, Scriptlets & The Client Template Literal Rule|4 `L236–279`]], [[GAS-Webapp-Architecture-Rulebook#5. High-Speed Data Engineering & The Dynamic Header Resolution Law|5 `L280–387`]], [[GAS-Webapp-Architecture-Rulebook#6. The 2-Stage Progressive Async Loading Architecture|6 `L388–424`]], [[GAS-Webapp-Architecture-Rulebook#7. Client-Server Bridge (`google.script.run`) & Serialization Matrix|7 `L425–455`]], [[GAS-Webapp-Architecture-Rulebook#8. Client-Side Compute, DOM & Virtualized Batch Chunking|8 `L456–509`]] | 2-Stage progressive load (`INITIAL_STRUCTURE` scriptlet pre-injection), `HeaderResolver.gs`, `fastFormatDate`, client compute, 50-row RAF virtual DOM. |
| **Archetype B: Interactive Grid with Inline Cell Edits & Saving** | [[GAS-Webapp-Architecture-Rulebook#1. The 12 Fatal AI Pitfalls in GAS (Negative Constraints)|Sec 1 `L44–62`]], [[GAS-Webapp-Architecture-Rulebook#2. Universal Project Scaffolding & Multi-File Architecture|2 `L63–165`]], [[GAS-Webapp-Architecture-Rulebook#3. The `.gs` Global Scope & Namespacing Rules|3 `L166–235`]], [[GAS-Webapp-Architecture-Rulebook#5. High-Speed Data Engineering & The Dynamic Header Resolution Law|5 `L280–387`]], [[GAS-Webapp-Architecture-Rulebook#7. Client-Server Bridge (`google.script.run`) & Serialization Matrix|7 `L425–455`]], [[GAS-Webapp-Architecture-Rulebook#8. Client-Side Compute, DOM & Virtualized Batch Chunking|8 `L456–509`]], [[GAS-Webapp-Architecture-Rulebook#13. Interactive Bidirectional Inline Editing & Data Validation Sniffing|13 `L814–907`]] | `AppState.modifiedMap` dirty tracking, `LockService.getScriptLock(15000)` atomic batch writeback, sheet validation sniffing (`getColumnValidationOptions`). |
| **Archetype C: Camera Photo Capture & Mobile Barcode Scanner** | [[GAS-Webapp-Architecture-Rulebook#1. The 12 Fatal AI Pitfalls in GAS (Negative Constraints)|Sec 1 `L44–62`]], [[GAS-Webapp-Architecture-Rulebook#2. Universal Project Scaffolding & Multi-File Architecture|2 `L63–165`]], [[GAS-Webapp-Architecture-Rulebook#3. The `.gs` Global Scope & Namespacing Rules|3 `L166–235`]], [[GAS-Webapp-Architecture-Rulebook#5. High-Speed Data Engineering & The Dynamic Header Resolution Law|5 `L280–387`]], [[GAS-Webapp-Architecture-Rulebook#7. Client-Server Bridge (`google.script.run`) & Serialization Matrix|7 `L425–455`]], [[GAS-Webapp-Architecture-Rulebook#15. Camera & Hardware Peripherals Architecture (WebRTC & Mobile Snaps)|15 `L962–1119`]] | HTML5 capture (`<input capture="environment">`) + canvas compress (1280px JPEG @ 0.8 -> ~250KB) + Drive upload; or `window.open` WebRTC live scanner popup. |
| **Archetype D: Enterprise Multi-Resource Hub & Partitioned Workbooks** | [[GAS-Webapp-Architecture-Rulebook#1. The 12 Fatal AI Pitfalls in GAS (Negative Constraints)|Sec 1 `L44–62`]], [[GAS-Webapp-Architecture-Rulebook#2. Universal Project Scaffolding & Multi-File Architecture|2 `L63–165`]], [[GAS-Webapp-Architecture-Rulebook#3. The `.gs` Global Scope & Namespacing Rules|3 `L166–235`]], [[GAS-Webapp-Architecture-Rulebook#5. High-Speed Data Engineering & The Dynamic Header Resolution Law|5 `L280–387`]], [[GAS-Webapp-Architecture-Rulebook#6. The 2-Stage Progressive Async Loading Architecture|6 `L388–424`]], [[GAS-Webapp-Architecture-Rulebook#7. Client-Server Bridge (`google.script.run`) & Serialization Matrix|7 `L425–455`]], [[GAS-Webapp-Architecture-Rulebook#10. Advanced Google Services Acceleration Engine (Sub-250ms Reads)|10 `L646–718`]], [[GAS-Webapp-Architecture-Rulebook#11. Declarative Multi-Resource Schema Registry (`SCHEMA_REGISTRY`)|11 `L719–782`]], [[GAS-Webapp-Architecture-Rulebook#12. Resilient Time-Partitioned Tab Discovery (`resolvePartitionTab`)|12 `L783–813`]] | Declarative `SCHEMA_REGISTRY`, `FastSheetsEngine.gs` (Sheets API v4 REST for sub-250ms reads), `TabResolver.resolvePartitionTab` (regex partition scanning). |
| **Archetype E: High-Volume Auto-Pruning Ledger** | [[GAS-Webapp-Architecture-Rulebook#1. The 12 Fatal AI Pitfalls in GAS (Negative Constraints)|Sec 1 `L44–62`]], [[GAS-Webapp-Architecture-Rulebook#2. Universal Project Scaffolding & Multi-File Architecture|2 `L63–165`]], [[GAS-Webapp-Architecture-Rulebook#3. The `.gs` Global Scope & Namespacing Rules|3 `L166–235`]], [[GAS-Webapp-Architecture-Rulebook#5. High-Speed Data Engineering & The Dynamic Header Resolution Law|5 `L280–387`]], [[GAS-Webapp-Architecture-Rulebook#7. Client-Server Bridge (`google.script.run`) & Serialization Matrix|7 `L425–455`]], [[GAS-Webapp-Architecture-Rulebook#14. Rolling Buffer Pruning & Storage Quota Management|14 `L908–961`]] | `PruningService.pruneByRetentionWindow`, rolling distinct-date sliding window retention (7-14 days), staying safely below 20M cell ceiling. |
| **Archetype F: Hybrid Cloud Microservice Suite (>50MB / Heavy Processing)** | [[GAS-Webapp-Architecture-Rulebook#1. The 12 Fatal AI Pitfalls in GAS (Negative Constraints)|Sec 1 `L44–62`]], [[GAS-Webapp-Architecture-Rulebook#2. Universal Project Scaffolding & Multi-File Architecture|2 `L63–165`]], [[GAS-Webapp-Architecture-Rulebook#3. The `.gs` Global Scope & Namespacing Rules|3 `L166–235`]], [[GAS-Webapp-Architecture-Rulebook#5. High-Speed Data Engineering & The Dynamic Header Resolution Law|5 `L280–387`]], [[GAS-Webapp-Architecture-Rulebook#10. Advanced Google Services Acceleration Engine (Sub-250ms Reads)|10 `L646–718`]], [[GAS-Webapp-Architecture-Rulebook#16. Hybrid Cloud Microservice Offload Pattern (The 50MB / 6-Min Escape Hatch)|16 `L1120–1148`]] | Zero-DOM FastAPI/Calamine offload, self-deleting 1-minute poller trigger, `ScriptProperties` state tracking, `Sheet.copyTo()` formatting replication. |

---

## 🔍 Feature Capability Lookup Table

| Feature / Capability | Target Section | Key Class / Engine / Pattern |
|:---|:---|:---|
| **Dynamic Column Resolution** | [[GAS-Webapp-Architecture-Rulebook#Rule 5.4: The Header Map Law (Zero Hardcoded Column Numbers)|Sec 5.4 `L343–387`]] | `HeaderResolver.createColumnMap(headers, aliases)` |
| **Sub-250ms Direct Reads** | [[GAS-Webapp-Architecture-Rulebook#10. Advanced Google Services Acceleration Engine (Sub-250ms Reads)|Sec 10 `L646–718`]] | `FastSheetsEngine.gs` (Sheets API v4 REST `batchGet`) |
| **Sub-Second Initial Load** | [[GAS-Webapp-Architecture-Rulebook#6. The 2-Stage Progressive Async Loading Architecture|Sec 6 `L388–424`]] | 2-Stage Async Loading (`INITIAL_STRUCTURE` scriptlet) |
| **Dynamic Partition Tabs** | [[GAS-Webapp-Architecture-Rulebook#12. Resilient Time-Partitioned Tab Discovery (`resolvePartitionTab`)|Sec 12 `L783–813`]] | `TabResolver.resolvePartitionTab(ss, prefix, date)` |
| **Multi-Resource Routing** | [[GAS-Webapp-Architecture-Rulebook#11. Declarative Multi-Resource Schema Registry (`SCHEMA_REGISTRY`)|Sec 11 `L719–782`]] | `SCHEMA_REGISTRY` & `GenericDataService.gs` |
| **Cell Edits & Dirty Tracking** | [[GAS-Webapp-Architecture-Rulebook#13. Interactive Bidirectional Inline Editing & Data Validation Sniffing|Sec 13 `L814–907`]] | `AppState.modifiedMap` dirty tracking |
| **Atomic Writeback Locking** | [[GAS-Webapp-Architecture-Rulebook#13. Interactive Bidirectional Inline Editing & Data Validation Sniffing|Sec 13 `L814–907`]] | `LockService.getScriptLock(15000)` concurrency protection |
| **Sheet Validation Sniffing** | [[GAS-Webapp-Architecture-Rulebook#13. Interactive Bidirectional Inline Editing & Data Validation Sniffing|Sec 13 `L814–907`]] | `getColumnValidationOptions(sheet, colIndex)` |
| **Native Mobile Camera Snap** | [[GAS-Webapp-Architecture-Rulebook#Pattern 1: 100% Native HTML5 Camera Snap (Zero-Setup, Mobile & Desktop Snaps)|Sec 15 (P1) `L973–1068`]] | HTML5 Media Capture + Canvas Compress (1280px JPEG @ 0.8) |
| **Continuous Live Barcode** | [[GAS-Webapp-Architecture-Rulebook#Pattern 2: Top-Level Tab Popup for Continuous Live Video (QR / Barcode Scanning)|Sec 15 (P2) `L1069–1076`]] | `window.open` Top-Level Tab + WebRTC (ZXing) + `postMessage` |
| **Dedicated Kiosk Peripherals** | [[GAS-Webapp-Architecture-Rulebook#Pattern 3: The Dedicated Host Shell Bridge (Enterprise Kiosks & Hardware Workstations)|Sec 15 (P3) `L1077–1119`]] | Dedicated Host Shell Bridge (`window.top.postMessage`) |
| **Rolling Retention Pruning** | [[GAS-Webapp-Architecture-Rulebook#14. Rolling Buffer Pruning & Storage Quota Management|Sec 14 `L908–961`]] | `PruningService.pruneByRetentionWindow()` (20M cell safe) |
| **Multi-Key Chunk Caching** | [[GAS-Webapp-Architecture-Rulebook#9. Caching, Quotas & Enterprise Concurrency Engineering|Sec 9 `L510–645`]] | `CacheManager.gs` (safe 85KB chunks) |
| **Concurrency Spike Retries** | [[GAS-Webapp-Architecture-Rulebook#9. Caching, Quotas & Enterprise Concurrency Engineering|Sec 9 `L510–645`]] | `callServerWithRetry(fn, args, cb)` (exponential backoff) |
| **Ultra-Fast Date Parsing** | [[GAS-Webapp-Architecture-Rulebook#Rule 5.1: Ban `Utilities.formatDate()` in Row Loops|Sec 5.1 `L282–342`]] | `fastFormatDate(d)` (native V8 string slicing) |
| **Virtualized DOM Rendering** | [[GAS-Webapp-Architecture-Rulebook#8. Client-Side Compute, DOM & Virtualized Batch Chunking|Sec 8 `L456–509`]] | `renderTableChunked(rows, container)` (50 rows/batch RAF) |
| **Styled Client Excel Export** | [[GAS-Webapp-Architecture-Rulebook#Pure Client-Side Styled XLSX Generation (`xlsx-js-style`)|Sec 17 (XLSX) `L1168–1202`]] | `exportStyledExcel(data, filename)` (`xlsx-js-style`) |
| **50MB / 6-Min Escape Hatch** | [[GAS-Webapp-Architecture-Rulebook#16. Hybrid Cloud Microservice Offload Pattern (The 50MB / 6-Min Escape Hatch)|Sec 16 `L1120–1148`]] | Hybrid Cloud FastAPI Streamer + 1-Min Poller Trigger |
| **Enterprise TypeScript Standard** | [[GAS-Webapp-Architecture-Rulebook#19. Enterprise TypeScript Scaffolding & Type Safety (The Clasp Native Standard)|Sec 19 `L1225–1366`]] | **Industry-Grade Enterprise Standard**: TypeScript (`.ts`) with Clasp Native Compilation (`module: "None"`), ambient `types.ts` contracts, full `@types/google-apps-script` signature validation, zero-downtime automated triggers, and 1:1 Stackdriver line parity. |
| **Local Clasp Deployments** | [[GAS-Webapp-Architecture-Rulebook#20. Local Development & `clasp` Push / Deploy Workflow|Sec 20 `L1367–1410`]] | `clasp push` + `clasp deploy -i <DEPLOYMENT_ID>` |
| **Multi-User Scaling Access** | [[GAS-Webapp-Architecture-Rulebook#18. Deployment, Permissions (`Execute as: Me`) & Multi-User Scaling|Sec 18 `L1203–1224`]] | `Execute as: Me` + Sub-second RPC bursts |

---

## 🛡️ Pre-Flight Verification Gate

Before presenting, saving, or deploying any Google Apps Script code, you **MUST** run through the complete verification checklist in **[[GAS-Webapp-Architecture-Rulebook#21. The Master AI Pre-Flight Verification Checklist|Section 21 of GAS-Webapp-Architecture-Rulebook.md `L1411–1435`]]**.

### Top Critical Failure Checks:

1. 🛑 **Mandatory Enterprise TypeScript & Interface Contracts**: All enterprise GAS applications must be authored in TypeScript (`.ts`) using Clasp Native Compilation (`module: "None"`), ambient contract interfaces defined in `types.ts`, full `@types/google-apps-script` signature validation, and pass `tsc --noEmit` with zero errors.
2. 🛑 **No Node.js ES6 modules in `.gs`/`.ts`** (`import` / `export` forbidden under `module: "None"`).
3. 🛑 **All services wrapped in frozen objects or TS namespaces** (`const Service = Object.freeze({...})` or `namespace Service { ... }`).
4. 🛑 **All RPC bridge endpoints exposed as top-level globals in `Controller.ts` / `Controller.gs`**.
5. 🛑 **Zero hardcoded column indices (`row[2]`)** — dynamic `HeaderResolver` strictly required.
6. 🛑 **Zero raw `Date` or `Blob` objects returned across `google.script.run`**.
7. 🛑 **Zero `Utilities.formatDate()` inside row loops** — use native V8 string slicing.
8. 🛑 **No unescaped regex/slashes/closing tags inside backtick template literals in client `<script>`**.
9. 🛑 **All external and parent links contain `target="_top"`**.
10. 🛑 **All client-to-server calls wrapped in `callServerWithRetry` exponential backoff**.
11. 🛑 **Clasp subfolder includes use full paths** (`include('Panes/Pane_Dashboard')`).
