# Folder Redirection 

## Folder create and give permision

1. trun on server1
2. open file expolar
3. go to local disk c
4. create Documment  folder
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/51c32206-0193-4bf0-a443-67b29e27ddcf" />



5. right click on Document folder
6. click on properties
7. go to security
8. click on edit
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/d5d28439-42ac-4162-a839-c824cc7de346" />

9. click on user (microsof\user)
10. trick on box full control
11. click on apply
12. click on ok
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/eb307cb9-8dfe-435a-8d95-1a3e3089354f" />

13. go to sharing tap
14. click on Advanced sharing
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/322c32f9-9650-40df-82b9-b19b4f7a2b74" />

15. tick on share this folder
16. click on permission
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/5bc48438-2950-42c1-8084-66bbad9f3805" />

17. tick on full control
18. click on apply
19. click ok ok
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/69c5800d-cd36-4377-9efd-61e59914e956" />


## Group Policy Folder Redirection

1. click on window icon
2. click on server manager
3. click on tools
4. click on group policy management
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/a0328924-3baf-4a52-b7d7-c34d5637924e" />

6. click on Domain
7. click on microsoft.com
8. right click on defalte domain policy
9. click on edit
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/e722e097-f99e-4d19-9471-ef27f48d886c" />

10. go to user configuration
11. click on policy
12. click onn window setting
13. click on folder redirection
14. right click on Documents
15. click on properties
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/92de9b95-86b2-478f-8a23-2e01ac1127d9" />
16. chose baic-Redirection Evaryones folder to the same location
17. Root path type `\\server1\Document` = this is you create folder path
18. click on Apply
19. clik on ok
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/46aa8548-9b19-46fa-a832-e5572dd4b95c" />

20. go to group policy managment
21. right click on Defalte domain policy
22. click on refresh it
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/2959c45b-332a-496d-8f8c-2f72888901cc" />

## create files on server 2 hr user

1. power on server2
2. log in HR1 User
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ea27335f-28ff-4625-a3e4-1d5d10ba1689" />
3. click on file explore icon
4. go to this pc
5. go to Documents folder
6. click on right click
7. clik on new
8. clik on Text Document
9. then create text Document `PK` and type some words like welcome to nextGen and save it
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/9fee7c2f-eb40-4223-8c4b-4aa8c08cae4a" />

## verify
1. go to server1
2. login Microsoft/administrator user
3. click on file explore icon
4. go to local c
5. click on Document folder i have manual create
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/ba08e621-c4e8-43b3-9490-424d928e377e" />
6. now see the HR1 folder for saving data in domain controlar server1
<img width="1919" height="1076" alt="image" src="https://github.com/user-attachments/assets/4284b305-488e-4248-a7b0-8f27df831a6b" />

