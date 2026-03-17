# 1️⃣ Base Image
FROM nginx:alpine

# 2️⃣ Working Directory
WORKDIR /usr/share/nginx/html

# 3️⃣ Copy Application Files
COPY index.html .

# 4️⃣ Expose Required Port
EXPOSE 80

# 5️⃣ Start Nginx
CMD ["nginx", "-g", "daemon off;"]
