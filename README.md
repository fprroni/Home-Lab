**FATJON Prroni** | Fachinformatiker Systemintegration (Umschulung) 
    Tel: +4915209017791 | Email: fatjonprroni@gmail.com



# Willkommen im HomeLab-Projekt von Fatjon Prroni

Dieses Dokument beschreibt die Dienste und Programme, die ich in meinem Projekt integriert habe.
---

## Warum mache ich das?

Mein Homelab-Projekt und die Doku hier auf Git sollen mehr sein, als nur zu zeigen, was ich in der IT kann. Es ist eine Plattform, auf der ich aktiv lerne:

* **Praxis vor Theorie:** Hier wende ich was ich in der Schule lerne, **direkt in der Praxis an**. Das hilft mir, mein Wissen zu vertiefen und meine Fähigkeit, **Probleme in echten Projekten zu lösen (Troubleshooting-Skills)**, zu verbessern.
  
* **Vorbereitung auf die Prüfung:** Durch die Planung, Virtualisierung, das Management der Netzwerk-Trennung (pfSense) und die Wartung der Systeme bereite ich mich konkret auf die **Abschlussprüfung** vor.

**Status:** Das Projekt ist **noch nicht fertig**. Ich werde es über die nächsten Wochen und Monate stetig erweitern und neue Themen und Inhalte aus dem Schulunterricht hinzufügen.


## Aufbau der Infrastruktur

Die Basis der Infrastruktur ist die **Segmentierung des Traffics** (VLAN) und die **Netzwerksicherheit**. Details zur gesamten Topologie und Konfiguration finden Sie in den Abschnitten gleich darunter.

---

## Was ich benutze: Die physische Homelab-Hardware

Ich habe mein Homelab aus einem Mix von vorhandener Hardware gebaut. Dazu gehört die virtuelle Umgebung der Berufsschule (Hyper-V Remote Lab) und meine eigenen Computer.

### 3.1. Die zentralen Geräte für das Netzwerk (Core-Infrastruktur)

Diese Geräte bilden die Grundlage für Layer 2 und Layer 3 zur Aufteilung des Datenverkehrs.

| Gerät | Modell / Typ | Aufgabe im Homelab |
| :--- | :--- | :--- |
| **Dedizierter PC (Firewall)** | **DELL** | **pfSense** (Physisch) \| Traffic-Steuerung, Inter-VLAN-Routing, Sicherheit (Layer 3) \| Niedriges Niveau (2+ NICs) |
| **Switch Quadro-Core** | **Managed Layer-2-Switch** | Basis-Segmentierung (Trunk G0/1), physische VLANs \| Layer 2 |
| **Hypervisor Host** | **Acer Travelmate P216 (16 GB RAM)** | Workstation-Host für VMs und Dienste (z.B. DNS/AD) \| VLAN 30 |

### 3.2. Test-Clients

Diese Geräte dienen dazu, die Endbenutzer nachzubilden und die Regeln, die ich in der pfSense-Firewall eingestellt habe, zu testen:

| Gerät | Betriebssystem | Spezielle Merkmale |
| :--- | :--- | :--- |
| **Client A** (Admin) | **Windows 11 Pro** \| I5-1335U, 16 GB RAM \| Verwaltung \| Routing / Admin-Workstation (VLAN 30) |
| **Client B** | **Windows 8.1 Pro** \| Celeron N3050, 4 GB RAM \| **Standard-Client** (VLAN 40) |
| **Client C** | **OS X El Capitan** \| Core i7, 4 GB RAM \| **Client** \| **Verbindungstest** / Kompatibilität mit Mac OS X |
