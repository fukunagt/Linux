# Red Hat Enterpirse Linux

## Change Timestamp Format of rsyslog
1. Open /etc/rsyslog.conf with a text editor.
1. The default format is RSYSLOG_TraditionalFileFormat.
   ```
   # Use default timestamp format
   module(load="builtin:omfile" Template="RSYSLOG_TraditionalFileFormat")
   ```
   ```
   Oct 24 17:51:38 rhel8-22 rsyslogd[942]: imjournal: journal files changed, reloading...  [v8.1911.0-7.el8 try https://www.rsyslog.com/e/0 ]
   ```
1. Change template as below.
   ```
   # Use default timestamp format
   module(load="builtin:omfile" Template="RSYSLOG_FileFormat")
   ```
   ```
   2022-10-25T07:43:03.043202+09:00 rhel8-22 rsyslogd[1027911]: imjournal: journal files changed, reloading...  [v8.1911.0-7.el8 try https://www.rsyslog.com/e/0 ]
   ```

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