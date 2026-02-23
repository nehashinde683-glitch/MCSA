# Install DFS Role 

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


## Create Folder And Give sharing Permission And NTFS Permision on Both Server 

### Server1
### Sharing Permision

1. Create folder CompanyData
2. right click on CompanyData
3. go to properties
4. click on sharing tab
5. Tick on share this folder
6. click on permision
7. tick on full contol
8. click on apply
9. click on ok
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/77cbc765-d0ae-4309-a6f0-b71c36146928" />

### Security Permission

1. Right click on CompanyData
2. Go to Properties
3. click on security tab
4. click on Edit
5. click on User (MICROSOFT\User)
6. tick on Full Control
7. click on Apply
8. click n ok
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/5850f806-53c3-4235-a441-e156b2203ff4" />

### Server 2
### Sharing Permision

1. Create folder CompanyData
2. right click on Company Data
3. go to properties
4. click on sharing tab
5. Tick on share this folder
6. click on permision
7. tick on full contol
8. click on apply
9. click on ok
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/82c2e074-50ce-4dc4-be8b-3d354a42b624" />


### Security Permission

1. Right click on CompanyData
2. Go to Properties
3. click on security tab
4. click on Edit
5. click on User (MICROSOFT\User)
6. tick on Full Control
7. click on Apply
8. click n ok

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/7f9171fd-ae7d-4847-951d-3f7369b3c75e" />



## Configure DFS Namespace
1. go to server manager
2. click on tools
3. click on DFS Management
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d66732c5-cba4-4784-ae65-1b265819819e" />

4. Right Click On Namespace
5. click on New Namespaces
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/434b3f0e-c71f-4038-bb1f-ff454ced3a26" />

6. Namespace server type `server1`
7. click on next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/64f83386-086e-438c-b1cf-84e7c320026d" />

8. Namespace name type `NextGen`
9. click next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/998ed695-945e-46c4-8211-1342e3eb8d9d" />

10. Select Domain Based Namespace
11. click next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b602650b-00de-4da7-b01f-cac7704de7f1" />
12. click create

## Add Second Namespace Server2
1. right click on \\microsoft.com\Nextgen
2. click on Add namespace server
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/bd2279c0-02be-4318-b175-e83d84fbd514" />
3. type namespace server `server2`
4. click ok
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2fd05148-2f5e-4327-82ac-bf790dacb7cf" />

## Add Folder to Namespace
1. right click on \\microsoft.com\Nextgen
2. click on new folder
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/1e60374d-ec98-48f2-ad3c-fa0f7ec87b96" />
3. Type Folder Name  `CompanyData`
4. click on add
5. type path to folder target:
  - \\server1\CompanyData
  - \\server2\CompanyData
6. click ok
<img width="1919" height="1072" alt="image" src="https://github.com/user-attachments/assets/08e53b8c-48a3-4629-85a8-287ec5530a70" />


## Configure DFS Replication
1. Redirect to Replicate folder wizard
2. type replication group name
  - \\microsoft.com\NextGen\CompanyData
3. type replicated folder name
 - CompanyData
4. click next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b7ba9ad2-9417-4233-a4cc-04bb7a49db21" />

5. Replication eligibility click next
6. select primary member
 - server1
7. click next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2209e942-f58f-43c8-886f-60e1e0dc97fe" />
8. Topology selection select:
   - Full mesh

9. click next
10. Replication group shedul and bandwith select:
 - Replicate continuously using the Secified bandwith
11. select bandwith
   - full
<img width="1919" height="1076" alt="image" src="https://github.com/user-attachments/assets/fc00fc01-8546-4ee9-804a-6c4cc2f7c9ed" />
12. click on next
13. click on create 
<img width="1919" height="1059" alt="image" src="https://github.com/user-attachments/assets/bfe15f46-c332-4bee-8e0e-5c5737522eed" />


##  Verification

1. Go to Server1
2. create textdocument under CopanyData
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ce2bc54d-7e72-4ebb-b426-20b1d26a1c73" />

3. Go to client1
4. press window key + R
 - type microsoft.com
<img width="1919" height="1073" alt="image" src="https://github.com/user-attachments/assets/bd2aa76d-6ff4-43c1-8b8e-531ede85d47d" />
4. go to NextGen Folder
5. go to CopmanyData Folder
6. Now see the files
<img width="1919" height="1050" alt="image" src="https://github.com/user-attachments/assets/d0b7eac5-589c-464b-b6b6-805af5164b60" />


# Window server Backup

## Install window Server Backup on Both Server1 and Server2
1. go to server manager
2. click on add role and feature
3. until feature click next
4. tick on window server backup
5. click next
6. click install
<img width="1919" height="1077" alt="image" src="https://github.com/user-attachments/assets/bf0d68af-c1ba-4c59-ae38-82932d2c684c" />

## Configuration
1. Go to server manager
2. click on tools
3. click on window server backup
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/06af9b89-e044-463c-8ff0-8e2c59dbeedf" />

4. Right click on local Backup
5. Click on Backup shedual
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9d0e43ec-f722-4761-8099-c6fa747ec305" />
6. Gating Started click next
7. select backup configuration
  - Custome
8. click next
<img width="1919" height="1077" alt="image" src="https://github.com/user-attachments/assets/48485a13-7702-4fa1-89e5-a0499e9f628e" />
9. Select itom for Backup
10. click on add item
    - go to Local disk c
    - select companyData
11. click on ok
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/feedffd2-e33f-47f0-9109-b6445d4b83ff" />
12. click on next
13. specify backup time
 - clickon ones a day
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/84f366e0-0a20-43be-a8a6-f06b917516f7" />

14. bckup specify destination
  - select backup to hard disk that is dedicated For backup (Recomended)
15. click next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/4232f598-67b7-4056-8ca4-7b926c6f776d" />

16. click on show all avalable disks
  - select E disks
17. click ok
<img width="1856" height="1000" alt="image" src="https://github.com/user-attachments/assets/93dbc6bf-d599-40e3-8342-f7a3f0c917f0" />
18. click next
19. click finish
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/48d22286-1cef-4cc7-87b5-ca0b4e417847" />

20. Now you can seen succesfull backup
<img width="1919" height="1001" alt="image" src="https://github.com/user-attachments/assets/2769bca3-515f-48ba-b351-ceddd786dcea" />
