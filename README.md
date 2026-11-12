# PENETRATION TESTING REPORT
## Footprinting, Reconnaissance & Network Scanning

**W2-PM-FINAL | CYBERSECURITY & ETHICAL HACKING | NETWORKWALKS**

---

### REPORT INFORMATION

| Field | Details |
|---|---|
| **Pentester Name** | Adigun Olamide Precious |
| **Program** | Cybersecurity & Ethical Hacking Internship |
| **Organization** | NETWORKWALKS |
| **Batch** | B084 |
| **Report Date** | 11 November 2026 |
| **Modules** | W2-PM1 – Multiple Kali Linux Tools; W2-PM5 – Zenmap Scanning |
| **Target Domain** | networkwalks.com |
| **Internal Network Target** | Personal VirtualBox Host-Only Network |
| **Testing Authorization** | Authorized educational testing / personally controlled lab |
| **Phases Covered** | Phase 1: Reconnaissance & Footprinting; Phase 2: Scanning & Network Discovery |

---

# 1. EXECUTIVE SUMMARY

This report documents the practical penetration testing activities completed during Week 2 of my Cybersecurity and Ethical Hacking Internship with NETWORKWALKS, Batch B084.

The exercises focused on two fundamental phases of penetration testing: Footprinting and Reconnaissance, followed by Scanning and Network Discovery.

During the first exercise, I used six Kali Linux tools to gather publicly available information about the target domain, `networkwalks.com`. The tools included WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon.

The results provided information about the domain registration, website technologies, DNS configuration, HTTP response headers and Web Application Firewall detection.

For the second exercise, I used Windows Command Prompt to identify my local network configuration and Zenmap to perform host discovery on my VirtualBox Host-Only network.

The network was identified as `192.168.56.0/24`, and the Ping Scan successfully detected three live hosts.

These exercises improved my practical understanding of reconnaissance techniques, network identification, host discovery, security observations and technical documentation.

# 2. LIABILITY DISCLAIMER

All activities documented in this report were conducted for educational and research purposes.

The reconnaissance exercise was limited to the specified target domain and the network scanning exercise was performed on my personally controlled VirtualBox Host-Only environment.

No unauthorized access, exploitation or malicious activity was intended.

The tools and techniques discussed in this report should only be used against systems and networks for which proper authorization has been obtained.

The responsibility for ensuring that cybersecurity activities comply with applicable laws, regulations and testing permissions rests with the individual performing them.

# 3. INTRODUCTION

Penetration testing is an authorized security assessment process used to identify potential weaknesses in computer systems, applications and networks.

Before attempting advanced security assessments, penetration testers must understand their target environment, gather relevant information and identify active systems.

This practical exercise introduced me to two important stages of penetration testing.

**3.1 Footprinting and Reconnaissance**

This involves gathering publicly available information about a target to understand its digital presence, infrastructure and technologies.

**3.2 Scanning and Network Discovery**

This involves identifying active devices and understanding the structure of a network through authorized scanning techniques.

For this practical, I used Kali Linux running inside Oracle VirtualBox, alongside my Windows host machine.

The target domain for the reconnaissance exercise was `networkwalks.com`, while the network discovery exercise was performed on my own Host-Only network.

# 4. OBJECTIVES OF THE PRACTICAL

The major objectives were to:

1. Understand the importance of footprinting and reconnaissance in penetration testing.
2. Learn how to use different Kali Linux reconnaissance tools.
3. Retrieve publicly available domain registration information.
4. Identify technologies used by a website.
5. Perform DNS queries and enumeration.
6. Examine HTTP response headers.
7. Identify whether a Web Application Firewall could be detected.
8. Understand local IP addresses, subnet masks and network ranges.
9. Use Zenmap to discover active devices on a local network.
10. Interpret network scanning results and document security observations.

# 5. TOOLS AND TECHNOLOGIES USED

The following tools and technologies were used during the practical exercises.

| Tool | Purpose |
|---|---|
| Kali Linux | Operating system for cybersecurity and penetration testing activities |
| Oracle VirtualBox | Running Kali Linux in a virtual machine |
| WHOIS | Retrieving domain registration information |
| WhatWeb | Identifying website technologies |
| Nslookup | Resolving domain names into IP addresses |
| Curl | Retrieving HTTP response information and headers |
| Wafw00f | Detecting Web Application Firewalls |
| DNSRecon | Enumerating DNS records |
| Zenmap | Graphical interface for Nmap scanning |
| Nmap | Discovering active hosts on a network |
| Windows CMD | Checking Windows network configuration |
| Npcap | Providing packet capture support for Windows-based network tools |

