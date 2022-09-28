### Install LVM on RHEL
```
sudo yum install lvm2
```

### Create partitions
Check current disk details by `fidsk`.
```
fdisk -l
```

Create partition on disk using cfdisk utility.
```
cfdisk /dev/sdb
```

Create physical volumes on new partitions
```
pvcreate /dev/sdb1
pvcreate /dev/sdb2
...
```

Display physical volume infomation
```
pvdisplay
```

Create virtual groups
```
vgcreate <vg_name> /dev/sdb1 /dev/sdb2
```

Display virtual group infomation
```
vgdisplay
```

Create logical volume
```
lvcreate -L <size-mb> -n <volume_name> <vg_name>
```

Create a filesystem on logical volumes
```
mkfs.ext4 -m 0 <logical_volume_path>
```

Edit fstab to automatically mount partitions
```
nano /etc/fstab
```

Create mount point and mount partition
```
mkdir <mount-point>
mount -a
```

Extend a logical volume
```
lvextend -L +<size-mb> <logical_volume_path>
resize2fs <logical_volume_path>
```

Remove a logical volume
```
lvremove <logical_volume_path>
```
