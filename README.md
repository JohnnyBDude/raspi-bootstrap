# raspi-bootstrap

This is just a few tips on how to get my Raspberry Pi u and running

## Download a raspbian image

Google it yourself

## Write the raspbian image to SD Card

8 GB SD card should be more than enough.

Tell what device you should write to by issuing
ll 
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

- Connect the ethernet cable, raspberry should connect to internet automatically
- Tell your IP address by `ifconfig -a eth0` 
