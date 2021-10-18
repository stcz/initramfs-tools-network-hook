# initramfs-tools-network-hook
With this initramfs scripts it is possible to add a bond or vlan device to your initramfs, for example to unlock your encrypted disks via SSH (Dropbear) over a vlan or bond interface.

You can add this hooks to your initramfs-tools to get support for bond interfaces or vlan interfaces during boot. You can configure the hooks in your /etc/initramfs-tools/initramfs.conf. Tested successful under debian 10. It should also work on other debian based Distros like ubuntu.

The scripts should leave a empty networkconfiguration for the operating system.

# Requiments
The package `iproute2` for bonding support.
The package `vlan` for vlan support.

# Installation
Copy the files to the corresponding folder on your system. Make sure the hooks and scripts are executable.

# Add VLAN Interface
Add the following Line to your `/etc/initramfs-tools/initramfs.conf` to enable the VLAN IDs 221 and 222 on eth0:
```
VLAN="eth0:221 eth0:222"
```
# Add Bond Interface
Add the following Line to your `/etc/initramfs-tools/initramfs.conf` to enslave eth0 and eth1 to bond0 and eth2 and eth3 to bond1.
```
BOND="bond0:eth0,eth1 bond1:eth2,eth3"
```
Optionally, the hardware address for the interface can be specified (this can be useful for DHCP, note the format):
```
BOND="bond0:eth0,eth1:aa-bb-cc-dd-ee-ff"
```
With the following Line you can define the [Bonding Driver Options](https://wiki.linuxfoundation.org/networking/bonding#bonding_driver_options)
For example use:
```
BOND_MODE="mode=802.3ad miimon=100"
```
# Other Things you should know
Maybe you have to add the driver for your NIC to your initramfs via modprobe

You can set `DEVICE=bond0` in `/etc/initramfs-tools/initramfs.conf` to ensure the correct interface is used for DHCP.
