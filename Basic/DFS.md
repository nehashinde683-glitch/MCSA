# DFS Installation & Configuration — Step-by-step

## Prerequisites

- You must be a domain administrator (or have equivalent privileges).
- **Server1**, **Server2**, and **Client1** must be joined to the domain (example domain used here: `microsoft.com`).
- File and Printer Sharing enabled and network connectivity between machines.
- If prompted during installation, allow automatic restart of the destination server (optional but convenient for lab).

---

# step 1 — Install DFS Roles (Server1 and Server2)

**On Server1 (repeat the same steps on Server2):**

1. Log in to **Server1** with an Administrator account.
2. Open **Server Manager**.
3. Click **Add roles and features**.
4. Click **Next** repeatedly until you reach the **Server Roles** page.
5. Expand **File and Storage Services → File and iSCSI Services**.
6. Tick **DFS Namespaces**.
7. Tick **DFS Replication**.
8. (Optionally) Tick **File Server Resource Manager**.
9. Tick **Restart the destination server automatically if required** (if you want automatic reboot).
10. Click **Install** and wait for the installation to complete.

**Screenshot — select roles (example):**  
![Select DFS Roles](https://github.com/user-attachments/assets/140b19f0-a239-4485-949b-a50986c0320f)

**Screenshot — install / reboot option:**  
![Install Complete / Restart Option](https://github.com/user-attachments/assets/0e7c9607-55a2-4170-9360-b266653fda21)

**Repeat same installation on Server2:**  
![Same installation on Server2](https://github.com/user-attachments/assets/113dbf73-42c2-420e-813d-8531ec8a16f4)

---

# Stap 2 — Create & Share Folders

> We will create `C:\hr1` on **Server2** and `C:\hr2` on **Client1** and share both (lab/demo uses `Everyone` Full Control — **do not** do this in production).

## Server2 — create and share `C:\hr1`

1. Log in to **Server2**.
2. Open **File Explorer → This PC → Local Disk (C:)**.
3. Create folder `hr1` (path: `C:\hr1`).
4. Right-click `hr1` → **Properties** → **Sharing** tab.
5. Click **Advanced Sharing**.
6. Tick **Share this folder**.
7. Click **Permissions**.
8. Select **Everyone** and grant **Full Control** (lab only).
9. Click **Apply** → **OK**.

**Screenshot — created folder hr1:**  
![Create hr1 on Server2](https://github.com/user-attachments/assets/24e7ce83-3c80-4d64-b435-1cb02c30cfb6)

**Screenshot — share permissions (Everyone Full Control):**  
![Share Permissions - Everyone Full Control](https://github.com/user-attachments/assets/515875b3-c87f-4b3b-902b-d3ef85092dc7)

## Client1 — create and share `C:\hr2`

1. Log in to **Client1**.
2. Create folder `hr2` on C: (`C:\hr2`).
3. Right-click `hr2` → **Properties** → **Sharing** → **Advanced Sharing** → tick **Share this folder**.
4. Set permissions: **Everyone** → **Full Control** (lab only).
5. Click **Apply** → **OK**.

**Screenshot — created folder hr2 on Client1:**  
![Create hr2 on Client1](https://github.com/user-attachments/assets/abe55937-cc15-47f5-a171-5cfb0ad0c4af)

> **Important:** For production, use AD groups and proper NTFS permissions instead of `Everyone`.

---

# Step 3 — Create a Domain-based DFS Namespace (hosted on Server1)

1. On **Server1**, open **Server Manager** → **Tools** → **DFS Management** (DFS Manager).
   - **Tools → DFS Management** opens the management console.

**Screenshot — open DFS Manager:**  
![Open DFS Manager](https://github.com/user-attachments/assets/b9d62c65-e41f-47ec-86e0-915ebd964b09)

2. In **DFS Management**, right-click **Namespaces** → **New Namespace**.

**Screenshot — New Namespace wizard:**  
![New Namespace](https://github.com/user-attachments/assets/45af4d91-f22e-4230-836b-1596b8e04523)

3. When prompted, enter the server that will host the namespace: **server1**. Click **Next**.

**Screenshot — select namespace server (server1):**  
![Select Namespace Server (server1)](https://github.com/user-attachments/assets/533f8571-18aa-4ec2-936d-512899dc0b51)

4. Enter the namespace name: **HR** — this forms the namespace path `\\microsoft.com\HR`. Click **Next**.

**Screenshot — enter namespace name HR:**  
![Enter Namespace Name: HR](https://github.com/user-attachments/assets/adbac635-f151-4927-937a-b3abcce5673b)

5. Choose **Domain-based namespace** and click **Next**.

**Screenshot — choose domain-based namespace:**  
![Domain-based Namespace selection](https://github.com/user-attachments/assets/ace27f39-931d-48ee-a8e6-d16e9db054df)

6. Click **Create** and wait for success message.

**Screenshot — namespace created successfully:**  
![Namespace created successfully](https://github.com/user-attachments/assets/86c6288d-30e0-4337-8c1e-fcada16496a0)

---

# Step 4 — Add Namespace Folders & Targets

We will add two namespace folders under `\\microsoft.com\HR`: `hr1` (points to `\\server2\hr1`) and `hr2` (points to `\\client1\hr2`).

## Add `hr1` (target → `\\server2\hr1`)

1. In DFS Management, expand `\\microsoft.com\HR`.
2. Right-click the `HR` namespace → **New Folder**.
3. Folder name: `hr1`.
4. Click **Add** to add a folder target.
5. In **Add Folder Target**, enter `\\server2\hr1` and click **OK** / **Add**.

**Screenshot — create hr1 under namespace and add target:**  
![Create folder hr1 under namespace and add target](https://github.com/user-attachments/assets/b2161584-73bb-4ceb-be55-3abfcf0b1af8)

## Add `hr2` (target → `\\client1\hr2`)

1. Right-click `\\microsoft.com\HR` → **New Folder**.
2. Folder name: `hr2`.
3. Click **Add** and enter target path `\\client1\hr2`.
4. Click **OK**.

**Screenshot — create hr2 under namespace and add target:**  
![Create folder hr2 under namespace and add client target](https://github.com/user-attachments/assets/899ad7e3-65d8-487e-9ad3-a487d2e3d278)

> Optionally, configure DFS Replication if you need the contents synced between targets. (See section 6 for brief steps.)

---

# Step 5 — Verify Namespace & Folder Targets

1. On any domain-joined machine (Server1, Server2, or Client1), press **Windows Key + R**.
2. Type `\\microsoft.com` and press **Enter**.
3. You should see the `HR` namespace and the namespace folders `hr1` and `hr2`.

**Screenshot — run \\microsoft.com to view namespace:**  
![Run \\microsoft.com to view namespace](https://github.com/user-attachments/assets/0389f2fb-f808-45cb-b84a-7a1f6e7e2405)

4. Open `HR` and click `hr1` and `hr2` to confirm they redirect to `\\server2\hr1` and `\\client1\hr2` respectively.

**Screenshot — HR namespace showing hr1 and hr2:**  
![Namespace shows hr1 and hr2 folders](https://github.com/user-attachments/assets/4bb12368-d63a-4b16-8c85-2706104f71a7)

> **Verify on Server2 and Client1** as well to ensure targets are reachable and permissions allow access.

---

# Step 6 — Optional: Configure DFS Replication (quick steps)

> Use Replication if you want automatic file synchronization between multiple targets (e.g., between two servers).

1. In **DFS Management**, right-click **Replication** → **New Replication Group**.
2. Choose **Multipurpose replication group** (common) and click **Next**.
3. Add the replication members (e.g., `server2` and another server).
4. Choose the replicated folder (`C:\hr1`) and schedule/bandwidth settings.
5. Finish the wizard and monitor replication via **DFS Replication** logs.

**Troubleshooting replication:** Check **Event Viewer → Applications and Services Logs → DFS Replication**.

---

# Troubleshooting & Tips

- **Permission denied:** Verify both Share permissions (Sharing tab) and NTFS permissions (Security tab). Both must allow the intended users.
- **Namespace not visible:** Confirm the namespace server (`server1`) is online, DNS resolves the domain, and the namespace is domain-based.
- **Cannot access target:** Check network connectivity, firewall rules, and that the target share exists (`\\server2\hr1` or `\\client1\hr2`).
- **Replication issues:** Review DFS Replication event logs and ensure RPC and SMB communication between replication members.
- **Security best practice:** Replace `Everyone` with specific AD groups and apply least-privilege NTFS permissions in production.

---
