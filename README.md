# Willkommen im Homelab-Projekt von Fatjon – Die Infrastruktur-Doku

Dieses Dokument beschreibt die Dienste und Programme, die ich in meinem Projekt zur "**Umschulung zum Fachinformatiker Systemintegration**" integriert habe. Alles wird – genau wie früher die einzelnen Dokumente aus dem `Docs`-Ordner – mit Git versioniert.

---

## Warum mache ich das? Die Motivation

Die Ziele für mein Homelab und die gesamte Doku hier auf Git gehen über ein einfaches "Zeigen, dass ich gut bin" in der IT hinaus. Es ist eine aktive Lernplattform:

* **Echte Praxis:** Es geht darum, das Gelernte nicht nur theoretisch zu verstehen, sondern es sofort praktisch anzuwenden und zu vertiefen.
* **Fit für die Prüfung:** Ich demonstriere hier die Planung, Virtualisierung, Verwaltung der Netzwerksegmentierung (pfSense), Überwachung und Wartung der Systeme.
* **Erfahrung teilen:** Das Dokument hält fest, welche Probleme ich hatte und wie ich sie während des Prozesses gelöst habe.

---

## Aufbau der Infrastruktur

Die Basis der Infrastruktur ist die **Segmentierung des Traffics** (VLAN) und die **Netzwerksicherheit**. Details zur gesamten Topologie und Konfiguration finden Sie in den Abschnitten gleich darunter.

---

## Was ich benutze: Die physische Homelab-Hardware (BOM)

Ich habe mein Homelab aus einem Mix von vorhandener Hardware gebaut. Dazu gehört die virtuelle Umgebung der Berufsschule (Hyper-V Remote Lab) und meine eigenen Computer, die jetzt als Layer-2-Switches für die Traffic-Segmentierung dienen.

### 3.1. Die zentralen Geräte für das Netzwerk (Core-Infrastruktur)

Diese Geräte bilden die Grundlage für Layer 2 und Layer 3 zur Aufteilung des Datenverkehrs.

| Gerät | Modell / Typ | Aufgabe im Homelab | Verbindung / Logik |
| :--- | :--- | :--- | :--- |
| **Dedizierter PC (Firewall)** | **DELL** | **pfSense** (Physisch) \| Traffic-Steuerung, Inter-VLAN-Routing, Sicherheit (Layer 3) \| Niedriges Niveau (2+ NICs) |
| **Switch Quadro-Core** | **Managed Layer-2-Switch** | Basis-Segmentierung (Trunk G0/1), physische VLANs \| Layer 2 |
| **Hypervisor Host** | **Acer Travelmate P216 (16 GB RAM)** | Workstation-Host für VMs und Dienste (z.B. DNS/AD) \| VLAN 30 |

### 3.2. Test-Clients

Diese Geräte dienen dazu, die Endbenutzer nachzubilden und die Regeln, die ich in der pfSense-Firewall eingestellt habe, zu testen:

| Gerät | Betriebssystem | Spezielle Merkmale | Rolle im Test |
| :--- | :--- | :--- | :--- |
| **Client A** (Admin) | **Windows 11 Pro** \| I5-1335U, 16 GB RAM \| Verwaltung \| Routing / Admin-Workstation (VLAN 30) |
| **Client B** | **Windows 8.1 Pro** \| Celeron N3050, 4 GB RAM \| **Standard-Client** (VLAN 40) |
| **Client C** | **OS X El Capitan** \| Core i7, 4 GB RAM \| **Client** \| **Verbindungstest** / Kompatibilität mit Mac OS X |
