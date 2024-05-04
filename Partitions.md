# Partitions 
---
#partitions #fdisk #gdisk #MBR #GPT 

---

### Partiion schemes

There are two types of partition schemes, MBR and GPT. 

### Fdisk

Fdisk is used to configure [[MBR]] partitioning scheme. To start partitining a drive, as root run the command 

```bash
fdisk /dev/disk_name
```

> In order to know what is the name of the device you want to partition, you can run the **lsblk** command, to know what type of file system the device is partitioned as, run the **df -Th** command.

##### Create MBR disk partition 

In the command prompt, to give a new partition to the device type **n** . The prompt will ask if is going to be a primary or extended partition, P for primary and E for extended. Then give the value of the first sector, the default is **2048** . Then you will give the value of the last sector, you can do this is three ways, you can give the value of the end of the sector, you can give the value as the size of the partition in sectors **+52448** or you can give the size of the partition in **size+(K,M,G)** for example **+512M** which is 512 megabytes the size fo partition. 

> Remember that for the MBR scheme, as a default, there is only 4 primary partitions, if you need more partitions, you can do 3 primary and one extended, the extended works as a container that can fit more primary partitions. 

To define the partition type, give the **t**  command and give the type code for the type of partition you want it to be, if you need to see the list of type codes, type the **L** command. When given the type code, if everything is like you want it, run the **w** command to write and exit fdisk. 

>Remember that if there is an error in the partition, before you give the **w** command, exit without writing to the partition.

When in the terminal, force a re-read of the partition table

```bash
sudo partprobe /dev/disk_name
```

##### Delete MBR disk partition

Start fdisk with the name of the device as an argument

```bash
sudo fdisk /dev/disk_name
```

When fdisk starts, to see the partition table, give the **p** command. to delete the partition table, give the **d** command, and because we only have one partition table, it will delete as a default the only partition we have, then if you are good with the changes, type **w** to write the changes and exit.

In terminal, fore the re-read of the partition with the probe command.

```bash
sudo partprobe /dev/disk_name
```

### Gdisk

Gdisk is the utility that we use to create and manage GPT partition tables. To run gdisk type the command

```bash
sudo gdisk /dev/disk_name
```

##### Creating partition tables with gdisk

In the gdisk interface,  to create a new partition table, type the **n** command. It will ask for the first partition, it goes either two ways, the default is the location **2048** or you can give it a value in K,M,G,P. so if you give it a +512M, then it will be 512 megabytes from the defualt. (Need more info about the - and + on the end of the partition) Define patition type by giving the hex code, if you need to see the list of codes give the **L** command. If you are happy with the configuration, the write by giving the **w** command. Confirm the write command and exit. 
Remember to always force a re-read of the partition

```bash
sudo partprobe /dev/disk_name
```

##### Deleting partition tables with gdisk

When entering the gdisk interface, to see the list of partitions give the **p** command. To delete a partition give the **d** command, and choose the partition. Then if happy with config, save changes by giving the **w** command to write. Confirm the save and exit.

Remember to partprobe the partition.