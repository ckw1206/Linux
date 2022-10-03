Mount the RHEL 6 installation ISO somewhere like /media/rhel6dvd, e.g.:
```
mount -o loop Red_Hat_Enterprise_Linux_6.10_DVD.iso /media/rhel6
```

Copy the media.repo file from the root of the mounted ISO to /etc/yum.repos.d/ and set the permissions to something sane, e.g.:
```
cp /media/rhel6/media.repo /etc/yum.repos.d/rhel6.repo
chmod 644 /etc/yum.repos.d/rhel6.repo
```

Edit the new repo file, adg the following 2 lines:
```
enabled=1
baseurl=file:///media/rhel6/Server
```
