# 🌐 Website Uptime Monitor & Telegram Alert — n8n Automation

![n8n](https://img.shields.io/badge/n8n-Automation-orange)
![HTTP](https://img.shields.io/badge/API-HTTP%20Request-blue)
![Google Sheets](https://img.shields.io/badge/Database-Google%20Sheets-green)
![Telegram](https://img.shields.io/badge/Notification-Telegram-blue)
![License](https://img.shields.io/badge/license-MIT-green)

A website monitoring automation workflow built using **n8n**, **HTTP Request**, **Google Sheets**, and **Telegram Bot API**.

This system automatically checks website availability at scheduled intervals, validates HTTP response codes, records uptime monitoring results, maintains historical logs in Google Sheets, and sends real-time Telegram alerts when a website becomes unavailable.

**Stack:**  
n8n · HTTP Request API · Google Sheets · Telegram Bot · Scheduled Automation · Monitoring System


---

# 🎯 Project Overview


## Problem

Website downtime can negatively impact users, businesses, and online services.

Common challenges include:

- Manual website checking
- Delayed detection of outages
- Missing downtime events
- Lack of uptime history tracking
- Slow incident response


Common scenarios:

- Personal websites
- Business applications
- APIs
- Online services
- Portfolio websites


---

## Solution

This project creates an automated website monitoring system by:


1. Running scheduled website checks
2. Sending HTTP requests automatically
3. Validating website response status
4. Logging uptime results
5. Detecting website failures
6. Sending Telegram alerts during downtime


The workflow acts as a lightweight monitoring assistant that continuously tracks website availability without manual checking.


---

# ✨ Features


## Website Monitoring

✅ Automatic website health checks  
✅ Scheduled monitoring intervals  
✅ HTTP status code validation  
✅ Online/offline detection  


## Data Management

✅ Google Sheets uptime database  
✅ Historical monitoring records  
✅ Automated status logging  
✅ Downtime tracking  


## Notifications

✅ Telegram downtime alerts  
✅ Real-time monitoring updates  
✅ Instant incident notification  


## Automation

✅ Fully automated workflow  
✅ Event-driven monitoring pipeline  
✅ No manual monitoring required  


---

# 🗺️ System Architecture


```mermaid
flowchart TD

A["⏰ Schedule Trigger"]

--> B["🌐 HTTP Request"]


B --> C["🔀 IF Status Code Check"]


C -->|200 OK| D["🟢 Online Log"]


C -->|Error / Failed| E["🔴 Offline Log"]


D --> F["📊 Google Sheets"]


E --> F


E --> G["📱 Telegram Alert"]

````

---

# 🏗️ Workflow Implementation

# Workflow 1: Website Monitoring Pipeline

## Node 1 — Schedule Trigger

### Purpose

Automatically starts the monitoring workflow at a configured interval.

Configuration:

```text
Trigger:

Every 5 Minutes
```

Execution Flow:

```text
Scheduled Time

      ↓

Start Website Check

      ↓

Send HTTP Request
```

---

# Node 2 — HTTP Request

### Purpose

Checks the availability of the target website by sending an HTTP GET request.

Configuration:

```text
Method:

GET


Authentication:

None


Response:

Include Status Code


Error Handling:

Never Error
```

Example:

```text
https://github.com
```

Captured Information:

| Field         | Description      |
| ------------- | ---------------- |
| Status Code   | Website response |
| Response Time | Server response  |
| URL           | Checked website  |
| Timestamp     | Check time       |

Example Response:

```json
{
"url":
"https://github.com",

"statusCode":
200,

"status":
"Online"
}
```

---

# Node 3 — IF Node

### Purpose

Determines whether the website is available.

Condition:

```javascript
statusCode == 200
```

## TRUE Branch

Website is online:

* Save uptime record
* Continue monitoring

## FALSE Branch

Website is offline:

* Save downtime record
* Send Telegram alert

---

# Node 4 — Google Sheets

### Purpose

Store website monitoring history.

Database Structure:

| Field     | Description          |
| --------- | -------------------- |
| Date      | Monitoring timestamp |
| Website   | Target URL           |
| Status    | Online/Offline       |
| HTTP Code | Response status      |

Example:

| Website     | Status  | HTTP Code |
| ----------- | ------- | --------- |
| github.com  | Online  | 200       |
| example.com | Offline | 503       |

---

# Node 5 — Telegram Notification

### Purpose

Send instant alerts when a monitored website becomes unavailable.

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

# 🔐 Credentials Required

| Service              | Purpose               |
| -------------------- | --------------------- |
| Google Sheets OAuth2 | Store monitoring logs |
| Telegram Bot API     | Send alerts           |
| n8n Instance         | Workflow execution    |

---

# ⚙️ Setup Guide

## 1. Configure Schedule Trigger

Set monitoring frequency.

Example:

```text
Every 5 Minutes
```

Test workflow execution.

---

## 2. Configure HTTP Request

Add target website URL.

Required:

```text
Website URL

GET Method

Response Status Enabled
```

Test response detection.

---

## 3. Create Google Sheets Database

Create:

```text
Website Monitoring Logs
```

Columns:

```text
Date

Website

Status

HTTP Code
```

---

## 4. Configure Telegram Bot

Steps:

1. Create Telegram bot using BotFather
2. Copy bot token
3. Add Telegram credentials in n8n
4. Configure chat ID

---

## 5. Import Workflow

Import:

```text
workflow.json
```

Configure:

* Website URL
* Google Sheets
* Telegram credentials

Activate workflow.

---

# 🧪 Testing Checklist

| Test Case            | Expected Result      |
| -------------------- | -------------------- |
| Schedule executes    | Workflow starts      |
| HTTP Request runs    | Website checked      |
| Status code received | Condition evaluated  |
| Website online       | Saved to Online Log  |
| Website offline      | Saved to Offline Log |
| Telegram executes    | Alert received       |

---

# 📁 Repository Structure

```text
Website-Uptime-Monitor-n8n/

│
├── README.md
│
├── workflow.json
│
├── screenshots/
│
│   ├── workflow.png
│   ├── schedule-trigger.png
│   ├── http-request.png
│   ├── if-node.png
│   ├── online-sheet.png
│   ├── offline-sheet.png
│   ├── telegram-alert.png
│   └── execution-result.png
│
└── LICENSE
```

---

# 📸 Screenshots

Recommended screenshots:

* Complete workflow
* Schedule Trigger configuration
* HTTP Request response
* IF Node condition
* Online Google Sheets log
* Offline Google Sheets log
* Telegram alert
* Workflow execution result

---

# 🚀 Future Improvements

| Feature                     | Implementation            |
| --------------------------- | ------------------------- |
| Multiple Website Monitoring | Monitor many URLs         |
| Response Time Tracking      | Measure website speed     |
| Email Alerts                | Add Gmail notifications   |
| Slack Integration           | Team notifications        |
| Discord Integration         | Community alerts          |
| Incident Reports            | Generate downtime reports |
| Analytics Dashboard         | Uptime visualization      |
| Notion Database             | Knowledge management      |

---

# 🎓 Skills Applied

## Automation

* n8n Workflow Automation
* Scheduled workflows
* Monitoring pipelines

## APIs

* HTTP Request Integration
* REST API communication
* Status code validation

## Data Management

* Google Sheets automation
* Monitoring logs
* Data organization

## Programming

* Conditional workflow logic
* Data processing
* Automation design

## Business Automation

* Website monitoring
* Incident detection
* Real-time notifications

---

# 📚 Learning Objectives

This project demonstrates:

* Building automated monitoring systems
* Working with HTTP APIs
* Creating scheduled workflows
* Implementing conditional logic
* Logging automation results
* Building notification systems

---

# 🙌 Acknowledgements

* n8n
* Google Sheets API
* Telegram Bot API
* HTTP Web Services

---

# 👨‍💻 Author

**Belio C. Sinangote**

BS Information Technology Student
Cebu Technological University (CTU)

GitHub:

[https://github.com/belioautomation](https://github.com/belioautomation)

This project is part of my **30-Day n8n Automation Portfolio**, showcasing practical automation solutions using **n8n, APIs, monitoring systems, and workflow automation**.

---

# 📄 License

MIT License

```
```
