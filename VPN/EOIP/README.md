Here is your **full, clean, English, GitHub-ready `README.md`** for the **EOIP VPN Project**, fully formatted and ready to **copy–paste**.

---

# ✅ **README.md — EOIP Tunnel Between Two MikroTik Routers (Ready to Copy & Paste)**

```md
# 🛰️ MikroTik EOIP VPN Project (By Shuvo)

This project demonstrates how to connect two MikroTik routers using an **EOIP (Ethernet Over IP)** tunnel.  
EOIP creates a *Layer 2 bridge* between routers, allowing both LANs to behave as a **single broadcast domain**.

Both routers are bridged using an EOIP tunnel and share the same subnet (`10.100.100.0/24`), allowing PCs on both sides to communicate as if they were in the same LAN.

---

## 📡 Network Topology

The following diagram is included in the project as **`image.png`**:

```

PC1 ---- Main Router ==== EOIP Tunnel ==== Secondary Router ---- PC2

````

Both PCs receive IPs from the same DHCP pool (Layer 2 bridging).

---

## 🧩 IP Scheme

| Device         | Interface  | IP Address          | Description |
|----------------|------------|---------------------|-------------|
| **Main**       | ether1     | DHCP Client         | WAN         |
| Main           | ether2     | 10.100.100.1/24     | LAN         |
| Main EOIP      | Tunnel     | Uses WAN IPs        | EOIP Local |
| **Secondary**  | ether1     | DHCP Client         | WAN         |
| Secondary      | ether2     | 10.100.100.100/24   | LAN         |
| Secondary EOIP | Tunnel     | Uses WAN IPs        | EOIP Remote |

---

## 🌉 EOIP Tunnel Configuration

### **Main Router EOIP Config**
```bash
/interface eoip
add local-address=192.168.122.196 \
    remote-address=192.168.122.250 \
    mac-address=FE:86:DE:1A:E8:05 \
    name=EOIP-Tunnel-Interface \
    tunnel-id=1
````

### **Secondary Router EOIP Config**

```bash
/interface eoip
add local-address=192.168.122.250 \
    remote-address=192.168.122.196 \
    mac-address=FE:BF:69:19:2F:94 \
    name=EOIP-Tunnel-Interface \
    tunnel-id=1
```

---

## 🔗 Bridge Configuration (L2)

Both routers must bridge their **LAN interface** and **EOIP tunnel interface**.

### **Main Router Bridge**

```bash
/interface bridge
add name=EOIP-Bridge

/interface bridge port
add bridge=EOIP-Bridge interface=ether2
add bridge=EOIP-Bridge interface=EOIP-Tunnel-Interface
```

### **Secondary Router Bridge**

```bash
/interface bridge
add name=EOIP-Bridge

/interface bridge port
add bridge=EOIP-Bridge interface=ether2
add bridge=EOIP-Bridge interface=EOIP-Tunnel-Interface
```

---

## 🛜 DHCP Configuration

### **Main Router DHCP**

```bash
/ip pool
add name=dhcp_pool0 ranges=10.100.100.2-10.100.100.95

/ip dhcp-server
add interface=ether2 name=dhcp1 address-pool=dhcp_pool0
```

### **Secondary Router DHCP**

(Disabled for real production — only Main should run DHCP)
But included as per your export:

```bash
/ip pool
add name=dhcp_pool0 ranges=10.100.100.101-10.100.100.254

/ip dhcp-server
add interface=ether2 name=dhcp1 address-pool=dhcp_pool0
```

---

## 🏷️ Router Exports

### **Main Router Export**

```bash
# Full export from the Main router
# (Paste from your file if needed)
```

### **Secondary Router Export**

```bash
# Full export from the Secondary router
# (Paste from your file if needed)
```

---

## 🧪 Connectivity Test

### From Main LAN PC:

```bash
ping 10.100.100.100
```

### From Secondary LAN PC:

```bash
ping 10.100.100.1
```

### Layer 2 Tests:

* ARP should show both PCs
* DHCP should flow through EOIP
* Broadcast traffic should pass over tunnel

---

## ⭐ Features

* EOIP Tunnel (Layer 2)
* Same LAN Subnet on both routers
* Bridge-based VPN
* Works over any IP network
* Supports DHCP broadcast forwarding

---

## 👨‍💻 Author

**Shuvo**
Network Engineering Enthusiast
MikroTik & Routing Learner

---

