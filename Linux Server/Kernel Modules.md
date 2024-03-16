loading
blacklisting

## For Blacklisting
file /etc/modules.d/blacklist.conf  --> add modules name here to blacklist

ex:  blacklist  module name



## For manually loading a module

file --> /etc/modules --> add the name of the module in the file



## Manipulating kernel modules

```bash
insmod
rmmod
modprobe
lsmod
depmod
```

```bash
modprobe <module name>
lsmod
```

