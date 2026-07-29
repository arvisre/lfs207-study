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



However on further research I learned that it does make sense to modify the permissions to 440 or the more conservative 400 for this file. Let me explain my understanding: </br>  

A regular user account can list the contents of **/etc** and **cd** into the directory. However, a regular user cannot list the contents of or **cd** into the **/etc/sudoers.d/** directory, because the group **Other** has no permissions.  
However


