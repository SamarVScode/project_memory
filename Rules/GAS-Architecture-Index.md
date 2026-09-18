# ⚡ GAS Architecture Index & Agent Router

> **AI Coding Agent Fast-Triage Router & Quick-Reference Index**  
> Read this index first. Match the task to an **Archetype** or **Feature**, read **ONLY** the designated sections in [`GAS-Webapp-Architecture-Rulebook.md`](GAS-Webapp-Architecture-Rulebook.md), and verify code against [Section 21 `L1411–1435`](GAS-Webapp-Architecture-Rulebook.md#21-the-master-ai-pre-flight-verification-checklist).

---

## 🤖 System Prompt Directive for AI Agents

```text
You are an expert Google Apps Script Software Architect. Before generating or modifying any GAS code, inspect GAS_ARCHITECTURE_INDEX.md to triage the user's task to its corresponding App Archetype or Feature Sections.
Read ONLY the targeted sections in GAS-Webapp-Architecture-Rulebook.md to conserve context and eliminate hallucinations.
You must strictly follow the 4 Non-Negotiable Core Laws (Flat Scope, Dynamic Headers, Safe Serialization, Client-Side Compute) and pass all 19 verification checks in Section 21 before writing final code.
```

---

## ⚖️ The 4 Non-Negotiable Core Laws (Applies to EVERY App)

| # | Core Law | Rulebook Citation | Mandatory Engineering Constraint |
|:-:|:---|:---|:---|
| **1** | **Flat Scope & Controller Gateways** | [Sec 1.1 `L44–62`](GAS-Webapp-Architecture-Rulebook.md#1-the-12-fatal-ai-pitfalls-in-gas-negative-constraints) & [Sec 3 `L166–235`](GAS-Webapp-Architecture-Rulebook.md#3-the-gs-global-scope-namespacing-rules) | Zero `import`/`export`. Encapsulate logic in frozen objects (`const Svc = Object.freeze({...})`) or TS namespaces. Expose RPC endpoints as top-level globals in `Controller.gs`. Zero top-level `SpreadsheetApp`/`DriveApp` calls. |
| **2** | **The Header Map Law** | [Sec 5.4 `L343–387`](GAS-Webapp-Architecture-Rulebook.md#rule-54-the-header-map-law-zero-hardcoded-column-numbers) | **Zero hardcoded column array indices** (`row[0]`, `row[2]`). Always map headers dynamically from Row 1 using `HeaderResolver.createColumnMap(headers, schemaAliases)` with candidate aliases. |
| **3** | **Safe Serialization Matrix** | [Sec 4 `L236–279`](GAS-Webapp-Architecture-Rulebook.md#4-htmlservice-scriptlets-the-client-template-literal-rule) & [Sec 7 `L425–455`](GAS-Webapp-Architecture-Rulebook.md#7-client-server-bridge-googlescriptrun-serialization-matrix) | **Zero raw `Date` objects** (convert to ISO string). Zero server `Blob` objects (use Base64 or Drive URLs). Zero `Map`/`Set` across RPC. Standard response: `{ success, data, error }`. Client script avoids unescaped regex/slashes/HTML in backticks. |
| **4** | **Client-Side Heavy Compute** | [Sec 8 `L456–509`](GAS-Webapp-Architecture-Rulebook.md#8-client-side-compute-dom-virtualized-batch-chunking) | Treat GAS backend as a dumb data pipe. Filter, sort, aggregate in browser memory (<10ms). For >100 rows, enforce 50-row batch chunking (`requestAnimationFrame`) to eliminate UI freeze. |

---

## 🧭 App Archetype Recipes (Instant Selection Matrix)

| App Archetype | Target Sections to Read | Core Stack & Implementation Focus |
|:---|:---|:---|
| **Archetype A: Read-Only Operations Dashboard & Metric Cockpit** | [Sec 1 `L44–62`](GAS-Webapp-Architecture-Rulebook.md#1-the-12-fatal-ai-pitfalls-in-gas-negative-constraints), [2 `L63–165`](GAS-Webapp-Architecture-Rulebook.md#2-universal-project-scaffolding-multi-file-architecture), [3 `L166–235`](GAS-Webapp-Architecture-Rulebook.md#3-the-gs-global-scope-namespacing-rules), [4 `L236–279`](GAS-Webapp-Architecture-Rulebook.md#4-htmlservice-scriptlets-the-client-template-literal-rule), [5 `L280–387`](GAS-Webapp-Architecture-Rulebook.md#5-high-speed-data-engineering-the-dynamic-header-resolution-law), [6 `L388–424`](GAS-Webapp-Architecture-Rulebook.md#6-the-2-stage-progressive-async-loading-architecture), [7 `L425–455`](GAS-Webapp-Architecture-Rulebook.md#7-client-server-bridge-googlescriptrun-serialization-matrix), [8 `L456–509`](GAS-Webapp-Architecture-Rulebook.md#8-client-side-compute-dom-virtualized-batch-chunking) | 2-Stage progressive load (`INITIAL_STRUCTURE` scriptlet pre-injection), `HeaderResolver.gs`, `fastFormatDate`, client compute, 50-row RAF virtual DOM. |
| **Archetype B: Interactive Grid with Inline Cell Edits & Saving** | [Sec 1 `L44–62`](GAS-Webapp-Architecture-Rulebook.md#1-the-12-fatal-ai-pitfalls-in-gas-negative-constraints), [2 `L63–165`](GAS-Webapp-Architecture-Rulebook.md#2-universal-project-scaffolding-multi-file-architecture), [3 `L166–235`](GAS-Webapp-Architecture-Rulebook.md#3-the-gs-global-scope-namespacing-rules), [5 `L280–387`](GAS-Webapp-Architecture-Rulebook.md#5-high-speed-data-engineering-the-dynamic-header-resolution-law), [7 `L425–455`](GAS-Webapp-Architecture-Rulebook.md#7-client-server-bridge-googlescriptrun-serialization-matrix), [8 `L456–509`](GAS-Webapp-Architecture-Rulebook.md#8-client-side-compute-dom-virtualized-batch-chunking), [13 `L814–907`](GAS-Webapp-Architecture-Rulebook.md#13-interactive-bidirectional-inline-editing-data-validation-sniffing) | `AppState.modifiedMap` dirty tracking, `LockService.getScriptLock(15000)` atomic batch writeback, sheet validation sniffing (`getColumnValidationOptions`). |
| **Archetype C: Camera Photo Capture & Mobile Barcode Scanner** | [Sec 1 `L44–62`](GAS-Webapp-Architecture-Rulebook.md#1-the-12-fatal-ai-pitfalls-in-gas-negative-constraints), [2 `L63–165`](GAS-Webapp-Architecture-Rulebook.md#2-universal-project-scaffolding-multi-file-architecture), [3 `L166–235`](GAS-Webapp-Architecture-Rulebook.md#3-the-gs-global-scope-namespacing-rules), [5 `L280–387`](GAS-Webapp-Architecture-Rulebook.md#5-high-speed-data-engineering-the-dynamic-header-resolution-law), [7 `L425–455`](GAS-Webapp-Architecture-Rulebook.md#7-client-server-bridge-googlescriptrun-serialization-matrix), [15 `L962–1119`](GAS-Webapp-Architecture-Rulebook.md#15-camera-hardware-peripherals-architecture-webrtc-mobile-snaps) | HTML5 capture (`<input capture="environment">`) + canvas compress (1280px JPEG @ 0.8 -> ~250KB) + Drive upload; or `window.open` WebRTC live scanner popup. |
| **Archetype D: Enterprise Multi-Resource Hub & Partitioned Workbooks** | [Sec 1 `L44–62`](GAS-Webapp-Architecture-Rulebook.md#1-the-12-fatal-ai-pitfalls-in-gas-negative-constraints), [2 `L63–165`](GAS-Webapp-Architecture-Rulebook.md#2-universal-project-scaffolding-multi-file-architecture), [3 `L166–235`](GAS-Webapp-Architecture-Rulebook.md#3-the-gs-global-scope-namespacing-rules), [5 `L280–387`](GAS-Webapp-Architecture-Rulebook.md#5-high-speed-data-engineering-the-dynamic-header-resolution-law), [6 `L388–424`](GAS-Webapp-Architecture-Rulebook.md#6-the-2-stage-progressive-async-loading-architecture), [7 `L425–455`](GAS-Webapp-Architecture-Rulebook.md#7-client-server-bridge-googlescriptrun-serialization-matrix), [10 `L646–718`](GAS-Webapp-Architecture-Rulebook.md#10-advanced-google-services-acceleration-engine-sub-250ms-reads), [11 `L719–782`](GAS-Webapp-Architecture-Rulebook.md#11-declarative-multi-resource-schema-registry-schema_registry), [12 `L783–813`](GAS-Webapp-Architecture-Rulebook.md#12-resilient-time-partitioned-tab-discovery-resolvepartitiontab) | Declarative `SCHEMA_REGISTRY`, `FastSheetsEngine.gs` (Sheets API v4 REST for sub-250ms reads), `TabResolver.resolvePartitionTab` (regex partition scanning). |
| **Archetype E: High-Volume Auto-Pruning Ledger** | [Sec 1 `L44–62`](GAS-Webapp-Architecture-Rulebook.md#1-the-12-fatal-ai-pitfalls-in-gas-negative-constraints), [2 `L63–165`](GAS-Webapp-Architecture-Rulebook.md#2-universal-project-scaffolding-multi-file-architecture), [3 `L166–235`](GAS-Webapp-Architecture-Rulebook.md#3-the-gs-global-scope-namespacing-rules), [5 `L280–387`](GAS-Webapp-Architecture-Rulebook.md#5-high-speed-data-engineering-the-dynamic-header-resolution-law), [7 `L425–455`](GAS-Webapp-Architecture-Rulebook.md#7-client-server-bridge-googlescriptrun-serialization-matrix), [14 `L908–961`](GAS-Webapp-Architecture-Rulebook.md#14-rolling-buffer-pruning-storage-quota-management) | `PruningService.pruneByRetentionWindow`, rolling distinct-date sliding window retention (7-14 days), staying safely below 20M cell ceiling. |
| **Archetype F: Hybrid Cloud Microservice Suite (>50MB / Heavy Processing)** | [Sec 1 `L44–62`](GAS-Webapp-Architecture-Rulebook.md#1-the-12-fatal-ai-pitfalls-in-gas-negative-constraints), [2 `L63–165`](GAS-Webapp-Architecture-Rulebook.md#2-universal-project-scaffolding-multi-file-architecture), [3 `L166–235`](GAS-Webapp-Architecture-Rulebook.md#3-the-gs-global-scope-namespacing-rules), [5 `L280–387`](GAS-Webapp-Architecture-Rulebook.md#5-high-speed-data-engineering-the-dynamic-header-resolution-law), [10 `L646–718`](GAS-Webapp-Architecture-Rulebook.md#10-advanced-google-services-acceleration-engine-sub-250ms-reads), [16 `L1120–1148`](GAS-Webapp-Architecture-Rulebook.md#16-hybrid-cloud-microservice-offload-pattern-the-50mb-6-min-escape-hatch) | Zero-DOM FastAPI/Calamine offload, self-deleting 1-minute poller trigger, `ScriptProperties` state tracking, `Sheet.copyTo()` formatting replication. |

---

## 🔍 Feature Capability Lookup Table

| Feature / Capability | Target Section | Key Class / Engine / Pattern |
|:---|:---|:---|
| **Dynamic Column Resolution** | [Sec 5.4 `L343–387`](GAS-Webapp-Architecture-Rulebook.md#rule-54-the-header-map-law-zero-hardcoded-column-numbers) | `HeaderResolver.createColumnMap(headers, aliases)` |
| **Sub-250ms Direct Reads** | [Sec 10 `L646–718`](GAS-Webapp-Architecture-Rulebook.md#10-advanced-google-services-acceleration-engine-sub-250ms-reads) | `FastSheetsEngine.gs` (Sheets API v4 REST `batchGet`) |
| **Sub-Second Initial Load** | [Sec 6 `L388–424`](GAS-Webapp-Architecture-Rulebook.md#6-the-2-stage-progressive-async-loading-architecture) | 2-Stage Async Loading (`INITIAL_STRUCTURE` scriptlet) |
| **Dynamic Partition Tabs** | [Sec 12 `L783–813`](GAS-Webapp-Architecture-Rulebook.md#12-resilient-time-partitioned-tab-discovery-resolvepartitiontab) | `TabResolver.resolvePartitionTab(ss, prefix, date)` |
| **Multi-Resource Routing** | [Sec 11 `L719–782`](GAS-Webapp-Architecture-Rulebook.md#11-declarative-multi-resource-schema-registry-schema_registry) | `SCHEMA_REGISTRY` & `GenericDataService.gs` |
| **Cell Edits & Dirty Tracking** | [Sec 13 `L814–907`](GAS-Webapp-Architecture-Rulebook.md#13-interactive-bidirectional-inline-editing-data-validation-sniffing) | `AppState.modifiedMap` dirty tracking |
| **Atomic Writeback Locking** | [Sec 13 `L814–907`](GAS-Webapp-Architecture-Rulebook.md#13-interactive-bidirectional-inline-editing-data-validation-sniffing) | `LockService.getScriptLock(15000)` concurrency protection |
| **Sheet Validation Sniffing** | [Sec 13 `L814–907`](GAS-Webapp-Architecture-Rulebook.md#13-interactive-bidirectional-inline-editing-data-validation-sniffing) | `getColumnValidationOptions(sheet, colIndex)` |
| **Native Mobile Camera Snap** | [Sec 15 (P1) `L973–1068`](GAS-Webapp-Architecture-Rulebook.md#pattern-1-100-native-html5-camera-snap-zero-setup-mobile-desktop-snaps) | HTML5 Media Capture + Canvas Compress (1280px JPEG @ 0.8) |
| **Continuous Live Barcode** | [Sec 15 (P2) `L1069–1076`](GAS-Webapp-Architecture-Rulebook.md#pattern-2-top-level-tab-popup-for-continuous-live-video-qr-barcode-scanning) | `window.open` Top-Level Tab + WebRTC (ZXing) + `postMessage` |
| **Dedicated Kiosk Peripherals** | [Sec 15 (P3) `L1077–1119`](GAS-Webapp-Architecture-Rulebook.md#pattern-3-the-dedicated-host-shell-bridge-enterprise-kiosks-hardware-workstations) | Dedicated Host Shell Bridge (`window.top.postMessage`) |
| **Rolling Retention Pruning** | [Sec 14 `L908–961`](GAS-Webapp-Architecture-Rulebook.md#14-rolling-buffer-pruning-storage-quota-management) | `PruningService.pruneByRetentionWindow()` (20M cell safe) |
| **Multi-Key Chunk Caching** | [Sec 9 `L510–645`](GAS-Webapp-Architecture-Rulebook.md#9-caching-quotas-enterprise-concurrency-engineering) | `CacheManager.gs` (safe 85KB chunks) |
| **Concurrency Spike Retries** | [Sec 9 `L510–645`](GAS-Webapp-Architecture-Rulebook.md#9-caching-quotas-enterprise-concurrency-engineering) | `callServerWithRetry(fn, args, cb)` (exponential backoff) |
| **Ultra-Fast Date Parsing** | [Sec 5.1 `L282–342`](GAS-Webapp-Architecture-Rulebook.md#rule-51-ban-utilitiesformatdate-in-row-loops) | `fastFormatDate(d)` (native V8 string slicing) |
| **Virtualized DOM Rendering** | [Sec 8 `L456–509`](GAS-Webapp-Architecture-Rulebook.md#8-client-side-compute-dom-virtualized-batch-chunking) | `renderTableChunked(rows, container)` (50 rows/batch RAF) |
| **Styled Client Excel Export** | [Sec 17 (XLSX) `L1168–1202`](GAS-Webapp-Architecture-Rulebook.md#pure-client-side-styled-xlsx-generation-xlsx-js-style) | `exportStyledExcel(data, filename)` (`xlsx-js-style`) |
| **50MB / 6-Min Escape Hatch** | [Sec 16 `L1120–1148`](GAS-Webapp-Architecture-Rulebook.md#16-hybrid-cloud-microservice-offload-pattern-the-50mb-6-min-escape-hatch) | Hybrid Cloud FastAPI Streamer + 1-Min Poller Trigger |
| **Native Clasp TypeScript** | [Sec 19 `L1225–1366`](GAS-Webapp-Architecture-Rulebook.md#19-enterprise-typescript-scaffolding-type-safety-the-clasp-native-standard) | `tsconfig.json` (`module: "None"`) + `types.ts` |
| **Local Clasp Deployments** | [Sec 20 `L1367–1410`](GAS-Webapp-Architecture-Rulebook.md#20-local-development-clasp-push-deploy-workflow) | `clasp push` + `clasp deploy -i <DEPLOYMENT_ID>` |
| **Multi-User Scaling Access** | [Sec 18 `L1203–1224`](GAS-Webapp-Architecture-Rulebook.md#18-deployment-permissions-execute-as-me-multi-user-scaling) | `Execute as: Me` + Sub-second RPC bursts |

---

## 🛡️ Pre-Flight Verification Gate

Before presenting, saving, or deploying any Google Apps Script code, you **MUST** run through the complete 19-gate verification checklist in **[Section 21 of GAS-Webapp-Architecture-Rulebook.md `L1411–1435`](GAS-Webapp-Architecture-Rulebook.md#21-the-master-ai-pre-flight-verification-checklist)**.

### Top Critical Failure Checks:

1. 🛑 **No Node.js ES6 modules in `.gs`** (`import` / `export` forbidden).
2. 🛑 **All services wrapped in frozen objects or TS namespaces** (`const Service = Object.freeze({...})`).
3. 🛑 **All RPC bridge endpoints exposed as top-level functions in `Controller.gs`**.
4. 🛑 **Zero hardcoded column indices (`row[2]`)** — dynamic `HeaderResolver` strictly required.
5. 🛑 **Zero raw `Date` or `Blob` objects returned across `google.script.run`**.
6. 🛑 **Zero `Utilities.formatDate()` inside row loops** — use native V8 string slicing.
7. 🛑 **No unescaped regex/slashes/closing tags inside backtick template literals in client `<script>`**.
8. 🛑 **All external and parent links contain `target="_top"`**.
9. 🛑 **All client-to-server calls wrapped in `callServerWithRetry` exponential backoff**.
10. 🛑 **Clasp subfolder includes use full paths** (`include('Panes/Pane_Dashboard')`).
