# SElinux

---

#SElinux 

---

### SElinux modes

SElinux has modes that have different affect in the system. There is three modes in linux 

1. Enforce 
2. Permissive
3. Dissable

##### Enforce Mode

In this mode, the rules that are set are enforce and users and services that are not in the rule will be restricted. It denies access to the server if any attempts to read files with the tmp_t type content. Also in this mode it protects an logs al the insidents 


##### Permissive

In this mode, it allows access to the server, and it does not denies access. It still logs all the insidents that would be denied. This mode is used to troubleshoot SElinux. When changed to this mode it does not require reboot from the system.


##### Dissable

This modes completly dissables SElinux. A system reboot is needed to go from Disable to any of the other modes.

