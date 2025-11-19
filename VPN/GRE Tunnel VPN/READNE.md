
```md
# 🛰️ MikroTik GRE Tunnel Project (By Shuvo)

This project connects two MikroTik routers using a GRE (Generic Routing Encapsulation) tunnel.  
Both routers use separate LAN subnets, DHCP servers, and static routes.  
The GRE tunnel allows full communication between the two networks.

---

## 🚀 Project Topology

The following diagram shows the full network topology:

**File:** `image.png`  
(Place this file in the root of the repository)

```

Main Router (Left)  <------ GRE Tunnel ------>  Secondary Router (Right)

````

---

## 🧩 IP Scheme

| Device         | Interface  | IP Address        | Description |
|----------------|------------|-------------------|-------------|
| **Main**       | ether1     | DHCP Client       | WAN         |
| Main           | ether2     | 10.100.100.1/24   | LAN         |
| Main           | GRE Tunnel | 10.100.250.2/30   | Tunnel Local |
| **Secondary**  | ether1     | DHCP Client       | WAN         |
| Secondary      | ether2     | 10.100.200.1/24   | LAN         |
| Secondary      | GRE Tunnel | 10.100.250.1/30   | Tunnel Remote |

---

## 🌉 GRE Tunnel Configuration

### **Main Router**
```bash
/interface gre
add local-address=192.168.122.196 name=GRE-1_By_Shuvo remote-address=192.168.122.250

/ip address
add address=10.100.250.2/30 interface=GRE-1_By_Shuvo
````

### **Secondary Router**

```bash
/interface gre
add local-address=192.168.122.250 name=GRE-1_By_Shuvo remote-address=192.168.122.196

/ip address
add address=10.100.250.1/30 interface=GRE-1_By_Shuvo
```

---

## 🛜 DHCP Configuration

### **Main Router**

```bash
/ip pool
add name=dhcp_pool0 ranges=10.100.100.2-10.100.100.254

/ip dhcp-server
add address-pool=dhcp_pool0 interface=ether2 name=dhcp1
```

### **Secondary Router**

```bash
/ip pool
add name=dhcp_pool0 ranges=10.100.200.2-10.100.200.254

/ip dhcp-server
add address-pool=dhcp_pool0 interface=ether2 name=dhcp1
```

---

## 🛣️ Static Routing Configuration

### **Main → Secondary LAN**

```bash
/ip route
add dst-address=10.100.200.0/24 gateway=10.100.250.1
```

### **Secondary → Main LAN**

```bash
/ip route
add dst-address=10.100.100.0/24 gateway=10.100.250.2
```

---

## 📤 Full Router Exports

### **Main Router Export**

```bash
[admin@Main] > export
# 2025-11-19 05:44:46 by RouterOS 7.20.2
# system id = +O0dftkOIdB
#
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
set [ find default-name=ether5 ] disable-running-check=no
set [ find default-name=ether6 ] disable-running-check=no
set [ find default-name=ether7 ] disable-running-check=no
set [ find default-name=ether8 ] disable-running-check=no
/interface gre
add local-address=192.168.122.196 name=GRE-1_By_Shuvo remote-address=192.168.122.250
/ip pool
add name=dhcp_pool0 ranges=10.100.100.2-10.100.100.254
/ip dhcp-server
add address-pool=dhcp_pool0 interface=ether2 name=dhcp1
/port
set 0 name=serial0
/ip address
add address=10.100.100.1/24 interface=ether2 network=10.100.100.0
add address=10.100.250.2/30 interface=GRE-1_By_Shuvo network=10.100.250.0
/ip dhcp-client
add interface=ether1
/ip dhcp-server network
add address=10.100.100.0/24 gateway=10.100.100.1
/ip route
add dst-address=10.100.200.0/24 gateway=10.100.250.1
/system identity
set name=Main
[admin@Main] > 

```

### **Secondary Router Export**

```bash
[admin@Secondary] > export
# 2025-11-19 05:43:57 by RouterOS 7.20.2
# system id = QQPC/ntA5IF
#
/interface ethernet
set [ find default-name=ether1 ] disable-running-check=no
set [ find default-name=ether2 ] disable-running-check=no
set [ find default-name=ether3 ] disable-running-check=no
set [ find default-name=ether4 ] disable-running-check=no
set [ find default-name=ether5 ] disable-running-check=no
set [ find default-name=ether6 ] disable-running-check=no
set [ find default-name=ether7 ] disable-running-check=no
set [ find default-name=ether8 ] disable-running-check=no
/interface gre
add local-address=192.168.122.250 name=GRE-1_By_Shuvo remote-address=192.168.122.196
/ip pool
add name=dhcp_pool0 ranges=10.100.200.2-10.100.200.254
/ip dhcp-server
add address-pool=dhcp_pool0 interface=ether2 name=dhcp1
/port
set 0 name=serial0
/ip address
add address=10.100.200.1/24 interface=ether2 network=10.100.200.0
add address=10.100.250.1/30 interface=GRE-1_By_Shuvo network=10.100.250.0
/ip dhcp-client
add interface=ether1
/ip dhcp-server network
add address=10.100.200.0/24 gateway=10.100.200.1
/ip route
add dst-address=10.100.100.0/24 gateway=10.100.250.2
/system identity
set name=Secondary
[admin@Secondary] > 


```

---

## 📘 How to Use

1. Clone the repository:

   ```bash
   git clone https://github.com/<your-username>/<repo-name>.git
   ```

2. Configure GRE tunnel on both MikroTik routers.

3. Ensure both WAN IPs are reachable.

4. Test GRE tunnel connectivity:

   * From Main:
     `ping 10.100.250.1`
   * From Secondary:
     `ping 10.100.250.2`

5. Test LAN reachability:

   * From PC1 → `ping 10.100.200.1`
   * From PC2 → `ping 10.100.100.1`

---

## 🏷️ Author

**Shuvo**
Networking Enthusiast & MikroTik Learner

---

## ⭐ Support

If you like this project, please give it a **Star** on GitHub!

```