# 6. ACTIVITIES PERFORMED

## 6.1 PHASE ONE: FOOTPRINTING AND RECONNAISSANCE

The first practical exercise focused on gathering publicly available information about a target domain using Kali Linux.

**Target Domain:**

`networkwalks.com`

I used six different tools to investigate the domain and understand its publicly visible infrastructure.

### 6.1.1 WHOIS – DOMAIN REGISTRATION INFORMATION

**Purpose**

WHOIS is a command-line utility used to retrieve publicly available domain registration information.

**Command Used**

```bash
whois networkwalks.com
```

**Information Investigated**

- Domain registrar.
- Domain creation date.
- Domain expiration date.
- Domain registration status.
- Name servers.
- Publicly available registration information.

**Results Obtained**

The WHOIS lookup returned the following information:

| Field | Result |
|---|---|
| Domain | networkwalks.com |
| Registrar | GoDaddy |
| Creation Date | 6 November 2019 |
| Expiration Date | 6 November 2027 |

**Security Relevance**

WHOIS information helps penetration testers understand a domain's registration history and identify publicly available information about its administration and infrastructure.

**Observation**

The domain registration lookup successfully returned information about the registrar and registration dates.

**Evidence:** `screenshots/01-whois.png`

### 6.1.2 WHATWEB – WEBSITE TECHNOLOGY FINGERPRINTING

**Purpose**

WhatWeb is a reconnaissance tool used to identify technologies and software components used by websites.

**Command Used**

```bash
whatweb networkwalks.com
```

**Information Investigated**

- Web server technology.
- Content Management System (CMS).
- Website IP address.
- Programming technologies.
- Other publicly detectable components.

**Results Obtained**

WhatWeb identified the following information:

| Field | Result |
|---|---|
| Website | networkwalks.com |
| IP Address | 192.232.216.135 |
| Web Server | Apache |
| CMS | WordPress |
| WordPress Version | 7.1.4 |
| HTTP Status | 200 OK |

**Security Relevance**

Technology fingerprinting helps security professionals understand the technologies running on a website and identify software components that may require further security assessment.

**Observation**

The scan identified Apache as the web server and WordPress as the Content Management System.

The information provides an initial understanding of the website's technology stack.

**Evidence:** `screenshots/02-whatweb.png`

### 6.1.3 NSLOOKUP – DNS RESOLUTION

**Purpose**

Nslookup is a network administration tool used to query DNS servers and resolve domain names into IP addresses.

**Command Used**

```bash
nslookup networkwalks.com
```

**Information Investigated**

- Domain IP address.
- DNS server response.
- Domain name resolution.

**Results Obtained**

| Field | Result |
|---|---|
| Domain | networkwalks.com |
| DNS Server | 8.8.8.8 |
| Resolved IP Address | 192.232.216.135 |
| Resolution Status | Successful |

**Security Relevance**

DNS resolution helps security professionals identify the IP address associated with a domain and understand part of its publicly accessible hosting infrastructure.

**Observation**

The Nslookup command successfully resolved `networkwalks.com` to `192.232.216.135` using DNS server `8.8.8.8`.

**Evidence:** `screenshots/03-nslookup.png`

### 6.1.4 CURL – HTTP RESPONSE HEADER ANALYSIS

**Purpose**

Curl is a command-line tool used to communicate with web servers and retrieve HTTP response information.

**Command Used**

```bash
curl -I https://networkwalks.com
```

**Information Investigated**

- HTTP response status.
- Server response headers.
- Web server information.
- Content type.
- Other available HTTP header details.

**Results Obtained**

| Field | Result |
|---|---|
| Target | https://networkwalks.com |
| HTTP Protocol | HTTP/2 |
| Response Status | 200 OK |
| Web Server | Apache |

**Security Relevance**

HTTP response headers can reveal technical information about a web application and its server configuration.

Reviewing these headers helps security professionals identify potentially unnecessary information exposure and assess the presence of security-related headers.

**Observation**

The server returned an HTTP/2 200 OK response, indicating that the request was successfully processed.

Apache was identified in the server response information.

**Evidence:** `screenshots/04-curl.png`

### 6.1.5 WAFW00F – WEB APPLICATION FIREWALL DETECTION

**Purpose**

Wafw00f is a reconnaissance tool used to identify whether a website is protected by a Web Application Firewall (WAF).

**Command Used**

```bash
wafw00f https://networkwalks.com
```

