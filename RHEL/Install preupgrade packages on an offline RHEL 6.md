### Download packages and dependencies from below link :

[Red Hat Customer Portal](https://access.redhat.com/downloads/content/69/ver=/rhel---6/6.10/x86_64/packages)

### Below is the list of packages and dependencies :

```
python-argparse
yum

rpm
rpm-build
rpmdevtools

openscap
openscap-utils
openscap-engine-sce
openscap-scanner

preupgrade-assistant                              
preupgrade-assistant-el6toel7                        
preupgrade-assistant-el6toel7-data                 
redhat-upgrade-tool

fakeroot                                            
fakeroot-libs                                         
pykickstart
redhat-rpm-config
rpm-build
rpmdevtools
```

Create a folder /tmp/packages on offline system, copy all the rpms to /tmp/packages. Install the packages.
```
# mkdir /tmp/packages
# cd /tmp/packages
# yum localinstall -y *
```
