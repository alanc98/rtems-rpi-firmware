This is the latest firmware that I could get working on the Raspberry Pi with RTEMS (5 branch)

I have tested it on all of the single core models and the Raspberry Pi 2 (first rev)

It is the git tag 1.20200601
All tags in the repository after this do not successfully boot the RTEMS images.

The RTEMS images are "kernel.img" which is the ticker.exe example for the Raspberrypi BSP
and "kernel7.img" which is the ticker.exe example for the RaspberryPi2 BSP.

The firmware will automatically choose kernel.img or kernel7.img depending on the model being booted.

Note that this is just the "boot" subdirectory of the RPI firmware repo.
In order to boot RTEMS on a Pi, just format a MicroSD card with the FAT file system (single volume/partition) and copy the contents of this repo to the card.
To boot a new RTEMS image, just create a binary executable:
arm-rtems5-objcopy -Obinary unlimited.exe kernel.img

You can also change the config.txt file to specify the kernel.img file:
kernel=unlimited.img


