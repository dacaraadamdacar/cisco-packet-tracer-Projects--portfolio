# 🏢 Small Office Network — Multi-VLAN Design
> Cisco Packet Tracer | Inter-VLAN Routing | Subnetting | Wireless


---

## 📋 Project Overview

A fully functional **Small Office Network** designed and simulated in Cisco Packet Tracer. The network segments three departments using VLANs with Inter-VLAN routing via a Cisco 2911 Router, wireless access per department, and automatic IP assignment through DHCP.

---

## 🗂️ Network Topology

| Department | VLAN | Subnet | Gateway |
|---|---|---|---|
| Admin / IT | VLAN 10 | 192.168.1.0/26 | 192.168.1.1 |
| Finance / HR | VLAN 20 | 192.168.1.64/26 | 192.168.1.65 |
| CS / Reception | VLAN 30 | 192.168.1.128/26 | 192.168.1.129 |

---

## 🔧 Technologies Used

- **Router:** Cisco 2911 — Router-on-a-Stick (Inter-VLAN Routing)
- **Switch:** Cisco 2960-24TT — VLAN segmentation, trunk port
- **Wireless:** Access Points per department (WPA2)
- **DHCP:** Configured on Router per VLAN pool
- **Subnetting:** /26 mask — 62 usable hosts per department
- **Encapsulation:** IEEE 802.1Q (dot1Q) on subinterfaces

---

## 📡 Devices Per Department

### 🔵 Admin / IT — VLAN 10
- 1x PC (wired)
- 1x Printer
- 1x Access Point
- 1x Laptop (wireless)
- 1x Smartphone (wireless)

### 🟢 Finance / HR — VLAN 20
- 1x PC (wired)
- 1x Printer
- 1x Access Point
- 1x Laptop (wireless)
- 1x Smartphone (wireless)

### 🟣 CS / Reception — VLAN 30
- 1x PC (wired)
- 1x Printer
- 1x Access Point
- 1x Laptop (wireless)
- 1x Smartphone (wireless)

---

## ⚙️ Key Configurations

### Router — Inter-VLAN (Router-on-a-Stick)
```bash
interface GigabitEthernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.1.1 255.255.255.192

interface GigabitEthernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.1.65 255.255.255.192

interface GigabitEthernet0/0.30
 encapsulation dot1Q 30
 ip address 192.168.1.129 255.255.255.192
```

### Router — DHCP Pools

ip dhcp pool Admin-Pool
 network 192.168.1.0 255.255.255.192
 default-router 192.168.1.1
 dns-server 192.168.1.1

ip dhcp pool Finance
 network 192.168.1.64 255.255.255.192
 default-router 192.168.1.65
 dns-server 192.168.1.65

ip dhcp pool Reception
 network 192.168.1.128 255.255.255.192
 default-router 192.168.1.129
 dns-server 192.168.1.129
```

### Switch — Trunk & Access Ports

interface FastEthernet0/1
 switchport mode trunk          ! Uplink to Router

interface FastEthernet0/2
 switchport access vlan 10
 switchport mode access         ! Admin/IT devices

interface FastEthernet0/5
 switchport access vlan 20
 switchport mode access         ! Finance/HR devices

interface FastEthernet0/8
 switchport access vlan 30
 switchport mode access         ! CS/Reception devices
```

---

## ✅ Testing & Verification

| Test | Result |
|---|---|
| PC0 (VLAN10) → Gateway ping     | ✅ Success |
| PC1 (VLAN20) → Gateway ping     | ✅ Success |
| PC2 (VLAN30) → Gateway ping     | ✅ Success |
| Laptop → AP wireless connection | ✅ Success |
| DHCP IP assignment all VLANs    | ✅ Success |
| Inter-VLAN communication        | ✅ Success |

---

## 📁 Project Files

```
soho-vlan-network/
├── topology.png          ← Network topology screenshot
├── README.md             ← This file
└── configs/
    ├── Router.txt        ← Full router running-config
    └── Switch.txt        ← Full switch running-config
```

---

## 💡 Key Takeaways

- How to design and subnet a /26 network for multiple departments
- Configuring **Router-on-a-Stick** for Inter-VLAN routing
- Setting up **802.1Q trunk** between router and switch
- Configuring **DHCP pools** per VLAN on a Cisco router
- Deploying **wireless access points** per department with WPA2

---

## 🚀 How to Open

1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
2. Clone this repository
3. Open the `.pkt` file in Packet Tracer
4. Explore the topology and test connectivity!

---

## 👤 Author

**MOHAMED ADAN MOHAMUD**
- GitHub: [(https://github.com/yourusername)](https://github.com/dacaraadamdacar)
- LinkedIn: www.linkedin.com/in/mohamed-adan-mohamud-97558213a

---

*Built with Cisco Packet Tracer as part of a Networking Portfolio*
