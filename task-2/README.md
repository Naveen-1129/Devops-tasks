# 🧠 MindCircuit DevOps Tasks

This repository demonstrates Linux fundamentals, file operations, text processing, and Jenkins CI/CD job configuration.

---

## 📁 TASK 1: Create Directory Structure

Create `mindcircuit` directory under `/opt` with subdirectories `dir1`, `dir2`, and `dir3`.

```bash
sudo mkdir -p /opt/mindcircuit/dir1 /opt/mindcircuit/dir2 /opt/mindcircuit/dir3
```

---

## 📄 TASK 2: Create Files

Create files in respective directories:

```bash
sudo touch /opt/mindcircuit/dir1/file1
sudo touch /opt/mindcircuit/dir2/file2
sudo touch /opt/mindcircuit/dir3/file3
```

---

## 🕒 TASK 3: Redirect Date & OS Name

Write system date and OS name into `file1`:

```bash
date > /opt/mindcircuit/dir1/file1
uname >> /opt/mindcircuit/dir1/file1
```

---

## 🔢 TASK 4: Count Characters from `/etc/passwd`

Fetch total number of characters from top 15 entries:

```bash
head -n 15 /etc/passwd | wc -m > /opt/mindcircuit/dir2/file2
```

---

## 📋 TASK 5: Copy file2 → file3

```bash
cp /opt/mindcircuit/dir2/file2 /opt/mindcircuit/dir3/file3
```

---

## 🚚 TASK 6: Move file3 → dir1

```bash
mv /opt/mindcircuit/dir3/file3 /opt/mindcircuit/dir1/
```

---

## 🗑️ TASK 7: Cleanup

Delete `dir3` and `file2`:

```bash
rm -f /opt/mindcircuit/dir2/file2
rm -rf /opt/mindcircuit/dir3
```

---

## 🔗 TASK 8: Preserve Data After Deletion

Create `file4` and ensure data persists even if deleted (using hard link):

```bash
echo "Persistent data example" > /opt/mindcircuit/dir1/file4
ln /opt/mindcircuit/dir1/file4 /opt/mindcircuit/dir1/file4_backup
```

---

## 📜 TASK 9: Combine passwd & shadow

Create `file5` with `/etc/passwd` and append last 5 entries of `/etc/shadow`:

```bash
cat /etc/passwd > /opt/mindcircuit/dir1/file5
sudo tail -n 5 /etc/shadow >> /opt/mindcircuit/dir1/file5
```

---

## ✂️ TASK 10: Extract Specific Values

Create file:

```bash
cat <<EOF > /opt/mindcircuit/dir1/file6
Cook:Book-Took
High:Why-Try
spare:care-mare
EOF
```

Extract only required output:

```bash
cut -d'-' -f2 /opt/mindcircuit/dir1/file6
```

**Expected Output:**

```
Took
Try
mare
```

---

## 📂 TASK 11: Directory & File Operations

```bash
mkdir project-dir Jenkins-dir
cd project-dir

mkdir Documents
touch Documents/notes.txt

echo "This is sample content" > Documents/notes.txt
cat Documents/notes.txt

rm Documents/notes.txt

cd ..
rm -rf Jenkins-dir
```

---

## ⚙️ TASK 12: Jenkins Parameterized Job

### 🎯 Objective

Print:

```
hey, "username" don’t forget to terminate the Instance.
```

---

### 🔧 Steps

1. Open Jenkins Dashboard
2. Click **New Item → Freestyle Project**
3. Enable **This project is parameterized**
4. Add:

   * **String Parameter**
   * Name: `USERNAME`

---

### 🖥️ Build Step → Execute Shell

```bash
echo "hey, ${USERNAME} don’t forget to terminate the Instance."
```

---

### ⭐ Recommended (Dynamic Username)

Install plugin:

* **Build User Vars Plugin**

Then use:

```bash
echo "hey, Naveen don’t forget to terminate the Instance."
```

---

## 📌 Notes

* Use `sudo` where required (especially `/opt` and `/etc/shadow`)
* Ensure proper permissions
* Hard links preserve data even after deletion
* Jenkins plugins may be required for dynamic username

---

## 🚀 Getting Started

```bash
git clone https://github.com/<your-username>/mindcircuit-devops-tasks.git
cd mindcircuit-devops-tasks
```

---

## 👨‍💻 Author

**Naveen Asarala**
DevOps Engineer | AWS | Kubernetes | CI/CD

---

