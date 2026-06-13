# Linux Web Server Deployment with Nginx

## Project Overview

This project demonstrates the deployment, configuration, and troubleshooting of an Nginx web server on Ubuntu Linux running inside VMware Workstation.

The objective was to understand how web servers operate, how HTTP requests are processed, and how to diagnose real-world connectivity issues using Linux administration and networking tools.

---

## Technologies Used

- Ubuntu Linux
- Nginx Web Server
- VMware Workstation
- UFW Firewall
- TCP/IP Networking
- HTML
- Systemd
- tcpdump
- PowerShell

---

## Project Architecture

Client (Windows Host)
        |
        | HTTP Request
        v
Ubuntu Virtual Machine
        |
        v
Nginx Web Server
        |
        v
Custom HTML Website

---

## Features Implemented

- Installed and configured Nginx
- Hosted a custom HTML web page
- Configured firewall rules
- Verified service status using systemctl
- Analyzed listening ports using ss
- Examined web server logs
- Performed packet capture and network troubleshooting
- Tested client-server communication between Windows and Ubuntu

---

## Project Screenshots

### Nginx Running

![Nginx Server](Installing%20Nginx.png)

### Successful Access from Client

![Web Server](Confirmation%20OF%20Nginx%20Installation.png)

---

## Key Commands

### Install Nginx

```bash
sudo apt update
sudo apt install nginx
```

### Start Nginx

```bash
sudo systemctl start nginx
```

### Enable Nginx at Boot

```bash
sudo systemctl enable nginx
```

### Check Service Status

```bash
sudo systemctl status nginx
```

### Check Listening Ports

```bash
sudo ss -tulnp | grep :80
```

### View Access Logs

```bash
sudo tail -f /var/log/nginx/access.log
```

### Configure Firewall

```bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

### Capture HTTP Traffic

```bash
sudo tcpdump -nn -i ens33 tcp port 80
```

---

## Troubleshooting Scenario

### Problem

The Windows host machine could not access the Ubuntu web server.

### Investigation Steps

1. Verified IP connectivity using ping.
2. Checked Nginx service status.
3. Verified port 80 was listening.
4. Examined firewall rules.
5. Tested HTTP connectivity from Windows PowerShell.
6. Captured packets using tcpdump.
7. Analyzed TCP SYN and TCP RST responses.

### Root Cause

The Nginx service had been stopped.

Because no process was listening on port 80, Ubuntu responded with TCP Reset (RST) packets, causing the connection to fail.

### Resolution

```bash
sudo systemctl start nginx
```

After restarting Nginx, the Windows host successfully accessed the web server.

---

## Concepts Learned

### Linux Administration

- Service management
- File system navigation
- Log analysis
- Package management

### Networking

- TCP/IP communication
- TCP SYN packets
- TCP RST packets
- Port listening
- Client-server architecture

### Web Servers

- Static content hosting
- HTTP request processing
- Nginx configuration basics

### Troubleshooting

- Root cause analysis
- Packet inspection
- Service verification
- Network diagnostics

---

## Skills Demonstrated

- Linux System Administration
- Nginx Configuration
- Web Server Deployment
- Network Troubleshooting
- TCP/IP Fundamentals
- Log Analysis
- VMware Virtualization

---

## Author

**Venkatesh Jatroth**

Aspiring Linux Administrator | DevOps Enthusiast | Cloud Learner

GitHub: https://github.com/VenkateshJatroth
