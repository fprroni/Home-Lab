# pfSense Firewall Documentation (Dell PC)

This section details the hardware, installation, and interface mapping for the pfSense appliance, which acts as the main gateway (192.168.1.1) for the Home Lab.

## Hardware: Initial and Upgraded

| Component | Specification | Notes |
| :--- | :--- | :--- |
| **Host PC** | Dell OptiPlex/Vostro (Based on images) | Originally ran Windows 7 Pro. |
| **CPU** | Intel(R) Pentium(R) CPU G630 @ 2.70GHz | Sufficient for basic routing and firewalling. |
| **RAM** | 4.00 GB | Plenty for pfSense. |
| **Storage** | Single 160GB HDD (or similar) | Plenty of space for the OS and logs. |

---

## 🛠️ Hardware Upgrade: Dual NIC Installation

The Dell PC initially only had one onboard Network Interface Card (NIC). A second NIC was required to separate the WAN and LAN traffic for proper firewall functionality.

### 1. New NIC Installation

* **NIC Purchased:** [Vendor/Model, e.g., Intel Pro/1000 PT Dual Port Server Adapter]
* **Installation Date:** [Date you installed it]
* **Action:** The PCIe card was installed into the available slot. The Dell PC booted without issue and immediately detected the new card.

!(images/dell-nic-install.jpg)

### 2. Interface Mapping in pfSense

After installation, the pfSense console (or web GUI) was used to assign the physical interfaces to their logical roles. This is crucial for defining the traffic paths.

| pfSense Interface Name | Physical Port (Chip/Name) | Assigned Role | Connection |
| :--- | :--- | :--- | :--- |
| **WAN** | `em0` (Onboard Realtek) | External / Internet | Connects directly to the ISP Modem/Router. |
| **LAN** | `igb0` (New Intel Card) | Internal / Home Lab Network | Connects to the main switch. IP: **192.168.1.1** |

> **Note:** We intentionally used the new, more reliable Intel card (`igb0`) for the internal LAN to ensure better performance for the Hyper-V host and VMs.

---

## Initial Configuration

* **Base IP:** The LAN interface was configured with the static IP **192.168.1.1**.
* **Default Rules:** The default "allow all" rule was kept on the LAN interface for initial setup.

```markdown
// Future: Add a brief code block or screenshot of your initial firewall rules here.
