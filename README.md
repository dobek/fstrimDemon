fstrimDemon
===========

Very lightweight demon executing fstrim every few hours.

MOTIVATION:
Usually fstrim is run from cron but cron can execute command only at particular time. If you turn off your computer you can miss it. This demon solves this problem running fstrim in the loop. It gives also very low priority to this task in order not to intrude your main activities.

-----------------------------------------

INSTALLATION

Run as root:
# ./install.sh

To start demon:
# /etc/init.d/fstrimDemon start

To stop demon:
# /etc/init.d/fstrimDemon start

To uninstall run as root:
# ./uninstall.sh

Files which are not removed during uninstallation:
 - /etc/conf.d/fstrimDemon
 - /var/log/fstrimDemon.log


-----------------------------------------

CONFIGURATION

Default config file: /etc/conf.d/fstrimDemon

# Directory for which fstrim will be run
TRIM_DIR="/"

# Time to wait after demon start to perform first fstrim
# e.g. "30m" - 30 minutes. See man sleep.
SLEEP_AT_START="3h"

# Time to sleep between next repetition of fstrim
# e.g. "5d" - 5 days. See man sleep.
SLEEP_BEFORE_REPEAT="12h"

# integer [-20 .. 19 ] default 0
# change the priority of the server -20 (high) to 19 (low)
# see nice(1) for description
NICE="19"

# See start-stop-daemon(8) for possible settings
# Modifies the IO scheduling priority of the daemon.  Class
# can be 0 for none, 1 for real time, 2 for best effort and 3
# for idle.  Data can be from 0 to 7 inclusive.
IONICE="3"

# Here Demon's process id will be stored
PID="/var/run/fstrimDemon.pid"

# Here Demon logs
LOG="/var/log/fstrimeDemon.log"

# The main demon script i.e. fstrim-sleep loop
DEMON="/usr/sbin/fstrimDemon.sh"


-----------------------------------------

LOG

See /var/log/fstrimDemon.log


-----------------------------------------

PROJECT HOME

https://github.com/dobek/fstrimDemon
