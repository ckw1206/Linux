### Instal local rpms
```
yum --nogpgcheck localinstall packagename.rpm
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

