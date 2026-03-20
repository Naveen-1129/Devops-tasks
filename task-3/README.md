## 🔐 TASK 13: AWS IAM Tasks

This section demonstrates AWS Identity and Access Management (IAM) concepts including roles, policies, EC2 access, and MFA.

---

### 🎯 Objective

* Create IAM roles: Developer, Tester, Admin
* Attach S3 and EC2 policies
* Assign IAM role to EC2 for secure S3 access
* Enable Multi-Factor Authentication (MFA)

---

## 👤 1. Create IAM Users

### Steps:

1. Go to **IAM → Users → Create User**
2. Create users:

   * `Developer`
   * `Tester`
   * `Admin`

---

### Attach Policies:

| Group           | Policies                                        |
| --------------- | ----------------------------------------------- |
| Developer-group | AmazonS3ReadOnlyAccess, AmazonEC2ReadOnlyAccess |
| Tester-group    | same as developer                               |
| Admin-group     | AdministratorAccess                             |

---

## 🛡️ 2. Create IAM Roles

### Roles to Create:

* Developer Role
* Tester Role
* Admin Role

👉 Go to:
**IAM → Roles → Create Role**

---

## 🔗 3. Assign IAM Role to EC2 (S3 Access)

### Step 1: Create Role for EC2

1. Select **Trusted Entity → AWS Service**
2. Choose:

   ```
   EC2
   ```
3. Attach policy:

   * `AmazonS3ReadOnlyAccess`

---

### Step 2: Attach Role to EC2

1. Go to **EC2 → Instances**
2. Select your instance
3. Click:

   ```
   Actions → Security → Modify IAM Role
   ```
4. Select role → Save

---

### Step 3: Verify Access

SSH into EC2 and run:

```bash
aws s3 ls
```

---

## 🔐 4. Enable MFA (Multi-Factor Authentication)

### Steps:

1. Go to **IAM → Users**
2. Select a user
3. Click **Security Credentials**
4. Assign MFA device

---

### MFA Options:

* Virtual MFA (Google Authenticator / Authy) ✅ Recommended
* Hardware MFA

---

## 📌 Best Practices

* ✅ Use **least privilege principle**
* ✅ Avoid using root account
* ✅ Prefer **IAM roles over access keys**
* ✅ Enable MFA for:

  * Root account (mandatory)
  * Admin users (highly recommended)
* ✅ Rotate credentials regularly

---

---
