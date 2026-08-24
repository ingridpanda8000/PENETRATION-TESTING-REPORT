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

## 4: Network Scanning with Zenmap

### Task 1: Download & Install Zenmap on Windows

#### Step 1: Download and install Zenmap
 Navigate to the official Nmap download page:
   - URL: https://nmap.org/download.html
---

### Task 2: Find Your Local IP Address & LAN Subnet

### Using Command Prompt (ipconfig)

- LAN Network is: 192.168.1.0/24

### Task 3: Find the List of Live Hosts/PCs in Your IP Subnet
#### Using Zenmap GUI
**Scan Target:** 192.168.1.0/24
**Scan Profile:** Ping Scan
**Command:** `nmap -sn 192.168.1.0/24`

- `192.168.1.3`
- `192.168.1.4`
- `192.168.1.5`
- `192.168.1.39`
- `192.168.1.40`

 ### Task 4: Host Count in Your Subnet

**Total IPs Scanned:** 256 (for /24 subnet)
**Live Hosts Found:** 5 include my computer

### Task 5: Live Host IP Addresses

| # | IP Address | 
|---|------------|
| 1 | 192.168.1.3 |
| 2 | 192.168.1.5 | 
| 3 | 192.168.1.39 | 
| 4 | 192.168.1.40 | 
| 5 | 192.168.1.4 | 

### Task 6: MAC Addresses of Live Hosts

| # | IP Address | MAC Address | 
|---|------------|-------------|
| 1 | 192.168.1.3 | AA:CD:92:CD:3B:24 | 
| 2 | 192.168.1.4 | 02:AA:C0:C3:60:38 | 
| 3 | 192.168.1.5 | 9A:76:20:61:9D:56  |
| 4 | 192.168.1.39 | 4A:C6:C9:60:2B:AE   |

### Task 7: Display & Save Topology in PDF Format

**Method:** Zenmap Topology Tab → Export to PDF

**Output Details:**
- **File Name:** `zenmap_topology.pdf`
- **Save Location:** Desktop
- **Format:** PDF
- **Contents:** Network topology visualization with all live hosts

## 5. Security Analysis

### 5.1 Identified Issues

The following security issues were identified during the footprinting and network scanning phases:

| # | Issue | Severity | Affected System | Description |
|---|-------|----------|-----------------|-------------|
| 1 | Exposed Web Technologies | 🟡 Medium | Web Server | WhatWeb identified Nginx, WordPress 7.1,WordPress Download Manager 3.3.58. Attackers can target version-specific vulnerabilities. |
| 2 | Server IP Address Disclosure | 🟡 Medium | Web Server | WHOIS and NSLookup revealed the server IP address (192.232.216.135). Attackers can bypass DNS protections and target infrastructure directly. |
| 3 | Live Hosts Discovery | 🟡 Medium | Local Network | Zenmap scan identified 5 live hosts including gateway, web server, workstations, and laptops. Attackers can map network topology. |
| 4 | HTTP Headers Exposure | 🟡 Medium | Web Server | cURL -I exposed response headers and exposed /wp-json. Aids technology fingerprinting. |
| 5 | DNS Reconnaissance | 🟡 Medium | DNS Infrastructure | DNSRecon identified NS records, MX records, and TXT. Attackers can map DNS infrastructure. |
| 6 | WAF Detection | 🟢 Low | Web Application | WAFW00F detected ModSecurity (SpiderLabs).|

### 5.2 Severity Legend

| Severity | Description | Action Required |
|----------|-------------|-----------------|
| 🔴 Critical | Immediate threat to system security | Action required within 1 hour |
| 🔴 High | Significant vulnerability | Action required within 24 hours |
| 🟡 Medium | Moderate risk requiring attention | Action required within 1 week |
| 🟢 Low | Minor issue, monitor only | Action recommended |

### 5.3 Recommended Actions

| # | Issue | Action | Priority |
|---|-------|--------|----------|
| 1 | Exposed Web Technologies | Hide headers (Server, X-Powered-By). Update all software. | 🔴 High |
| 2 | Server IP Disclosure | Use CDN/reverse proxy. Enable WHOIS privacy. | 🔴 High |
| 3 | Live Hosts Discovery | Network segmentation. Close unused ports. | 🟡 Medium |
| 4 | HTTP Headers Exposure | Remove sensitive headers. Add security headers (CSP, HSTS, X-Frame-Options). | 🔴 High |
| 5 | DNS Reconnaissance | Restrict zone transfers. Hide subdomains. Implement DNSSEC. | 🟡 Medium |
| 6 | WAF Detection |  WAF exists: Update rules. | 🟡 Medium |

## 6. Conclusion

This assignment provided hands-on experience with **footprinting tools** (WHOIS, WhatWeb, NSLookup, DNSRecon, cURL -I, WAFW00F) and **network scanning** (Zenmap).

**Key Learnings:**
- Reconnaissance techniques are essential for understanding attack surfaces
- Information disclosure is a common vulnerability that can be easily remediated
- Network topology mapping helps identify security risks
- Professional documentation is critical in cybersecurity

The practical experience gained has strengthened understanding of penetration testing methodologies and their importance in maintaining robust security postures.

---
