### Download packages and their dependencies from Red Hat customer portal at below link :

[Red Hat Customer Portal](https://access.redhat.com/downloads/content/69/ver=/rhel---6/6.10/x86_64/packages)

### Below is the list of packages and their dependencies :

```
preupgrade-assistant                              
preupgrade-assistant-el6toel7                        
preupgrade-assistant-el6toel7-data                 
redhat-upgrade-tool

fakeroot                                            
fakeroot-libs                                         
openscap
openscap-engine-sce
openscap-scanner
openscap-utils
pykickstart
redhat-rpm-config
rpm-build
rpmdevtools
```

Create a folder /tmp/packages on offline system, copy all the rpms to /tmp/packages. Install the packages.
```
# mkdir /tmp/packages
# cd /tmp/packages
# yum localinstall *
```
