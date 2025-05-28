# Lab 4 – Attack Analysis and Response

In this lab, I performed a comprehensive analysis of a cybersecurity breach using forensic evidence including Windows Event Viewer logs and packet capture (PCAP) files. The purpose was to determine the attacker’s methods, the extent of the compromise, and provide a narrative supported by event IDs, timestamps, and network traffic patterns.

## 🧪 Objectives
- Analyze system event logs for signs of compromise and privilege escalation.
- Review and interpret Wireshark PCAPs for evidence of data exfiltration or malicious connections.
- Reconstruct the sequence of attack activities and identify tactics, techniques, and procedures (TTPs).

## 🔧 Tools Used
- Windows Event Viewer
- Wireshark
- ICMP/TCP protocol analysis
- Knowledge of WMI, DLL injection, and system event codes

## 🔍 Key Findings
- **Event Viewer Logs**:
  - `WinMgmt` Event ID 63: Indicated abuse of WMI for privilege escalation and command triggers.
  - Event ID 5603: Changes to RSOP policy — signs of attacker persistence setup.
  - `Print` Event ID 20: DLL injection via print service installation.
  - Time sync disabled (`W32Time`), likely to obscure timelines.
  - `Tcpip` Event ID 4226: Concurrent TCP limit hit — possible DoS or massive data transfer.

- **Network Traffic**:
  - Large data transmissions between internal IPs `192.168.134.129` ↔ `192.168.134.132`.
  - Repeated `[RST, ACK]` packets indicating forced connection resets.
  - ICMP unreachable errors suggesting device evasion or shutdown.

## 🧠 Summary
The logs and PCAP data show a coordinated attack involving:
- WMI abuse to trigger malicious payloads.
- Time sync disruption to confuse forensic timelines.
- Exfiltration of data followed by system sabotage (reset packets, disabled drivers).

This was likely a multi-stage breach: infiltration, escalation, exfiltration, and cover-up.

## 📂 Project Files

- 📄 Lab Instructions (PDF) - [ISCS_3523_Lab 4 Attack Analysis (1).pdf](https://github.com/user-attachments/files/20495036/ISCS_3523_Lab.4.Attack.Analysis.1.pdf)
- 📄 My Full Analysis Report (PDF) - [Okuyiga_qvj870_3523_lab04 (1).pdf](https://github.com/user-attachments/files/20495062/Okuyiga_qvj870_3523_lab04.1.pdf)

## 📚 References
- [Windows Event Logging Guide – Sumo Logic](https://www.sumologic.com/blog/windows-event-logging/)
- [Microsoft LocalSystem Account](https://learn.microsoft.com/en-us/windows/win32/services/localsystem-account)
- [TCP Reset Explanation – Pico](https://www.pico.net/kb/what-is-a-tcp-reset-rst/)
- [Group Policy RSOP Explanation](https://activedirectorypro.com/how-to-use-rsop-to-check-and-troubleshoot-group-policy-settings/)
[Okuyiga_qvj870_3523_lab04 (1).pdf](https://github.com/user-attachments/files/20495062/Okuyiga_qvj870_3523_lab04.1.pdf)