**Information Investigated**

- Whether a WAF was detected.
- Identified WAF technology.
- Available vendor information.
- Detection information returned by the tool.

**Results Obtained**

| Field | Result |
|---|---|
| WAF Detection | Detected |
| Identified Technology | ModSecurity |
| Associated Name | SpiderLabs |
| Reported Version | 2.3.2 |

**Security Relevance**

A Web Application Firewall helps protect web applications by monitoring and filtering HTTP traffic based on configured security rules.

Identifying a WAF provides insight into the defensive technologies that may be deployed to protect a website.

**Observation**

Wafw00f identified ModSecurity (SpiderLabs), with version 2.3.2 reported by the scan.

This result indicates that the tool detected a WAF-associated technology. It does not independently establish the effectiveness of its security configuration.

**Evidence:** `screenshots/05-wafw00f.png`

### 6.1.6 DNSRECON – DNS ENUMERATION

**Purpose**

DNSRecon is a DNS enumeration tool used to collect information about a domain's publicly available DNS infrastructure.

**Command Used**

```bash
dnsrecon -d networkwalks.com
```

**Information Investigated**

- A records.
- NS records.
- MX records.
- TXT records.
- SPF information, where published.
- SRV records.
- Other DNS information returned by the tool.

**Results Obtained**

DNSRecon successfully identified eight DNS records associated with the target domain.

The identified record types included:

| DNS Record | Purpose |
|---|---|
| A | Maps a domain name to an IPv4 address |
| NS | Identifies authoritative name servers |
| MX | Identifies mail exchange servers |
| TXT | Stores text-based DNS information |
| SRV | Provides information about specific network services |

**Security Relevance**

DNS enumeration helps security professionals understand the publicly visible DNS infrastructure associated with a domain.

It can also help identify exposed infrastructure information that may require further security review.

**Observation**

The DNSRecon exercise successfully returned eight DNS records, including A, NS, MX, TXT and SRV records.

**Evidence:** `screenshots/06-dnsrecon.png`

## 6.2 PHASE TWO: NETWORK SCANNING AND HOST DISCOVERY

The second practical exercise focused on identifying active devices on my local network using Zenmap.

Zenmap is the graphical interface for Nmap. It makes it easier to configure network scans, examine results and visualize discovered network hosts.

### 6.2.1 NETWORK ENVIRONMENT

I used Oracle VirtualBox to run Kali Linux on my Windows computer.

During the exercise, I identified the following network interfaces:

| Device / Interface | IP Address | Purpose |
|---|---|---|
| Kali Linux – eth0 | 10.0.2.15 | VirtualBox NAT connection |
| Kali Linux – eth1 | 192.168.56.102 | Host-Only network connection |
| Kali Linux – lo | 127.0.0.1 | Loopback interface |
| Windows Host-Only Adapter | 192.168.56.1 | Host machine connection |

**Host-Only Network Configuration**

| Field | Value |
|---|---|
| Network Address | 192.168.56.0 |
| Subnet Mask | 255.255.255.0 |
| CIDR Notation | /24 |
| Usable Host Range | 192.168.56.1 – 192.168.56.254 |
| Broadcast Address | 192.168.56.255 |

**Observation**

The Host-Only network allowed communication between my Windows host machine and the Kali Linux virtual machine through a separate virtual network.

This configuration provided an environment for conducting controlled network discovery exercises.

### 6.2.2 IDENTIFYING MY LOCAL IP ADDRESS AND SUBNET

Before performing the scan, I used Windows Command Prompt to identify my local network configuration.

**Command Used**

```cmd
ipconfig
```

I examined the VirtualBox Host-Only Ethernet adapter to identify its IPv4 address and subnet mask.

**Results Obtained**

| Field | Result |
|---|---|
| IPv4 Address | 192.168.56.1 |
| Subnet Mask | 255.255.255.0 |
| Network Address | 192.168.56.0 |
| CIDR | /24 |

The identified Host-Only network was:

```text
192.168.56.0/24
```

**Observation**

The `ipconfig` command helped me identify the correct network interface and subnet before carrying out the Zenmap scan.

**Evidence:** `screenshots/07-ipconfig.png`

### 6.2.3 CONFIGURING ZENMAP

After identifying my subnet, I opened Zenmap on my Windows computer.

I configured the scan using the following settings:

**Target**

```text
192.168.56.0/24
```

**Scan Profile**

```text
Ping Scan
```

**Nmap Command**

```bash
nmap -sn 192.168.56.0/24
```

**Explanation of the Command**

