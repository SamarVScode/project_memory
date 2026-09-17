---
type: gas-app
script_name: "Lake Ingestion Pipeline"
script_id: "1idsSpNf7ENmLjiUIH0lZ4XQiA35Ib-zJdsi47aRWfmeAlbDulOhPJcSP"
editor_url: "https://script.google.com/home/projects/1idsSpNf7ENmLjiUIH0lZ4XQiA35Ib-zJdsi47aRWfmeAlbDulOhPJcSP/edit"
cluster: "logistics-stream-engine"
connected_repo: "[[Projects/Repo-XLSX-STREAM-REPORT-GENERATOR]]"
tags: [gas, data-lake, render-client, async-polling, ei-pipeline]
---

# ⚡ GAS: Lake Ingestion Pipeline (EI Report Client)

## 📌 Real-World Architecture (Audited)
Asynchronous Google Apps Script orchestrator connecting Google Drive data lakes to the Render streaming server [[Projects/Repo-XLSX-STREAM-REPORT-GENERATOR|XLSX-STREAM-REPORT-GENERATOR]].

### Execution Workflow:
1. **Source Export:** Extracts Google Sheet as `.xlsx` to Drive (`1Htvyq9NZriYM6aUed77-S29QTVkJpNWYHXk7Y42GKMg`).
2. **Token Generation:** Generates OAuth token via `ScriptApp.getOAuthToken()` to create an authenticated direct download URL.
3. **Job Submission:** Submits job to `https://xlsx-stream-report-generator.onrender.com`.
4. **Time Trigger Polling:** Stores `job_id` in `ScriptProperties` and schedules a 1-minute time-driven trigger (`MAX_POLL_ATTEMPTS = 180`, up to 3 hours).
5. **Download & Cleanup:** Pulls the assembled OpenXML workbook into Google Drive and removes temporary polling triggers.

---

## 🛠️ Configuration
* **Server Endpoint:** `https://xlsx-stream-report-generator.onrender.com`
* **Target Spreadsheet:** `1Htvyq9NZriYM6aUed77-S29QTVkJpNWYHXk7Y42GKMg`
* **Polling Interval:** 1 minute via GAS Time-Driven Triggers.

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **Domain Sharing Restrictions:** If Google Workspace policies prevent `ANYONE_WITH_LINK` sharing on Drive files, direct link generation can fail unless the OAuth token fallback in `startDriveLinkPipelineFromUI` succeeds.
* **404 Handling:** Uses `PROP_404_COUNT` to handle cold-start restarts on Render free-tier containers.
