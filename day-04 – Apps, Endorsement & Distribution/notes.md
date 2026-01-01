# 📅 Day 4 – Apps, Endorsement & Distribution (Power BI Service)

## 🎯 Objective

Understand how to **securely distribute Power BI content**, control user access, build **trust in datasets**, and track **usage & adoption**.

---

## 1️⃣ Apps vs Workspace Access

### 🔹 Workspace Access

* Designed for **developers and BI team**
* Used to **build, edit, and manage** reports & datasets
* Roles: Admin, Member, Contributor, Viewer

❌ Not recommended for business users (risk of edits/deletions)

### 🔹 Power BI Apps

* **Read-only package** created from a workspace
* Designed for **end users / business users**
* Clean UI and controlled access

✅ Best practice for sharing reports

### 🆚 Comparison

| Feature        | Workspace  | App            |
| -------------- | ---------- | -------------- |
| Target users   | Developers | Business users |
| Edit rights    | Yes        | No             |
| Safe sharing   | ❌          | ✅              |
| Enterprise use | ❌          | ✅              |

---

## 2️⃣ App Audiences

### 🔹 What is an Audience?

* Allows **different users** to see **different content** in the **same app**
* One app → Multiple audiences

### 🔹 Why Audiences?

* Improves security
* Better user experience
* No need to create multiple apps

### 🔹 Example

* Executives → Summary dashboard
* Managers → Region-level reports
* Sales team → Detailed reports

---

## 3️⃣ Dataset Endorsement

Dataset endorsement helps users **identify trusted data sources**.

### 🟡 Promoted Dataset

* Marked by dataset owner
* Indicates dataset is reliable
* Not officially approved

Use when:

* Dataset is under testing
* Limited audience

### 🟢 Certified Dataset

* Approved by Power BI Admin / Governance team
* Verified and trusted
* Acts as **single source of truth**

Use when:

* Production-ready
* Organization-wide usage

### 🆚 Comparison

| Feature        | Promoted  | Certified   |
| -------------- | --------- | ----------- |
| Approved by    | Developer | Admin       |
| Trust level    | Medium    | High        |
| Org-wide usage | Limited   | Recommended |

---

## 4️⃣ Usage Metrics

### 🔹 What are Usage Metrics?

* Built-in Power BI reports
* Show how reports/apps are used

### 🔹 What can you track?

* Number of views
* Active users
* Popular reports
* Usage trends over time

### 🔹 Why Important?

* Identify unused reports
* Improve report performance
* Demonstrate business value

---

## 🔁 End-to-End Flow

1. Build reports → Workspace
2. Package content → Power BI App
3. Control access → Audiences
4. Build trust → Dataset endorsement
5. Monitor adoption → Usage metrics

---

## 🧠 Best Practice Note

> **Never share workspace access with business users. Always distribute content using Power BI Apps.**

---


