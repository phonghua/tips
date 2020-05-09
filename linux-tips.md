##Step 0.1: Check remaining disks available

```
$ df -h
Filesystem Size Used Avail Use% Mounted on
udev 77G 0 77G 0% /dev
tmpfs 16G 9.1M 16G 1% /run
/dev/sda1 970G 552G 418G 57% /
tmpfs 77G 228K 77G 1% /dev/shm
tmpfs 5.0M 0 5.0M 0% /run/lock
tmpfs 77G 0 77G 0% /sys/fs/cgroup

##Step 0.2: Check partition

```
$ sudo lsblk
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sda 8:0 0 1000G 0 disk 
└─sda1 8:1 0 1000G 0 part /
