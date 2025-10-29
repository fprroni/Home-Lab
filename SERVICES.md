#[+] Virtual and Physical Services[/+][-] ⚙️ Virtual and Physical Services[/-]
| VM Name | OS | Role / Service | IP Address | vCPU / RAM |
| :--- | :--- | :--- | :--- | :--- |
| **VM-DC01** | Windows Server 2019 | Active Directory Domain Controller | 192.168.1.20 | 2 / 4 GB |
| **VM-Web01** | Ubuntu Server 22.04 | Nginx Web Server / Testing | 192.168.1.30 | 1 / 2 GB |
| **VM-Client** | Windows 10 | Testing Client / Management Access | DHCP (192.168.1.5x) | 2 / 2 GB |
##[+] Dedicated Physical Services (HP Celeron PC)[/+][-] 🖥️ Dedicated Physical Services (HP Celeron PC)[/-]
| Service Name | Host | IP Address | Purpose |
| :--- | :--- | :--- | :--- |
| **Pi-hole DNS** | HP Celeron PC | 192.168.1.11 | Provides network-wide ad-blocking and primary DNS resolution for the LAN. |