- `nmap`: Starts the Nmap network scanning tool.
- `-sn`: Performs host discovery without a port scan.
- `192.168.56.0/24`: Specifies the network range to be scanned.

**Observation**

The scan was configured to identify active devices within my VirtualBox Host-Only network without performing a port scan.

### 6.2.4 LIVE HOST DISCOVERY RESULTS

After executing the Ping Scan, Zenmap successfully identified three live hosts on the network.

**Summary of Scan Results**

| Metric | Observed Result |
|---|---|
| Network Scanned | 192.168.56.0/24 |
| Scan Type | Ping Scan |
| Command | nmap -sn 192.168.56.0/24 |
| Live Hosts Detected | 3 |
| Individual Host IPs | Refer to original Zenmap output |
| MAC Addresses | Refer to original Zenmap output |

**Observation**

The successful discovery of three live hosts demonstrated that Zenmap could identify devices responding to host discovery probes on my local network.

This exercise improved my understanding of network scanning and the importance of identifying active devices before performing more advanced security assessments.

**Evidence:**
- `screenshots/08-zenmap-scan.png`
- `screenshots/08-zenmap-scan-2.png`

### 6.2.5 NETWORK TOPOLOGY VISUALIZATION

After completing the network discovery scan, I explored the Topology tab in Zenmap.

The topology feature provides a graphical representation of discovered hosts and displays network relationships based on the available scan information.

**Purpose of the Topology View**

- Visualize discovered network hosts.
- Understand how devices are represented within a network.
- Examine the available network topology information.
- Improve understanding of network discovery results.

**Observation**

The Zenmap Topology tab provided a visual representation of the network discovery information and helped me understand how discovered hosts can be presented graphically.

**Evidence:** `screenshots/09-network-topology.png`

# 7. SUMMARY OF PRACTICAL RESULTS

The following table summarizes the results obtained from both practical exercises.

| No. | Tool | Major Result |
|---|---|---|
| 1 | WHOIS | Identified GoDaddy as registrar and retrieved domain registration dates |
| 2 | WhatWeb | Identified Apache, WordPress 7.1.4 and IP 192.232.216.135 |
| 3 | Nslookup | Resolved the domain to 192.232.216.135 using 8.8.8.8 |
| 4 | Curl | Retrieved HTTP/2 200 OK response and Apache server information |
| 5 | Wafw00f | Detected ModSecurity (SpiderLabs), version 2.3.2 reported |
| 6 | DNSRecon | Identified eight DNS records |
| 7 | Windows CMD | Identified the Host-Only network as 192.168.56.0/24 |
| 8 | Zenmap | Successfully discovered three live hosts |
| 9 | Zenmap Topology | Examined the graphical network topology view |

# 8. RISK ANALYSIS AND SECURITY OBSERVATIONS

The practical exercises provided information that can help security professionals understand the potential security exposure of a target environment.

The following table presents preliminary observations and potential security implications.

These observations are not confirmed vulnerabilities because no exploitation or vulnerability validation was performed.

| No. | Risk / Observation | Potential Security Impact | Risk Level |
|---|---|---|---|
| 1 | Website technology fingerprinting | Publicly detectable technologies may help attackers identify components requiring further security review | Medium |
| 2 | Public DNS information | DNS information may provide insight into the target's infrastructure | Low |
| 3 | HTTP header information exposure | Server information may assist technology fingerprinting | Low |
| 4 | WAF identification | Information about defensive technologies may assist an attacker in understanding the security environment | Low |
| 5 | Multiple active network devices | Unexpected or unauthorized devices may introduce security risks | Medium |
| 6 | Network configuration visibility | Improper network isolation or access controls may expose devices to unintended communication | Low |

**Risk Level Classification**

- **Critical:** Immediate and severe security concern.
- **High:** Significant security concern requiring urgent attention.
- **Medium:** Requires investigation and appropriate security controls.
- **Low:** Limited potential impact but worth reviewing.

The risk levels above are preliminary assessments of potential exposure, not validated vulnerability ratings.

# 9. SECURITY RECOMMENDATIONS

Based on the activities performed, I recommend the following security practices:

**1. Regular Technology Reviews**

Organizations should periodically review publicly exposed website technologies and ensure that unnecessary technical information is not disclosed.

**2. Software Updates**

CMS platforms, plugins, web servers and other application components should be updated regularly to address known security weaknesses.

**3. Secure HTTP Headers**

Organizations should review their HTTP response headers and implement appropriate security headers to improve web application security.

**4. DNS Security**

