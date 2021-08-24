**spinmedown** – Simple script for timed spindown of disk drives


### Summary ###

`spinmedown` spins down a disk drive if it has not been accessed since the last
time the script was called. This is especially useful with USB drives that do
not enter standby/power-saving mode by themselves.

The script should be able to run fine on most Unix/Linux shells and requires
**hdparm**[[1]] as its only dependency. It also requires sysfs and such,
Linux.


### Installation ###

Copy the `spinmedown` script to somewhere in your path, like `~/bin`.
Symlinking works too.


### Usage ###

    spinmedown fsuuid

`fsuuid` is a valid filesystem UUID. Use the `blkid` command for a list of
your mounts.


### Crontab example ###

    # Spin down USB HD if idle for 30 minutes
    */30 * * * * root spinmedown 01234567-89ab-cdef-0123-456789abcdef

If using cron.d, make sure to set up the PATH correctly in the file, and that
it is chowned to root.

[1]: https://sourceforge.net/projects/hdparm/
