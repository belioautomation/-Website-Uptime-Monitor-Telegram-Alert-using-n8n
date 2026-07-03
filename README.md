# 🌐 Website Uptime Monitor & Telegram Alert using n8n

A lightweight website monitoring workflow built with **n8n**. This automation periodically checks whether a website is online, records the status in Google Sheets, and instantly sends a Telegram notification whenever the website becomes unavailable.

Designed as part of my **30-Day n8n Automation Portfolio**, this project demonstrates API monitoring, conditional workflow logic, automated logging, and real-time notifications.

---

# 📌 Features

- 🌐 Automatically monitors website availability
- ⏰ Runs on a scheduled interval
- 📡 Checks website HTTP status codes
- 📊 Logs every uptime check to Google Sheets
- 🚨 Sends Telegram alerts when a website is offline
- 📈 Maintains a historical uptime log
- 🆓 Uses only free services

---

# 🛠 Technologies Used

- n8n
- Schedule Trigger
- HTTP Request
- IF Node
- Google Sheets API
- Telegram Bot API

---

# 📂 Workflow

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

# ⚙ Workflow Explanation

## 1. Schedule Trigger

Automatically starts the workflow at a fixed interval.

Configuration:

- Trigger: Every 5 Minutes

---

## 2. HTTP Request

Sends a GET request to the target website and retrieves its HTTP response.

Configuration:

- Method: GET
- Authentication: None
- Response Format: JSON
- Include Response Headers and Status: Enabled
- Never Error: Enabled

Example Website:

```
https://www.github.com
```

---

## 3. IF Node

Checks whether the website is online.

Condition:

```
Status Code == 200
```

If **True**

- Save the result to the **Online Log** sheet.

If **False**

- Save the result to the **Offline Log** sheet.
- Send a Telegram notification.

---

## 4. Google Sheets (Online Log)

Stores successful uptime checks.

Example:

| Date | Website | Status | HTTP Code |
|------|----------|--------|-----------|
| 2026-07-03 09:30 | https://github.com | Online | 200 |

---

## 5. Google Sheets (Offline Log)

Stores failed website checks.

Example:

| Date | Website | Status | HTTP Code |
|------|----------|--------|-----------|
| 2026-07-03 10:45 | https://github.com | Offline | 503 |

---

## 6. Telegram

Sends an alert whenever the monitored website becomes unavailable.

Example:

```
🚨 Website Offline Alert

🌐 Website:
https://github.com

❌ Status:
Offline

🔢 HTTP Status:
503

🕒 Checked:
2026-07-03 10:45

🤖 Monitored automatically by n8n.
```

---

# 📊 Google Sheets Structure

| Date | Website | Status | HTTP Code |
|------|----------|--------|-----------|

---

# 📁 Repository Structure

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
│
└── assets/
    └── sample-output.json
```

---

# 📷 Screenshots

Include the following screenshots:

- Complete Workflow
- HTTP Request Node
- IF Node Configuration
- Google Sheets (Online Log)
- Google Sheets (Offline Log)
- Telegram Alert
- Workflow Execution

---

# 🎯 Learning Objectives

This project demonstrates:

- Website monitoring
- HTTP Request integration
- HTTP status code validation
- Conditional workflow logic
- Google Sheets automation
- Telegram notifications
- Scheduled automation
- Real-time uptime monitoring

---

# 🚀 Possible Improvements

- Monitor multiple websites
- Email notifications
- Discord notifications
- Slack notifications
- Website response time tracking
- Downtime analytics dashboard
- Automatic incident reports
- Daily uptime summary
- Integration with Notion or Airtable

---

# 📄 License

This project is licensed under the MIT License.

---

# 🙌 Acknowledgements

- n8n
- Google Sheets API
- Telegram Bot API

---

## ⭐ About

A lightweight website uptime monitoring workflow built with **n8n** that periodically checks website availability, logs HTTP status results to Google Sheets, and sends Telegram alerts whenever a website becomes unavailable.
