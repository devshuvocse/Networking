# 🛰️ Static Routing Demonstration

This project demonstrates **Static Routing** using **Cisco Packet Tracer**.  
It is designed for learners who want to understand how routers forward packets manually through predefined routes.

---

## 📹 Video Tutorial
You can watch the full demonstration on YouTube:  
👉 [Static Routing Explanation & Configuration](https://youtu.be/b4ZxOdQMq3g)

---

## 📁 Project Files

| File Name | Description |
|------------|-------------|
| `Static Routing.pkt` | Cisco Packet Tracer simulation file showing the complete static routing setup |
| `README.md` | Documentation and usage guide for this project |

---

## ⚙️ Network Overview

This simulation includes:
- Multiple routers connected in a small topology  
- Static routes manually configured on each router  
- End devices (PCs) connected to different networks to test connectivity  
- Verification using the `ping` command

---

## 🧠 Learning Objectives

By exploring this project, you will learn:
1. What static routing is and when to use it  
2. How to configure static routes in Cisco routers  
3. How to verify network connectivity using `ping` and `traceroute`  
4. The difference between static and dynamic routing  

---

## 🚀 How to Use

1. Open **Cisco Packet Tracer**.  
2. Load the file `Static Routing.pkt`.  
3. Click on each router and open the **CLI tab**.  
4. Use `show ip route` to view static routes.  
5. Try to `ping` between PCs from different networks to test connectivity.  

---

## 🧩 Example Commands Used

```bash
Router(config)# ip route [destination_network] [subnet_mask] [next_hop_ip]
Router# show ip route
Router# ping [destination_ip]
