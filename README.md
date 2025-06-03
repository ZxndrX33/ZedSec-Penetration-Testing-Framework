# ZedSec-Penetration-Testing-Framework
 A professional-grade, tactical penetration testing framework engineered by **ZedSec**. This framework aligns with industry standards (PTES, MITRE ATT&amp;CK) and ZedSec's hardcore offensive methodology.

---

## 🔥 Features

- ⚙️ Automated setup scripts for **Kali** & **Arch (BlackArch)**
    
- 🧠 PTES-aligned attack lifecycle methodology
    
- 📒 Modular playbooks with real-world command sets
    
- ⚔️ Advanced scripts and implant modules
    
- 📘 Instruction Manual for framework deployment and use
    
- 🧾 Tactical reporting & evidence templates
    
- 🗂 Clean, scalable directory structure for long-term ops
    

---

## 🛠 Methodology (PTES-Enhanced)

1. Pre-Engagement Interactions
    
2. Intelligence Gathering
    
3. Threat Modeling
    
4. Vulnerability Analysis
    
5. Exploitation
    
6. Post-Exploitation
    
7. Reporting
    

---

## 🧰 Toolsets by Phase

|Phase|Tools|
|---|---|
|Recon|whois, amass, subfinder, theHarvester, dnsx, shodan, whatweb, wafw00f|
|Enumeration|nmap, masscan, gobuster, feroxbuster, enum4linux, smbclient, snmpwalk|
|Exploitation|metasploit, sqlmap, crackmapexec, evil-winrm, hydra, medusa, ncrack|
|Privilege Escalation|linPEAS, winPEAS, GTFOBins, BeRoot, pspy, LES, WES|
|Post-Exploitation|mimikatz, BloodHound, LaZagne, impacket, rubeus, sharpHound|

---

## 🔄 Setup Scripts

### setup/kali-install.sh

```bash
#!/bin/bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y nmap masscan gobuster feroxbuster whatweb wafw00f amass subfinder theharvester dnsrecon wfuzz seclists \
python3-pip bloodhound neo4j git metasploit-framework sqlmap crackmapexec evil-winrm enum4linux \
linpeas winpeas unzip john hashcat impacket-scripts wordlists
pip3 install -r requirements.txt
git clone https://github.com/swisskyrepo/PayloadsAllTheThings.git tools/PayloadsAllTheThings
git clone https://github.com/danielmiessler/SecLists.git wordlists/SecLists
```

### setup/arch-install.sh

```bash
#!/bin/bash
sudo pacman -Syu --noconfirm
sudo pacman -S --noconfirm nmap masscan gobuster feroxbuster whatweb wafw00f amass theharvester dnsrecon wfuzz seclists \
python-pip bloodhound neo4j git metasploit sqlmap crackmapexec evil-winrm enum4linux unzip john hashcat
pip install -r requirements.txt
git clone https://github.com/swisskyrepo/PayloadsAllTheThings.git tools/PayloadsAllTheThings
git clone https://github.com/danielmiessler/SecLists.git wordlists/SecLists
```

---

## 📂 Directory Structure

```
ZedSec_Pentest_Framework/
├── setup/
│   ├── kali-install.sh
│   └── arch-install.sh
├── tools/
│   └── PayloadsAllTheThings/
├── wordlists/
│   └── SecLists/
├── scripts/
│   ├── quickscan.sh
│   ├── extract-metadata.py
│   └── http-status-checker.py
├── playbooks/
│   ├── recon.md
│   ├── web_enum.md
│   ├── linux_priv_esc.md
│   └── lateral_movement.md
├── templates/
│   ├── report-template.md
│   └── evidence-template.md
├── manual/
│   └── framework-guide.md
├── scans/
├── reports/
└── README.md
```

---

## 📜 Playbooks (playbooks/)

### recon.md

```markdown
# Reconnaissance Playbook

## Passive Recon
- whois target.com
- theHarvester -d target.com -l 100 -b all
- subfinder -d target.com
- amass enum -passive -d target.com

## Active Recon
- nmap -sC -sV -Pn -T4 -oA scans/target target.com
- whatweb http://target.com
- wafw00f http://target.com
- dnsrecon -d target.com -t std
```

### web_enum.md

```markdown
# Web Enumeration Playbook

## Fuzzing
- gobuster dir -u http://target.com -w /usr/share/seclists/Discovery/Web-Content/common.txt
- feroxbuster -u http://target.com -w /usr/share/seclists/Discovery/Web-Content/common.txt

## Fingerprinting
- whatweb http://target.com
- wafw00f http://target.com

## Vulnerability Scanning
- nikto -h http://target.com
```

### linux_priv_esc.md

```markdown
# Linux Privilege Escalation

## Automated
wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh
chmod +x linpeas.sh
./linpeas.sh

## Manual Checks
- sudo -l
- find / -perm -4000 2>/dev/null
- ps -aux | grep root
- cat /etc/passwd
- cat /etc/shadow
```

