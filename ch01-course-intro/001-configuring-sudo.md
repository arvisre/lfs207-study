# Lab 1.1. Configuring the System for 'sudo' </br>  
Both Ubuntu Server and openSUSE Leap have added my user account "as" to the **sudo** and the **wheel** group, respectively. </br>  
In both in Rocky Linux 9.8 and 10.2 I have to add **sudo** permissions to my user account. This involves: </br>  
1. Switching as root user using the **su -l root** command and providing the **root** user's password.  
2. Then using the **cd** command and navigating to /etc/sudoers.d/  
3. Creating a file with the text **<userid> ALL=(ALL) ALL**  
4. The above text input is a rule which applies to "userid" on "ALL" hosts (that particular system in my case), to run command as "any user", and to run "any command". </br>  

## Observation and Learning: </br>  
As mentioned above, I created a file "as" using the touch command and made the text input using the nano editor. The course material had suggested that I use the command **sudo chmod 440 /etc/sudoers.d/as** or **sudo chmod 400 /etc/sudoers.d/as** to ensure the permissions for this file. </br>  

As can be seen the image below, the default file permissions (rw-r--r--) (644) are applied to this file I created.  </br>  
<img width="574" height="286" alt="Screenshot From 2026-07-29 15-42-54" src="https://github.com/user-attachments/assets/024700bb-135d-4212-bff8-e50ec1442ca4" /> </br>  
I did not bother taking the extra step of modifying permissions because the directory **/etc/sudoers.d** is owned by user **root** and group **root** and this file also was owned by user **root** and group **root**. </br>  
The permissions for **/etc**, **/etc/sudoers.d/**, and **/etc/sudoers.d/as** as shown in the image below: </br>  
<img width="597" height="153" alt="Screenshot From 2026-07-29 15-52-11" src="https://github.com/user-attachments/assets/1fdc5a8f-2196-409b-bb64-a7281a8af17f" /> </br>  
Because the directory **/etc/sudoers.d/** does NOT provide any permission to **Other**, a normal user will not be able to list the contents of the directory, **cd** into the directory, or read the files inside the directory by providing the absolute path and filename. This can be confirmed from the image below: </br>  
<img width="584" height="164" alt="Screenshot From 2026-07-29 16-07-41" src="https://github.com/user-attachments/assets/3a16e91c-5567-4a70-a20e-0e0de69d1f0d" /> </br>  

However, the suggestion to set 440 or 400 on the file is a good practice. The command **sudo** has **setuid** enabled such that it runs with the **user owner** permissions - which is the root - and the sudoers file is parsed as root. Hence there is no need to provide permissions for the **Other** group. </br>  
<img width="594" height="111" alt="Screenshot From 2026-07-29 16-15-01" src="https://github.com/user-attachments/assets/c2ce6e38-cd08-47f3-ac73-fd3f6c591052" /> </br>  

### A different scenario: </br>  
"IF" the **/etc/sudoers.d/** directory had the permissions "drwxr-x--x" and the file had "-rw-r--r--", then a normal user may NOT be able to list the contents of the directory - because there is NO **read** permission for **Other**, but if he can guess what filename can be in that directory, he can use the **cat** command and read the contents - because there IS **execute** permission for **Other**.
