

# ⚙️ Mikrotik Minimum Configuration Lab (GNS3)

A comprehensive GNS3 lab demonstrating the **minimum required configuration** for a Mikrotik router to achieve full network functionality — using both **Command Line Interface (CLI)** and **Graphical User Interface (GUI)** via **Winbox**.

This project simulates a **two-site Wide Area Network (WAN)** setup, featuring a **Head Office (HO)** connected to the internet and a **Branch Office (BO)** linked via a **point-to-point connection**.

---

## 🖼️ Project Topology Overview

Here’s the visual topology of the complete Mikrotik Minimum Configuration Lab:

![Project Topology](Mikrotik/Basic%20Configuration(All-Over)/Project%20image.png)

## 🎯 Project Goal

The goal of this lab is to provide a fully functional GNS3 topology that helps learners and professionals practice Mikrotik configuration using both:

1. **CLI (Command Line Interface)** — for direct, hands-on configuration.
2. **GUI (Winbox)** — for quick setup, monitoring, and verification.

---

## 🚀 Key Features & Configuration Topics

This project covers the following core networking concepts and configurations:

- **Dual-Site Topology:** Head Office (HO) and Branch Office (BO) Mikrotik routers.
- **Interface Renaming:** Custom port names (e.g., `ether1` → `WAN1`, `ether2` → `LAN2`).
- **Internet Access:** DHCP Client setup on the WAN interface (for dynamic internet IP).
- **NAT (Masquerade):** Enables LAN devices to access the internet through the HO router.
- **DHCP Server:** Automatic IP and DNS assignment for LAN clients.
- **Static Routing:** 
  - **Default Route:** For internet access.
  - **Inter-Site Static Route:** For communication between HO and BO.
- **Connectivity Verification:** `ping` tests to verify inter-site and internet connectivity.

---

## 💻 Prerequisites

You will need the following software installed before starting:

| Software | Version | Purpose |
| :--- | :--- | :--- |
| **GNS3** | v2.2.x or later | Network simulation platform |
| **Mikrotik CHR** | Latest Stable | Cloud Hosted Router image for GNS3 |
| **Winbox** | Latest | Mikrotik GUI management tool |
| **Client OS Image** | Any lightweight OS | For DHCP and connectivity testing (e.g., Microcore Linux or Windows) |

---

## 🗺️ Network Topology Overview

| Site | Device | WAN Interface (IP) | LAN Interface (IP) |
| :--- | :--- | :--- | :--- |
| **Head Office (HO)** | Router-A (Mikrotik) | DHCP (from GNS3 Cloud) | 10.1.1.1/30 (Link to BO) |
| **Branch Office (BO)** | Router-B (Mikrotik) | 10.1.1.2/30 (Link to HO) | 192.168.1.1/24 (LAN Clients) |
| **WAN Link** | — | **Network:** 10.1.1.0/30 | **Type:** Point-to-Point |
| **Internet** | GNS3 Cloud Node | — | — |

---

## 🛠️ Installation & Setup Steps

1. **Clone all of my Repository:**
   ```bash
   git clone https://github.com/[your-username]/mikrotik-minimum-configuration-lab.git](https://github.com/devshuvocse/Networking.git

Open the Project in GNS3:


Locate and open the .gns3 project file inside the repository.


Verify Mikrotik Image:


Ensure the correct Mikrotik CHR image is linked to both routers.


Start the Devices:


Right-click the topology → Start All Devices.


Access Routers:


CLI: Double-click routers in GNS3 to open the console.


GUI (Winbox): Use MAC or IP to connect via the Winbox tool.


Default Credentials:


Username: admin


Password: (blank) but I add "itbd" in both router.
 ⚠️ Note: The tutorial sets a new password immediately for security.



🎥 Video Tutorial
Watch the full step-by-step configuration guide on YouTube:
 👉 https://youtu.be/Bb08oIsBnCQ
This video explains both CLI and GUI (Winbox) methods for configuring Mikrotik routers from start to finish.

📚 Additional Resources
Mikrotik Official Wiki: https://wiki.mikrotik.com


GNS3 Documentation: https://docs.gns3.com


Mikrotik Downloads: https://mikrotik.com/download





🤝 Contributing
Contributions are welcome!
 You can:
Add advanced features (e.g., VLANs, Firewall rules, OSPF).


Improve documentation or visual diagrams.


Submit a Pull Request (PR) with your enhancements.



📜 License
This project is open-source and available under the MIT License.
 Feel free to use, modify, and share it for educational or professional purposes.

💬 Author
Developed and demonstrated by [Your Name or GitHub Username]
 📺 YouTube: Mikrotik Minimum Configuration Lab Tutorial

⭐ If you found this project helpful, please give it a star on GitHub!

