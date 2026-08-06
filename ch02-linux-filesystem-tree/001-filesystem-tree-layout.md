# Linux Filesystem Tree Layout </br>  

### '/' - Root Directory  
The top-most level directory under which other directories branch out. As can be seen in the image below - "Storage Editor" Fedora Workstation 44 installation - the **/** directory is one of the **required** directories for a Linux system. </br>  
<img width="1528" height="617" alt="Screenshot From 2026-07-30 23-06-18" src="https://github.com/user-attachments/assets/eb9b3549-f7d3-46cf-94bd-4c404d90abc7" /> </br>  
Other directories listed under the **/** directory need not be in the same partition as root. For example, in my host system, the directories **/home**, **/isos**, and **/vms** which are sub-directories of the **/** directory, are stored in separate partitions - as shown in the image below: </br>  
<img width="1486" height="865" alt="Screenshot From 2026-07-30 23-24-23" src="https://github.com/user-attachments/assets/5a48c5ff-9c6c-4933-bcff-9b02a604571e" /> </br>  
The **/** directory must contain all the essential files such as the bootloader, configuration files, and utilities to boot the system and mount other file systems. </br>  

### '/bin' Directory  
The **/bin** directory contains executable programs for both System Administrators and regular non-privileged users. Both in RHEL-based Fedora 9.8 and Debian-based Ubuntu the **/bin** directory is symbolically linked to the **/usr/bin** directory. When we run the command **ls /bin** the command follows the symbolic link to **/usr/bin** and lists the files at that location. There are no sub-directories to the **/bin** directory. </br>  
<img width="571" height="119" alt="Screenshot From 2026-07-31 17-25-45" src="https://github.com/user-attachments/assets/7ddd6683-e88c-48ea-921e-a4b8b91190ce" />
<img width="571" height="119" alt="Screenshot From 2026-07-31 17-25-53" src="https://github.com/user-attachments/assets/c59a9691-5753-4bc8-927b-4fd2798cc855" /> </br>  

### '/boot' Directory  
After the Power On Self Test (POST) is complete, the configuration utility (in my case UEFI) looks for the EFI system partition (ESP) which contains the **bootloader**. The bootloader's function is to load two components 1) the Kernel 2) initramfs into memory. These two components the **Kernel**(the file named vmlinuz-5.x.y or vmlinuz-6.x.y) and **initramfs**(initial RAM filesystem) are part of the **/boot** directory. The bootloader is mounted at **/boot/efi** in UEFI-based systems. In addition to these, the **/boot** directory consists of the files **config**, and **System.map**. The RHEL-based Rocky Linux system uses the term **initramfs** whereas the Debian-based Ubuntu Server system names it **initrd**(initial RAM disk). </br>  
<img width="1500" height="403" alt="Screenshot From 2026-07-31 18-44-52" src="https://github.com/user-attachments/assets/44bc9eba-121e-4d43-ae41-333fb7edb4a1" />  
<img width="980" height="277" alt="Screenshot From 2026-07-31 18-45-52" src="https://github.com/user-attachments/assets/e68c8cd0-1988-4b28-8e99-952013a0c1c6" />  </br>  

### '/dev' Directory
This directory consists of the "device files" also known as "device nodes" that are connected to the system. The CPU, Physical Memory (RAM), Storage devices, Graphics card, Parallel ports - to name a few - are represented as special files in this directory. </br>  
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
The **/home** directory is conventionally the place where users' personal data is stored. One exception is that the **root** user has a separate Home Directory which is **/root**. </br>  
<img width="583" height="624" alt="Screenshot From 2026-08-02 18-21-47" src="https://github.com/user-attachments/assets/b765b62d-27ac-40b5-b530-59c0594cc96a" /> </br>  
In the Minimal Install version I don't find the directories that are found in the GUI version above. </br>  
<img width="586" height="312" alt="Screenshot From 2026-08-02 18-35-59" src="https://github.com/user-attachments/assets/71d7a7a7-5e37-47e9-893b-5ec22857fed0" /> </br>  
In the command prompt, typing **cd** or **cd ~** takes the user to the respective home directory. Typing **echo $HOME** displays the value of the variable - which is the user's home directory: </br>  
<img width="474" height="310" alt="Screenshot From 2026-08-02 18-39-24" src="https://github.com/user-attachments/assets/482d58a0-0f21-4131-aab0-5611ce937425" /> </br>  

### '/lib' and '/lib64' Directories  
These directories contain the shared libraries for the executable programs in **/bin** and **/sbin** and Kernel modules. While **/lib** is 32-bit, **/lib64** contains 64-bit shared libraries.
**/lib** and **/lib64** are symbolically linked to **/usr/lib** and **/usr/lib64**. </br>  
<img width="657" height="142" alt="Screenshot From 2026-08-02 20-24-11" src="https://github.com/user-attachments/assets/07d841e4-dd32-4818-9a6e-934c301cb76e" /> </br>  

