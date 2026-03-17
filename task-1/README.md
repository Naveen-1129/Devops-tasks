# 🐧 Linux Practice Tasks

This repository contains **basic to intermediate Linux command-line practice tasks**.  
It is designed for **Linux beginners, DevOps engineers, and system administrators** who want to strengthen their Linux fundamentals.

The tasks cover:

- File and directory management
- File permissions and ownership
- Searching and viewing files
- Process and system monitoring
- Package management
- Networking basics

---

# 📂 Project Setup

Create the practice directory:

```bash
mkdir ~/linux_practice
cd ~/linux_practice
```

Create practice files:

```bash
touch file{1..5}.txt
```

---

# Level 1: Basic Linux Commands

### 1. Create a directory called `linux_practice`

```bash
mkdir ~/linux_practice
```

### 2. Create 5 empty files

```bash
touch ~/linux_practice/file{1..5}.txt
```

### 3. Write your name and today's date into `file1.txt`

```bash
echo "Your Name $(date)" > ~/linux_practice/file1.txt
```

### 4. Display file contents

```bash
cat ~/linux_practice/file1.txt
less ~/linux_practice/file1.txt
```

### 5. Copy `file1.txt`

```bash
cp ~/linux_practice/file1.txt ~/linux_practice/backup_file1.txt
```

### 6. Rename `file2.txt` to `data.txt`

```bash
mv ~/linux_practice/file2.txt ~/linux_practice/data.txt
```

### 7. Delete `file5.txt`

```bash
rm ~/linux_practice/file5.txt
```

---

# Level 2: File Permissions & Ownership

### 8. Check permissions

```bash
ls -l ~/linux_practice
```

### 9. Change permission of `data.txt` to `rw-r-----`

```bash
chmod 640 ~/linux_practice/data.txt
```

### 10. Make `file3.txt` executable

```bash
chmod +x ~/linux_practice/file3.txt
```

### 11. Change ownership of `file4.txt`

```bash
sudo chown username ~/linux_practice/file4.txt
```

### 12. Permission Explanation

| Permission | Meaning |
|-------------|--------|
| r | Read |
| w | Write |
| x | Execute |

Example:

```
-rwxr-xr--
```

Owner → read, write, execute  
Group → read, execute  
Others → read

---

# Level 3: Searching & Viewing Files

### 13. Search for the word **Linux**

```bash
grep "Linux" ~/linux_practice/*.txt
```

### 14. Count lines, words, characters

```bash
wc ~/linux_practice/file1.txt
```

### 15. Display last 10 lines of system logs

Ubuntu:

```bash
tail -10 /var/log/syslog
```

CentOS / RHEL:

```bash
tail -10 /var/log/messages
```

### 16. Find all `.txt` files

```bash
find ~/linux_practice -name "*.txt"
```

---

# Level 4: Process & System Monitoring

### 17. List running processes

```bash
ps -ef
```

### 18. Find PID of sshd

```bash
ps -ef | grep sshd
```

### 19. Kill a process

```bash
kill PID
```

Force kill:

```bash
kill -9 PID
```

### 20. Check CPU and memory usage

```bash
top
```

### 21. Disk usage

```bash
df -h
du -sh ~/linux_practice
```

---

# Level 5: Package Management

### 22. Install `tree`

Ubuntu/Debian:

```bash
sudo apt install tree
```

CentOS/RHEL:

```bash
sudo yum install tree
```

### 23. Remove `tree`

```bash
sudo apt remove tree
```

### 24. Check git version

```bash
git --version
```

### 25. List installed packages

Ubuntu:

```bash
dpkg -l
```

CentOS/RHEL:

```bash
rpm -qa
```

---

# Level 6: Networking Basics

### 26. Check IP address

```bash
ip addr
```

or

```bash
hostname -I
```

### 27. Test internet connectivity

```bash
ping google.com
```

### 28. Display open ports

```bash
ss -tuln
```

### 29. Check DNS configuration

```bash
cat /etc/resolv.conf
```

### 30. Download a file

Using wget:

```bash
wget https://example.com/file.zip
```

Using curl:

```bash
curl -O https://example.com/file.zip
```

---

# 🎯 Learning Outcomes

After completing these tasks you will understand:

- Linux file and directory management
- File permissions and ownership
- Searching files using grep
- Monitoring processes
- Managing packages
- Basic networking commands

---

# 👨‍💻 Author

**Naveen Asarala**  
DevOps Engineer | AWS | Kubernetes | Terraform

---

⭐ If this repository helped you, consider **starring the repo**.
