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

### '/boot' Directory  
After the Power On Self Test (POST) is complete, the configuration utility (in my case UEFI) looks for the EFI system partition (ESP) which contains the **bootloader**. The bootloader's function is to load two components 1) the Kernel 2) initramfs into memory. These two components the **Kernel**(the file named vmlinuz-5.x.y or vmlinuz-6.x.y) and **initramfs**(initial RAM filesystem) are part of the **/boot** directory. The bootloader is mounted at **/boot/efi** in UEFI-based systems. In addition to these, the **/boot** directory consists of the files **config**, and **System.map**. The RHEL-based Rocky Linux system uses the term **initramfs** whereas the Debian-based Ubuntu Server system names it **initrd**(initial RAM disk).  
<img width="1500" height="403" alt="Screenshot From 2026-07-31 18-44-52" src="https://github.com/user-attachments/assets/44bc9eba-121e-4d43-ae41-333fb7edb4a1" />  
<img width="980" height="277" alt="Screenshot From 2026-07-31 18-45-52" src="https://github.com/user-attachments/assets/e68c8cd0-1988-4b28-8e99-952013a0c1c6" />  </br>  

### '/dev' Directory
This directory consists of the "device files" also known as "device nodes" that are connected to the system. The CPU, Physical Memory (RAM), Storage devices, Graphics card, Parallel ports - to name a few - are represented as special files in this directory.  
<img width="516" height="455" alt="Screenshot From 2026-07-31 19-19-55" src="https://github.com/user-attachments/assets/d86da27f-6550-4deb-b5ce-e036f1d898e6" />  
<img width="594" height="193" alt="Screenshot From 2026-07-31 19-22-55" src="https://github.com/user-attachments/assets/794818af-7613-443a-ac4d-128c137297bf" />  
<img width="666" height="166" alt="Screenshot From 2026-07-31 19-16-43" src="https://github.com/user-attachments/assets/d315a553-5f04-49fe-a428-fef5f24018dc" />  
<img width="606" height="152" alt="Screenshot From 2026-07-31 19-27-44" src="https://github.com/user-attachments/assets/0ac10962-8164-4285-8d33-bd2975fbd4ef" /> </br>  

### '/etc/' Directory  
The '/etc' directory consists of Configuration files and Scripts and **cannot** contain executable files. Some of the files and directories that I have used in this directory are:  
/etc/sudoers.d/  
/etc/default/useradd
/etc/passwd
/etc/group
/etc/shadow
/etc/nsswitch.conf
/etc/hosts
/etc/resolv.conf
/etc/os-release
/etc/fstab </br>  

### '/home' Directory  
The **/home** directory is conventionally the place where users' personal data is stored. 
