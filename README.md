# Ansible

## Introduction

Ansible is a powerful, open-source automation tool used for configuration management, application deployment, and task automation. It enables system administrators and developers to manage IT infrastructure efficiently by automating repetitive tasks. Ansible operates agentlessly, connecting to remote machines via SSH or PowerShell.

This repository contains resources and sample YAML playbooks for Ansible, including system checks, Docker installation, NGINX installation, and guidance on configuring Ansible hosts. You'll also find step-by-step instructions for installing Ansible and configuring your Ansible environment.

---

## Table of Contents

- [What is Ansible?](#what-is-ansible)
- [Use Cases of Ansible](#use-cases-of-ansible)
- [Installation](#installation)
  - [Installing Ansible](#installing-ansible)
  - [Adding Hosts to Ansible Master](#adding-hosts-to-ansible-master)
- [Sample Playbooks](#sample-playbooks)
  - [System Checks](#system-checks)
  - [Docker Installation](#docker-installation)
  - [NGINX Installation](#nginx-installation)
- [Contributors](#contributors)
- [License](#license)

---

## What is Ansible?

Ansible is an IT automation platform that simplifies the management of systems by:
- Allowing you to define infrastructure as code.
- Managing systems without requiring agents installed on client systems.
- Being highly extensible through its modules.

---

## Use Cases of Ansible

- **Configuration Management**: Automate system setup (e.g., configuring users, firewalls, and software installations).
- **Application Deployment**: Simplify and automate application deployment across multiple environments.
- **Provisioning**: Set up servers, cloud instances, and containers quickly.
- **Orchestration**: Manage complex workflows, such as multi-tier applications.
- **Continuous Integration/Delivery (CI/CD)**: Facilitate DevOps pipelines with seamless automation.

---

## Installation

### Installing Ansible

1. **Update System Packages**:
   ```bash
   sudo apt update
   sudo apt upgrade
