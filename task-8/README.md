# 🐳 DevOps Docker Task – Static Website with Nginx

## 📌 Objective

This project demonstrates how to **containerize a simple static HTML website using Docker and Nginx**.

The goal of this task is to understand:

- Docker basics
- Creating Docker images
- Writing Dockerfiles
- Running containers
- Accessing applications through a browser

This task is part of **DevOps learning and containerization practice**.

---

# 📂 Project Structure

```
devops-docker-task/
│
├── index.html
├── Dockerfile
└── README.md
```

---

# 🌐 Application

The application is a **simple static HTML page** that displays the message:

```
Hi this is naveen, i am a devops trainee
```

---

# 📄 index.html

```html
<!DOCTYPE html>
<html>
<head>
    <title>DevOps Docker Task</title>
</head>
<body>
    <h1>Hi this is naveen, i am a devops trainee</h1>
</body>
</html>
```

---

# 🐳 Dockerfile

```dockerfile
# Base Image
FROM nginx:alpine

# Working Directory
WORKDIR /usr/share/nginx/html

# Copy HTML file
COPY index.html .

# Expose Port
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
```

---

# ⚙️ Step 1: Install Docker

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install docker.io -y
```

Enable and start Docker:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

Check Docker version:

```bash
docker --version
```

---

# 🏗 Step 2: Build Docker Image

Navigate to the project directory and run:

```bash
docker build -t devops-docker-task .
```

Check images:

```bash
docker images
```

---

# 🚀 Step 3: Run Docker Container

Run the container:

```bash
docker run -d -p 8080:80 devops-docker-task
```

Check running containers:

```bash
docker ps
```

---

# 🌍 Step 4: Access the Application

Open your browser and visit:

```
http://localhost:8080
```

You should see:

```
Hi this is naveen, i am a devops trainee
```

---

# 🛠 Useful Docker Commands

### Stop container

```bash
docker stop <container_id>
```

### Remove container

```bash
docker rm <container_id>
```

### Remove image

```bash
docker rmi devops-docker-task
```

---

# 🎯 Learning Outcomes

After completing this task you will understand:

- Docker image creation
- Dockerfile structure
- Container deployment
- Running web applications inside containers
- Basic DevOps container workflow

---

# 👨‍💻 Author

**Naveen Asarala**  

---

⭐ If you found this project useful, consider **starring the repository**.
