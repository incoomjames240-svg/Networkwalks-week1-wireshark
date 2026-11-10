# Week 1 — Wireshark SOC Investigation Report

**Internship:** NetworkWalks Cybersecurity Internship  
**Project:** Lab 3 — Identify the Attacker's IP  
**Tool:** Wireshark  
**Lab completion:** 6 November 2026  
**Score:** 100/100

## 1. Objective

Investigate suspicious network traffic directed toward a company's web server, identify the suspected attacker, and analyze the network packets using Wireshark.

## 2. Investigation Findings

| Item | Finding |
|---|---|
| Suspected attacker IP | 192.168.10.66 |
| Target server IP | 192.168.10.20 |
| Attacker-side TCP port observed | 52311 |
| Protocol | TCP |
| Observed target ports | 21, 25, 139, 445, 3306, 3389, 5900, 8080 |
| Response flags | RST, ACK |
| Lab result | 100% |

## 3. Wireshark Analysis

The following filter was used to examine TCP reset responses from the target server:

`ip.src == 192.168.10.20 && ip.dst == 192.168.10.66 && tcp.flags.reset == 1`

The displayed packets showed the target server responding with TCP RST-ACK packets associated with multiple service ports.

A separate capture view used the filter:

`tcp.flags.syn == 1`

This showed TCP SYN and SYN-ACK traffic involving the target IP address 192.168.10.20 and several other hosts.

## 4. Security Interpretation

The lab identified 192.168.10.66 as the suspected attacker IP address.

The multiple service ports and TCP reset responses are consistent with a port-probing investigation. However, the reset-response screenshot alone does not prove malicious intent. Examining the original connection requests would provide stronger independent confirmation.

## 5. Conclusion

I completed the NetworkWalks Wireshark SOC Lab 3 investigation and achieved 100/100 marks.

This exercise helped me practise packet filtering, TCP flag interpretation, source and destination IP identification, and basic SOC traffic investigation.

## 6. Evidence

The GitHub repository contains three screenshots documenting TCP SYN analysis, the attacker IP investigation, and the official lab completion result.
