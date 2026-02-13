# BNRM Enterprise Console – Production-Grade Network Security & Risk Management

## 🎯 Overview

**BNRM Enterprise Console** is a desktop-grade, enterprise-level network security and risk management system that transforms monitoring dashboards into a **real-time autonomous decision engine**. It integrates:

- **AI-Driven Predictive Analytics** – Zero-day detection, behavioral fingerprinting, threat intelligence correlation
- **Automatic Network Discovery** – Real-time detection, identification, and profiling of all connected devices
- **Context-Aware Risk Computation** – Dynamic risk scoring with contextual analysis
- **Executive Containment Controls** – Isolation, bandwidth reduction, access blocking, and force re-authentication
- **System Map & Blast Radius** – Visual topology with impact simulation before action
- **AI Security Copilot** – Intelligent alert triage, explainable recommendations, secure action execution

**Designed for**: Up to **120 users / 120 devices**, **Windows & Kali Linux**, local encrypted SQLCipher database, background services architecture.

---

## ✨ Core Features

### 1. **Automatic Network Device Discovery**
- **Passive Discovery**: ARP, DHCP, DNS, TCP handshake monitoring via Scapy/PyShark
- **Active Discovery**: Controlled subnet scanning (e.g., 192.168.x.0/24) with ARP sweep
- **Device Classification**: Internal Managed, Unknown Internal, External, Suspicious, Infrastructure, Sensitive System
- **Real-Time Updates**: Live network topology refresh every X seconds
- **Unmanaged Devices Registry**: Auto-discovered devices appear under "Unmanaged Devices" with provisional risk scoring
- **Admin Controls**: Approve & register, monitor-only, block, or ignore discovered devices

### 2. **Risk Engine**
- Dynamic contextual risk calculation (0–100 score)
- Integration with auto-discovered devices
- Blast Radius simulation before containment
- Context states: working hours logic, behavioral analysis, threat level correlation

### 3. **AI Predictive Layer**
- **Behavioral Fingerprinting**: Random Forest + XGBoost
- **Zero-Day Detection**: Graph Neural Networks (PyTorch)
- **Alert Triage**: NLP + clustering for smart alert prioritization
- **Explainable AI**: All predictions include confidence scores and reasoning
- **AI Security Copilot**: Command execution via secure action pipeline

### 4. **System Map (Live Auto-Discovery Integrated)**
- Displays all manually registered + auto-discovered devices
- Traffic animation with real-time node addition/removal
- Click-to-blast-radius simulation
- Node type visualization (router, server, endpoint, suspicious)
- Dynamically updated by Network Monitor Service

### 5. **Threat Intelligence Engine**
- CVE correlation with local device vulnerability mapping
- AI contextual transformation of threat feeds
- Automated vulnerability profiling

### 6. **Blast Radius Impact Visualization**
- Visual impact assessment before containment actions
- Integration with sensitive systems and departments
- Automatic recalculation with network topology changes

### 7. **Alert & Logging System**
- 4-tier severity: Low / Medium / High / Critical
- Each alert includes: Why Now, Risk Trend, AI Confidence, Suggested Action
- Dynamic action buttons with secure execution
- Read-only encrypted audit logs, AI decision tracking
- Exportable logs for compliance

### 8. **Device Management & Control**
- Add/register devices with identity, sensitivity level, behavioral baseline
- Device profiles: Risk Score, Trust Level, Context States, Behavioral Timeline
- Action panel: Reduce Bandwidth, Block External Access, Lock Access, Force Re-auth, Monitor Only, Honey-Net Diversion, Full Isolation
- Full manual override logging
- Device behavior tracking and anomaly detection

### 9. **Employee Risk Tracking**
- Trust score calculation per employee
- Device assignment tracking
- Department-level risk aggregation

### 10. **Executive Settings**
- Working hours logic for risk contextualization
- Silent Mode for executives
- Single Authority enforcement
- Backup and restore tools

---

## 📋 System Requirements

### Windows
- **OS**: Windows 10 / Windows 11 / Windows Server 2019+
- **RAM**: 4 GB minimum (8 GB recommended)
- **Disk**: 2 GB free space
- **Network**: Active Ethernet or Wi-Fi connection
- **Python**: 3.9+ (bundled in installer)

### Kali Linux
- **OS**: Kali Linux 2023.1+ or Debian-based distributions
- **RAM**: 4 GB minimum (8 GB recommended)
- **Disk**: 2 GB free space
- **Network**: Active network interface
- **Python**: 3.9+ (system package)
- **Privileges**: sudo access for network sniffing

### Prerequisites (All Platforms)
- Administrator / sudo privileges for network operations
- Libpcap development libraries (Linux only)
- OpenSSL for encryption

---

## 🚀 Installation

### Windows Installation

#### Step 1: Download Installer
1. Obtain `BNRM-Setup.exe` from the official release repository
2. Verify file signature (if provided)