### lateral_movement.md

```markdown
# Lateral Movement Playbook

- Credential reuse
- SMB enumeration and psexec
- SSH hopping

## Tools
- crackmapexec smb
- impacket's psexec.py
- BloodHound for AD pathing
```

---

## 🧾 Templates (templates/)

### report-template.md

```markdown
# Penetration Test Report

## Executive Summary

## Methodology
- Recon
- Enumeration
- Exploitation
- Post-Exploitation

## Vulnerability Details
| ID | Severity | Title | Description | Recommendation |
|----|----------|-------|-------------|----------------|
| 1  | High     | Sample Vuln | Description | Fix recommendation |
```

### evidence-template.md

````markdown
# Evidence Log

## Test Name:
- Date:
- Target:
- Command:
```bash
nmap -sC -sV -oA scans/target target.com
````

- Output:
    

```
[Paste output here]
```

```

---

## 📘 Instruction Manual (manual/framework-guide.md)

Includes:
- Deployment walkthroughs
- Lab setup validation
- Tool usage tutorials
- Report writing techniques
- Real-world ops workflow integration

---

## 🧑‍💼 Maintainers

Built & maintained by **ZedSec**.

Pull requests welcome. Keep it ruthless.

## ⚖️ License

MIT. For ethical engagements only. If you're not licensed to test, you're not licensed to touch this.

---

> “Dominate the system. Respect the boundaries.” — ZedSec

```

# 📘 ZedSec Pentest Framework Instruction Manual

> Tactical Guidance for Deployment, Usage & Domination

---

## 🧭 1. Introduction

Welcome to the **ZedSec Elite Penetration Testing Framework**. This guidebook is your operational doctrine—follow it to deploy, dominate, and document every engagement with surgical precision.

### Purpose

- Ensure operators can deploy the framework across supported OS (Kali/Arch)
    
- Provide usage strategies per directory and module
    
- Define procedures for evidence collection and reporting
    
- Enable lab reproducibility and automation
    

---

## ⚙️ 2. Installation & Environment

### Supported Distros

- Kali Linux
    
- Arch Linux (or BlackArch)
    

### Install Scripts

- For Kali: `setup/kali-install.sh`
    
- For Arch: `setup/arch-install.sh`
    

### Validate Environment

```bash
nmap --version
python3 --version
gobuster --help
```

If any fail, re-run the setup script and check your `$PATH`.

---

## 🗂 3. Directory Usage

### `setup/`

Automated install scripts for initial provisioning.

### `tools/`

Stores cloned offensive repositories like PayloadsAllTheThings.

### `wordlists/`

Preloaded with SecLists and customizable space for custom wordlists.

### `scripts/`

Fast execution tools. Use `scripts/quickscan.sh` to immediately assess hosts.

### `playbooks/`

Modular field references. Follow step-by-step recon, enumeration, privesc, and movement tactics.

### `templates/`

Copy templates into `reports/` and edit with findings and command output.

### `scans/`

Save raw output from tools (e.g., `nmap -oA scans/target`).

### `reports/`

Store compiled and finalized reports. Use markdown and then convert to PDF.

---

## 🧪 4. Engagement Lifecycle Workflow

1. **Reconnaissance**
    
    - Start passive: WHOIS, DNS
        
    - Transition to active: `nmap`, `whatweb`, `gobuster`
        
2. **Enumeration**
    
    - Use `enum4linux`, `smbclient`, `ldapsearch`
        
3. **Exploitation**
    
    - Leverage `sqlmap`, `crackmapexec`, `evil-winrm`
        
4. **Post-Exploitation**
    
    - BloodHound, LaZagne, custom tools
        
5. **Privilege Escalation**
    
    - Run PEAS scripts or manual enumeration
        
6. **Reporting**
    
    - Log evidence in `templates/evidence-template.md`
        
    - Summarize in `report-template.md`
        

---

## 🧠 5. Operator Pro Tips

- Keep a daily `ops.log` journal per target inside `reports/`
    
- Hash and sign reports with GPG for integrity
    
- Use `pyarmor` or `nuitka` if delivering payloads to clients
    
- Add custom payload modules to `scripts/` and version control them
    

---

## 🔐 6. Ethics & Legal Notice

This framework is for **legal penetration testing only**. All usage must be authorized in writing by the owner of the systems being tested.

> ZedSec is not responsible for unauthorized deployments or misuse. If you're doing this without consent, you're not a red teamer. You're a criminal.

---

## 💀 Final Words from the Operator

Stay sharp.  
Work clean.  
Log everything.  
Break what you must.  
Protect what you can.

> "Code like a weapon. Think like the enemy. Report like a professional."

— ZedSec
