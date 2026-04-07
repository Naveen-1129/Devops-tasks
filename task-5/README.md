# 🚀 AWS Transit Gateway Setup (Console-Based Lab)

## 📌 Objective
Learn how to create and configure an **AWS Transit Gateway (TGW)** using the AWS Management Console to enable communication between multiple VPCs.

---

## 🧠 Overview

AWS Transit Gateway acts as a **central hub** to connect:
- Multiple VPCs
- On-premises networks (via VPN/Direct Connect)

It simplifies networking using a **hub-and-spoke model** instead of complex VPC peering.

---

## 🏗️ Architecture

- VPC-1 → CIDR: `10.0.0.0/16`
- VPC-2 → CIDR: `10.1.0.0/16`
- Transit Gateway → Central routing hub
- EC2 instances → Used for connectivity testing

---

## 🛠️ Prerequisites

- AWS Account
- Basic knowledge of:
  - VPC
  - Subnets
  - Route Tables
  - EC2

---

## ⚙️ Step-by-Step Implementation

### 🔹 Step 1: Open VPC Dashboard
1. Login to AWS Console
2. Search for **VPC**
3. Open **VPC Dashboard**

---

### 🔹 Step 2: Create Transit Gateway

1. Navigate to:
VPC → Transit Gateways → Create Transit Gateway

2. Provide:
- Name: `my-tgw`
- Leave defaults (DNS support enabled recommended)

3. Click **Create**

---

### 🔹 Step 3: Create VPCs

Create two VPCs:

| VPC Name | CIDR Block      |
|----------|----------------|
| VPC-1    | 10.0.0.0/16     |
| VPC-2    | 10.1.0.0/16     |

Ensure each VPC has:
- At least one subnet
- Route table

---

### 🔹 Step 4: Create TGW Attachments

1. Navigate to:
2. Transit Gateway Attachments → Create attachment
   
2. Select:
- Resource Type: VPC
- Choose VPC
- Select subnets (one per AZ)

3. Repeat for both VPCs

---

### 🔹 Step 5: Update VPC Route Tables

#### For VPC-1:
Destination: 10.1.0.0/16
Target: Transit Gateway


#### For VPC-2:

Destination: 10.0.0.0/16
Target: Transit Gateway

---

### 🔹 Step 6: Update Transit Gateway Route Table

1. Navigate to:

Transit Gateway Route Tables


2. Add routes:


10.0.0.0/16 → VPC-1 attachment
10.1.0.0/16 → VPC-2 attachment


---

### 🔹 Step 7: Launch EC2 Instances

- Launch one EC2 instance in each VPC
- Ensure:
  - Security Group allows ICMP (ping) or SSH

---

### 🔹 Step 8: Test Connectivity

From EC2 in VPC-1:

```bash
ping <private-ip-of-ec2-in-vpc2>

✅ If successful → TGW is working correctly
