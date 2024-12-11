Ansible README
Introduction
Ansible is a powerful, open-source automation tool used for configuration management, application deployment, and task automation. It enables system administrators and developers to manage IT infrastructure efficiently by automating repetitive tasks. Ansible operates agentlessly, connecting to remote machines via SSH or PowerShell.

This repository contains resources and sample YAML playbooks for Ansible, including system checks, Docker installation, NGINX installation, and guidance on configuring Ansible hosts. You'll also find step-by-step instructions for installing Ansible and configuring your Ansible environment.

Table of Contents
What is Ansible?
Use Cases of Ansible
Installation
Installing Ansible
Adding Hosts to Ansible Master
Sample Playbooks
System Checks
Docker Installation
NGINX Installation
Contributors
License
What is Ansible?
Ansible is an IT automation platform that simplifies the management of systems by:

Allowing you to define infrastructure as code.
Managing systems without requiring agents installed on client systems.
Being highly extensible through its modules.
Use Cases of Ansible
Configuration Management: Automate system setup (e.g., configuring users, firewalls, and software installations).
Application Deployment: Simplify and automate application deployment across multiple environments.
Provisioning: Set up servers, cloud instances, and containers quickly.
Orchestration: Manage complex workflows, such as multi-tier applications.
Continuous Integration/Delivery (CI/CD): Facilitate DevOps pipelines with seamless automation.
Installation
Installing Ansible
Update System Packages:

bash
Copy code
sudo apt update
sudo apt upgrade
Install Required Dependencies:

bash
Copy code
sudo apt install -y software-properties-common
Add Ansible Repository:

bash
Copy code
sudo add-apt-repository --yes --update ppa:ansible/ansible
Install Ansible:

bash
Copy code
sudo apt install -y ansible
Verify Installation:

bash
Copy code
ansible --version
Adding Hosts to Ansible Master
Open the inventory file located at /etc/ansible/hosts:

bash
Copy code
sudo nano /etc/ansible/hosts
Add hosts to groups in the following format:

ini
Copy code
[webservers]
192.168.1.10
192.168.1.11

[dbservers]
db.example.com
Test the connection to the hosts:

bash
Copy code
ansible all -m ping
Sample Playbooks
System Checks
A playbook to check uptime and disk usage:

yaml
Copy code
---
- name: System Health Checks
  hosts: all
  tasks:
    - name: Check system uptime
      command: uptime
      register: uptime_output
    - debug: var=uptime_output.stdout

    - name: Check disk usage
      command: df -h
      register: disk_usage
    - debug: var=disk_usage.stdout
Docker Installation
A playbook to install Docker:

yaml
Copy code
---
- name: Install Docker
  hosts: all
  become: yes
  tasks:
    - name: Install required packages
      apt:
        name:
          - apt-transport-https
          - ca-certificates
          - curl
          - software-properties-common
        state: present

    - name: Add Docker’s official GPG key
      shell: curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

    - name: Set up the stable repository
      shell: add-apt-repository \
        "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

    - name: Install Docker
      apt:
        name: docker-ce
        state: latest
NGINX Installation
A playbook to install and configure NGINX:

yaml
Copy code
---
- name: Install NGINX
  hosts: all
  become: yes
  tasks:
    - name: Install NGINX
      apt:
        name: nginx
        state: present

    - name: Start and enable NGINX
      service:
        name: nginx
        state: started
        enabled: true

    - name: Create a simple NGINX configuration
      copy:
        dest: /var/www/html/index.html
        content: |
          <html>
          <body>
          <h1>Welcome to NGINX!</h1>
          </body>
          </html>
Contributors
Karan Bhand
