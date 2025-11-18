# 🏡 Willkommen im Homelab-in-E und Fatjon – Dokumentation der Infrastruktur

Dieses Dokument beschreibt die integrierten Dienste und Programme meines Projekts "**Umschulung Fachinformatiker Systemintegration**", die – wie bisher in den Dokumenten aus dem Ordner `Docs` – von Git verwaltet werden (Versionskontrolle mittels Git).

---

## 🎯 Ziele der Motivation

Die Hauptziele und die Dokumentation dieses Homelabs, das in einem Git-Repository gespeichert ist, sind nicht darauf beschränkt, "nur zu zeigen", dass ich gut in der IT und vernetzt bin. Stattdessen dienen sie als aktive Lernplattform:

* **Praktisches Lernen:** Der Zweck der Übung ist es, die Konzepte, die ich lerne, nicht nur theoretisch, sondern praktisch anzuwenden.
* **Vorbereitung auf die Abschlussprüfung:** Sie dient dazu, die Erstellung, Virtualisierung, Verwaltung der Segmentierung (pfSense), Überwachung und Wartung von Systemen zu demonstrieren.
* **Reflexion:** Das Dokument beschreibt die Herausforderungen und die gefundenen Lösungen während des gesamten Prozesses.

---

## 🏗️ Überblick über die Infrastruktur

Die Infrastruktur ist um die Segmentierung des Datenverkehrs (VLAN) und die Netzwerksicherheit herum aufgebaut. Details zu Topologie und Konfiguration finden Sie in den Abschnitten weiter unten.

---

## 💻 Physische Homelab-Geräte (BOM)

Zur Realisierung des Homelabs habe ich meine Kombination aus vorhandener Hardware genutzt, einschließlich der virtuellen Umgebung der Berufsschule (Hyper-V Remote Lab), sowie eigener Heimcomputer, die jetzt als Layer-2-Switches zur Verkehrssegmentierung dienen.

### 3.1. Wichtige Geräte für das Netzwerk (Core Infrastructure)

Die folgenden Geräte bilden die Basis für Layer 2 und Layer 3 zur Verkehrssegmentierung.

| Gerät | Modell / Typ | Rolle im Homelab | Verbindung / Logik |
| :--- | :--- | :--- | :--- |
| **Firewall Dedizierter PC** | **DELL** | **pfSense** (Physische Instanz. Physik. Schnittstellen) \| Kontrolle des Traffics, Inter-VLAN-Routing, Sicherheit (Layer 3) \| Niedriges Niveau (2+ NIC) |
| **Switch Quadro-Core** | **Switch** (Managed Layer-2-Switch) \| Basis für Segmentierung (Trunk G0/1), Physische Schicht für VLAN- und Switch-Ports \| Niedriges Niveau |
| **Hypervisor Host** | **Acer Travelmate P216 (16 GB RAM)** \| Workstation-Hypervisor Host für VM-Dienste und Server (z.B. DNS/AD) \| VLAN 30 |

### 3.2. Test-Client-Geräte

Die folgenden Geräte werden verwendet, um Endbenutzer zu simulieren und die implementierten pfSense-Firewall-Regeln zu testen:

| Gerät | Betriebssystem | Spezifische Hauptmerkmale | Rolle im Test |
| :--- | :--- | :--- | :--- |
| **Client A** (Admin) | **Windows 11 Pro** \| I5-1335U, 16 GB RAM \| Verwaltung \| Routing / Admin-Workstation (VLAN 30) |
| **Client B** | **Windows 8.1 Pro** \| Celeron N3050, 4 GB RAM \| **Standard-Client** (VLAN 40) |
| **Client C** | **OS X El Capitan** \| Core i7, 4 GB RAM \| **Client** \| **Verbunden** / **Test** der Kompatibilität mit Mac OS X |
