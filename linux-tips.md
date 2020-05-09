## Step 0.1: Check remaining disks available

```
$ df -h
Filesystem Size Used Avail Use% Mounted on
udev 77G 0 77G 0% /dev
tmpfs 16G 9.1M 16G 1% /run
/dev/sda1 970G 552G 418G 57% /
tmpfs 77G 228K 77G 1% /dev/shm
tmpfs 5.0M 0 5.0M 0% /run/lock
tmpfs 77G 0 77G 0% /sys/fs/cgroup
```

## Step 0.2: Check partition

```
$ sudo lsblk
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sda 8:0 0 1000G 0 disk 
└─sda1 8:1 0 1000G 0 part /
```

## Step 1: Increase disk size

In your VM . instance setting, click on the disk (either boot disk or additional disk), then increase the capacity by the amount you need.

## Step 2: Grow the partition
```
$ sudo growpart /dev/sda 1
CHANGED: partition=1 start=2048 old: size=419428319 end=419430367 new: size=2097149919
,end=2097151967
```

## Step 3: Resize file system
```
$ sudo resize2fs /dev/sda1
resize2fs 1.42.13 (17-May-2015)
Filesystem at /dev/sda1 is mounted on /; on-line resizing required
old_desc_blocks = 13, new_desc_blocks = 63
The filesystem on /dev/sda1 is now 262143739 (4k) blocks long.
```
