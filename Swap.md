# SWAP

--- 
#swap #filesystem #partitions 

---

## Swap Space

Swap space is an area of a disk wich can be used by the kernel memory managment subsystem. Swap supplements the RAM by holding inactive pages of the memory.
RAM + SWAP = Virtual Memory

The way it works is the the kernel will comb RAM for idle pages and when found, it will write the idle pages to the swap and reassigns the pages to a new process. When a page that is in swap is needed, the kernel will look for an idle page in the RAM and assign it to the needed page. And so on.

## Create a swap space 

There is three things you need to do in order to create a swap space.

1. Create a partition

2. Set the type of partition to **82 Linux Swap** 

3. Format a swap signature on the device

You can create a partition with [[fdisk]] or [[gdisk]]
	
#### How to crate a swap

If you are using fdisk, run **fdisk /dev/disk_name**. At the command prompt, we will make a new patition for swap, so we will issue the **n** command. At the partition type prompt, we want a primary partition so issue the **p** command and give the parititon the first parititon value of **1**. At the first sector prompt we will press **Enter**. At the last sector prompt we will give the desired size or sector number. Then we will issue the command **p**.
We will assing a partition type by giving the command **t**. We will use the hex code 82 for the type wich is **'linux swap / Solaris'**. Then give the command **p** 

#### Format the device 

We will be using the command **mkswap** wich applies a swap signature to the device. Give this command in the terminal:

```bash
mkswap /dev/disk_name
```

The command **swapon** will activate formated swap spaces. Also **swapon -a** will acitvate all swap spaces  listed  in the **/etc/fstab** 


