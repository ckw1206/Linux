### Enalbe local repos
```
createrepo -v /var/www/html/<repo-id>
yum clean all
```
#### Create a new file in /etc/yum.repos.d/<*file*.repo>
```
[local_repo]
name=RHEL7.9-extra-repo
metadata_expire=-1
gpgcheck=0

enabled=1
baseurl=file:///local/repo/path
```

### Instal local rpms
```
yum --nogpgcheck localinstall packagename.rpm
```

### Leapp anwserfile
```
vi /var/log/leapp/answerfile
```

### Remove module if pre-upgrade failed: Detected loaded kernel drivers which have been removed in RHEL 8. Upgrade cannot proceed.
```
rmmod <module name>
```

### Manully add 'unsupported_driver_names.json' for Leapp utility metadata in-place offline upgrades
```
tar -xzf leapp-data18.tar.gz -C /etc/leapp/files && rm leapp-data18.tar.gz
```

https://access.redhat.com/node/3664871/5121/0/23153919

### Remove OpenSSH ciphers
```
/etc/ssh/ssh_config
```

### Replace pam_tally2 with pam_faillock
```
auth        required      pam_env.so
auth        required      pam_tally2.so deny=4                                              # Delete this line
auth        required      pam_faillock.so preauth silent audit deny=4 unlock_time=1200      # Insert this line
auth        sufficient    pam_unix.so nullok try_first_pass
auth        requisite     pam_succeed_if.so uid >= 1000 quiet_success
auth        required      pam_faillock.so authfail audit deny=4 unlock_time=1200            # Insert this line
auth        required      pam_deny.so

account     required      pam_faillock.so                                                   # Insert this line
account     required      pam_unix.so
account     required      pam_tally2.so                                                     # Delete this line
account     sufficient    pam_localuser.so
account     sufficient    pam_succeed_if.so uid < 1000 quiet
account     required      pam_permit.so
```

### Disable NFS
```
#systemctl list-units | grep -i nfs

nfs-idmapd.service                                 loaded active running   NFSv4 ID-name mapping service  
nfs-mountd.service                                 loaded active running   NFS Mount Daemon
nfs-server.service                                 loaded active exited    NFS server and services


#systemctl stop nfs-idmapd.service
#systemctl stop nfs-mountd.service
#systemctl stop nfs-server.service
```
