# AWS CloudDeployment 


🌍 Travel Memory – AWS Deployment
📌 Project Overview

This project demonstrates deployment of the Travel Memory (MERN Stack) application on AWS EC2.

The deployment includes:

Backend: Node.js

Frontend: React

Database: MongoDB Atlas

Reverse Proxy: Nginx

Load Balancer for scalability

Custom Domain using Cloudflare

---


🎯 Objectives

Set up backend running on Node.js

Configure frontend built with React

Ensure communication between frontend & backend

Deploy application on EC2

Enable load balancing with multiple instances

Connect custom domain via Cloudflare


## 📌 <span style="color:#1F618D;">Project Overview</span>




##  <span style="color:#AF601A;">Deployment Architecture</span>

🏗️ Deployment Architecture

User -> CloudflareAWS -> Load Balancer -> Multiple EC2 Instances -> Nginx -> Node Backend ->MongoDB Atlas


Cloning Travel Memory Repository : 🔗 https://github.com/UnpredictablePrashant/TravelMemory

<img width="621" height="265" alt="image" src="https://github.com/user-attachments/assets/d9c8263a-b1b3-4b31-9180-228450b11677" />


⚙️ 1️⃣ Backend Configuration

Step 1: Clone Repository
git clone https://github.com/UnpredictablePrashant/TravelMemory.git
cd TravelMemory/backend
npm install
Step 2: Create .env File

Create .env inside backend folder:

PORT=3000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
Step 3: Install and Configure Nginx

Install Nginx:

sudo apt update
sudo apt install nginx -y

Remove default config:

sudo rm /etc/nginx/sites-enabled/default

Create new config:

sudo nano /etc/nginx/sites-available/travelmemory

Add:

server {
    listen 80;

    location / {
        proxy_pass http://localhost:3000;
    }
}

Create soft link:

sudo ln -s /etc/nginx/sites-available/travelmemory /etc/nginx/sites-enabled/

Test & restart:

sudo nginx -t
sudo systemctl restart nginx

Now backend runs via Port 80.


<img width="618" height="295" alt="image" src="https://github.com/user-attachments/assets/ee060dfd-6b52-4ad0-9ea2-97f6719de297" />



## Checking Test 

<img width="623" height="235" alt="image" src="https://github.com/user-attachments/assets/4e27e2f5-e480-45ea-b68a-87d6e415fb0a" />





<img width="629" height="303" alt="image" src="https://github.com/user-attachments/assets/854dc4e0-6a5b-4323-a73a-24f3dc65ee51" />


Changing port  in URL


<img width="618" height="322" alt="image" src="https://github.com/user-attachments/assets/74b640ff-7259-4e5a-b935-e40a1118519e" />




<img width="640" height="344" alt="image" src="https://github.com/user-attachments/assets/1d27df63-20c3-48dd-b91e-60d973ffc0bc" />

## 🔗 2️⃣ Frontend & Backend Connection

Navigate to:

frontend/src/utils/urls.js

Update base URL:

export const baseUrl = "/api";

Install & build frontend:

cd ../frontend
npm install
npm run build


<img width="622" height="307" alt="image" src="https://github.com/user-attachments/assets/c41c90dd-1c4b-4514-9e28-b414d4e95b95" />

  EC2 Instance Running

  
<img width="622" height="304" alt="image" src="https://github.com/user-attachments/assets/0e77ea4e-a5ba-4e1a-857d-9b544b5ed958" />





<img width="623" height="428" alt="image" src="https://github.com/user-attachments/assets/e796d6b8-66a9-4252-88f9-a82eaea45d4b" />




<img width="629" height="327" alt="image" src="https://github.com/user-attachments/assets/7955f547-1384-4f0f-9870-8e834b0f92d9" />




<img width="625" height="332" alt="image" src="https://github.com/user-attachments/assets/4d33ec4f-3d11-47db-aac1-31c7a906b052" />


<span style="color:#B03A2E;">Scaling the Application</span>


## 🔁 3️⃣ Scaling the Application

To improve performance and availability:

Created AMI of configured EC2 instance

Launched multiple EC2 instances

Created Application Load Balancer

Added instances to target group

Enabled health checks

Load balancer distributes traffic evenly across instances.




<img width="631" height="363" alt="image" src="https://github.com/user-attachments/assets/014d6ad7-ce56-4a63-a09a-1f67b9fe3e84" />

Screenshot (Target group in Loadbalancer )

<img width="624" height="324" alt="image" src="https://github.com/user-attachments/assets/3efb36e2-7544-4cc1-9c73-e40bce89e255" />

## 🌐 4️⃣ Domain Setup with Cloudflare

Steps:

Add domain to Cloudflare.

Create CNAME record:

Name: www

Target: Load Balancer DNS

Create A record:

Name: @

IP: EC2 public IP

Enable proxy (orange cloud).


🌍 Live Application

http://yourdomain.com

## 🔐 Security Best Practices

Only ports 22, 80, 443 open

Backend port 3000 not publicly exposed

Environment variables secured

Health checks enabled

SSL enabled in Cloudflare

## 📦 Deliverables

GitHub Repository Link

Live Application URL

Deployment Screenshots

Architecture Diagram

## ✅ Conclusion

The Travel Memory application has been successfully deployed on AWS EC2 with:

Reverse proxy configuration

Load balancing

Custom domain integration

Scalable architecture















 
