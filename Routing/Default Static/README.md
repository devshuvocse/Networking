
````markdown
# 🛰️ Default Static Routing Lab

This project documents a **network configuration exercise** performed in **Cisco Packet Tracer**, focusing on implementing **Variable Length Subnet Masking (VLSM)** and a combination of **Static Routing** and **Default Static Routing** to achieve full connectivity between multiple, differently sized networks.

The lab simulates a scenario where internal networks must communicate with external networks (such as the Internet, represented by the **YouTube Server**) through an **intermediate ISP router**.

---

## 🚀 Key Concepts Covered

The following networking principles were applied and demonstrated in this lab:

- **Variable Length Subnet Masking (VLSM):**  
  The main network `172.16.0.0` was divided into subnets for 400, 300, and two 2-user links, optimizing address allocation and conserving IP space.  
  ⏱️ [02:32](http://www.youtube.com/watch?v=zuar5r4EKu4&t=152)

- **IP Addressing and Configuration:**  
  Each device (PCs, routers, and interfaces like **Gi0/0** and **Gi0/1**) was assigned an address based on calculated subnets.  
  ⏱️ [08:43](http://www.youtube.com/watch?v=zuar5r4EKu4&t=523)

- **Static Routing (`ip route`):**  
  Manually defining routes on the ISP router to reach non-directly connected networks.  
  ⏱️ [52:38](http://www.youtube.com/watch?v=zuar5r4EKu4&t=3158)

- **Default Static Routing (`ip route 0.0.0.0 0.0.0.0`):**  
  Configuring a *route of last resort* on edge routers (Home Router, YouTube Server Router) to send all unknown traffic toward the ISP.  
  ⏱️ [36:31](http://www.youtube.com/watch?v=zuar5r4EKu4&t=2191), [44:19](http://www.youtube.com/watch?v=zuar5r4EKu4&t=2659)

---

## ⚙️ Configuration Overview

| Feature | Details | Timestamp |
| :-- | :-- | :-- |
| **Main Network** | `172.16.0.0` | [01:00](http://www.youtube.com/watch?v=zuar5r4EKu4&t=60) |
| **VLSM Subnets** | Created for 400, 300, and two 2-user links (`172.16.0.0/23`, `172.16.2.0/23`, `172.16.4.0/30`, `172.16.4.4/30`) | [04:26](http://www.youtube.com/watch?v=zuar5r4EKu4&t=266) |
| **Edge Routers** | Used **Default Static Routing** to forward all traffic to the ISP router. | [43:47](http://www.youtube.com/watch?v=zuar5r4EKu4&t=2627), [50:07](http://www.youtube.com/watch?v=zuar5r4EKu4&t=3007) |
| **ISP Router** | Configured **Static Routes** to reach the edge networks directly. | [52:38](http://www.youtube.com/watch?v=zuar5r4EKu4&t=3158) |

---

### 💻 Default Static Route Command

Below is the core command used to define a default route in Cisco IOS:

```bash
Router(config)# ip route 0.0.0.0 0.0.0.0 [Next-Hop IP Address]
````

This tells the router to forward any traffic for unknown destinations to the specified next-hop (typically the ISP or upstream router).

---

## 🧩 Network Topology (Conceptual)

```
[PCs] --- [Home Router] --- [ISP Router] --- [YouTube Server Router] --- [Server]
```

* Home Router → Default route points to ISP
* YouTube Server Router → Default route points to ISP
* ISP Router → Static routes back to both edge routers

---

## 🎓 Learning Outcomes

By completing this lab, you’ll understand how to:

* Efficiently allocate IP addresses using VLSM
* Configure static and default routes in Cisco IOS
* Verify full network connectivity across multiple routers
* Simulate Internet access in a controlled Packet Tracer environment

---

## 📺 Watch the Full Tutorial

For a complete step-by-step demonstration of subnetting, configuration, and verification:

🎥 **[Default Static Routing Using Packet Tracer (Online Batch 2025)](http://www.youtube.com/watch?v=zuar5r4EKu4)**
🔗 [http://googleusercontent.com/youtube_content/0](http://googleusercontent.com/youtube_content/0)

---

## 🧠 Author Notes

> This project was created as part of a hands-on networking lab to practice static routing and default route configuration concepts in **Cisco Packet Tracer**.
>
> Contributions, feedback, and suggestions are always welcome!

---

### 📘 License

This project is released under the [MIT License](LICENSE).

```
