# Task 2: Network Scanning & Vulnerability Assessment

## 🎯 Objective
Perform network reconnaissance, identify running services, check for potential vulnerabilities, and analyze network traffic using Kali Linux security tools in a controlled virtual lab environment.

## 💻 1. Lab Environment Setup
* **Attacker Machine:** Kali Linux running on VMware.
* **Target Machine:** Metasploitable 2.
* **Target IP Address:** `192.168.91.129`
* **Scanning Tool:** Nmap 7.99.1.
* **Packet Analysis Tool:** Wireshark.
* **Network Configuration:** VMware virtual lab network.

The lab was used to practice basic security assessment techniques against an intentionally vulnerable target.

## 🌐 2. Network Connectivity Testing

Verified connectivity between Kali Linux and Metasploitable 2 using the `ping` command.

```bash
ping -c 4 192.168.91.129
```

**Purpose:**
* Check whether the target machine is reachable.
* Observe ICMP echo requests and replies.
* Check for packet loss.

**Observation:** The target responded to the connectivity test.

<img width="1034" height="297" alt="Screenshot 2026-10-29 120817" src="https://github.com/user-attachments/assets/2f71dae3-99b6-4555-8530-b71f5b14619f" />

## 🔎 3. Nmap Vulnerability Scanning

Nmap was used to identify services and check for potential vulnerabilities on selected ports.

```bash
nmap -sV --script vuln -p 21,22,80 192.168.91.129 -oN task2_vuln_scan.txt
```

### Command Explanation
* `-sV`: Detect service versions.
* `--script vuln`: Run Nmap scripts that check for known vulnerability indicators.
* `-p 21,22,80`: Scan FTP, SSH, and HTTP ports.
* `-oN task2_vuln_scan.txt`: Save results in a readable text file.

### Observations
* The target host was reported as up.
* Port `21/tcp` was open.
* The FTP service was identified as `vsftpd 2.3.4`.
* The output listed vulnerability-related references associated with the detected service.

<img width="1261" height="791" alt="Screenshot 2026-10-29 121125" src="https://github.com/user-attachments/assets/e3eaa2ef-5f7a-4588-89c1-e2d8f77ad24a" />

## 📄 4. Saving and Reviewing Scan Results

The scan results were saved to a text file for documentation and later review.

```bash
cat task2_vuln_scan.txt
```

**Purpose:**
* Review the scan output.
* Keep a record of detected services and vulnerability references.
* Use the results as evidence in the assessment report.

<img width="1286" height="761" alt="Screenshot 2026-10-29 121159" src="https://github.com/user-attachments/assets/4b92273b-460f-4b07-a01c-71985858bb5e" />

## 🦈 5. Wireshark Packet Capture and Analysis

Wireshark was used to capture and inspect network traffic between Kali Linux and the target machine.

### Procedure
1. Open Wireshark in Kali Linux.
2. Select the network interface connected to the lab network.
3. Start packet capture.
4. Generate traffic using the `ping` command.
5. Apply the display filter:

```text
icmp
```

### Observation
The `icmp` filter isolates Internet Control Message Protocol packets, making it easier to inspect ping requests and replies.

**Purpose:**
* Learn basic packet capture.
* Identify ICMP traffic.
* Understand how network troubleshooting and traffic analysis work.

<img width="1165" height="756" alt="Screenshot 2026-10-29 120548" src="https://github.com/user-attachments/assets/2856ae54-0edd-4634-8a64-6919dd3aff11" />

## 🌍 6. HTTP Service Check

The target's web service was checked using Firefox.

```bash
firefox http://192.168.91.129/
```

**Purpose:**
* Check whether the target's HTTP service is accessible.
* Observe the web page served by the target machine.

<img width="1282" height="795" alt="Screenshot 2026-10-29 120510" src="https://github.com/user-attachments/assets/d555305e-2470-4580-9575-666cde24aacb" />

## 📊 7. Results and Findings

| Test | Result |
|---|---|
| Network connectivity | Target responded to ping |
| Nmap scan | Target reported as up |
| FTP service | Port 21 open |
| FTP version | `vsftpd 2.3.4` |
| Vulnerability checks | Vulnerability-related references were reported |
| Scan report | Saved as `task2_vuln_scan.txt` |
| Wireshark | Used to inspect ICMP traffic |
| HTTP check | Performed using Firefox, if the page loaded successfully |

## ✅ 8. Conclusion

This task provided practical experience with network connectivity testing, Nmap scanning, basic vulnerability assessment, and Wireshark packet analysis. The scan identified an FTP service running on the target and displayed vulnerability-related references for further investigation. The exercise demonstrated how security tools can help identify potential weaknesses and inspect network traffic in an authorized lab environment.

## ⚠️ 9. Ethical Considerations

All scanning and analysis should be performed only on systems owned by the tester or where explicit permission has been granted. Metasploitable 2 is an intentionally vulnerable training machine and should remain isolated from public networks.
