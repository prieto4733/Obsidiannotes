# NFS 

---
#nfs #tcp #udp #firewall

---

### What is NFS

[[NFS]] (Network File System) it is a native file system for linux and unix base systems. 
It uses the TCP protocol in v.4 and in older versions it uses [[TCP]] and [[UDP]].
It supports native linux [[file permissions]] and file system features.
NFS export shares and NFS clients mount or unmount exported shares (directories).
The local mount point must exist. 
There are three ways to mount shares 
 1. Manually mounting an NFS share using the mount command
 2. Automatically mounting NFS share at boot time using /etc/fstab
 3. Mounting on demand using proccess called automounting


> When giving permission to a NFS is like giving permission for users to rwx a file.


To get nfs you need to download two packages: 

1. nfs-utils
2. libnfsidmap

When downloaded you need to enable two services and start a few:

``` bash
systemctl enable rpcbind
systemctl enable nfs-server

systemctl start rpcbind, nfs-server, rpc-statd, nfs-idmapd

```
> Remember that the start command is done one by one.

#### Setting up [[Firewall]]
Remember that you will let NFS run as a service through the firewall by giving this command:

``` bash
firewall-cmd --permanent --add-service=nfs

systemctl reload firewalld
```
This will let the NFS service through the firewall.

#### Setting up Server Side 
For simplicity purpose, the share will be made in the /root directory of the server side. 

We will make a directory called toshare

```bash
mkdir /toshare
```

Then we will give the directory user permissions to read and write in order for the client to be able to read and write the files in this directory.

```bash 
chmod 777 /toshare
```

> Translated this will write -rwxrwxrwx /toshare

Then we will configure the exports file and add the share, the exports file will be located in /etc/exports 

```bash
vi /etc/exports
```

Add the line with the share, add the options, write and quit

```bash
/toshare *(rw,sync)
```

Reload the NFS server 

```bash
systemctl reload nfs-server
```

Now you can add files to the /toshare directory and be able to share with any client that connects. 

#### Setting up the clients side

Make a directory in /mnt and we will direct the share to that directory 

> Remember to use the mkdir for this step, dont use the touch command

```bash
mkdir /mnt/nfs1
```

Now mount the nfs directory

```bash
mount -t nfs <serverIpAddress>:/toshare /mnt/nfs1
```

Now cd to the nfs1 directory and issue the ls command to make sure that you have accomplished the connection.

> If you issue a read only to the nfs directory, this will give the permission deny to the client and wont be able to access the files.
