**spinmedown** – Simple script for timed spindown of disk drives


### Summary ###

`spinmedown` is a script that can be called repeatedly to check whether a disk
drive has been accessed in the meantime, and to spin it down if it has not.
This is useful for USB drives that do not enter standby/power-saving
mode automatically.

The script should be able to run fine on most Unix/Linux shells and requires
**hdparm**[[1]] as its only dependency. It also requires sysfs, and therefore
an operating system based on the Linux kernel.


### Installation ###

Copy the `spinmedown` script to somewhere in your path, like `~/bin`.
Symlinking works too.


### Usage ###

    spinmedown fsuuid

`fsuuid` is a valid filesystem UUID. Use the `blkid` command for a list of
active mounts. Then call the script in a regular interval corresponding to the
desired disk drive timeout.


### Crontab example ###

    # Spin down USB HD if idle for 30 minutes
    */30 * * * * root spinmedown 01234567-89ab-cdef-0123-456789abcdef

If using `/etc/cron.d`, make sure to set up the PATH correctly in the file, and
that it is chowned to root.

[1]: https://sourceforge.net/projects/hdparm/
