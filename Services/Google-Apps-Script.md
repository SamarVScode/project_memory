# ☁️ Google Apps Script Infrastructure

## Overview
Serverless JavaScript execution platform powering core operations, sheet automations, and enterprise web applications across Myntra SCM.

## Runtime Constraints & Guardrails
* **Execution Timeout:** 6 minutes maximum per trigger.
* **Heap Memory:** ~50 MB RAM per execution context.
* **Mitigation Architecture:**
  * Heavy computational tasks (200 MB+ Excel parsing) are offloaded to [[Projects/Repo-XLSX-STREAM-REPORT-GENERATOR|XLSX-STREAM-REPORT-GENERATOR]] and [[Projects/Repo-xlsx_to_csv_bridge|xlsx_to_csv_bridge]].
  * High-throughput video/camera streaming uses client-side WebM encoding in [[Projects/Repo-Bagging-VMS-overlay|Bagging-VMS-overlay]] with iframe `postMessage` delivery.

## Local Tooling & Deployment
* **CLI:** `@google/clasp` (installed locally at `C:\Users\User\AppData\Roaming\npm\clasp.ps1`).
* **Auth Config:** `$HOME/.clasprc.json`.
