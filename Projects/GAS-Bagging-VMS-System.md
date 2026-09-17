---
type: gas-app
script_name: "Bagging VMS System"
script_id: "1uAIv2MzEv9pfF4x9bfT6LudxU22KRc0zG4B87egvLfDLTQ9nEjNhV8eO"
editor_url: "https://script.google.com/home/projects/1uAIv2MzEv9pfF4x9bfT6LudxU22KRc0zG4B87egvLfDLTQ9nEjNhV8eO/edit"
cluster: "warehouse-vision-vms"
connected_repo: "[[Projects/Repo-Bagging-VMS-overlay]]"
tags: [gas, vms, video-upload, drive-storage, footage-logs]
---

# 📹 GAS: Bagging VMS System (Video Capture Backend)

## 📌 Real-World Architecture (Audited)
Backend video telemetry and asset management service for the [[Projects/Repo-Bagging-VMS-overlay|Bagging-VMS-overlay]] workstation camera system.

### Execution Workflow:
1. **Authenticated Iframe Delivery:** Serves the frontend web application via `doGet()` with `HtmlService.XFrameOptionsMode.ALLOWALL`.
2. **Payload Parsing:** Ingests Base64 WebM VP9 video streams via `uploadVideoRecord(payload)`.
3. **Drive Storage:** Decodes bytes to a `video/webm` blob, formats filename as `BAG_<bagId>_SEAL_<sealId>_<yyyyMMdd_HHmmss>.webm`, and uploads directly to Google Drive Folder `1TYA0VByXijI-v7787GyfzTGrIHd8QA-i`.
4. **Sheet Audit Trail:** Appends log entry to `Footage_Logs` tab in Spreadsheet `1foxi4mQkaqMaZSYVQi1LIQbBVYEuv7Q_yVbPniG7RLA` with start/end timestamps, file size in MB, duration, and direct Drive URL.

---

## 🛠️ Configuration
* **Target Google Drive Folder ID:** `1TYA0VByXijI-v7787GyfzTGrIHd8QA-i`
* **Audit Spreadsheet ID:** `1foxi4mQkaqMaZSYVQi1LIQbBVYEuv7Q_yVbPniG7RLA`
* **Log Tab Name:** `Footage_Logs`
* **Timezone:** `GMT+05:30`

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **Base64 Payload Size Limits:** In Google Apps Script, payloads passed to `google.script.run` cannot exceed **~50 MB**. The frontend VP9 codec bitrate is throttled to ~300–800 kbps to keep typical 30–60 second recordings under 5 MB.
* **Sheet Append Non-Blocking:** The spreadsheet log is wrapped in a `try/catch` to ensure video file creation in Drive succeeds even if the spreadsheet hits a temporary Google lock.
