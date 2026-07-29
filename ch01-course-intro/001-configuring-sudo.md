# Lab 1.1. Configuring the System for 'sudo' </br>  
Both Ubuntu Server and openSUSE Leap have added my user account "as" to the **sudo** and the **wheel** group, respectively. </br>  
In both in Rocky Linux 9.8 and 10.2 I have to add **sudo** permissions to my user account. This involves: </br>  
1. Switching as root user using the **su -l root** command and providing the **root** user's password.  
2. Then using the **cd** command and navigating to /etc/sudoers.d/  
3. Creating a file with the text **<userid> ALL=(ALL) ALL**  
4. The above text input is a rule which applies to "userid" on "ALL" hosts (that particular system in my case), to run command as "any user", and to run "any command". </br>  

## Observations and Learning: </br>  
