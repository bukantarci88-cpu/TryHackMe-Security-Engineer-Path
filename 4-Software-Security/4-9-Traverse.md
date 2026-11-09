# Eng 4.9. Traverse

**Traverse**

Bob is a security engineer at a firm and works closely with the software/DevOps team to develop a tourism web application. Once the website was moved from QA to Production, the team noticed that the website was getting hacked daily and wanted to know the exact reason. Bob consulted the blue team as well but has yet to be successful. 

Can you help Bob find the vulnerabilities and restore the website?

**Answer the questions below**

> What type of encoding is used by the hackers to obfuscate the JavaScript file?
> 

hex (First, go to the page source and click the link provided in it.)

<img width="696" height="130" alt="image" src="https://github.com/user-attachments/assets/50259f9e-2b66-4cf1-add8-34545fc90b71" />


> What is the flag value after deobfuscating the file?
> 

DIRECTORY LISTING IS THE ONLY WAY

<img width="1366" height="472" alt="image 1" src="https://github.com/user-attachments/assets/344d8cdf-9b8e-4692-9c62-48ce84c6e34b" />


> Logging is an important aspect. What is the name of the file containing email dumps?
> 

email_dump.txt

<img width="867" height="467" alt="image 2" src="https://github.com/user-attachments/assets/61408d5b-165b-407e-b661-fb221fb514f1" />

<img width="517" height="257" alt="image 3" src="https://github.com/user-attachments/assets/8529a2ff-5c71-4b09-9b74-9e374d2afbbf" />


> The logs folder contains email logs and has a message for the software team lead. What is the name of the directory that Bob has created?
> 

planning (aquasec.com SDLC)

<img width="1268" height="327" alt="image 4" src="https://github.com/user-attachments/assets/457d67af-3808-4b96-86df-ca6b5e3d25cb" />

<img width="1062" height="556" alt="image 5" src="https://github.com/user-attachments/assets/d7e75b65-0925-4775-8a06-bca1d07f191e" />

<img width="1050" height="832" alt="image 6" src="https://github.com/user-attachments/assets/30261245-51f6-4903-b779-462dcc34df6d" />


> What is the key file for opening the directory that Bob has created for Mark?
> 

THM{100100111}

<img width="947" height="285" alt="image 7" src="https://github.com/user-attachments/assets/14fffd2b-0834-4ce3-9d93-63cb7318f78e" />


> What is the email address for ID 5 using the leaked API endpoint?
> 

[john@traverse.com](mailto:john@traverse.com)

<img width="546" height="301" alt="image 8" src="https://github.com/user-attachments/assets/d61658af-7e0c-495f-9314-a141cac79540" />


> What is the ID for the user with admin privileges?
> 

3 

<img width="530" height="317" alt="image 9" src="https://github.com/user-attachments/assets/d47581cf-c7ee-45e5-99b9-2eb27f004949" />


> What is the endpoint for logging in as the **admin**?
> 

Mention the last endpoint instead of the URL. For example, if the answer is URL is tryhackme.com/admin - Just write **/admin**. realadmin 

> The attacker uploaded a web shell and renamed a file used for managing the server. Can you find the name of the web shell that the attacker has uploaded?
> 

thm_shell.php

<img width="1042" height="692" alt="image 10" src="https://github.com/user-attachments/assets/23c31a5e-8081-445e-a2c6-4d959ec2d0ab" />


 write ls in whoami then execute

<img width="1070" height="866" alt="image 11" src="https://github.com/user-attachments/assets/20bb1d58-23dc-494b-8bef-f9ff28e900cb" />


> What is the name of the file renamed by the attacker for managing the web server?
> 

renamed_file_manager.php

> Can you use the file manager to restore the original website by removing the "**FINALLY HACKED**" message? What is the flag value after restoring the main website?
> 

<img width="992" height="820" alt="image 12" src="https://github.com/user-attachments/assets/c6fa538e-ff0f-4b0b-9d3e-6c8622da624d" />

<img width="1057" height="836" alt="image 13" src="https://github.com/user-attachments/assets/9def332c-b678-4ea3-87f8-2341ed21cd0e" />

<img width="1067" height="590" alt="image 14" src="https://github.com/user-attachments/assets/028e9091-c8db-4fbf-9840-2b81925f66ea" />

