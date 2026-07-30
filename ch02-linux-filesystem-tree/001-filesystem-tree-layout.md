# Linux Filesystem Tree Layout </br>  

### '/' - Root Directory  
The top-most level directory under which other directories branch out. As can be seen in the image below - "Storage Editor" Fedora Workstation 44 installation - the **/** directory is one of the **required** directories for a Linux system. </br>  
<img width="1528" height="617" alt="Screenshot From 2026-07-30 23-06-18" src="https://github.com/user-attachments/assets/eb9b3549-f7d3-46cf-94bd-4c404d90abc7" /> </br>  
Other directories listed under the **/** directory need not be in the same partition as root. For example, in my host system, the directories **/home**, **/isos**, and **/vms** which are sub-directories of the **/** directory, are stored in separate partitions - as shown in the image below: </br>  
<img width="1486" height="865" alt="Screenshot From 2026-07-30 23-24-23" src="https://github.com/user-attachments/assets/5a48c5ff-9c6c-4933-bcff-9b02a604571e" /> </br>  
The **/** directory must contain all the essential files such as the bootloader, configuration files, and utilities to boot the system and mount other file systems. </br>  

