# PENETRATION TESTING REPORT
## Footprinting, Reconnaissance & Network Scanning

**W2-PM-FINAL | CYBERSECURITY & ETHICAL HACKING | NETWORKWALKS**

| Field | Details |
|---|---|
| **Pentester Name** | Adigun Olamide Precious |
| **Program** | Cybersecurity & Ethical Hacking Internship |
| **Batch** | B084 – NETWORKWALKS |
| **Report Date** | 11 November 2026 |
| **Modules** | W2-PM1 – Multiple Kali Linux Tools; W2-PM5 – Zenmap Scanning |
| **Target Domain** | `networkwalks.com` |
| **Internal Network Target** | My own VirtualBox Host-Only Network |
| **Permission** | Authorized educational testing / personally controlled lab |
| **Phases Covered** | Phase 1: Reconnaissance & Footprinting; Phase 2: Scanning & Network Discovery |
| **Practical Status** | Footprinting evidence and detailed host records to be completed from verified outputs |

---

# 1. Liability Disclaimer

All activities documented in this report were intended for educational and research purposes.

Testing was restricted to systems and networks for which authorization was available or which I personally controlled. No unauthorized access, exploitation or malicious activity was intended.

The techniques and tools discussed in this report must only be used within an approved testing scope. Unauthorized access to computer systems and networks may result in legal consequences.

The responsibility for the proper and lawful use of the knowledge gained from these exercises rests with the individual performing the activities.

# 2. Introduction

This report documents the practical activities I carried out during Week 2 of my Cybersecurity and Ethical Hacking Internship with NETWORKWALKS, Batch B084.

The practical activities focused on two important stages of penetration testing:

1. **Footprinting and Reconnaissance:** Gathering publicly available information about a target domain using multiple Kali Linux tools.
2. **Scanning and Network Discovery:** Identifying active devices on my own local network using Zenmap (Nmap GUI).

During the network scanning exercise, I worked with Kali Linux running inside Oracle VirtualBox and a Windows host machine.

I identified my network interfaces and subnet configuration before performing a Ping Scan with Zenmap. The scan detected **three live hosts** on my Host-Only network.

The purpose of these exercises was to understand how cybersecurity professionals gather information about a target, identify active devices and document potential security risks before proceeding to more advanced testing.

This report presents the tools used, practical procedures, verified network configuration, observations, risk analysis, recommendations and supporting evidence.

# 3. Tools and Technologies Used

The following tools and technologies were used or covered during the Week 2 practical exercises.

| Tool | Purpose |
|---|---|
| Kali Linux | Linux environment for reconnaissance and footprinting |
| Oracle VirtualBox | Running Kali Linux in a virtual machine |
| WHOIS | Retrieving publicly available domain registration information |
| WhatWeb | Identifying website technologies and web server information |
| Nslookup | Resolving domain names into IP addresses |
| Curl | Inspecting HTTP response headers |
| Wafw00f | Identifying Web Application Firewalls |
| DNSRecon | Enumerating DNS records |
| Zenmap | Graphical interface for Nmap network scanning |
| Nmap | Discovering active hosts on a network |
| Windows CMD | Checking Windows network configuration |
| Npcap | Supporting packet capture and network scanning on Windows |

# 4. Activities Performed

## 4.1 Footprinting and Reconnaissance

The first practical activity involved understanding how to collect information about a target domain using Kali Linux.

The target domain for the exercise was:

`networkwalks.com`

The following six tools were covered.

### 4.1.1 WHOIS

**Purpose:** WHOIS is used to retrieve publicly available domain registration information.

**Command used:**

```bash
whois networkwalks.com
```

**Information investigated:**

- Domain registrar.
- Domain creation and expiration dates.
- Domain registration status.
- Name servers.
- Publicly available registration information.

**Security relevance:**

WHOIS information can help a penetration tester understand a domain's registration history and identify publicly exposed infrastructure details.

**Result:** [Insert verified WHOIS findings.]

**Evidence:** `screenshots/01-whois.png`

### 4.1.2 WhatWeb

**Purpose:** WhatWeb identifies technologies used by websites.

**Command used:**

```bash
whatweb networkwalks.com
```

**Information investigated:**

- Content Management System (CMS).
- Web server technologies.
- Programming technologies.
- Website frameworks.
- Other publicly detectable technologies.

**Security relevance:**

Technology fingerprinting helps security professionals understand the technologies running on a website and identify components that may require further security assessment.

**Result:** [Insert the actual technologies and versions returned by your scan.]

**Evidence:** `screenshots/02-whatweb.png`

### 4.1.3 Nslookup

**Purpose:** Nslookup is used to query DNS servers and resolve domain names into IP addresses.

**Command used:**

```bash
nslookup networkwalks.com
```

**Information investigated:**

- Domain IP address.
- DNS server response.
- Domain name resolution.

**Security relevance:**

DNS resolution helps identify the IP address associated with a domain and provides useful information about its hosting infrastructure.

**Result:** [Insert the actual IP address returned.]

**Evidence:** `screenshots/03-nslookup.png`

### 4.1.4 Curl

