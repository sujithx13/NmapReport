 Nmap TCP SYN Scan on Localhost

This repository contains the results and analysis of an `nmap` scan conducted on the localhost IP address. The primary objective of this scan is to identify open TCP ports using a **TCP SYN scan**, and assess potential security risks associated with the exposed services.


Nmap (Network Mapper) is an open-source tool for network exploration and security auditing. This project focuses on scanning the localhost using the TCP SYN scan (`-sS`), which is known for being stealthy and effective in identifying open ports without establishing a full TCP connection.

Prerequisites

- Operating System: Linux
- Nmap version 7.90 or higher recommended
sudo nmap -sS -T4 -Pn -v  192.168.191.134/24

 192.168.191.134/24	Target IP (localhost)

🔐 Security Risk Analysis

Potential Security Risks from Open Ports:

1. Port 902
Usage: Often used by VMware for remote management and authentication between VMware products.
Risks:If VMware services are running and exposed to untrusted networks, attackers could exploit vulnerabilities in VMware authentication or management services.

Potential for brute-force attacks against VMware credentials.

Mitigation: Restrict access to trusted IPs only, patch VMware software, disable if VMware is not in use.

2. Port 912
Usage: Related to VMware or sometimes network file system services.
Risks:Could allow unauthorized remote control or interaction if not secured.

Vulnerable versions could be exploited to gain control over virtual machines.

Mitigation: Disable the service if unused; otherwise, secure with strong authentication and firewall rules.

3. Port 5357
Usage: Used by Windows for device discovery and control (e.g., printers, scanners) via Web Services on Devices API.
Risks:Attackers on the same network could query or interact with connected devices.

Could leak network information or device details that help in reconnaissance.

Mitigation: Disable WSDAPI if not using network device discovery; block from untrusted networks with a firewall.


Disclaimer:

This scan was conducted in a controlled local environment for educational and research purposes. Do not scan external networks without proper authorization.
