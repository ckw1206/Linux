# Upgrading from GRUB Legacy to GRUB 2
### Remove GRUB legacy
```
yum remove grub
```

### Intall GRUB 2
```
yum install grub2
```

### Create the /etc/default/grub file with follow lines
Replace the GRUB_CMDLINE_LINUX parameter by the list from fetching `/proc/cmdline`
```
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
GRUB_DEFAULT=saved
GRUB_DISABLE_SUBMENU=true
#GRUB_TERMINAL_OUTPUT="console"
GRUB_CMDLINE_LINUX="root=/dev/mapper/volgroup_lv_root rd.lvm.lv=vg_<volgroup>/<lvm_1> rd.lvm.lv=vg_<volgroup>/<lvm_1> custom_parameter_1 custom_parameter_2"
GRUB_DISABLE_RECOVERY="true"
GRUB_THEME="/boot/grub2/themes/system/theme.txt"
```

### Install GRUB 2 specifing the install device
```
grub2-install /dev/<DEVICE_NAME> --grub-setup=/bin/true
```

### Generate the GRUB 2 configuration file
```
grub2-mkconfig -o /boot/grub2/grub.cfg
```

### Testing GRUB 2 with GRUB Legacy
Adding the below section into /boot/grub/grub.conf
  - For systems with a separate /boot partition, use
  ```
  title GRUB 2 Test
    root (hd0,0)
    kernel /grub2/i386-pc/core.img
    boot
  ```
  
  - For systems without a separate /boot partition, use
  ```
  title GRUB 2 Test
	root (hd0,0)
	kernel /boot/grub2/i386-pc/core.img
	boot
  ```
  
### Replace the GRUB Legacy bootloader with the GRUB 2 bootloader
```
grub2-install /dev/sda
rm /boot/grub/grub.conf
reboot
```
