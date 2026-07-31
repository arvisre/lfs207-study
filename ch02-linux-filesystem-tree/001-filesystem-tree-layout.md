# Linux Filesystem Tree Layout </br>  

### '/' - Root Directory  
The top-most level directory under which other directories branch out. As can be seen in the image below - "Storage Editor" Fedora Workstation 44 installation - the **/** directory is one of the **required** directories for a Linux system. </br>  
<img width="1528" height="617" alt="Screenshot From 2026-07-30 23-06-18" src="https://github.com/user-attachments/assets/eb9b3549-f7d3-46cf-94bd-4c404d90abc7" /> </br>  
Other directories listed under the **/** directory need not be in the same partition as root. For example, in my host system, the directories **/home**, **/isos**, and **/vms** which are sub-directories of the **/** directory, are stored in separate partitions - as shown in the image below: </br>  
<img width="1486" height="865" alt="Screenshot From 2026-07-30 23-24-23" src="https://github.com/user-attachments/assets/5a48c5ff-9c6c-4933-bcff-9b02a604571e" /> </br>  
The **/** directory must contain all the essential files such as the bootloader, configuration files, and utilities to boot the system and mount other file systems. </br>  

### '/bin' Directory  
The **/bin** directory contains executable programs for both System Administrators and regular non-privileged users. Both in RHEL-based Fedora 9.8 and Debian-based Ubuntu the **/bin** directory is symbolically linked to the **/usr/bin** directory. When we run the command **ls /bin** the command follows the symbolic link to **/usr/bin** and lists the files at that location. There are no sub-directories to the **/bin** directory.
<img width="571" height="119" alt="Screenshot From 2026-07-31 17-25-45" src="https://github.com/user-attachments/assets/7ddd6683-e88c-48ea-921e-a4b8b91190ce" />
<img width="571" height="119" alt="Screenshot From 2026-07-31 17-25-53" src="https://github.com/user-attachments/assets/c59a9691-5753-4bc8-927b-4fd2798cc855" /> </br>  
