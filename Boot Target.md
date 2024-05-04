# Boot Target

---

#boot #systemctl #boottarget #rescuemode #emergencymode #systemd #grub2 

---

### Systemd Boot Target

[[Systemd]] has four different boot targets 

| Target | Purpose| 
| --------------------- | -------- |
| graphical.target | it supports multiple users, graphical and text-based logins |
| mutli-user.target | it supports multiple users, only text-based logins only |
| rescue.target | sulogin prompt, basic system initialization completed |
| emergency.target | sulogin prompt, initramfs pivot complete and system root mounted on / read-only |


... more hear

### Seleting Boot Target

##### Rescue Mode

To select boot target you need to run systemctl, you will see hear the command and its output:

```bash

systemctl set-default multi-user.target
rm ' /etc/systemd/sys t em/defaul t . target '
ln - s ' / u s r/lib/systemd/sy s t em/mult i - u s e r . t arget ' ' /etc/ systemd/system/
default . ta rget '
```

then you need to reboot the system

```bash

systemctl reboot

```

When the system reboots, interfere with [[GRub2]]  boot process pressing any key. Then choosing the first option press the e key to edit the boot process.  Then you will see the proccesses that the boot will take. There will be a process called "Linux", This process is the process before the selinux process kicks in the system. At the end of the line that starts with "Linux" add to the line:

> This is a [[systemd.target]] 

```bash 

systemd.unit=rescue.target
```

and press ctrl + x to choose the change. This will start the rescue mode in a multi-user mode, text only. When in rescue mode enter the root password to enter terminal and troubleshoot. If you need to come back to the graphical target:

```bash 
systemctl set-default graphical.target

```
and then press ctrl + d , this will start the graphical mode. 

> this way of appending to the boot process and adding the systemd.target 


##### Boot time vs logged in


> These targets can be choosen when the system is on or in boot time.  When using the systemctl command obiously you are logged in. But you can change that in the boot process by interrupting the boot and editing the first option and appending the desired boot target to the end of the line that starts with LINUX

To enter boot targets by appending to the boot process add the line:

```bash
systemd.unit=<desired>.target

```

but to enter emergency mode you need to break the process before the selinux starts its service. 

```bash

rd.break
```


##### Emergency mode

In boot time, editing the linux boot process, appending to the LINUX line at the end:

```bash

rd.break

```
this will not let selinux service start, it will start the root shell in a read-only
mount the root file system as a read and write

```bash
mount -oremount,rw /sysroot

```
change into chroot where /sysroot is treated as the root of the system file tree

```bash
chroot /sysroot

```

hear is where you can recover or resetting a lost root password.

to recover:

```bash
passwd root

```


to reset:

```root
echo <password> | passwd --stdin root

```

after recover and reseting a password, you need to touch a file to relabel for selinux

```bash
touch ./autorelabel

```

When it is finished relabeling, you can exit by typing exit twice.

