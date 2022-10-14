# Red Hat Enterpirse Linux

## Enable DVD Repository
1. Move to the following directory.
   ```sh
   cd /etc/yum.repos.d/
   ```
1. Create dvd.repo and edit as below.
   ```
   [InstallMedia-BaseOS]
   name=Red Hat Enterprise Linux 8 - BaseOS
   metadata_expire=-1
   gpgcheck=1
   enabled=1
   baseurl=file:///media/BaseOS/
   gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release
   
   [InstallMedia-AppStream]
   name=Red Hat Enterprise Linux 8 - AppStream
   metadata_expire=-1
   gpgcheck=1
   enabled=1
   baseurl=file:///media/AppStream/
   gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release   
   ```
1. Mount DVD-ROM as below.
   ```sh
   mount /dev/sr0 /media
   ```
### Get Maximum Supported MTU Size for Interface
```sh
ip -d link list
```
- Amazon Web Services
  - Red Hat Enterprise Linux release 8.4
    ```
    2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9001 qdisc mq state UP mode DEFAULT group default qlen 1000
        link/ether 06:db:e6:c4:c3:6d brd ff:ff:ff:ff:ff:ff promiscuity 0 minmtu 128 maxmtu 9216 addrgenmode eui64 numtxqueues 8 numrxqueues 8 gso_max_size 65536 gso_max_segs 65535
    ```
    - maxmtu is 9216.