💰 Expense Application – Ansible Automation

This repository contains Ansible playbooks and configurations to automate the deployment and management of a complete Expense Tracking Application stack, including Frontend, Backend, and Database (MySQL) components.

It is designed to provide repeatable, consistent, and scalable deployments across Linux servers using Infrastructure as Code (IaC) principles.

📌 Key Features

Automated deployment using Ansible

Separate playbooks for frontend, backend, and database

Systemd-based service management

Centralized inventory-driven configuration

Idempotent execution for safe re-runs

Suitable for Dev / QA / Prod environments

🧠 Architecture Overview
User
  |
  v
Frontend (Nginx / Web UI)
  |
  v
Backend API (Systemd Service)
  |
  v
MySQL Database


Frontend serves the UI and forwards requests to backend

Backend processes business logic and connects to MySQL

MySQL stores expense data

All components are provisioned and managed via Ansible playbooks

📁 Repository Structure
expense_application/
├── 01_ec2_server.yaml      # Base server provisioning & setup
├── backend.yaml            # Backend service deployment
├── frontend.yaml           # Frontend deployment & configuration
├── mysql.yaml              # MySQL installation & configuration
├── patching.yaml           # OS patching and updates
├── inventory.ini           # Ansible inventory
├── backend.service         # Systemd unit file for backend
├── expense.conf            # Application / Nginx configuration
└── README.md

🧰 Prerequisites

Ensure the following before execution:

Linux-based control node

Ansible installed

SSH key-based authentication to managed hosts

Python installed on target machines

Sudo privileges on target servers

Install Ansible
sudo yum install ansible -y
# or
pip install ansible

🚀 Usage & Execution Flow
1️⃣ Clone Repository
git clone https://github.com/RajGitUser/expense_application.git
cd expense_application

2️⃣ Configure Inventory

Edit inventory.ini:

[frontend]
frontend ansible_host=FRONTEND_IP

[backend]
backend ansible_host=BACKEND_IP

[database]
mysql ansible_host=DB_IP

3️⃣ Recommended Execution Order

⚠️ Always follow this order for a clean deployment

🔹 Base Server Setup
ansible-playbook -i inventory.ini 01_ec2_server.yaml

🔹 MySQL Database
ansible-playbook -i inventory.ini mysql.yaml

🔹 Backend Service
ansible-playbook -i inventory.ini backend.yaml

🔹 Frontend
ansible-playbook -i inventory.ini frontend.yaml

🔹 OS Patching (Optional)
ansible-playbook -i inventory.ini patching.yaml
🛠️ Playbooks & Configurations
File	                      Purpose
01_ec2_server.yaml	        Initial server setup and provisioning
backend.yaml	              Deploy and configure the backend API service
frontend.yaml	              Deploy and configure the frontend web UI
mysql.yaml	                Install/configure MySQL database
patching.yaml	              Patch and update managed systems
inventory.ini	              Ansible inventory of hosts
backend.service	            Systemd unit for backend service
expense.conf	              Application configuration file
🤝 Contributing

⚙️ Service Management

Backend service is managed via systemd:

systemctl status backend
systemctl restart backend
systemctl enable backend
