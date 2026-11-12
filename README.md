# 🔐 Footprinting, Reconnaissance & Network Scanning

Practical cybersecurity exercises covering information gathering, domain reconnaissance, and network discovery using Kali Linux tools.

## 📌 Project Overview

This repository documents the practical exercises completed during Week 2 of the Networkwalks Cybersecurity Internship (Batch B082).

The project focuses on footprinting, reconnaissance, and network scanning using different tools available in Kali Linux.

The exercises involved gathering publicly available information about an authorised domain, examining DNS and web technologies, identifying information exposed through reconnaissance tools, and performing host discovery within an authorised virtual lab network.

## 🎯 Objectives

The main objectives of this project were to:

- Perform domain footprinting and information gathering using multiple Kali Linux tools.
- Identify domain registration details and DNS records.
- Examine web technologies, HTTP response headers, and WAF detection results.
- Use theHarvester to gather publicly available information from different sources.
- Perform network host discovery using Nmap and Zenmap.
- Identify live hosts within the authorised virtual lab network.
- Generate a network topology map.
- Document practical activities, observations, and results.

## 🛡️ Scope and Purpose

The exercises were conducted for educational purposes under the Networkwalks cybersecurity internship authorisation.

The authorised website target for the footprinting exercises was:

- `networkwalks.com`

Network scanning was restricted to the tester's authorised virtual lab network.

All activities were limited to permitted information gathering and host discovery. No exploitation, brute-force attacks, denial-of-service activities, or unauthorised access were performed.

## ⚙️ Tools and Environment

| Component | Configuration |
|---|---|
| Operating System | Kali Linux |
| Environment | Oracle VM VirtualBox |
| Network Interface | eth0 |
| Footprinting Target | networkwalks.com |
| Network Scanning | Authorised virtual lab network |
| Nmap Version | 7.95 |
| theHarvester Version | 4.11.1 |

## 🧰 Project Modules

### W2-PM1: Footprinting with Multiple Kali Linux Tools

**Objective:** Gather and analyse publicly available information about the authorised target domain using multiple reconnaissance tools.

**Tools Used:**

- WHOIS
- WhatWeb
- Nslookup
- cURL
- WAFW00F
- DNSRecon

#### Step 1. WHOIS – Domain Registration Information

Command:

`whois networkwalks.com`

Purpose:

To retrieve publicly available domain registration information, including registrar details, domain creation and expiry dates, name servers, and domain status.

#### Step 2. WhatWeb – Web Technology Identification

Command:

`whatweb networkwalks.com`

Purpose:

To identify technologies and services associated with the target website, including its web server, content management system, frameworks, and other detectable components.

#### Step 3. Nslookup – DNS Resolution

Command:

`nslookup networkwalks.com`

Purpose:

To resolve the target domain to its associated IP address and examine the DNS response.

#### Step 4. cURL – HTTP Header Analysis

Command:

`curl -I https://networkwalks.com`

Purpose:

To retrieve HTTP response headers and examine server responses, cookies, content type, and other header information.

#### Step 5. WAFW00F – Web Application Firewall Detection

Command:

`wafw00f https://networkwalks.com`

Purpose:

To identify whether a web application firewall could be detected by the tool.

#### Step 6. DNSRecon – DNS Enumeration

Command:

`dnsrecon -d networkwalks.com`

Purpose:

To enumerate DNS records, including SOA, NS, MX, A, TXT, and SRV records.

#### Key Observations

- Domain registration information and name server details were retrieved.
- The website redirected HTTP requests to HTTPS.
- Web technologies and server information were identified.
- DNS records associated with the target domain were enumerated.
- WAFW00F identified a ModSecurity (SpiderLabs) WAF.
- DNSRecon reported eight SRV records.

### W2-PM4: theHarvester-Based Footprinting

**Objective:** Gather publicly available information about the authorised domain using different search sources.

**Tool Used:** theHarvester 4.11.1

#### Task 1. Baidu Search

Command:

`theHarvester -d networkwalks.com -l 1000 -b baidu`

Purpose:

To search Baidu for publicly available information associated with the target domain.

Observation:

The search completed without returning email addresses, IP addresses, people, or hostnames.

#### Task 2. Multiple Search Sources

Command:

`theHarvester -d networkwalks.com -l 50 -b all`

Purpose:

To gather information from multiple supported public sources.

Key Observations:

- The tool identified hostnames and subdomain-related entries.
- No email addresses or people were returned.
- Some search sources required API keys that were unavailable or invalid.
- The tool reported an ASN associated with the results.
- Some results contained aliases and mapped addresses, so the number of returned entries should not be interpreted as the number of unique subdomains.

**Important:** Results were limited by source availability and API-key configuration. The findings therefore do not represent a complete inventory of the target's publicly available information.

### W2-PM5: Zenmap-Based Network Scanning

**Objective:** Discover live hosts within the authorised virtual lab network and generate a network topology map.

**Tools Used:**

- Nmap
- Zenmap

#### Step 1. Identify the Network Configuration

Commands:

`ip -br addr`

`ip route`

Purpose:

To identify the Kali Linux interface, assigned IP address, subnet, and default gateway.

#### Step 2. Perform Host Discovery

Command:

`sudo nmap -sn 10.0.0.0/24`

Purpose:

To discover active hosts within the virtual lab subnet without performing a port scan.

#### Step 3. Identify Network Interface MAC Address

Command:

`ip link show eth0`

Purpose:

To retrieve the MAC address assigned to the Kali Linux network interface.

#### Step 4. Generate Network Topology

Zenmap was used to visualise the network discovery results and generate a network topology report in PDF format.

#### Key Observations

- Three live hosts were reported within the scanned virtual subnet.
- IP and MAC address information was recorded for the discovered hosts.
- Kali Linux was identified as one of the active hosts.
- A network topology map was generated using Zenmap.

**Note:** The scanned subnet was the VirtualBox lab network, not the physical local Wi-Fi network.

## 📊 Skills Practised

- Domain footprinting and reconnaissance
- WHOIS information gathering
- DNS enumeration and analysis
- Web technology identification
- HTTP header inspection
- WAF detection
- Public-source information gathering
- Network host discovery
- IP and MAC address identification
- Network topology visualisation
- Technical documentation and evidence handling

## 💡 Key Takeaway

This project provided practical experience with different reconnaissance and network discovery tools.

An important lesson was that automated tools do not always return complete or consistent results. Understanding their outputs, recognising their limitations, and interpreting findings within the authorised testing scope are essential parts of responsible cybersecurity practice.

---

👤 **Author:** Mercy Oyanimughan

📌 **Project Information:** Footprinting, Reconnaissance & Network Scanning | Week 02 | Networkwalks Cybersecurity Internship

**Batch:** B082

**Instructor:** Waqas Karim (CCIE)

**Programme:** Networkwalks Cybersecurity Internship
