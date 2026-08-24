# PENETRATION TESTING REPORT (SAMPLE)
### Footprinting & Network Scanning Phases

**W2-PM-FINAL  |  CYBERSECURITY  |  NETWORKWALKS**

| Field | Detail |
|---|---|
| **Pentester Name (Cybersecurity Professional)** | **Ingrid Kombe** |
| **Program/Batch** | B082-Networkwalks |
| **Date** | 22 August 2026 |
| **Modules completed** | W2-PM1 (Multiple Kali Tools)<br>W2-PM5 (Zenmap Scanning) |
| **Client/Target** | 1. Networkwalks (secured written permission already)<br>2. My own local LAN Network |
| **Permission secured from client?** | Yes |
| **Phases covered** | **Phase 1:** Reconnaissance & Footprinting<br>**Phase 2:** Scanning & Network Discovery<br>

# 1. Liability Disclaimer

I have performed these activities only on the systems & devices where I had secured written permission or the devices/systems that I own myself. All these materials are for education and research purpose only. Do not use anything from here to break the law. The instructor, the authors and Networkwalks are not responsible for what you do with this knowledge. Every action you take is your own responsibility. Misuse can lead to criminal charges, heavy fines, loss of your job and a permanent record. In most countries unauthorised access is a crime even when nothing is damaged.

## 2. Assignment Overview
This penetration testing assignment is part of my cybersecurity internship program. The objective is to demonstrate practical skills in reconnaissance and network scanning with Zenmap.

## 3. Scope of Work

### Phase 1: Footprinting
The first phase involves passive reconnaissance using the following tools to gather information about target systems:

| Tool | Purpose |
|------|---------|
| **WHOIS** | Domain ownership and registration details |
| **WhatWeb** | Web technology identification |
| **NSLookup** | DNS record resolution |
| **DNSRecon** | Comprehensive DNS enumeration |
| **cURL -I** | HTTP header analysis |
| **WAFW00F** | Web Application Firewall detection |

### Phase 2: Network Scanning
The second phase uses Zenmap (Nmap GUI) to identify:
- Live hosts on the local network
- Open ports and services
- Operating systems
- Network topology

## Learning Objectives
- Understand reconnaissance methodologies
- Master footprinting tools and techniques
- Develop network scanning skills
- Document findings professionally

## Testing Environment
- **Platform:** Kali Linux
- **Network:** Local area network.
- **Targets:** Authorized Website only

## 3. Footprinting Results

### 3.1 WHOIS Analysis

**Command:** `whois networkwalks.com`
**Key Observations:**
- Domain Created: 2019-11-06T22:51:46Z.
- Registrar: GoDaddy.com, LLC
- Nameservers: NS6135.HOSTGATOR.COM, NS6136.HOSTGATOR.COM
- DNSSEC: unsigned.

- ---

### 3.2 WhatWeb Analysis

**Command:** `whatweb networkwalks.com`
**Key Observations:**
- Web Server: Apache
- Technologies: WordPress 7.1,WordPress Download Manager 3.3.58.
- Frameworks: Bootstrap[7.1].

- ---

- ### 3.3 NSLookup Analysis

**Command:** `nslookup networkwalks.com`
**Key Observations:**
- IPv4 Address: 192.232.216.135
- DNS Server:  8.8.8.8

- ---

- ### 3.4 DNSRecon Analysis

**Command:** `dnsrecon -d networkwalks.com`
**Key Observations:**
- NS Records: ns6136.hostgator.com 192.232.216.131, ns6135.hostgator.com 50.87.144.87
- MX Records: mail.networkwalks.com 192.232.216.135
- TXT Records: TXT networkwalks.com v=spf1 +a +mx +ip4:50.87.144.87 +include:websitewelcome.com ~all, TXT networkwalks.com google-site-verification=rr04eRmqHoWY3XemnizDNVK4q75X-Ij-mjgEeg-UsYI

- ---

- ### 3.5 cURL Headers Analysis

**Command:** `curl -I networkwalks.com`
| Header | Value | Implication |
|--------|-------|-------------|
| `x-endurance-cache-level` | 0 | Endurance page cache is bypassed/disabled for this page |
| `x-nginx-cache` | WordPress | Nginx FastCGI cache is active for WordPress |
-WordPress REST API endpoint /wp-json/

---

### 3.6 WAFW00F Analysis

**Command:** `wafw00f networkwalks.com`
**Key Observations:**
- WAF Detected: Yes
- WAF Type: ModSecurity (SpiderLabs) WAF

## 4. Network Scanning with Zenmap

### Task 1: Download & Install Zenmap on Windows

#### Step 1: Download and install Zenmap
 Navigate to the official Nmap download page:
   - URL: https://nmap.org/download.html
---
