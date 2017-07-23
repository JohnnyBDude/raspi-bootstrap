# raspi-bootstrap

This is just a few simple steps to get my Raspberry Pi up and running

## Download a raspbian image

Google it yourself

## Write the raspbian image to SD Card

8 GB SD card should be more than enough.

Tell what device you should write to by issuing
 
```
ls -a /dev | grep sd
```

before and after inserting the card to your linuxbox.

Then write by using.

```
sudo dd if=/path/to/image/raspbian.img of=/dev/sdx status=progress bs=4M
```

where if is your path to the image and of is the memory card device.

## Boot Raspberry from the sdcard

- Put the SDCard into raspberry slot and power it up
- Connect it to a monitor using HDMI cable


## Set up networking

### Connect to the network

- Connect the ethernet cable, raspberry should connect to internet automatically

### Set up reserved static IP

To be able to connect using ssh at any time.

- Tell your IP address by `ifconfig -a eth0` 
- In browser go to modem administation - 192.168.0.1 address and eserve the current address for raspberry, so it has the same address every time it connects (Usually in the `Advanced >> DHCP` section of the administration interface)
- append the following lines in the `/etc/dhcpcd.conf` file

```
interface eth0

static ip_address=192.168.0.88
static routers=192.168.0.1
static domain_name_servers=192.168.0.1
```


### Set up ssh for remote access

### Basic ssh access

- Enable ssh access by starting the raspberry configuration tool with `raspi config`, then go to `Interfacing Options >> SSH >> Enable`
- While you are at it, you can also expand the filesystem so it fills the whole SD cards (in `Advanced Options`)
- Exit and reboot

ssh should be set up now, you can verify that by issuing on your laptop:

```
ssh pi@192.168.0.88
```

- you should now change the password using `passwd` command

### Setting up key based authentication

Append to `/etc/hosts` on your laptop 

```
192.168.0.88 raspberry
```

Now you should be all set up. You can unplug the display and other periferies 
and just hide the raspberry somewhere it can be connected to power and ethernet.
