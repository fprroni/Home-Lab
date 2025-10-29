#[+] Network Configuration & Map[/+][-] Network Configuration & Map[/-]
## IP Address Scheme
| Component | Role | IP Address | Notes |
| :--- | :--- | :--- | :--- |
| **pfSense (Dell PC)** | Gateway / Firewall | **192.168.1.1** | Controls all internal traffic. |
| **Acer Hyper-V Host** | Virtualization Host | **192.168.1.10** | Static IP. |
| **HP Celeron PC** | Light Services / Pi-hole Host | **192.168.1.11** | Static IP for reliable service hosting. |
| **DHCP Range** | Clients & Management | 192.168.1.50 - 192.168.1.150 | For MacBook, VM-Client, and other devices. |
## Physical Connectivity
1. **Internet $\rightarrow$** Dell PC (pfSense WAN NIC)
2. Dell PC (pfSense LAN NIC) **$\rightarrow$** Main Switch
3. Main Switch **$\rightarrow$** All other physical hosts (Acer, HP Celeron PC, MacBook Air)
