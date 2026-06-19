# Day 14

## Overview

Day 14 focused on exploring **Storm-Breaker**, understanding its setup process, configuring **Ngrok**, and learning how Python virtual environments help manage dependencies for cybersecurity tools.

The session was less about the tool itself and more about understanding the technologies that work behind the scenes, including GitHub repositories, Python package management, virtual environments, and tunneling services.

---

## Topics Covered

- Storm-Breaker Installation & Setup
- GitHub Repository Cloning
- Python Dependency Management
- Virtual Environments (venv)
- Ngrok Configuration
- Authentication Tokens
- Security Awareness & Phishing Simulations

---

# Storm-Breaker Setup

## Clone Repository

```bash
git clone https://github.com/ultrasecurity/Storm-Breaker
cd Storm-Breaker
```

## Run Installation Script

```bash
sudo bash install.sh
```

## Install Dependencies

```bash
sudo python3 -m pip install -r requirements.txt
```

## Launch Storm-Breaker

```bash
sudo python3 st.py
```

---

# Python Virtual Environment (venv)

While working with Python-based cybersecurity tools, virtual environments help keep dependencies isolated from the main operating system.

## Create Virtual Environment

```bash
python3 -m venv venv
```

## Activate Virtual Environment

```bash
source venv/bin/activate
```

## Deactivate Virtual Environment

```bash
deactivate
```

### Why Use Virtual Environments?

- Prevent package conflicts
- Keep projects isolated
- Easier dependency management
- Common industry practice

---

# Ngrok Configuration

Ngrok creates a secure tunnel between a local machine and the internet.

## Download Ngrok

```bash
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz
```

## Extract and Install

```bash
sudo tar xvzf ./ngrok-v3-stable-linux-amd64.tgz -C /usr/local/bin
```

## Connect Account Using Auth Token

```bash
ngrok authtoken NGROK_AUTHTOKEN
```

A free Ngrok account was created and linked with the local installation using the generated authentication token.

---

# Key Learnings

### Git & Open Source Projects

Learned how cybersecurity tools are distributed through GitHub repositories and how to clone and work with them locally.

### Python Dependency Management

Understood the purpose of `requirements.txt` and how it simplifies dependency installation.

### Virtual Environments

Learned why Python virtual environments are important when working with multiple cybersecurity tools and projects.

### Ngrok Tunneling

Observed how local services can be securely exposed to the internet using Ngrok.

### Security Awareness

Explored how phishing simulation frameworks operate in controlled environments to help security professionals understand attacker methodologies and improve defensive strategies.

---

# Commands Practiced

```bash
git clone https://github.com/ultrasecurity/Storm-Breaker

cd Storm-Breaker

sudo bash install.sh

sudo python3 -m pip install -r requirements.txt

sudo python3 st.py

python3 -m venv venv

source venv/bin/activate

wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz

sudo tar xvzf ./ngrok-v3-stable-linux-amd64.tgz -C /usr/local/bin

ngrok authtoken NGROK_AUTHTOKEN
```

---
