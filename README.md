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

💰 Expense Application

Ansible automation to deploy and manage a full Expense Tracking Application stack including backend, frontend, and database infrastructure. This repo includes playbooks, inventory, and service configurations that help provision servers, install dependencies, and run services consistently using Ansible. 
GitHub

📌 Table of Contents

About

Repository Structure

Prerequisites

Usage

Playbooks & Configs

Contributing

License

🧠 About

This project automates deployment of an Expense Application stack using Ansible. It orchestrates provisioning of backend and frontend services along with database setup (MySQL), patching, and system settings — all configured to run on remote hosts defined in the inventory. 
GitHub


*.yaml — Ansible playbooks for provisioning servers and services. 
GitHub

inventory.ini — Defines target hosts and groups for Ansible. 
GitHub

*.service — Systemd service unit definitions for application services. 
GitHub

expense.conf — Application or service configuration template. 
GitHub

🧰 Prerequisites

Before running the automation:

✔ Ansible is installed on the control node (pip install ansible or OS package).
✔ SSH key-based access to all managed hosts.
✔ Target servers are reachable and have Python installed (required by Ansible).
✔ Inventory (inventory.ini) is configured with host IP addresses and group names. 
GitHub

🚀 Usage
1. Clone the Repository
git clone https://github.com/RajGitUser/expense_application.git
cd expense_application

2. Update Inventory

Edit inventory.ini to reflect remote hosts where you want to deploy the application:

[expense_app]
app1 ansible_host=SERVER_IP or DNS (rajkumardaws.space)

3. Execute Playbooks

Provision EC2 or Base Server Setup (Patching, Users, etc.)

ansible-playbook -i inventory.ini 01_ec2_server.yaml


Deploy Backend Service

ansible-playbook -i inventory.ini backend.yaml


Deploy Frontend Service

ansible-playbook -i inventory.ini frontend.yaml


Install and Configure MySQL

ansible-playbook -i inventory.ini mysql.yaml


Apply Patches or System Updates

ansible-playbook -i inventory.ini patching.yaml


Modify playbook names as needed based on your environment. 
GitHub

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

Adding more playbooks for monitoring, logging, CI/CD

Improving configuration modularization with roles

Documenting environment variables and secrets management
