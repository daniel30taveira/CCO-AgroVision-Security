# CCO Integrated Project - AgroVision Cybersecurity Lab

**Deadline:** 11 Jan 2026 | **Status:** 🚀 In Progress  
**Institution:** IPB ESTIG | **Course:** Mestrado Integrado Cibersegurança  

---

## 🖥️ Infrastructure Overview

### VMs Configuration (Bridged Network 192.168.1.0/24)

| VM | IP Address | Role | Status |
|---|---|---|---|
| **WS-01** | 192.168.1.10 | Workstation 1 | ✅ |
| **WS-02** | 192.168.1.11 | Workstation 2 | ✅ |
| **FW-GW** | 192.168.1.1 | Firewall/Gateway | ✅ |
| **SRV-SAAS** | 192.168.1.20 | SaaS Application Server | ✅ |
| **SRV-DATA** | 192.168.1.21 | Database Server | ✅ |
| **SIEM-WAZ** | 192.168.1.60 | Wazuh Manager SIEM | ✅ |

### Network Details
- **Subnet Mask:** 255.255.255.0 (/24)
- **Gateway:** 192.168.1.254 (ISP Router)
- **DNS:** 8.8.8.8, 8.8.4.4
- **Network Type:** VMware Bridged (WiFi)
- **OS:** Ubuntu Server 22.04 LTS

---

## 📊 Project Progress

### ✅ Phase 3.1 - Planning [COMPLETE]
- Company context defined: AgroVision Analytics (SME)
- Infrastructure designed: 6 VMs centralized with SIEM

### ✅ Phase 3.3 - Asset & Vulnerability Management [50%]
**Network Setup:** All 6 VMs static IPs via Netplan
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: no
      addresses:
        - 192.168.1.X/24
      routes:
        - to: default
          via: 192.168.1.254
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
