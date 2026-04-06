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
```
### 3. Permissions & Security (Sudoers)
To allow Jenkins to deploy files into the Nginx directory without manual intervention, I configured NOPASSWD access in the /etc/sudoers file:
```bash
jenkins ALL=(ALL) NOPASSWD: ALL
```
### 4. Jenkins Pipeline Configuration
Created a Pipeline Job connected to this GitHub repository. The deployment logic is defined in the Jenkinsfile:
```bash
pipeline {
    agent any
    stages {
        stage('Deploy to Nginx') {
            steps {
                sh 'sudo cp index.html /usr/share/nginx/html/index.html'
                echo 'Deployment successful!'
            }
        }
    }
}
```
🛑 Troubleshooting (Senior Level Insights)
Several technical challenges were resolved during the process:
1. Port Conflicts: Port 80 was occupied by a default process. Resolved by identifying and killing the ghost process using sudo fuser -k 80/tcp.
2. Resource Constraints: Jenkins node went offline due to low disk space in /tmp (t3.micro limitations). Solved by clearing logs and adjusting Jenkins' Free Temp Space threshold to 50MiB.
3. Git Integration: Fixed "Command not found" errors by manually installing Git on the EC2 instance and aligning the Branch Specifier to */main.

🌐 Live Demo
The application is live and accessible via the EC2 Public IP:
```bash
URL: [http://50.16.109.143|http://50.16.109.143]
```
---

### 5. Push the changes to GitHub
Run these commands in your terminal to update your repo with the English documentation:

```bash
git add README.md
git commit -m "Docs: added professional English documentation"
git push origin main
```
