---
type: gas-app
script_name: "userdefinedDB"
script_id: "1IuUyTgsvqjs1NC8h4OtbHAiADHqKbab2s0qMTreId1aD96NB5JxkvVK6"
editor_url: "https://script.google.com/home/projects/1IuUyTgsvqjs1NC8h4OtbHAiADHqKbab2s0qMTreId1aD96NB5JxkvVK6/edit"
cluster: "mrz-operations-hub"
connected_repo: "[[Projects/Repo-agent-summary-mechanism]]"
tags: [gas, backend, mrz-ops-dashboard, central-db, relational-sheets]
---

# 🏛️ GAS: userdefinedDB (MRZ OPS DASHBOARD Backend)

## 📌 Real-World Architecture (Audited)
The master operational backend service for the **MRZ OPS DASHBOARD (Mirzapur MYNTRA Hub - `MRZ`)**. Acts as a centralized schema controller and relational database engine routing queries across 10+ operational Google Sheets and Google Forms.

---

## 🗄️ Linked Systems & Datastores (`SYSTEM_CONFIG`)

| Subsystem | Spreadsheet ID | Target Tab | Key Fields Tracked |
| :--- | :--- | :--- | :--- |
| **Forward Pendency** | `18RMRu7rCWKESWLw29U1nZSNpBpauPEU7m4TE7bwXDLs` | `FIRST_TAB` | `Tracking No`, `Ageing`, `RCA` |
| **BRSNR** | `1FNhmEqcQSLJg37ymzcTYDld6_ujPj0mD3bnHrvcrrWg` | `Pendency Till Date` | `ShipmentId`, `TotalPrice`, `Video Footage`, `Ticket ID` |
| **TASKY** | `1c9QrKJ-EPHUYi-QYgd1zuUY3bcTo4uHW5K7qsRbqeCs` | `Tasks` | `Final_Tracking_Number`, `Attribute`, `Status` |
| **RVP Q2 (Reverse)** | `1LPIyz836cmnIjFG0kpVByDt2TfpntGOX4eiPreaPyc4` | `RVP Q2` | `tracking_number`, `reject_reason`, `OPS RCA` |
| **RTO Q2 (Return)** | `1LPIyz836cmnIjFG0kpVByDt2TfpntGOX4eiPreaPyc4` | `RTO Q2` | `tracking_number`, `GMV`, `RCA` |
| **SPF Loss** | `1gYvbUD94skoX34FsqkImV3yKD-8fdYGwrvtWonS2TBM` | `FIRST_TAB` | `tracking_number`, `issue_category`, `final_amount` |
| **COD Synergy** | `1mS9hIiqZWbXUsCiWFgCW_ZEqjcPPyhibJ_AIkK6aqwg` | `NORTH` | `Collection Date`, `Deposit slip number` |
| **EOB Pendency** | `1Ik8EsOA5EUs_v0Qy6pi9S8RWoFwk40FgOiDDh7tRhf0` | `FIRST_TAB` | `tracking_no`, `Ageing Bucket`, `RCA` |
| **Reverse Bagging** | `1WyFf-TO66z9kN5KWzVG9mAl2QTUXL_QLX4e3ZraXTDg` | `FIRST_TAB` | `TRACKING ID`, `Current Location`, `RCA` |
| **Wishmaster Yesterday** | `1avV2Tx9SGaaUeFu2alONmXeXkGYqE4I5r1ZncPYmY7M` | `Agent_view` | `AgentName`, `ofd`, `ofp`, `del_update` |
| **Wishmaster Current** | `1vuzG3MNccbOBNKBBTQ0kf9yKT8UQLVV7J9AUj1vR5Rw` | `Agent_view` | `AgentName`, `ofd`, `ofp`, `del_update` |

---

## ⚠️ Known Gotchas & Bugs (Audit)
* **High Column Variance:** The script must handle 12 different case/underscore variations of Hub identifiers (`"Source DC"`, `"source_dc"`, `"hubname"`, etc.) due to inconsistent upstream Excel formats.
* **Batching Limits:** The script spans 1,106 lines and multiple `openById` connections; querying all cards simultaneously can exceed Google Apps Script's execution quota if cache layers fail.
