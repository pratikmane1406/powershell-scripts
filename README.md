# 💻 Disk Space Monitor (PowerShell)

## 📌 Overview
This PowerShell script monitors disk usage on Windows systems and alerts administrators when free space drops below a defined threshold.

## 🚀 Features
- Checks all local drives
- Calculates free space percentage
- Logs results to a file
- Displays console alerts
- Optional email notification support

## ⚙️ Requirements
- Windows OS
- PowerShell 5.1 or later

## 📂 Script Details
- Script Name: disk-space-monitor.ps1
- Log Location: C:\Logs\DiskSpaceReport.txt
- Default Threshold: 20% free space

## ▶️ How to Run

```powershell
.\disk-space-monitor.ps1
---------------------------------------------------------------------------------------------------------------------------------------

# 🛡️ Windows Event Monitoring Script – README

## 📌 Overview

This PowerShell script scans Windows Event Logs across one or more servers and generates a **security & system alert report** based on critical event IDs.

It helps administrators quickly identify:

* Failed logins
* Account lockouts
* User/account changes
* Service disruptions
* Unexpected shutdowns
* Audit log tampering

---

## ⚙️ Parameters

| Parameter    | Type     | Default          | Description                  |
| ------------ | -------- | ---------------- | ---------------------------- |
| `Servers`    | string[] | Local machine    | List of servers to scan      |
| `HoursBack`  | int      | 24               | Time window for event search |
| `ReportPath` | string   | `C:\Lab\Reports` | Path to save the CSV report  |

---

## 🔍 What It Monitors

| Event ID(s)      | Log      | Severity | Description              |
| ---------------- | -------- | -------- | ------------------------ |
| 4625             | Security | High     | Failed Logon             |
| 4740             | Security | Critical | Account Lockout          |
| 4720             | Security | High     | New User Created         |
| 4728, 4732, 4756 | Security | Critical | Group Membership Changed |
| 7036             | System   | Medium   | Service State Changed    |
| 6008, 41         | System   | High     | Unexpected Shutdown      |
| 4698             | Security | High     | Scheduled Task Created   |
| 1102             | Security | Critical | Audit Log Cleared        |

---

## 🚀 How to Use

### ▶️ Run for local machine (default)

```powershell
.\EventMonitor.ps1
```

### ▶️ Run for multiple servers

```powershell
.\EventMonitor.ps1 -Servers "Server1","Server2"
```

### ▶️ Change time range (last 12 hours)

```powershell
.\EventMonitor.ps1 -HoursBack 12
```

### ▶️ Custom report location

```powershell
.\EventMonitor.ps1 -ReportPath "D:\Reports"
```

---

## 📊 Output

### ✅ Console Output

* Displays alerts sorted by **severity**
* Color-coded:

  * 🔴 Critical
  * 🟡 High
  * ⚪ Medium/Low

Example:

```
[Critical] SERVER01   Account Lockout              Count:   3  Latest:14:32
[High]     SERVER01   Failed Logon                 Count:  25  Latest:15:10
```

---

### 📁 CSV Report

* Automatically saved in:

```
C:\Lab\Reports\EventAlerts_YYYY-MM-DD_HHMM.csv
```

* Contains:

  * Server
  * Severity
  * Alert Name
  * Event IDs
  * Count
  * Latest occurrence time
  * Log Name

---

## 🧠 How It Works

1. Defines alert rules (`$checks`)
2. Queries logs using `Get-WinEvent`
3. Filters events by:

   * Event ID
   * Log name
   * Time range
4. Aggregates results into custom objects
5. Sorts by severity
6. Outputs to console + CSV

---

## ⚠️ Requirements

* PowerShell 5.1 or later
* Administrative privileges (recommended)
* Remote access enabled for target servers:

  * WinRM / RPC access
  * Proper firewall rules

---

## 💡 Use Cases

* Daily security monitoring
* Incident response
* Audit compliance checks
* Detecting suspicious activity
* Server health tracking

---

## 🔥 Future Enhancements (Optional Ideas)

* Email alerts (Send-MailMessage)
* Teams/Slack integration
* Scheduled Task automation
* HTML dashboard report
* Real-time monitoring

---

## 👨‍💻 Author Notes

This script is designed as a **lightweight SOC-style monitoring tool** using native PowerShell.
It can be extended into enterprise monitoring or integrated with SIEM solutions.

---

## 📌 Summary

✔ Centralized event monitoring
✔ Multi-server support
✔ Severity-based alerting
✔ CSV reporting for audits
✔ Easy to extend and automate

---
