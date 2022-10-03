Mount the RHEL 6 installation ISO somewhere like /media/rhel6dvd, e.g.:

```
mount -o loop Red_Hat_Enterprise_Linux_6.10_DVD.iso /media/rhel6dvd
```
If you use DVD media, you can mount like below.

```
mkdir -p  /mnt/disc
mount /dev/sr0  /mnt/disc
```
Copy the media.repo file from the root of the mounted ISO to /etc/yum.repos.d/ and set the permissions to something sane, e.g.:

```
cp /media/rhel6dvd/media.repo /etc/yum.repos.d/rhel6dvd.repo
chmod 644 /etc/yum.repos.d/rhel6dvd.repo
```

Edit the new repo file, changing the gpgcheck=0 setting to 1 and adding the following 3 lines (make sure to replace "Server" with "Client" or "Workstation", depending on the type of RHEL DVD in use):
```
enabled=1
baseurl=file:///media/rhel6dvd/Server
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
```

In the end, the new repo file could look like the following (though the mediaid will be different depending on the version of RHEL):

```
[dvd-Server]
name=DVD for Red Hat Enterprise Linux 6.6 Server
mediaid=1359576196.686790
metadata_expire=-1
gpgcheck=1
cost=500
enabled=1
baseurl=file:///media/rhel6dvd/Server
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
```

As a final step, it might be a good idea to run the command yum clean all once

To configure access to the supplementary packages in the directories HighAvailability, LoadBalancer, ResilientStorage, and ScalableFileSystem, add additional repositories for them in the same file, e.g.:

```
[dvd-HighAvailability]
mediaid=1359576196.686790
name=DVD for RHEL6 - HighAvailability
baseurl=file:///media/rhel6dvd/HighAvailability
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
enabled=1
gpgcheck=1

[dvd-LoadBalancer]
mediaid=1359576196.686790
name=DVD for RHEL6 - LoadBalancer
baseurl=file:///media/rhel6dvd/LoadBalancer
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
enabled=1
gpgcheck=1

[dvd-ResilientStorage]
mediaid=1359576196.686790
name=DVD for RHEL6 - ResilientStorage
baseurl=file:///media/rhel6dvd/ResilientStorage
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
enabled=1
gpgcheck=1

[dvd-ScalableFileSystem]
mediaid=1359576196.686790
name=DVD for RHEL6 - ScalableFileSystem
baseurl=file:///media/rhel6dvd/ScalableFileSystem
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
enabled=1
gpgcheck=1
```
