# 🌐 Website Uptime Monitor & Telegram Alert using n8n

A lightweight website monitoring workflow built with **n8n**. This workflow automatically checks whether a website is online at scheduled intervals, records the status in Google Sheets, and sends instant Telegram alerts whenever the website becomes unavailable.

Built as part of my **30-Day n8n Automation Portfolio**, this project demonstrates scheduled automation, HTTP monitoring, conditional workflow logic, automated logging, and real-time notifications.

---

## 📌 Features

- 🌐 Monitors website availability automatically
- ⏰ Runs on a scheduled interval
- 📡 Checks website HTTP status codes
- 📊 Logs uptime results to Google Sheets
- 🚨 Sends Telegram alerts when a website is offline
- 📈 Maintains a historical uptime log
- ⚡ Fully automated workflow

---

## 🛠️ Technologies Used

- n8n
- Schedule Trigger
- HTTP Request
- IF Node
- Google Sheets API
- Telegram Bot API

---

## 📂 Workflow

```text
Schedule Trigger
      │
      ▼
HTTP Request
      │
      ▼
IF (Status Code = 200?)
 ┌──────────────┐
 ▼              ▼
Online       Offline
 │              │
 ▼              ▼
Google Sheets Google Sheets
               │
               ▼
           Telegram
```

---

## ⚙️ Workflow Explanation

### 1. Schedule Trigger

Automatically starts the workflow at a fixed interval.

Configuration:

- Trigger: Every 5 Minutes

---

### 2. HTTP Request

Sends an HTTP GET request to the target website and retrieves its response.

Configuration:

- Method: GET
- Authentication: None
- Include Response Status: Enabled
- Never Error: Enabled

Example Website:

```text
https://github.com
```

---

### 3. IF Node

Checks whether the website is online.

Condition:

```text
Status Code == 200
```

If **True**

- Save the result to the **Online Log**

If **False**

- Save the result to the **Offline Log**
- Send a Telegram notification

---

### 4. Google Sheets

Stores all website monitoring results.

**Online Log**

Stores successful uptime checks.

**Offline Log**

Stores failed website checks.

---

### 5. Telegram

Sends an alert whenever the monitored website becomes unavailable.

Example:

```text
🚨 Website Offline Alert

🌐 Website:
https://github.com

❌ Status:
Offline

🔢 HTTP Status:
503

🕒 Checked:
2026-07-03 10:45

🤖 Monitored automatically using n8n.
```

---

## 📊 Google Sheets Structure

| Date | Website | Status | HTTP Code |
|------|----------|--------|-----------|

---

## 📁 Repository Structure

```text
Website-Uptime-Monitor/
│
├── README.md
├── workflow.json
│
├── screenshots/
│   ├── workflow.png
│   ├── http-request.png
│   ├── if-node.png
│   ├── online-sheet.png
│   ├── offline-sheet.png
│   ├── telegram-alert.png
│   └── workflow-execution.png
```

---

## 📷 Screenshots

Include the following screenshots:

- Complete Workflow
- HTTP Request Node
- IF Node Configuration
- Google Sheets (Online Log)
- Google Sheets (Offline Log)
- Telegram Alert
- Workflow Execution

---

## 🎯 Learning Objectives

This project demonstrates:

- Website Monitoring
- HTTP Request Integration
- HTTP Status Code Validation
- Conditional Workflow Logic
- Google Sheets Automation
- Telegram Notifications
- Scheduled Workflow Automation
- Real-Time Uptime Monitoring

---

## 🚀 Future Improvements

- Monitor multiple websites
- Email notifications
- Slack and Discord integration
- Website response time tracking
- Downtime analytics dashboard
- Automatic incident reports
- Daily uptime summaries
- Integration with Notion or Airtable

---

## 📜 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

**Belio C. Sinangote**

BS Information Technology Student  
Cebu Technological University (CTU)

**GitHub:** https://github.com/belioautomation

This project is part of my **30-Day n8n Automation Portfolio**, showcasing practical workflow automation using **n8n**, **HTTP APIs**, and **website monitoring**.
