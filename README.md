# VirtualBox Home Lab - System Integration Practice

# Beschreibung (German)

In diesem Projekt habe ich eine virtualisierte Umgebung mit VirtualBox aufgebaut, um grundlegende Systemadministrations- und Netzwerkkonzepte zu erlernen und zu üben.

Das Lab umfasst die Installation und Konfiguration eines Ubuntu Server 24.04 LTS, Benutzerverwaltung, SSH-Konfiguration, Linux-Dateiberechtigungen sowie Netzwerk-Troubleshooting.

# Description (English)

This project involves building a virtualized environment using VirtualBox to learn and practice fundamental system administration and networking concepts.

The lab includes Ubuntu Server 24.04 LTS installation and configuration, user management, SSH configuration, Linux file permissions, and network troubleshooting.


# Project Objectives

- Learn practical Linux server administration
- Understand system service management with systemd
- Practice user and permission management
- Gain hands-on experience with SSH configuration
- Develop network troubleshooting skills
- Document technical work professionally



# Lab Environment

# Host System
- **Host OS:** Windows 11 Pro
- **Virtualization:** Oracle VirtualBox

# Virtual Machines
# Linux
VM Name - Ubuntu Server
OS  - Ubuntu Server 24.04 LTS
Role - Linux Server
Network Mode - NAT (initial), Bridged (planned)

# Windows
VM Name - Windows Client
OS - Windows 10/11
Role - Client System
Network Mode - NAT/Bridged


# Skills Learned

# Linux System Administration
-  Ubuntu Server 24.04 LTS installation
-  System updates and package management with APT
-  Installation of common administrative tools (net-tools, curl, wget, htop)

# Network Configuration & Troubleshooting
-  Network verification with `ip a`, `ip route`, `ping`
-  Understanding of DHCP and NAT networking
-  DNS resolution testing
-  Analysis of NAT networking limitations vs. Bridged mode

# Service Management
-  SSH server installation and configuration
-  systemd service management (`systemctl` commands)
-  Service status verification

# User & Permission Management
-  Creating users with `adduser`
-  Managing groups and sudo privileges
-  User permission testing and privilege escalation
-  File and directory permissions with `chmod` and `chown`
-  Group-based access control

# Problem-Solving & Documentation
-  Identifying and analyzing SSH connection issues
-  Understanding network topology limitations
-  Professional technical documentation with screenshots
-  Systematic troubleshooting methodology


# Repository Contents

```
homelab-documentation/
├── README.md                           # This file
├── Home_Lab_Documentation.pdf          # Complete lab documentation
├── screenshots/                        # Visual evidence of work
│   ├── ubuntu_login.png
│   ├── system_update.png
│   ├── ip_a_output.png
│   ├── ssh_status.png
│   ├── ssh_timeout_error.png
│   ├── user_groups.png
│   └── shared_directory_permissions.png
└── notes/                              # Additional notes
    └── lessons_learned.md
```


# What I Learned

**1. Network Topology Matters**
- Discovered that NAT networking prevents inbound connections by default
- Learned the practical difference between NAT and Bridged networking modes
- Understood why SSH from host to guest VM failed with NAT configuration

**2. systemd Service Management**
- Learned to distinguish between socket-activated and continuously running services
- Practiced enabling, starting, stopping, and checking service status
- 

**3. Professional Documentation**
- Learned to document not just successes but also failures and their analysis
- Practiced taking meaningful screenshots for technical documentation
- 

# Challenges Overcome

**Challenge 1: SSH Connection Timeout**
- **Problem:** SSH connection from Windows host to Ubuntu VM failed with timeout error
- **Root Cause:** NAT networking mode doesn't allow direct inbound connections
- **Learning:** Understood network topology implications for service accessibility
- **Solution (planned):** Switch to Bridged mode or configure port forwarding

**Challenge 2: Understanding systemd**
- **Problem:** SSH service initially socket-activated instead of continuously running
- **Solution:** Disabled socket activation and enabled standard service mode
- **Learning:** Different service activation methods serve different use cases


# Detailed Lab Steps

# Phase 1: System Installation & Setup
1. Downloaded Ubuntu Server 24.04 LTS ISO
2. Created VM in VirtualBox with appropriate resources
3. Installed Ubuntu Server in text-based mode
4. Configured user account and network settings

# Phase 2: System Hardening & Updates
1. Updated system packages: `sudo apt update && sudo apt upgrade -y`
2. Installed essential tools: `sudo apt install net-tools curl wget htop -y`
3. Verified system connectivity and DNS resolution

