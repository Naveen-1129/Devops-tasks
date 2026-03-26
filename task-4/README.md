# 🔐 AWS WAF Integration with Application Load Balancer (ALB)

![AWS](https://img.shields.io/badge/AWS-WAF%20%7C%20ALB-orange)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)
![License](https://img.shields.io/badge/License-MIT-blue)

---

## 📌 Project Overview

This project demonstrates how to secure a web application by integrating **AWS WAF (Web Application Firewall)** with an **Application Load Balancer (ALB)**.

### 🎯 Key Objectives

* Attach a Web ACL to ALB
* Block traffic from a specific IP address (laptop IP)
* Validate application access before and after applying WAF rules

---

## 🏗️ Architecture

```text
Client → AWS WAF → ALB → EC2 (Nginx)
```

---

## 🛠️ Prerequisites

* AWS Account
* EC2 instance with Nginx installed and running
* Application Load Balancer configured
* Target group attached to ALB
* Security Groups allowing HTTP (port 80)
* Basic AWS knowledge

---

## 🚀 Implementation Steps

### 🔹 Step 1: Verify Application (Before WAF)

1. Go to **EC2 → Load Balancers**
2. Copy ALB DNS name
3. Open in browser:

```bash
http://<alb-dns-name>
```

✅ **Expected Output:**

* Application loads successfully

---

### 🔹 Step 2: Get Your Public IP

Run in browser:

```
what is my ip
```

Example:

```bash
49.xxx.xxx.xxx
```

---

### 🔹 Step 3: Create IP Set

1. Navigate to **AWS WAF → IP Sets**
2. Click **Create IP Set**

**Configuration:**

```text
Name        : block-my-ip
Region      : Same as ALB
IP Version  : IPv4
IP Address  : <your-ip>/32
```

Example:

```bash
49.xxx.xxx.xxx/32
```

---

### 🔹 Step 4: Create Web ACL

1. Go to **AWS WAF → Web ACLs**
2. Click **Create Web ACL**

**Configuration:**

```text
Name         : my-web-acl
Region       : Same as ALB
Resource     : Regional
```

---

### 🔹 Step 5: Attach Web ACL to ALB

1. In Web ACL setup → **Add AWS resources**
2. Select your ALB
3. Click **Add**

---

### 🔹 Step 6: Add Blocking Rule

1. Click **Add rules → Add my own rules**

**Rule Configuration:**

```text
Rule Name   : block-laptop-ip
Rule Type   : IP set rule
IP Set      : block-my-ip
Action      : BLOCK
Priority    : 1
```

---

### 🔹 Step 7: Wait for Deployment

⏳ Allow 1–2 minutes for rule propagation

---

### 🔹 Step 8: Test Application (After WAF)

Open browser:

```bash
http://<alb-dns-name>
```

❌ **Expected Output:**

* HTTP 403 Forbidden
* Access denied

---

## 🔍 Verification

Using curl:

```bash
curl -I http://<alb-dns-name>
```

Expected response:

```bash
HTTP/1.1 403 Forbidden
```

---

## 🔄 Rollback Steps

To unblock your IP:

1. Go to **AWS WAF → Web ACL**
2. Edit rule or remove IP from IP set
3. Save changes

---

## 🧠 Key Learnings

* AWS WAF filters traffic before reaching ALB
* IP sets are effective for blocking specific clients
* Rule priority is critical (lower number = higher priority)
* Always validate changes with real-time testing

---

## 📚 AWS Services Used

* AWS WAF
* Application Load Balancer (ALB)
* Amazon EC2
* Nginx

---

## 👨‍💻 Author

**Naveen Asarala**
DevOps Engineer | AWS | Kubernetes | Terraform


This project is licensed under the MIT License.

