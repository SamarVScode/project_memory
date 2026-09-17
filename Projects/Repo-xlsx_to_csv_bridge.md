---
type: github-repo
repo: SamarVScode/xlsx_to_csv_bridge
url: https://github.com/SamarVScode/xlsx_to_csv_bridge
stack: [Python 3.9+, FastAPI, xlsx2csv, Render]
cluster: logistics-stream-engine
tags: [project, bridge, gas-integration, streaming, excel-to-csv]
---

# 🌉 xlsx_to_csv_bridge

## 📌 Executive Summary
High-speed HTTP streaming bridge built specifically for **Google Apps Script** to overcome GAS's strict 50 MB execution memory limit and 6-minute timeout. It ingests `.xlsx` files uploaded or referenced by GAS, converts them into chunked `.csv` streams on the fly, and returns data safely.

---

## 🛠️ Tech Stack & Key Configurations
* **Runtime:** Python 3.9+ (FastAPI + Uvicorn)
* **Conversion Engine:** `xlsx2csv` (memory-buffered streaming)
* **CORS Scope:** Locked strictly to `https://script.google.com`
* **Hosting:** Render Free/Starter Web Service (optimized for 512 MB RAM limit).

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **Empty Documentation in Repo:** The repository's `README.md` contains only 1 line (`# xlsx_to_csv_bridge`). Deployment steps exist only in `deployment.md`.
* **Port Binding Syntax:** In `deployment.md`, the start command is hardcoded to `--port 10000`. On Render, the `$PORT` environment variable should be passed dynamically: `uvicorn main:app --host 0.0.0.0 --port ${PORT:-10000}`.
* **Header Authorization:** Requests require the `X-API-KEY` header matching `MY_SECRET_API_KEY` defined in the Render dashboard.

---

## 🚀 Setup & Runbook
```bash
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 10000
```

### Environment Variables
* `MY_SECRET_API_KEY`: Secret shared with Google Apps Script `Code.gs`.
* `PYTHON_VERSION`: `3.9.0`

---

## 🔗 Knowledge Graph Connections
* Connected Hub: [[Projects/Repo-XLSX-STREAM-REPORT-GENERATOR|XLSX-STREAM-REPORT-GENERATOR]]
* Connected GAS Scripts:
  * [[Projects/GAS-EI-Pan-India-Report|GAS: EI Pan India Report]]
  * [[Projects/GAS-Lake-Ingestion-Pipeline|GAS: Lake Ingestion Pipeline]]
  * [[Projects/GAS-shipVerify-Bridge|GAS: shipVerify_BridgeAuto]]
