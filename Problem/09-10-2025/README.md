# Network Design and Configuration Task

## Overview
You are required to design and configure a network system based on the given topology structure.  
The upstream has provided a single IP block. Your task is to plan and assign IP addresses efficiently while following the given requirements.

---

## Objectives
- Use the provided IP block efficiently and minimize IP wastage.  
- Maintain proper subnetting and address planning.  
- Keep some IP addresses fixed as instructed in the topology.  
- Avoid any IP conflicts or overlapping subnets.  
- Configure devices according to their assigned roles.

---

## Server Requirements

### 1. Telnet Server (R1)
- Enable **Telnet** access.  
- Configure idle session timeout to **10 minutes**.  
- If a user remains idle for more than 10 minutes, the session should be locked automatically.  

### 2. DHCP Server (R2)
- Configure **DHCP service** for all connected user networks.  
- Exclude the first few IPs in each subnet as required.  
- Assign IPs automatically to all users in the network.  
- Verify that all devices receive the correct gateway and DNS information.

### 3. SSH Server (R3)
- Allow **only SSH** access (Telnet must be disabled).  
- Configure a **login lockout** for **5 minutes** after **2 failed login attempts**.  
- Ensure all SSH connections are encrypted and authenticated with local user credentials.

---

## Router Configuration Guidelines
- Configure routing between all routers to ensure full connectivity.  
- Set appropriate hostnames for each router.  
- Configure a secure **enable secret password**.  
- Create a **local username and password** for authentication.  
- Apply **Telnet and SSH** restrictions as per the requirements.

### Example Commands
```bash
enable secret 123
username shuvo secret 123
