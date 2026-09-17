---
type: gas-app
script_name: "HourlyConversionReport"
script_id: "1385RHzZzU52h6Mjs-eUmaQle84gjjHANZ-eX_tvou_JhLdgCwHxnux1M"
editor_url: "https://script.google.com/home/projects/1385RHzZzU52h6Mjs-eUmaQle84gjjHANZ-eX_tvou_JhLdgCwHxnux1M/edit"
cluster: "logistics-stream-engine"
connected_repo: "[[Projects/Repo-xlsx_to_csv_bridge]]"
tags: [gas, hourly-conversion, sameday, telegram-alerts, mrz-hub]
---

# ⚡ GAS: HourlyConversionReport (E2E Sameday Poller)

## 📌 Real-World Architecture (Audited)
Automated hourly report ingestor and alert dispatcher for Mirzapur Hub (`MRZ`).

### Workflow:
1. **Gmail Ingestion:** Scrapes incoming emails every hour from 10:00 AM to 8:00 PM matching `subject:"E2E_sameday_Summary_{{DATE}} {{HOUR}}.xlsx"`.
2. **Streaming Bridge:** Dispatches the attached Excel workbook to [[Projects/Repo-xlsx_to_csv_bridge|xlsx_to_csv_bridge]] on Render (`https://xlsx-to-csv-bridge.onrender.com`).
3. **Data Transformation:** Converts and filters raw rows for target DC `MRZ` across `Agent_view` and `E2E_DC` sheets.
4. **Google Sheets Sync:** Updates the live tracking spreadsheet (`1vuzG3MNccbOBNKBBTQ0kf9yKT8UQLVV7J9AUj1vR5Rw`).
5. **Telegram Dispatch:** Posts structured shift delivery metrics and alert notifications to Telegram Chat `-1003779595579` (Topics 5 and 6).

---

## 🛠️ Configuration & Endpoints
* **Bridge Endpoint:** `https://xlsx-to-csv-bridge.onrender.com`
* **Target DC:** `MRZ` (Mirzapur Hub)
* **Master Sheet ID:** `1vuzG3MNccbOBNKBBTQ0kf9yKT8UQLVV7J9AUj1vR5Rw`
* **Telegram Integration:** Bot Token configured; Topics 5 (`E2E_DC` / Alerts) and 6 (`Agent_view`).

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **Email Arrival Delays:** The script expects reports ~40 minutes past each hour. If emails arrive outside the 10:00–20:40 window, triggers will skip without processing.
* **BOM & CRLF Inconsistencies:** Requires `cleanKey_()` sanitization to strip `\r` and zero-width characters before sheet matching.
