# FIle System

---
#filesystem #xfs #ext4 #btrfs #mount

	---

### Creating file system

To create a filesystem in a device give this command

```bash
sudo mkfs -t type_of_fs /dev/disk_name
```

if there was a table writen in the past on the drive, you may need to force the command on the drive by 

```bash
sudo mkfs -t type_of_fs -f /dev/disk_name
```

If you dont specify what type of filesystem with the **-t** flag, it will default to the **ext2** file system which most of the type is no the desireable.

### Mounting the file system

##### Manual mounting

The manual mounting is done but will not be permanent until you add the configuration to the **/etc/fstab** . You can use the **mount** command mount to mount point

```bash
mount /dev/disk_name /mnt
```

To confirm that the device is mounted as desired, issue this command. The output of this command will give the information of a succesful mounted device. This wll also give you the type of file system that the device has intalled for example xfs, ext4, btrfs ext. 

```bash
mount | grep disk_name
```

##### Permisive mount

To have a device permanently mounted, we need to add the configuration to the **/etc/fstab** config file.

>**/etc/fstab** is a white space-delimited (having fixed bounderies or limits) file with six  fields per line.


**The six spaces** 
1) The first space is the device that is going to be used, it is defined by the **UUID** , it is better to use the uuid because in a big envirement, the definers may change. To find out what is the UUID of the device used, use the **blkid** command.

```bash
blkid /dev/disk_name
```
This will give the UUID and type of file system. 

2) The second space in the fstab config file mount point. The mount point can be a directory but this directory or mount point should already exist. If not create it with [[mkdir]].
 
3) The third space contains the file system type that has been applied to the block device.
 
4) The fourth space is where the list of flags or options that will be applied to the device when mounted to customize the behaviour. This field is required. There is a list of common flags or **Defaults**. Other options are listed in the mount **man** page.
 
5) The last two spaces are the **dump** flag and the **fsck** order. The dump flag is used with the [[dump]] command to make a backup of the content of the device. The fsck order determines if fsck is runned at boot time. In the event that the file system was not unmounted cleanly, the fsck order indicates the order in which file systems should have fsck run on them if multiple file systems are required to be checked.

 example of a line in the fstab:

```bash
UUID-123b123b-123b-123b-123b-123b123b123b  /mnt   xfs   defaults  1  2

```

> REMEMBER, having an incorrect entry in **/etc/fstab*** may render the machine unbootable. To avoid this problem, the admin should first **unmount** the new file system. Then verify the fstab by running **mount -a** which reads the fstab to mount the file system back into place. If running **mount -a** returns an error, fstab should be corrected before rebooting the machine. 

To unmount a file system run the umount command:

```bash
umount /dev/disk_name
```

To verify that a device is mounted on a specific mountpoint: 

```bash
mount | grep -w /mountpoint
```
