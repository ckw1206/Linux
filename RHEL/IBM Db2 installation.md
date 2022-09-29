### Installation prerequisites
  - Disable SELinux
  
  Change SELINUX=enforcing to SELINUX=disabled
  ```
  nano /etc/selinux/config
  ```
  
  - Install required packages
  ```
  yum install -y \
  libibverbs \
  librdmacm \
  rdma-core \
  dapl \
  ibacm \
  ibutils \
  libstdc++ \
  libstdc++.so.6 \
  glibc \
  gcc-c++ \
  gcc \
  kernel \
  kernel-devel \
  kernel-headers \
  linux-firmware \
  ntp \
  ntpdate \
  sg3_utils \
  sg3_utils-libs \
  binutils \
  binutils-devel \
  m4 \
  openssh \
  cpp \
  ksh \
  libgcc \
  file \
  libgomp \
  make \
  patch \
  perl-Sys-Syslog \
  mksh \
  psmisc
  ```
  
  Reference: https://www.ibm.com/docs/en/db2/11.5?topic=linux-installation-prerequisites-db2-purescale-feature-intel

</br>
  
### Install IBM Db2

pre-install check
```
./db2prereqcheck
```

install Db2 
```
./db2_install
```