#### Step 2: Run Installer
```batch
# Double-click BNRM-Setup.exe
# OR run from command line as Administrator:
BNRM-Setup.exe
```

#### Step 3: Follow Setup Wizard
1. **Splash Screen** – Displays for 2-3 seconds (press Space to skip)
2. **First Run Admin Setup**:
   - Enter **Admin Username**
   - Create **Master Password** (Argon2/bcrypt hashed)
   - Optional: Generate Recovery Key
   - Confirm installation directory (default: `C:\Program Files\BNRM\`)

#### Step 4: Complete Installation
- Background services automatically installed and started
- Desktop shortcut created
- BNRM Console launches on completion

#### Step 5: First Login
- Use Admin credentials set during setup
- System initializes encrypted SQLCipher database
- Network Monitor Service begins passive discovery

---

### Kali Linux Installation

#### Step 1: Download Installer
```bash
wget https://releases.bnrm-console.io/BNRM-Setup.sh
chmod +x BNRM-Setup.sh
```

#### Step 2: Install System Dependencies
```bash
sudo apt-get update
sudo apt-get install -y python3.9 python3-pip libpcap-dev libssl-dev
```

#### Step 3: Run Installer
```bash
sudo ./BNRM-Setup.sh
```

#### Step 4: Follow Setup Wizard
1. **Splash Screen** – Displays for 2-3 seconds
2. **First Run Admin Setup**:
   - Enter **Admin Username**
   - Create **Master Password**
   - Optional: Generate Recovery Key
   - Confirm installation directory (default: `/opt/bnrm/`)

#### Step 5: Verify Installation
```bash
# Check if service is running
sudo systemctl status bnrm-monitor

# Check if console can launch
python3 /opt/bnrm/bin/console.py
```

#### Step 6: Automatic Service Start
```bash
# Enable auto-start on boot
sudo systemctl enable bnrm-monitor
sudo systemctl enable bnrm-alerts
sudo systemctl enable bnrm-analysis
```

---

## 🎮 Usage Guide

### Launching the Application

#### Windows
```batch
# Double-click desktop shortcut, OR:
"C:\Program Files\BNRM\bin\console.exe"
```

#### Linux
```bash
# Launch console (requires X11 or Wayland)
python3 /opt/bnrm/bin/console.py

# Or use systemd:
sudo systemctl start bnrm-console
```

### First Run Setup Steps

1. **Login Screen**
   - Enter Admin Username
   - Enter Master Password
   - Click "Login"

2. **Network Discovery Activation**
   - System automatically begins passive network monitoring
   - Initial ARP sweep of local subnet
   - Device classification begins

3. **Dashboard Initialization**
   - Global Threat Level indicator (top-left)
   - Devices Summary card
   - Departments at Risk panel
   - Latest Alerts feed (right panel)
   - System Map tab loads with discovered devices

---

## 📍 Main Navigation

### Left Sidebar Menu

#### **Dashboard**
- Global threat level visualization
- Device count and status
- Risk distribution by department
- Critical alerts summary
- AI Copilot quick-action panel

#### **Devices**
- View all registered devices
- Add new device manually
- Search/filter by name, IP, MAC, risk level
- Device detail view: Risk Score, Trust Level, Behavioral Timeline
- Action panel: Isolate, Block, Monitor, etc.
- Unmanaged Devices section (auto-discovered)

#### **Employees**
- Employee risk profiles
- Assigned device tracking
- Trust score visualization
- Department aggregation

#### **System Map** ⭐
- Interactive network topology
- Node types: Managed, Unmanaged, Router, Server, Endpoint, Suspicious
- Real-time device addition/removal
- Click node → Blast Radius simulation
- Traffic animation between nodes
- Legend and zoom controls

#### **Blast Radius**
- Impact zone visualization
- Affected devices list
- Suggested containment actions
- Rollback simulation

#### **Alerts**
- 4-tier severity filtering
- Alert details: Timestamp, Why Now, Risk Trend, AI Confidence
- Suggested actions with one-click execution
- Alert history and resolution tracking

#### **AI Chat / Security Copilot**
- Natural language security queries
- Threat intelligence summaries
- Predictive recommendations
- Secure action execution (with approval)
- Explainable reasoning for all suggestions

#### **Logs & Audit**
- Read-only encrypted logs
- Filter by timestamp, severity, action, user
- Export to CSV/JSON for compliance
- AI decision audit trail

#### **Settings**
- Admin account management
- Master password change
- Recovery key management
- Working hours configuration
- Silent Mode toggle
- Silent Backup scheduling
- Database backup/restore
- Service health monitoring

---

## 🔧 Available Commands

### Windows Command Line (if applicable)

```batch
# Check service status
BNRM-CLI.exe status

# Manual network scan
BNRM-CLI.exe scan --subnet 192.168.1.0/24

# Export logs
BNRM-CLI.exe export-logs --output C:\logs.csv
```

### Linux Command Line

```bash
# Check service status
sudo systemctl status bnrm-monitor
sudo systemctl status bnrm-analysis
sudo systemctl status bnrm-alerts

# Manual network scan
sudo /opt/bnrm/bin/bnrm-cli scan --subnet 192.168.1.0/24

# Export logs
sudo /opt/bnrm/bin/bnrm-cli export-logs --output /var/log/bnrm.csv

# Restart all services
sudo systemctl restart bnrm-*

# View service logs
sudo journalctl -u bnrm-monitor -f
```

---

## 🛡️ Security & Data Protection

### Encryption
- **Database**: SQLCipher with 256-bit AES encryption
- **Passwords**: Argon2 hashing (Admin credentials only)
- **Communications**: TLS 1.3 for inter-service communication
- **Backups**: Encrypted by default

### Access Control
- Single Authority enforced (one admin account per installation)
- Master password required for sensitive operations
- All actions logged with timestamp, user, and outcome
- Manual override fully logged for audit compliance

### Network Operations
- Passive discovery non-intrusive (packet sniffing only)
- Active discovery limited to local subnet
- No external communication without explicit admin approval
- All network operations logged

---

## 📊 Architecture Overview

```
┌─────────────────────────────────────────────────────┐
│           BNRM Enterprise Console GUI (PyQt5)        │
│  Dark Theme | System Map | Alerts | AI Copilot     │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────┴──────────────────────────────┐
│           Core Services (Background)                 │
│                                                      │
│  ├─ Network Monitor Service (Scapy/PyShark)         │
│  ├─ Behavioral Analysis Service (XGBoost)           │
│  ├─ Alert Service (NLP + Clustering)                │
│  └─ Update Service (CVE feeds, intelligence)        │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────┴──────────────────────────────┐
│         AI & Risk Engine Layer (PyTorch)            │
│                                                      │
│  ├─ Risk Computation Engine                         │
│  ├─ Behavioral Fingerprinting (Random Forest)       │
│  ├─ Zero-Day Detection (GNN)                        │
│  └─ Predictive Analytics                            │
└──────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────┴──────────────────────────────┐
│      Encrypted Database Layer (SQLCipher)           │
│                                                      │
│  ├─ Device Registry (manual + auto-discovered)      │
│  ├─ Device Profiles & Baselines                     │
│  ├─ Alert History & Audit Logs                      │
│  └─ Risk Scores & Behavioral Data                   │
└─────────────────────────────────────────────────────┘
```

---

## 🔄 Typical Workflow

### 1. System Initialization
- Admin runs BNRM-Setup.exe/.sh
- First-run setup creates master password
- Network Monitor Service starts automatically

### 2. Network Discovery Phase
- Passive monitoring begins immediately
- ARP sweep identifies local devices
- Devices classified automatically
- Unmanaged devices appear in "Unmanaged Devices" section

### 3. Risk Scoring
- Each device assigned provisional risk score
- Behavioral baseline established
- Integrated with CVE intelligence feeds

### 4. Executive Dashboard
- Global threat level calculated
- Devices summary displayed
- Departments at risk highlighted
- System Map shows live topology

### 5. Alerts & Recommendations
- Anomalies detected in real-time
- AI Copilot provides explainable reasoning
- Admin approves/denies suggested actions
- Actions logged for compliance

### 6. Containment (if needed)
- Admin selects device and action
- Blast Radius simulation shows impact
- One-click isolation/blocking/throttling
- All operations logged

---

## 🐛 Troubleshooting

### Windows Issues

**Console won't start:**
```batch
# Check if services are running
tasklist | findstr bnrm

# Restart services
net stop bnrm-monitor
net start bnrm-monitor

# Check logs
type "C:\Program Files\BNRM\logs\console.log"
```

**Network discovery not working:**
- Verify network adapter is active
- Check Windows Firewall allows Scapy traffic
- Run as Administrator

### Linux Issues

**Services won't start:**
```bash
sudo systemctl start bnrm-monitor
sudo journalctl -u bnrm-monitor -n 50
```

**Permission denied errors:**
- Ensure running with sudo for network operations
- Check libpcap is installed: `dpkg -l | grep libpcap`

**Can't find Python:**
```bash
sudo apt-get install python3.9 python3-pip
```

---

## 📞 Support & Documentation

- **Installation Help**: See Installation section above
- **API Reference**: `/docs/API.md` in installation directory
- **Architecture**: `/docs/ARCHITECTURE.md`
- **Logs Location**:
  - Windows: `C:\Program Files\BRNM\logs\`
  - Linux: `/var/log/bnrm/`

---

## 📄 License & Compliance

BNRM Enterprise Console is provided for authorized enterprise deployments only. All network operations are logged and auditable for compliance requirements (SOC 2, ISO 27001, etc.).

---

## Version
**BNRM Enterprise Console v1.0.0** (Production Ready)
Last Updated: 2026-02-13