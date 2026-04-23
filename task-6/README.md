# 🌐 AWS Custom Domain Setup with Route 53, ALB & ACM

This project demonstrates how to configure a custom domain in AWS using Route 53, Application Load Balancer (ALB), and AWS Certificate Manager (ACM) with HTTPS support.

---

## 📌 Architecture Overview

- Domain managed via Route 53
- Traffic routed to ALB
- ALB distributes traffic to target groups
- SSL termination handled by ACM
- HTTP redirected to HTTPS

---

## 🛠️ Prerequisites

- AWS Account
- Registered Domain (Route 53 or external registrar)
- Running application (EC2 / ECS / EKS)
- Application Load Balancer (ALB)

---

## 🚀 Implementation Steps

### 1. Create Route 53 Hosted Zone

- Go to Route 53 → Hosted Zones
- Click **Create Hosted Zone**
- Enter domain name (e.g., example.com)
- Select **Public Hosted Zone**

---

### 2. Add Domain DNS Records

- NS and SOA records are created automatically
- Update domain registrar with Route 53 name servers

---

### 3. Connect Custom Domain to ALB

- Copy ALB DNS name  
  Example:

my-alb-123456.ap-south-1.elb.amazonaws.com


---

### 4. Create Alias A Record

- Go to Hosted Zone → Create Record
- Record type: `A`
- Enable **Alias**
- Select ALB as target

---

### 5. Add CNAME Records for Subdomains

Example:


api.example.com → my-alb-123456.ap-south-1.elb.amazonaws.com
www.example.com
 → example.com


---

### 6. Request ACM SSL Certificate

- Go to AWS Certificate Manager (ACM)
- Request public certificate
- Add:
  - example.com
  - *.example.com (optional)

---

### 7. Validate SSL Certificate (DNS)

- Choose DNS validation
- Add CNAME records provided by ACM into Route 53
- Wait until status becomes **Issued**

---

### 8. Configure HTTPS Listener (ALB)

- Go to ALB → Listeners
- Add:
  - Protocol: HTTPS
  - Port: 443
- Attach ACM certificate

---

### 9. Redirect HTTP to HTTPS

- Edit HTTP (port 80) listener
- Add redirect rule:
  - Protocol: HTTPS
  - Port: 443
  - Status code: 301

---

### 10. Create Target Groups

- Target type: Instance / IP
- Protocol: HTTP
- Port: 80

---

### 11. Attach Target Groups to ALB

- Go to ALB → Listeners
- Forward traffic to target group

---

### 12. Configure Health Checks

- Path: `/` or `/health`
- Interval: 30 seconds
- Healthy threshold: 2–5

---

### 13. Enable Route 53 Health Checks

- Go to Route 53 → Health Checks
- Create health check for endpoint
- Associate with DNS record (optional failover)

---

### 14. Enable ALB Access Logs

- Go to ALB → Attributes
- Enable access logs
- Select S3 bucket

---

### 15. Verify Setup

Test:


http://example.com
 → redirects to https://example.com

https://example.com
 → loads successfully


---

### 16. Check DNS Propagation

Use:

- nslookup
- dig
- https://dnschecker.org

---

## ✅ Validation Checklist

- [ ] Domain resolves to ALB  
- [ ] SSL certificate issued  
- [ ] HTTPS working  
- [ ] HTTP redirects to HTTPS  
- [ ] Target group healthy  
- [ ] Health checks passing  
- [ ] Access logs enabled  

---

## 📚 Best Practices

- Use wildcard certificates (*.example.com)
- Enable AWS WAF for security
- Enforce HTTPS only
- Automate using Terraform or CloudFormation

---

## 🔥 Future Improvements

- Infrastructure as Code (Terraform)
- CI/CD integration
- Blue/Green deployment using ALB