# Phase 3: SSH Configuration
1. Installed OpenSSH server: `sudo apt install openssh-server -y`
2. Configured SSH to run continuously (not socket-activated)
3. Verified SSH service status: `systemctl status ssh`
4. Attempted remote connection (identified NAT limitation)

# Phase 4: User Management
1. Created test user: `sudo adduser testuser`
2. Granted sudo privileges: `sudo usermod -aG sudo testuser`
3. Verified user permissions and group membership
4. Tested privilege escalation

# Phase 5: File Permissions
1. Created shared directory: `sudo mkdir /srv/shared`
2. Set ownership: `sudo chown root:sudo /srv/shared`
3. Applied group permissions: `sudo chmod 770 /srv/shared`
4. Tested access control with different users


# Next Steps

# Planned Improvements

- [ ] **Switch to Bridged Networking**
  - Reconfigure VM network settings
  - Obtain IP from local router via DHCP
  - Successfully establish SSH connection from Windows host

- [ ] **Firewall Configuration**
  - Install and configure UFW (Uncomplicated Firewall)
  - Allow SSH (port 22) and HTTP (port 80)
  - Test firewall rules

- [ ] **Web Server Installation**
  - Install Apache2 web server
  - Create simple HTML page
  - Access web server from Windows client

- [ ] **Advanced Services**
  - Configure basic DNS with dnsmasq
  - Set up file sharing (Samba/NFS)
  - Implement automated backup scripts

- [ ] **Monitoring & Logging**
  - Set up system resource monitoring
  - Practice log analysis with `journalctl`
  - Configure log rotation


# Key Takeaways

1. **Hands-on practice is essential** - Reading tutorials is not enough; actually building and breaking things teaches more than any book.

2. **Failures are learning opportunities** - The SSH timeout error taught me more about networking than a successful connection would have.

3. **Documentation matters** - Proper documentation helps track progress, identify patterns, and demonstrate skills to potential employers.

4. **Fundamentals are critical** - Understanding basics like permissions, services, and networking is crucial before moving to advanced topics.


# Learning Resources Used

- [Ubuntu Server Documentation](https://ubuntu.com/server/docs)
- [The Linux Command Line by William Shotts](https://linuxcommand.org/tlcl.php)
- [DigitalOcean Linux Tutorials](https://www.digitalocean.com/community/tags/linux-basics)
- [NetworkChuck YouTube Channel](https://www.youtube.com/@NetworkChuck)
- The Complete Networking Fundamentals Course by David Bombal (https://www.udemy.com/course/complete-networking-fundamentals-course-ccna-start/learn/lecture/47039631?start=0#overview)



# Technical Specifications

# Ubuntu Server Configuration
- **OS Version:** Ubuntu Server 24.04 LTS
- **Installation Type:** Minimal (headless)
- **Disk:** 20 GB dynamically allocated
- **RAM:** 2 GB
- **CPU:** 2 cores
- **Network:** NAT (initial), Bridged (planned)

# Software Installed
- OpenSSH Server
- net-tools (ifconfig, netstat)
- curl, wget
- htop (process monitoring)
- vim (text editor)

---

# About This Project

**Author:** Stanley Kafuko  
**Purpose:** Career transition preparation - Fachinformatiker für Systemintegration Ausbildung  
**Date:** December 2025 - ongoing  
**Status:** In Progress (Phase 1 Complete, Phase 2 Planned)

**Contact:**
- 📧 Email: stanleykafuko@gmail.com
- 💼 LinkedIn: www.linkedin.com/in/stanley-kafuko-5787b72a8
- 🐱 GitHub: https://github.com/kstanl



#  License

This project is for educational purposes. Documentation and screenshots are provided as-is for learning and portfolio demonstration.


#  Acknowledgments

- ReDI School of Digital Integration (München) for foundational IT training
- Ubuntu community for comprehensive documentation
- VirtualBox community for virtualization support
- Online IT communities for troubleshooting guidance


#  Project Tags

`linux` `ubuntu-server` `system-administration` `virtualization` `virtualbox` `ssh` `networking` `homelab` `learning` `it-ausbildung` `systemintegration` `portfolio-project`


**Note:** This is an ongoing learning project. Updates and improvements are continuously being made as I expand my knowledge of Linux system administration and networking.

For the complete technical documentation with detailed commands and screenshots, see [Home_Lab_Documentation.pdf](Home_Lab_Documentation.pdf).