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