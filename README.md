# API Load & Performance Testing | Apache JMeter

## Overview
This project demonstrates **API-level load and performance testing** using **Apache JMeter 5.6.3**.  
It simulates realistic backend traffic across multiple user roles with weighted request distribution.

> **Scope:** Backend API testing only. UI/frontend not included.

---

## 🎯 Objectives
- Measure API response time and throughput under load
- Validate backend stability during sustained traffic
- Model realistic user behavior across roles
- Identify bottlenecks under constrained conditions

---

## 📋 Project Info
| **Attribute**      | **Value**                     |
|--------------------|-------------------------------|
| Tool               | Apache JMeter 5.6.3           |
| Test Type          | API Load & Performance        |
| Execution Mode     | Non-GUI (CLI)                 |
| Scope              | Backend APIs only             |

---

## ✅ Test Coverage
**Included:**
- Guest users (unauthenticated)
- Authenticated users
- Dealer users
- Browsing, engagement, and payment flows

**Not Included:**  
UI testing, production environments

---

## 📊 Traffic Distribution
| **Action Type** | **Weight** |
|-----------------|------------|
| Browsing        | 80%        |
| Engagement      | 15%        |
| Payment         | 5%         |

---

## 🔄 User Flows
- **Guest Flow:** Unauthenticated browsing
- **User Flow:** Login once → token reused across loops
- **Dealer Flow:** Dealer-specific authenticated actions

---

## 🔗 Correlation Handling
- Auth tokens
- Dynamic IDs
- Session-specific values

---

## ⚙️ CLI Execution Example
```bash
cd C:\apache-jmeter-5.6.3\bin
jmeter -n -t "path\to\test_plan.jmx" -l "path\to\results.jtl" -e -o "path\to\report"
```

---

## 🧩 Test Flow Structure
```
Guest Users
 └─ Browsing Flow

Authenticated Users
 ├─ Login (once) → Token Extraction
 └─ Loop
     ├─ Browsing (80%)
     ├─ Engagement (15%)
     └─ Payment (5%)

Dealer Users
 ├─ Login (once) → Token Extraction
 └─ Loop
     ├─ Browsing (80%)
     ├─ Engagement (15%)
     └─ Payment (5%)
```

---

## ⚠️ Known Constraints
- Rate-limited APIs may return `HTTP 429`
- Payment endpoints may throttle under high concurrency

---

## 🛠️ Tools & Technologies
- Apache JMeter 5.6.3
- CLI execution for performance optimization
- JTL result files for analysis
