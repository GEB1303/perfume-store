# 🏺 Guanago Perfumes - Automated CI/CD Pipeline

This project demonstrates a full **Continuous Integration and Continuous Deployment (CI/CD)** workflow. It automates the deployment of a static web application (Perfume Store) hosted on an **Amazon Linux 2023** instance running on **AWS EC2**.



## 🛠️ Tech Stack
* **Cloud Provider:** AWS (EC2 t3.micro).
* **OS:** Amazon Linux 2023.
* **Web Server:** Nginx.
* **Automation:** Jenkins.
* **Version Control:** Git & GitHub.

---

## 🚀 Implementation Steps

### 1. Infrastructure Setup (AWS EC2)
* Provisioned an EC2 instance with Amazon Linux 2023.
* Configured **Security Groups** to allow traffic on:
    * Port `22` (SSH) for management.
    * Port `8080` for Jenkins Dashboard.
    * Port `80` (HTTP) for the web service.

### 2. Dependency Installation
Installed the required environment using the `dnf` package manager:
```bash
sudo dnf install java-17-amazon-corretto-devel -y
sudo dnf install jenkins -y
sudo dnf install nginx -y
sudo dnf install git -y
### 3. Permissions & Security (Sudoers)
To allow Jenkins to deploy files into the Nginx directory without manual intervention, I configured NOPASSWD access in the /etc/sudoers file:
