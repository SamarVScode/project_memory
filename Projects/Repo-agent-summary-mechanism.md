---
type: github-repo
repo: SamarVScode/agent-summary-mechanism
url: https://github.com/SamarVScode/agent-summary-mechanism
stack: [Android, Kotlin, Jetpack Compose, React, Vite, Supabase, Tailwind]
cluster: agent-operations-payout
tags: [project, android, react, supabase, agent-management, leave-system]
---

# 📱 agent-summary-mechanism

## 📌 Executive Summary
Dual-facing operational system comprising an **Android Tracker application** for field/warehouse agents to log daily operations and submit requests, alongside a **React + Vite Admin Dashboard** connected to **Supabase** for reviewing and managing agent leaves and operational summaries.

---

## 🛠️ Subsystems & Stack

### 1. `agentflow-android/` (Mobile Client)
* **Language & Framework:** Kotlin, Android Jetpack Compose, Coroutines.
* **Key Features:** OCR Parser (`OcrParserTest.kt`), Daily Tracker (`TrackerScreen.kt`), release keystore configured (`agentflow-release.jks`).

### 2. `leave-management/admin/` (Web Dashboard)
* **Framework:** React 18, Vite, Tailwind CSS.
* **Database:** Supabase PostgreSQL (`supabase_leave_requests.sql`).
* **Components:** `PendingRequestsTable.jsx`, `LeaveHistoryTable.jsx`, `ReviewModal.jsx`.

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **Hardcoded Supabase Credentials in Frontend:** In `leave-management/admin/src/config.js`, default fallbacks are hardcoded:
  `SUPABASE_URL = "https://matoieqhletkjcjfvars.supabase.co"`
  `SUPABASE_ANON_KEY = "sb_publishable_h4qeENgYle29ywox-PyN3g_A6QG-2XJ"`
  Ensure Row-Level Security (RLS) is strictly enabled in `supabase_leave_requests.sql` so anonymous users cannot read/write unapproved leave records.
* **Android Keystore in VCS:** The file `agentflow-release.jks` is stored directly in the Git repository. Ensure the keystore password and alias are protected or moved to environment secrets in production pipelines.

---

## 🚀 Setup & Runbook
```bash
# Web Dashboard
cd leave-management/admin
npm install
npm run dev

# Android App
cd agentflow-android
./gradlew assembleRelease
```

---

## 🔗 Knowledge Graph Connections
* Connected GAS Payout & Management Services:
  * [[Projects/GAS-live-l4d-test|GAS: Live L4D Inactivity Engine]]
  * [[Projects/GAS-Agent-payout|GAS: Agent payout]]
  * [[Projects/GAS-agent-backend-payout|GAS: agent backend payout]]
  * [[Projects/GAS-userdefinedDB|GAS: userdefinedDB]]
  * [[Projects/GAS-App-Dashborad|GAS: App Dashborad]]
  * [[Projects/GAS-North-Dashboard-Server|GAS: North Dashboard Server]]
