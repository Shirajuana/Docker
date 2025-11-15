# Docker Containerization Guide

![Docker](https://img.shields.io/badge/Docker-Containerized-blue.svg)
![Django](https://img.shields.io/badge/Django-4.2.11-green.svg)
![Python](https://img.shields.io/badge/Python-3.11-slim-orange.svg)
![Compose](https://img.shields.io/badge/Docker--Compose-3.8-yellow.svg)

A comprehensive guide to containerizing Django applications using Docker, providing consistent development and deployment environments across all platforms.

## 📋 Overview

This documentation covers the complete process of Dockerizing Django applications, from basic concepts to production deployment. Learn how to eliminate "it works on my machine" problems and create portable, scalable applications that run consistently anywhere.

## ✨ Key Features

### 🐳 Core Docker Concepts
- **Container vs VM Comparison**: Understand the fundamental differences between containers and virtual machines
- **Lightweight Architecture**: MB-sized containers vs GB-sized VMs
- **Rapid Deployment**: Seconds to start vs minutes for traditional VMs
- **Resource Efficiency**: Shared kernel architecture reduces overhead
- **Process Isolation**: Secure environment separation without full OS duplication

### 🔧 Development Advantages
- **Environment Consistency**: Identical development, testing, and production environments
- **Dependency Management**: Isolated Python environments with precise version control
- **Cross-Platform Compatibility**: Run the same application on Windows, Mac, and Linux
- **Rapid Onboarding**: New developers can start contributing in minutes, not hours

### 🚀 Deployment Excellence
- **Docker Hub Integration**: Cloud registry for image storage and distribution
- **Multi-Container Management**: Orchestrate complex applications with Docker Compose
- **Version Control for Environments**: Track environment changes alongside code
- **Scalable Architecture**: Easy horizontal scaling for production workloads

## 🛠 How It Works

### 🔄 The Docker Workflow

**Development Phase**:
1. **Dockerfile Definition**: Blueprint containing step-by-step application setup instructions
2. **Image Building**: Create reproducible application snapshots
3. **Local Testing**: Run containers in isolated development environments

**Distribution Phase**:
1. **Docker Hub Push**: Store built images in cloud registry
2. **Version Tagging**: Manage different application versions
3. **Image Sharing**: Distribute applications across teams and servers

**Deployment Phase**:
1. **Image Pulling**: Retrieve pre-built images from registry
2. **Container Orchestration**: Manage multi-service applications
3. **Production Running**: Deploy consistent environments worldwide

### 📊 Architecture Components

| Component | Purpose | Benefit |
|-----------|---------|---------|
| **Dockerfile** | Application blueprint | Reproducible builds |
| **Docker Image** | Application snapshot | Portable deployment |
| **Docker Container** | Running instance | Isolated execution |
| **Docker Compose** | Multi-service management | Simplified orchestration |
| **Docker Hub** | Image registry | Centralized distribution |

# Instructions on how to run the program
### Prerequisites
1. System Requirements
- **Windows 10/11** (64-bit) or **macOS** or **Linux**
- At least **4GB RAM**
- **Virtualization enabled** in BIOS

### 2. Enable Virtualization (Windows)
1. Restart your computer
2. Press **F2, F10, Delete, or Esc** during startup (varies by manufacturer)
3. Find **"Virtualization Technology"** or **"Intel VT-x"** or **"AMD-V"**
4. **Enable** it and save changes

### 3. Install WSL 2 (Windows Only)
```
wsl --install
wsl --set-default-version 2
```

# Docker Installation
1. Install Docker Desktop
Download from: https://www.docker.com/products/docker-desktop

    Run the installer

    Check "Use WSL 2 instead of Hyper-V" (recommended)

    Complete installation and restart when prompted

2. Verify Installation
```
docker --version
```

# Running the PSUSphere Application
### Method 1: Using Docker Compose (Recommended)
Step 1: Create Project Folder

```
mkdir psusphere-client
cd psusphere-client
```

### Step 2: Create docker-compose.yml
Create a file named docker-compose.yml with this content:
```
version: '3.8'

services:
  web:
    image: shirajuana/django-app:latest # Note: 'image' not 'build'
    command: sh -c "python manage.py migrate && python manage.py runserver 0.0.0.0:8000"
    ports:
    - "8000:8000"
    volumes:
    - django_data:/app
    environment:
    - DEBUG=1
    - USE_SQLITE=true
    - DJANGO_ALLOWED_HOSTS=localhost 127.0.0.1 [::1]
    - SITE_ID=4
volumes:
  django_data:
```
### Step 3: Run the Application
```
docker-compose up -d
```

### Step 4: Verify it's Running
```
docker-compose ps
```

# Accessing the Application
### Open Web Browser
Navigate to: http://localhost:8000
## 🎯 Use Cases

### 💻 Development Teams
- **Onboarding**: New developers running applications in 5 minutes
- **Collaboration**: Shared environments across Windows, Mac, and Linux
- **Testing**: Consistent test environments for QA processes

### 🏭 Production Deployment
- **Web Applications**: Django, Flask, FastAPI containerization
- **Microservices**: Multi-container application orchestration
- **CI/CD Pipelines**: Automated build and deployment processes

### 🎓 Educational Purposes
- **Student Projects**: Easy project distribution and submission
- **Team Collaborations**: Simplified environment sharing
- **Demo Applications**: Portable presentation-ready applications

## 📈 Benefits

### ⚡ Performance
- **Fast Startup**: Containers start in seconds vs minutes for VMs
- **Low Overhead**: Minimal resource consumption compared to full virtualization
- **High Density**: Run multiple containers on single host

### 🔒 Reliability
- **Consistent Behavior**: Same application behavior everywhere
- **Isolated Environments**: No conflicts between application dependencies
- **Rollback Capability**: Easy version management and rollbacks

### 💰 Cost Efficiency
- **Reduced Infrastructure**: Higher container density per server
- **Lower Storage**: Smaller image sizes compared to VM images
- **Faster Deployment**: Reduced deployment and maintenance time

## 🧑 Authors

<div style="display: flex; flex-wrap: wrap; gap: 20px; margin-bottom: 30px;">

<div style="flex: 1; min-width: 300px; border: 1px solid #444; border-radius: 10px; padding: 20px; background: #000; color: white;">
    <div style="text-align: center;">
        <a href="https://github.com/Shirajuana">
            <img src="https://github.com/Shirajuana.png" width="120" height="120" style="border-radius: 50%; border: 3px solid #fff;">
        </a>
    </div>
    <h3 style="text-align: center; margin-top: 15px; color: white;">SHEILA MAE VELUYA (Owner)</h3>
    <p style="text-align: center; margin: 10px 0; color: #ccc;">
        <strong>Email:</strong> 202380038@psu.palawan.edu.ph
    </p>
    <div style="display: flex; justify-content: center; gap: 10px; margin-top: 15px;">
        <a href="https://github.com/Shirajuana" style="text-decoration: none;">
            <img src="https://img.shields.io/badge/-GitHub-181717?logo=github&logoColor=white&style=for-the-badge" alt="GitHub">
        </a>
        <a href="https://facebook.com/shielamae.veluya" style="text-decoration: none;">
            <img src="https://img.shields.io/badge/-Facebook-1877F2?logo=facebook&logoColor=white&style=for-the-badge" alt="Facebook">
        </a>
    </div>
</div>

<div style="flex: 1; min-width: 300px; border: 1px solid #444; border-radius: 10px; padding: 20px; background: #000; color: white;">
    <div style="text-align: center;">
        <a href="https://github.com/Erlybird21">
            <img src="https://github.com/Erlybird21.png" width="120" height="120" style="border-radius: 50%; border: 3px solid #fff;">
        </a>
    </div>
    <h3 style="text-align: center; margin-top: 15px; color: white;">ERL JOSEPH MANGUBAT (Collaborator)</h3>
    <p style="text-align: center; margin: 10px 0; color: #ccc;">
        <strong>Email:</strong> 202380004@psu.palawan.edu.ph
    </p>
    <div style="display: flex; justify-content: center; gap: 10px; margin-top: 15px;">
        <a href="https://github.com/Erlybird21" style="text-decoration: none;">
            <img src="https://img.shields.io/badge/-GitHub-181717?logo=github&logoColor=white&style=for-the-badge" alt="GitHub">
        </a>
        <a href="https://facebook.com/erljoseph.mangubat" style="text-decoration: none;">
            <img src="https://img.shields.io/badge/-Facebook-1877F2?logo=facebook&logoColor=white&style=for-the-badge" alt="Facebook">
        </a>
    </div>
</div>

</div>

---
