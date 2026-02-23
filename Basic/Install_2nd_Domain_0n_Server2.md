# Second Server Domain Configuration (Server2) 

## Install Role Active directory

1. go to Server Manager
2. click on Add Role and Feature
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/55421e07-716f-425b-ae4f-dbb0b49a2d61" />

3. click on next until Server Role
4. tick on active directory Domain Service
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b94517f8-e393-43cd-b0a9-fc986b8d9486" />
5. click on add feature
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/8559471f-883f-410b-a0b7-705ab1e8c58b" />
6. tick on restart the destination Server Atomaticaly if Requare
7. click Install
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/47a42f87-b494-42ff-91ed-1d51402eec72" />
8. click on Flag Icone
9. click on Promote this server to a domain
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e88dbf6d-44ea-46e8-8bd5-38a3468be675" />

10. redirect to active directory domain serveviceconfiguration wizard
11. select the deployment option
    - add a Domain controler to an existing Domain
12. specify the Domain Information for this option
    - domain : microsoft.com
13. click next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/6e9f4735-5b38-4795-9de4-bcefad8e0f1e" />

14. Specify Domain Controler capebilities and site infromation
    - select domain name system syver
    - select Globle category
15. site name : Defalte-First-side-name
16. type the directory service Restrore mode Password
    - password `pass@123`
    - conform `pass@123`
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/637b4031-c676-46bb-8316-c710f61de273" />
17. DNS option
    - click next
18. specify additinal replication option
    - replication option : sever1.microsoft.com
19. click next
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/38f4d42b-a17b-43d0-b794-d746d6c1a84e" />
20. specify the location of the AD DS Database , log files , and SYSVOL
    - By defalte 
21. click next
22. click install
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/b4e585e6-dd72-4462-b67f-ff4a742cfc3d" />

### Create User 
1. Go to server Manager
2. click on tools
3. Click on Active directory Users abd computers
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/bdcf85c5-4dc6-420a-aa30-62d46f6e30f6" />

4. click on microsoft.com
5. Right click on user
6. click on new
7. click on user
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e0a6bcac-2c8d-4c97-b0b4-25b335fc0f2e" />
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d325600b-415e-4a25-a892-24e32f40d660" />
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/4f0fc233-1c06-4c69-aee3-8be7bfd0c275" />

## Verifiacation 
1. Go to Main Domain Server (server1)
2. go to server manager
3. click on tool
4. go to active directory user and computer
5. click on microsoft.com
6. click on user
7. now see the user `Adity`
<img width="1919" height="1006" alt="image" src="https://github.com/user-attachments/assets/3edca8b0-a75c-403d-84c1-98355a4b4654" />
