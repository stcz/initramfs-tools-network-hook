# Requiments
The package `iproute2`.

# Installation
Copy the files to the corresponding folder on your system. Make sure the hooks and scripts are executable.

# Add VLAN Interface
Add the following Line to your `/etc/initramfs-tools/initramfs.conf` or in a file in `/etc/initramfs-tools/conf.d/*.conf` to enable the VLAN IDs 221 and 222 on eth0:
```
VLAN="eth0:221 eth0:222"
```
