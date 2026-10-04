# Black-Box Penetration Testing on Mediroza Hospital 
NetworkWalks | Week 4 

# 📌 Introduction
This project covers 4 milestones to be achieved after purely doing pentesting on a target, Mediroza Hospital (`medirozahospital.com`).
M1. Attack the website and find the 3 confidential PDF lab reports of patients
M2. Crack the encryption on all 3 retrieved files
M3. Find the critical data exposure on the client server
M4. Write your detailed Penetration Testing Report

``Note: This project is conducted in a controlled environment for educational purposes only. The target has been authorised for security testing by Networkwalks. These techniques must never be applied to any system without explicit written permission from the owner.``

---

# 🔨 Tools 
| Tools | Purpose | 
| --- | --- |
| whois | Find registration and ownership information  |
| wafw00f | Detect whether a Web Application Firewall protects the target |
| dnsrecon | Enumerate DNS records (NS, MX, SPF/TXT, SRV) |
| Manual SQL Injection | Bypass authentication in the patient portal login form |
| Networkwalks Hash Calculator | Extract a crackable hash from each password protected PDF |
| Networkwalks Password Cracker | Dictionary attack against each extracted PDF hash |
| exiftool | Display PDF metadata for information such as modification dates |
| qpdf | Decrypt PDFs using recovered passwords before metadata inspection |
| curl | Retrieve directory listings and download the exposed database backup |

---

# 📑Activities Performed
1. Recon — Profiled the target with whois, wafw00f, and dnsrecon. Identified a LiteSpeed-hosted WordPress site behind a LiteSpeed WAF.

2. Enumeration — Found sensitive paths via robots.txt (/patient/, /staff/, /old/) and discovered directory indexing on the patient portal.

3. Initial Access — Bypassed the login form using a manual SQL injection payload (admin'--) — no credentials needed.

4. Data Extraction — Downloaded 3 encrypted PDF lab reports, extracted hashes, and cracked them via dictionary attack.

5. Metadata Analysis — Used exiftool to uncover an internal comment in a PDF that pointed to a database backup.

6. Critical Exposure — Located an unauthenticated SQL database backup at /old/ containing staff payroll records and shareholder data.

7. Reporting — Documented the full engagement with findings, risk ratings, and remediation advice.

---

## 🔑 Key Findings 
| Finding | Risk |
|---|---|
| SQL Injection login bypass | 🔴 Critical |
| Exposed database backup with no access control | 🔴 Critical |
| Confidential information of staff and shareholders | 🔴  Critical |
| Encrypted PDFs accessible after login bypass | 🟠 High |
| Sensitive internal comment left in client-facing PDF metadata | 🟠 High |
| `robots.txt` discloses sensitive paths | 🟡 Medium |
| Weak, dictionary-crackable PDF passwords | 🟡 Medium |

Notes: All the screenshot evidence, recommendations, and remediation are in the report file (WK4_Mediroza_Pentest_Report.docx). 
---

## ✒️ Author
Vivi Hanna Handison | Batch 083 | LinkedIn : (https://www.linkedin.com/in/vivihanna/) |