**Purpose:** Curl is used to communicate with web servers and retrieve HTTP response information.

**Command used:**

```bash
curl -I https://networkwalks.com
```

**Information investigated:**

- HTTP response status.
- Server response headers.
- Content type.
- Web server information.
- Other exposed HTTP header details.

**Security relevance:**

HTTP headers can reveal technical information about a web application. Reviewing them helps identify information that may be unnecessarily exposed.

**Result:** [Insert the actual HTTP response and relevant headers.]

**Evidence:** `screenshots/04-curl.png`

### 4.1.5 Wafw00f

**Purpose:** Wafw00f is used to identify whether a website is protected by a Web Application Firewall (WAF).

**Command used:**

```bash
wafw00f https://networkwalks.com
```

**Information investigated:**

- Whether a WAF was detected.
- The identified WAF technology, if any.
- Additional detection information.

**Security relevance:**

Identifying a WAF helps a security professional understand part of the website's defensive infrastructure.

**Result:** [Insert the actual Wafw00f output. Do not assume a WAF was detected.]

**Evidence:** `screenshots/05-wafw00f.png`

### 4.1.6 DNSRecon

**Purpose:** DNSRecon is used to perform DNS enumeration and collect information about a domain's DNS infrastructure.

**Command used:**

```bash
dnsrecon -d networkwalks.com
```

**Information investigated:**

- A records.
- NS records.
- MX records.
- TXT records.
- SPF information, where published.
- Other DNS information returned by the tool.

**Security relevance:**

DNS enumeration helps security professionals understand the publicly visible DNS infrastructure associated with a domain.

**Result:** [Insert the actual DNSRecon findings.]

**Evidence:** `screenshots/06-dnsrecon.png`

## 4.2 Network Scanning with Zenmap

The second practical activity involved identifying active devices on my local network using Zenmap.

Zenmap is the graphical interface for Nmap and makes it easier to configure scans, view results and understand network topology.

### 4.2.1 Network Environment

I used Oracle VirtualBox to run Kali Linux on my Windows computer.

During the practical, I identified the following network interfaces:

| Device / Interface | IP Address | Purpose |
|---|---|---|
| Kali Linux – eth0 | `10.0.2.15` | VirtualBox NAT connection |
| Kali Linux – eth1 | `192.168.56.102` | Host-Only network connection |
| Kali Linux – lo | `127.0.0.1` | Loopback interface |
| Windows Host-Only Adapter | `192.168.56.1` | Host machine connection |

**My Host-Only network configuration:**

| Field | Value |
|---|---|
| Network Address | `192.168.56.0` |
| Subnet Mask | `255.255.255.0` |
| CIDR Notation | `/24` |
| Network Range | `192.168.56.1 – 192.168.56.254` |
| Broadcast Address | `192.168.56.255` |

The Host-Only network allowed communication between my Windows host machine and the Kali Linux virtual machine.

### 4.2.2 Identifying My Local IP Address and Subnet

I used Windows Command Prompt to check the network configuration of my computer.

**Command used:**

```cmd
ipconfig
```

I examined the VirtualBox Host-Only Ethernet adapter to identify its IPv4 address and subnet mask.

The Windows Host-Only adapter had the IP address:

```text
192.168.56.1
```

The subnet mask was:

```text
255.255.255.0
```

This confirmed that the Host-Only network was:

```text
192.168.56.0/24
```

**Evidence:** `screenshots/07-ipconfig.png`

### 4.2.3 Configuring Zenmap

After identifying my subnet, I opened Zenmap on Windows.

I entered the network range into the Target field.

**Target:**

```text
192.168.56.0/24
```

**Scan Profile:**

```text
Ping Scan
```

**Nmap Command:**

```bash
nmap -sn 192.168.56.0/24
```

The `-sn` option performs host discovery without conducting a port scan.

I used this scan to identify devices responding on my local network.

### 4.2.4 Live Host Discovery Results

After executing the Ping Scan, Zenmap identified:

**3 live hosts on my local network.**

This demonstrated that three devices responded to the host discovery scan.

| Metric | Observed Result |
|---|---|
| Network Scanned | `192.168.56.0/24` |
| Scan Type | Ping Scan |
| Command | `nmap -sn 192.168.56.0/24` |
| Live Hosts Detected | **3** |
| MAC Addresses | To be documented from actual Zenmap output |
| Individual Host IPs | To be documented from actual Zenmap output |

The individual host IP addresses and MAC addresses should be copied directly from the Zenmap scan results.

**Evidence:** `screenshots/08-zenmap-scan.png`

### 4.2.5 Network Topology

After completing the network discovery scan, I used the Topology tab in Zenmap to view the discovered network structure.

The topology feature provides a graphical representation of discovered hosts and their relationships within the scanned network.

I examined the topology view and used the available legend to understand the displayed network information.

The topology was intended to provide a visual representation of the devices discovered during the scan.

**Evidence:** `screenshots/09-network-topology.png`

# 5. Risk Analysis and Impact

The following table highlights potential security observations associated with the practical activities.

These are preliminary observations and not confirmed vulnerabilities.

