# Commands

## LVM
- In advance, create a partition and change partition type to LVM using fdisk or partd.
- The following commands are to create LVs for Mirror Disk Resource of EXPRESSCLUSTER.
  1. Create PV.
     ```sh
     pvcreate /dev/sdb1
     ```
  1. Create VG with a name (e.g., md1).
     ```sh
     vgcreate md1 /dev/sdb1
     ```
  1. Create LV for Cluster Partition.
     ```sh
     lvcreate -L 1G -n cp md1
     ```
  1. Create LV for Data Partition.
     ```sh
     lvcreate -l100%FREE -n dp md1
     ```

## tcpdump

