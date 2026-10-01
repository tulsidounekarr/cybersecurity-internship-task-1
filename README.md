# Cyber Security Internship – Task 1

## Scan Local Network for Open Ports

## 1. Objective

The objective of this task was to perform basic network reconnaissance by scanning an authorized local network for active devices and open TCP ports using Nmap.

The purpose was to understand network exposure, identify open ports and associated services, and evaluate potential security considerations.

---

## 2. Tools Used

- Nmap 7.991
- Windows Command Prompt
- Windows Defender Firewall

---

## 3. Network Information

- Network Range: `192.168.31.0/24`
- Number of IP addresses scanned: 256
- Scan Type: TCP SYN Scan
- Nmap Command:

nmap -sS 192.168.31.0/24

## 4. Nmap Scan Results

The scan identified 5 active hosts.

| IP Address     | Host   | Open TCP Ports                     |
| -------------- | ------ | ---------------------------------- |
| 192.168.31.1   | Router | 53, 80, 443, 7443, 8080, 8443      |
| 192.168.31.18  | Host-2 | 2869, 8008, 8009, 8443             |
| 192.168.31.122 | Host-3 | None detected                      |
| 192.168.31.238 | Host-4 | 7000, 8008, 8009, 8010, 8443, 9000 |
| 192.168.31.243 | Host-5 | 135, 139, 445, 554, 2869, 10243    |

The original Nmap scan output is retained locally as nmap_scan.txt. A sanitized version, nmap_scan_public.txt, is included in the public repository.


## 5. Service Identification
192.168.31.1

| Port | Nmap Service   |
| ---- | -------------- |
| 53   | domain         |
| 80   | http           |
| 443  | https          |
| 7443 | oracleas-https |
| 8080 | http-proxy     |
| 8443 | https-alt      |

192.168.31.18

| Port | Nmap Service |
| ---- | ------------ |
| 2869 | icslap       |
| 8008 | http         |
| 8009 | ajp13        |
| 8443 | https-alt    |

192.168.31.122

No open TCP ports were detected among the 1,000 ports scanned.
192.168.31.238

| Port | Nmap Service    |
| ---- | --------------- |
| 7000 | afs3-fileserver |
| 8008 | http            |
| 8009 | ajp13           |
| 8010 | xmpp            |
| 8443 | https-alt       |
| 9000 | cslistener      |

192.168.31.243

| Port  | Nmap Service |
| ----- | ------------ |
| 135   | msrpc        |
| 139   | netbios-ssn  |
| 445   | microsoft-ds |
| 554   | rtsp         |
| 2869  | icslap       |
| 10243 | unknown      |


## 6. Security Risk Analysis

An open port means that a TCP service is accepting connections. An open port does not automatically mean that the service is vulnerable.

Potential security considerations identified during the assessment include:

Unnecessary Services-
Services that are not required should be disabled where possible because every exposed service can increase the network attack surface.

Web Services-
HTTP and HTTPS-related ports such as 80, 443, 8080 and 8443 should be reviewed to ensure that only required interfaces are exposed and that administrative interfaces use appropriate authentication and encryption.

Windows Networking Services-
Ports 135, 139 and 445 on the Windows host are associated with Windows networking and file-sharing functionality.

These services should be protected using appropriate Windows Firewall rules and should only be accessible where required.

Service Updates-
Network-facing services should be kept updated to reduce exposure to known security vulnerabilities.

Network Access Control-
Services should preferably be restricted to trusted devices or networks when broad access is not required.

## 7. Firewall Observation

Windows Defender Firewall was checked on the test computer.

The firewall was enabled for the checked profiles.

Observed configuration included:

- Firewall State: ON
- Inbound Policy: BlockInbound
- Outbound Policy: AllowOutbound
- Remote Management: Disabled
- Inbound User Notification: Enabled

The firewall provides a layer of protection by controlling network traffic according to configured firewall rules.

## 8. Security Findings

The scan demonstrated that multiple devices on the local network expose TCP services.

The main observations were:

1. Five active hosts were identified.
2. Multiple TCP services were exposed on four of the five hosts.
3. One discovered device had no open TCP ports among the 1,000 ports scanned.
4. Windows networking ports 135, 139 and 445 were open on the Windows host.
5. The local firewall was enabled and configured to block inbound traffic by default.
6. Open ports should be reviewed periodically and unnecessary services should be disabled or restricted.


## 9. Limitations

This assessment was limited to the local network and the TCP ports scanned by Nmap.

The scan does not by itself:

- Confirm that a service is vulnerable.
- Identify every application running on a port.
- Test authentication security.
- Test application-level vulnerabilities.
- Determine whether a service is accessible from the public Internet.

Further authorized testing would be required to make those determinations.

## 10. Conclusion

This task provided practical experience with network reconnaissance and TCP port scanning using Nmap.

The assessment identified active devices, open TCP ports, and the service associations reported by Nmap. The results demonstrate how network service exposure can be identified and evaluated from a cybersecurity perspective.

The Nmap results were saved for documentation, and a sanitized version was prepared for public repository sharing.

## 11. Repository Contents

cybersecurity-internship-task-1/
│
├── README.md
├── nmap_scan_public.txt
│
└── screenshots/
    ├── nmap_scan_result.png
    ├── nmap_version.png
    └── firewall_status.png

The original nmap_scan.txt containing raw device information is retained locally and is not included in the public repository.

## 12. Key Concepts
- Port Scanning
- TCP SYN Scanning
- Network Reconnaissance
- IP Address Ranges
- Open and Closed Ports
- Network Services
- Attack Surface
- Firewall
- Network Security