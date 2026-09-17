---
type: gas-app
script_name: "COD Automation"
script_id: "1gcCe2od7PapnNtHzmwc12RMwzGd23nSp-Q-mlSuMeW7sYrV429reEwNQ"
editor_url: "https://script.google.com/home/projects/1gcCe2od7PapnNtHzmwc12RMwzGd23nSp-Q-mlSuMeW7sYrV429reEwNQ/edit"
cluster: "financial-operations"
connected_repo: "[[Projects/Repo-XLSX-STREAM-REPORT-GENERATOR]]"
tags: [gas, cod, runsheet-bridge, pdf-generator, finance]
---

# ⚡ GAS: COD Automation (Excel Runsheet & PDF Bridge)

## 📌 Real-World Architecture (Audited)
Cash-On-Delivery runsheet processing engine and automated PDF deposit slip generation service.

### Execution Flow:
1. **Payload Ingestion:** Ingests runsheet JSON from the `index.html` frontend using `processPastedTextAndGeneratePDF()`.
2. **Concurrency Control:** Acquires a `LockService.getUserLock()` (5000 ms wait) to prevent duplicate remittance generations.
3. **Metrics Calculation:** Computes remittance totals and collection dates across delivery runsheets.
4. **Spreadsheet & PDF Generation:** Generates the structured Google Sheet, flushes changes, exports the PDF deposit slip, and archives both to Google Drive folders.

---

## 🛠️ Configuration
* **Target Spreadsheet ID:** `1JL7dO-CWo6B3HaG0UbcIpgmVmBqlRTGgjmvsUsL0Ifw`
* **Primary Drive Folder:** `1d69rY5MCHYj7zWKP8mi0VSACXYoXMLkN`
* **Archive PDF Folder:** `1S-q1DUU8_3FeE8cDr74TzmK0rVpbXdwd`

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **Lock Timeouts:** If a user submits large runsheet JSON payloads while another thread is rendering PDFs, `LockService` can throw `"Server execution lock timeout"`.
* **Direct Object References:** The code avoids `SpreadsheetApp.openById()` in inner functions by passing around the active spreadsheet object directly to prevent Google Apps Script quota limits.
