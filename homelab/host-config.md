# Host Computer Configuration:

Processor - Intel(R) Core(TM) i5-10500 CPU @ 3.10GHz
Memory - 64GB DDR4 RAM
Storage - 1TB m.2 NVME SSD
Network controller: Intel Corporation Wi-Fi 6E(802.11ax) AX210/AX1675
Operating System - Fedora Linux 43 (Workstation Edition)

## Storage Information:

`|`NAME`|`                                       |MAJ:MIN| |RM|   |SIZE| |RO| |TYPE|  |MOUNTPOINTS|
|zram0|                                      |251:0|    |0|     |8G|  |0| |disk|  |[SWAP]|
nvme1n1                                       259:0    0 931.5G  0 disk  
├─nvme1n1p1                                   259:1    0   1.9G  0 part  /boot
├─nvme1n1p2                                   259:2    0   954M  0 part  /boot/efi
├─nvme1n1p3                                   259:3    0  93.1G  0 part  /
├─nvme1n1p4                                   259:4    0 139.7G  0 part  
│ └─luks-                                     252:0    0 139.7G  0 crypt /home
├─nvme1n1p5                                   259:5    0  43.8G  0 part  /isos
└─nvme1n1p6                                   259:6    0 652.1G  0 part  /vms

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/nvme1n1p3 ext4       92G   11G   76G  13% /
/dev/nvme1n1p1 ext4      1.8G  425M  1.3G  25% /boot
/dev/nvme1n1p2 vfat      953M   20M  933M   3% /boot/efi
/dev/nvme1n1p5 xfs        44G   21G   23G  48% /isos
/dev/nvme1n1p6 xfs       652G   21G  632G   4% /vms
/dev/dm-0      ext4      137G  8.7G  121G   7% /home