DNS records should be reviewed periodically to ensure that unnecessary information is not exposed publicly.

**5. WAF Configuration**

Web Application Firewalls should be properly configured, maintained and monitored to help protect web applications against malicious traffic.

**6. Network Monitoring**

Organizations should perform authorized network discovery exercises to identify devices connected to their networks.

**7. Unknown Device Investigation**

Any unexpected device identified during network scanning should be investigated to determine whether it is authorized.

**8. Network Documentation**

Organizations should maintain accurate records of their network devices, IP addresses, subnet configurations and network topology.

**9. Access Control**

Network access should be restricted to authorized users and devices through appropriate access control policies.

**10. Authorized Security Testing**

All reconnaissance, scanning and penetration testing activities should be conducted within an approved testing scope.

# 10. CHALLENGES AND LESSONS LEARNED

During the practical exercises, I gained experience working with different cybersecurity tools and troubleshooting network configurations.

Some important lessons from the activities include:

1. Understanding network interfaces is important before performing network scans.
2. NAT and Host-Only networking serve different purposes in VirtualBox.
3. Identifying the correct subnet helps prevent scanning the wrong network.
4. Different reconnaissance tools provide different types of information about a target.
5. A successful HTTP response does not automatically mean a website is completely secure.
6. Identifying a WAF does not establish that all security protections are properly configured.
7. Zenmap provides a convenient graphical interface for understanding Nmap scan results.
8. Proper evidence collection is important when documenting cybersecurity exercises.
9. Network scanning results should be interpreted carefully and only within the authorized testing scope.

The exercises also improved my confidence in using Kali Linux, Windows networking commands and Zenmap.

# 11. CONCLUSION

During Week 2 of my Cybersecurity and Ethical Hacking Internship with NETWORKWALKS, Batch B084, I completed practical exercises covering Footprinting, Reconnaissance and Network Scanning.

For the reconnaissance exercise, I worked with six important Kali Linux tools: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f and DNSRecon.

These tools helped me gather publicly available information about the target domain, including registration details, website technologies, DNS information, HTTP response headers and WAF detection results.

For the network scanning exercise, I used Windows Command Prompt to identify my local network configuration and Zenmap to perform a Ping Scan on my VirtualBox Host-Only network.

I successfully identified my network as `192.168.56.0/24` and discovered three live hosts using the Nmap command:

```bash
nmap -sn 192.168.56.0/24
```

I also gained practical experience working with VirtualBox network interfaces, understanding NAT and Host-Only networking, and exploring network topology visualization.

One major lesson from this practical is that effective penetration testing begins with understanding the target environment. Reconnaissance and scanning provide important information that helps security professionals make informed decisions before proceeding to advanced security assessments.

Overall, this practical strengthened my foundational cybersecurity knowledge, improved my technical troubleshooting skills and increased my confidence in using industry-relevant tools for authorized security assessments.

# 12. EVIDENCE COLLECTED

The screenshots collected during the practical exercises are organized in the `screenshots/` directory.

| No. | Screenshot | Description |
|---|---|---|
| 1 | `01-whois.png` | WHOIS domain registration information |
| 2 | `02-whatweb.png` | WhatWeb website technology fingerprinting |
| 3 | `03-nslookup.png` | Nslookup DNS resolution results |
| 4 | `04-curl.png` | Curl HTTP response headers |
| 5 | `05-wafw00f.png` | Wafw00f detection results |
| 6 | `06-dnsrecon.png` | DNSRecon DNS enumeration results |
| 7 | `07-ipconfig.png` | Windows IP configuration |
| 8 | `08-zenmap-scan.png` | Zenmap Ping Scan results |
| 9 | `09-network-topology.png` | Zenmap network topology visualization |

# 13. GITHUB PROJECT STRUCTURE

The recommended repository structure for this project is:

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

# 14. ACKNOWLEDGEMENT

I sincerely appreciate NETWORKWALKS for providing the opportunity to develop my practical knowledge and skills in Cybersecurity and Ethical Hacking.

The hands-on exercises provided valuable exposure to reconnaissance tools, network scanning techniques and technical documentation.

I look forward to building on these foundational skills as I continue my cybersecurity learning journey.

---

**PROGRAM:** Cybersecurity & Ethical Hacking Internship

**ORGANIZATION:** NETWORKWALKS

**BATCH:** B084

**REPORT CODE:** W2-PM-FINAL

**AUTHOR:** Adigun Olamide Precious

**REPORT DATE:** 11 November 2026

**END OF REPORT**