### '/media' and '/mnt' Directories  
The **/mnt** directory is where a SysAdmin would manually mount a filesystem - a disk or an ISO image or an Network share - for temporary access.  
The **/media** directory is where the system would conventionally **auto-mount** a USB flash drive, a CD/DVD drive, or a SD card. However, currently USB flash drives are mounted to **/run/media/userid/devicelabel**.  
I have tried to connect a USB Flash Drive to two virtual machines - one with a GNOME Graphical Desktop environment and the other which is a minimal install - to check the behaviour.  
The Virtual Machine with the Desktop Environment **auto-mounts** the flash drive at **/run/media/$USER/<device-label>, as shown in the image below: </br>  
<img width="1542" height="357" alt="Screenshot From 2026-08-05 19-45-53" src="https://github.com/user-attachments/assets/b0eb118e-15b9-4743-9b27-792b1082ff4b" /> </br>  
<img width="839" height="311" alt="Screenshot From 2026-08-05 20-08-03" src="https://github.com/user-attachments/assets/ad967267-058a-454b-99b9-3aa3dcc0c4b4" /> </br>  

On further research I understand that a **daemon**("service" in the Windows world") named **udisks2** is responsible for auto-mounting flash drives. This information can be found using the **mount** command and searching for the device's label. This can be seen on the image above. </br>  

Further research about **udisks2** reveals that this daemon may NOT be running in "Minimal Install" instances. Hence to check this, I executed the **systemctl status udisks2** command in the other Virtual Machine. As shown in the image below, the **udisks2** daemon is not running in the Minimal Install Virtual Machine. This means that flash drives will not be auto-mounted in this system. Hence a SysAdmin would have to **manually** mount the drive to the conventional location - which is the **/mnt** directory. </br>  
<img width="866" height="131" alt="Screenshot From 2026-08-05 20-09-12" src="https://github.com/user-attachments/assets/c4baf810-5f0d-420a-9b06-01b2b5d90a86" /> </br>  

Connecting the flash drive to the "Minimal Install" Virtual Machine does nothing. As can be seen in the image below, the device appears in the list of **block devices** but has NOT been mounted. </br>  <img width="1075" height="254" alt="Screenshot From 2026-08-05 20-14-18" src="https://github.com/user-attachments/assets/42ee7715-88eb-409e-a289-ccf831f5b163" /> </br>  

The simple usage of the **mount** command is: **mount <what-device-to-mount> <where-to-mount-it>**. In my case, I would mount the device **/dev/sdb1** to **/media/myusb/** </br>  
1. This involves creating a **Mount Point** - the **myusb** directory under **/media** will be the **Mount Point**. Creating the **Mount Point** requires elevated privileges. </br>
2. The **mount** command also requires elevated privileges. </br>
The image below shows the operations: </br>  
<img width="1123" height="373" alt="Screenshot From 2026-08-05 20-21-43" src="https://github.com/user-attachments/assets/7417f6ff-81f2-4b83-875b-322412cf4aa5" />  
The command to **Unmount** a device is **umount <Mount-Point>**. Hence, executing the command **sudo umount /media/myusb** unmounts the device. Image below: </br>  
<img width="441" height="115" alt="Screenshot From 2026-08-05 20-35-44" src="https://github.com/user-attachments/assets/cc41f55a-3821-41ce-8d6e-6f7de2a2f415" /> </br>

### '/opt' Directory  
This directory consists of optional and add-on software packages. Software packages that did NOT come with the distribution and those that are NOT part of the system's software manager repositories are stored here. Sub-directories of **/opt** are named after the **vendor** or **package name** and all the files that are required by the software package **MUST** be bundled and stored in the package's directory. For example, my host computer has the Brave Browser and Mega Sync software applications installed; these applications were NOT part of the Linux Distribution and separate software package repositories were added. </br>  
It can seen in the image below that under **/opt** I have two directories each representing the **Vendor/Package Name** and if more than one flavour of the Package from the same Vendor has been installed, then there are sub-directories with distinct Package Names. </br>  
<img width="564" height="295" alt="Screenshot From 2026-08-05 22-57-01" src="https://github.com/user-attachments/assets/2f95651b-c0f1-4fa6-87a5-e94900849305" /> </br>  

### '/proc' Directory  
The **/proc** directory is a pseudo-filesystem: the contents of this directory are dynamically generated and stored in RAM and not on disk. On a non-running system this directory is empty. Other pseudo-filesystems are **/dev**, **/run**, and **/sys**. In the **/proc** directory, each running process has a directory named after the process' **PID**(Process ID). As shown in the image below, all running processes are listed and each process contains all related information within its directory. </br>  
<img width="1567" height="292" alt="Screenshot From 2026-08-06 19-02-05" src="https://github.com/user-attachments/assets/31572c5e-c49e-4105-9ef7-61f0d2cc2c73" /> </br>  
<img width="819" height="617" alt="Screenshot From 2026-08-06 18-34-25" src="https://github.com/user-attachments/assets/cf1330b8-7188-4fd3-9da1-5c378182d7ea" /> </br>  
In addition to the process directories, the **/proc** directory contains important virtual files/directory such as:  
**/proc/cpuinfo**  
**/proc/filesystems**  
**/proc/meminfo**  
**/proc/mounts**  
**/proc/partitions**  
**/proc/sys/** </br>  
