### Linux Logical Volume Manager (LVM)

Install LVM on RHEL
```
sudo yum install lvm2
```
</br>

Create partitions
Check current disk infomation by using `fidsk`
```
fdisk -l
```
</br>

Create partition on disk by using `cfdisk`
```
cfdisk /dev/sdb
```
</br>

Create physical volumes on new partitions
```
pvcreate /dev/sdb1
pvcreate /dev/sdb2
...
```
</br>

Display physical volume infomation
```
pvdisplay
```
</br>

Create virtual groups
```
vgcreate <vg_name> /dev/sdb1 /dev/sdb2
```
</br>

Display virtual group infomation
```
vgdisplay
```
</br>

Create logical volume
```
lvcreate -L <size-mb> -n <volume_name> <vg_name>
```
</br>

Create a filesystem on logical volumes
```
mkfs.ext4 -m 0 <logical_volume_path>
```
</br>

Edit fstab to automatically mount partitions
```
nano /etc/fstab
```
</br>

Create mount point and mount partition
```
mkdir <mount-point>
mount -a
```
</br>

Extend a logical volume
```
lvextend -L +<size-mb> <logical_volume_path>
resize2fs <logical_volume_path>
```
</br>

Remove a logical volume
```
lvremove <logical_volume_path>
```
</br>
