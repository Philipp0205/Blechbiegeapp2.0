# Configure Trackpoint
Source: https://askubuntu.com/questions/37824/what-is-the-best-way-to-configure-a-thinkpads-trackpoint
Refs: [[!Linux]]
Tags: #thinkpad #trackpoint #linux #ubuntu

---
# Sensivity 
```bash
xinput --set-prop "TPPS/2 Elan TrackPoint" "libinput Accel Speed" 1.0
```

https://askubuntu.com/questions/1240460/how-to-get-the-trackpoint-sensitivity-right-on-my-thinkpad-x1-carbon-gen-6-with

---
## Step 0. Figure out the name of the device (as htorque suggested):

`find /sys/devices/platform/i8042 -name name | xargs grep -Fl TrackPoint | sed 's/\/input\/input[0-9]*\/name$//'`

For me it returns /sys/devices/platform/i8042/serio1 (without serio2).

## Step 1. Install sysfsutils:

`sudo apt-get install sysfsutils`

## Step 2. Edit the /etc/sysfs.conf. Add the following lines at the end.
([Original Post](https://silvae86.github.io/2019/05/17/tuning-ibm-lenovo-trackpoint/))

devices/platform/i8042/serio1/sensitivity = 215
devices/platform/i8042/serio1/rate = 280
devices/platform/i8042/serio1/speed = 150
devices/platform/i8042/serio1/inertia = 1

Play with the values until you find the ones you like. Run sudo service sysfsutils restart to apply the changes.


