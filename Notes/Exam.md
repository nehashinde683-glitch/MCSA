
# 🖥️ Windows Networking & Server Concepts

---

## 🔹 Workgroup
- Peer-to-peer model, no central control.  
- User accounts are local to each PC.  
- Best for small networks (≤10 PCs).  
- Simple to set up, no domain controller required.  

---

## 🔹 Domain
- Client-server model managed by a **Domain Controller (DC)**.  
- Centralized management of users, computers, and policies.  
- Users can log in to any PC in the domain with one account.  
- Best for enterprises, universities, and large organizations.  

---

## 🔹 NTFS vs FAT32
- **NTFS**: Supports large files, encryption, permissions, journaling, reliable.  
- **FAT32**: Max file size 4 GB, simple, compatible with almost all OS.  
- NTFS = system/internal drives; FAT32 = USB drives/cross-platform use.  

---

## 🔹 DNS vs NetBIOS
- **DNS**: Converts domain name → IP, hierarchical, used on internet, port 53.  
- **NetBIOS**: Converts computer name → IP in LAN, flat naming, legacy, ports 137–139.  
- DNS = modern/global; NetBIOS = old/local.  

---

## 🔹 DNS Record Types
- **A / AAAA** → Domain to IPv4/IPv6.  
- **CNAME** → Alias of another domain.  
- **MX** → Mail server.  
- **PTR** → Reverse lookup (IP → Domain).  
- **NS / SOA / SRV / TXT** → Authority, services, verification.  

---

## 🔹 Group Policy (GPO)
- Used to centrally manage users and computers.  
- Types: Local & Domain GPO.  
- Applied in order: Local → Site → Domain → OU.  
- Managed with Group Policy Management Console (GPMC).  

---

## 🔹 Forward vs Reverse Lookup Zone
- **Forward**: Domain → IP (A, AAAA, MX, CNAME records).  
- **Reverse**: IP → Domain (PTR records).  
- Forward used for browsing; Reverse used in troubleshooting/security.  

---

## 🔹 DNS Zones
- **Primary Zone**: Master copy, can edit records.  
- **Secondary Zone**: Read-only copy for redundancy/load balancing.  
- Provides high availability in DNS infrastructure.  

---

## 🔹 Recursive vs Iterative Query
- **Recursive**: DNS server finds final IP for client (one response).  
- **Iterative**: DNS gives referral, client queries step by step.  
- Clients use recursive; DNS servers use iterative.  

---

## 🔹 DHCP & DORA
- DHCP auto-assigns IP, subnet, gateway, DNS.  
- **DORA** process: Discover → Offer → Request → Acknowledge.  
- Saves time and avoids manual IP setup.  

---

## 🔹 MBR vs GPT
- **MBR**: Old style, max 2 TB disk, 4 partitions, BIOS-based.  
- **GPT**: Modern, supports very large disks, 128 partitions, UEFI-based.  
- GPT is more reliable (stores multiple partition tables).  

---

## 🔹 Local vs Roaming Profile
- **Local**: Profile stored only on one PC.  
- **Roaming**: Profile stored on server, follows user across PCs.  
- Local = fast, single machine; Roaming = consistent but slower.  

---

## 🔹 Windows Deployment Services (WDS)
- Installs OS over network using PXE boot.  
- Components: Boot, Install, Capture, Discover images.  
- Simplifies large-scale OS deployment.  

---

## 🔹 Network Load Balancing (NLB)
- Distributes traffic across multiple servers.  
- Provides high availability and scalability.  
- Modes: None, Single, Class C affinity.  
- Commonly used for web and app servers.  

---

## 🔹 DFS (Distributed File System)
- Combines shared folders from different servers into one namespace.  
- **DFS Namespace**: Virtual folder tree for users.  
- **DFS Replication**: Keeps data synced across servers.  
- Ensures availability and easier access.  

---

## 🔹 Active Directory (AD)
- Directory service by Microsoft for centralized management.  
- Stores users, computers, printers, groups in a hierarchical structure.  
- Uses **Domain Controllers** to authenticate and apply policies.  
- Backbone for domains, GPOs, and enterprise security.  

---
