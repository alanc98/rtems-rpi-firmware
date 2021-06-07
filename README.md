This is the latest firmware that I could get working on the Raspberry Pi with RTEMS (5 branch)

With the current configuraton options, it seems to work on the following:
with the "raspberrypi" BSP:
- Raspberry Pi Model B (original)
- Raspberry Pi A+ (small form factor single core)
- Raspberry Pi Zero (non wireless)
- Raspberry Pi Zero W
With the "raspberrypi2"BSP:
- Raspberry Pi 2 (original rev)
- Raspberry Pi 3 B

These files are from the raspberrypi Firmware repo with git tag 1.20200601
I tried many tags of the firmware prior to this, and they also seem to work.
All tags in the repository after this do not successfully boot the RTEMS images.

The RTEMS images are "kernel.img" which is the ticker.exe example for the "raspberrypi" BSP
and "kernel7.img" which is the ticker.exe example for the "raspberrypi2" BSP.

The firmware will automatically choose kernel.img or kernel7.img depending on the model being booted.

Note that this is just the "boot" subdirectory of the RPI firmware repo.
In order to boot RTEMS on a Pi, just format a MicroSD card with the FAT file system (single volume/partition) and copy the contents of this repo to the card.
To boot a new RTEMS image, just create a binary executable:
arm-rtems5-objcopy -Obinary unlimited.exe kernel.img

You can also change the config.txt file to specify the kernel.img file:
kernel=unlimited.img