| No. | Risk / Finding | Evidence / Observation | Potential Impact | Risk Level |
|---|---|---|---|---|
| 1 | Website technology fingerprinting | WhatWeb can reveal publicly detectable technologies | Attackers may use technology information to identify components requiring security review | Medium |
| 2 | Public DNS information | Nslookup and DNSRecon retrieve DNS information | May help an attacker understand the target's infrastructure | Low |
| 3 | HTTP header information exposure | Curl retrieves HTTP response headers | Unnecessary technical information may assist further fingerprinting | Low |
| 4 | WAF identification | Wafw00f checks for WAF technology | Reveals information about the website's defensive infrastructure | Low |
| 5 | Multiple active network devices | Zenmap identified three live hosts | Unknown devices may require investigation | Medium |
| 6 | Network configuration visibility | VirtualBox Host-Only network uses a shared subnet | Misconfiguration or excessive access could expose lab devices to unintended communication | Low |

**Risk Level Key:**

- Critical: Immediate and severe security concern.
- High: Significant security concern.
- Medium: Requires investigation and appropriate controls.
- Low: Limited potential impact but worth reviewing.

The findings in this report are based on information gathering and network discovery. No exploitation or vulnerability validation was performed during these exercises.

# 6. Recommendations

Based on the activities performed, I recommend the following security practices:

1. **Regular technology reviews:** Organizations should regularly review publicly exposed website technologies and software versions.

2. **Software updates:** CMS platforms, plugins and web applications should be updated regularly to address known security issues.

3. **Secure HTTP headers:** Organizations should review HTTP response headers and configure appropriate security headers.

4. **DNS security:** DNS records should be reviewed periodically to ensure that unnecessary information is not exposed.

5. **WAF configuration:** Web Application Firewalls should be properly configured, maintained and monitored.

6. **Network monitoring:** Organizations should perform regular network discovery to identify devices connected to their networks.

7. **Unknown device investigation:** Any unexpected device discovered during a network scan should be investigated.

8. **Network documentation:** Organizations should maintain updated records of their network devices, IP addresses and network topology.

9. **Access control:** Network access should be restricted to authorized users and devices.

10. **Authorized security testing:** All reconnaissance and scanning activities should be conducted within an approved testing scope.

# 7. Conclusion

During Week 2 of my Cybersecurity and Ethical Hacking Internship with NETWORKWALKS, Batch B084, I worked on practical activities covering footprinting, reconnaissance and network scanning.

The footprinting exercise introduced me to six important Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon. These tools demonstrate how security professionals gather publicly available information about a target domain.

For the network scanning exercise, I used Windows Command Prompt to identify my network configuration and Zenmap to perform host discovery on my VirtualBox Host-Only network.

I successfully identified my network configuration as `192.168.56.0/24` and detected **three live hosts** using the Nmap Ping Scan command:

```bash
nmap -sn 192.168.56.0/24
```

I also learned how to work with different VirtualBox network interfaces, distinguish between NAT and Host-Only networking, and understand the purpose of network topology visualization.

One important lesson from this practical is that reconnaissance and network scanning are essential stages of penetration testing. Before attempting advanced security assessments, a cybersecurity professional needs to understand the target environment and identify the systems and services within the approved scope.

The exercises also improved my understanding of technical documentation, evidence collection, network identification and responsible security testing.

Overall, this practical strengthened my foundational knowledge of ethical hacking and gave me more confidence in using Kali Linux, Windows networking tools and Zenmap for authorized security assessments.

# 8. Evidence Collected

Screenshots and supporting evidence from the practical exercises are organized in the `screenshots/` directory.

| No. | Screenshot | Description |
|---|---|---|
| 1 | `01-whois.png` | WHOIS domain information |
| 2 | `02-whatweb.png` | WhatWeb technology fingerprinting |
| 3 | `03-nslookup.png` | DNS resolution results |
| 4 | `04-curl.png` | HTTP response headers |
| 5 | `05-wafw00f.png` | WAF detection results |
| 6 | `06-dnsrecon.png` | DNS enumeration results |
| 7 | `07-ipconfig.png` | Windows IP configuration |
| 8 | `08-zenmap-scan.png` | Zenmap Ping Scan showing three live hosts |
| 9 | `09-network-topology.png` | Zenmap network topology |

## 9. Project Structure

The recommended GitHub repository structure is:

```text
WEEK-2-PENETRATION-TESTING/
│
├── README.md
│
├── screenshots/
│   ├── 01-whois.png
│   ├── 02-whatweb.png
│   ├── 03-nslookup.png
│   ├── 04-curl.png
│   ├── 05-wafw00f.png
│   ├── 06-dnsrecon.png
│   ├── 07-ipconfig.png
│   ├── 08-zenmap-scan.png
│   └── 09-network-topology.png
│
└── reports/
    └── week-2-penetration-testing-report.pdf
```

---

**PROGRAM:** Cybersecurity & Ethical Hacking Internship

**ORGANIZATION:** NETWORKWALKS

**BATCH:** B084

**REPORT:** W2-PM-FINAL

**AUTHOR:** Adigun Olamide Precious

**END OF REPORT**
