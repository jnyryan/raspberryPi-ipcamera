# raspberryPi-ipcamera
====================

a quick set-up to get your raspberry Pi working as an IP Camera

# overview

this is a very simple setup that uses the motion application to record activity and save images in the format required.

To spice this up i used it combined with my Synology NAS which has a Surviellance Station package.

# installation

1. Create an OS iamge on the raspberryPi
All up-to-date instructions are [here](https://www.raspberrypi.org/documentation/installation/installing-images/mac.md)

These are the commands I used from the above
```
wget https://downloads.raspberrypi.org/raspbian_latest -P ~/Downloads
unzip ~/Downloads/raspbian_latest
diskutil list
diskutil unmountDisk /dev/disk2
sudo dd bs=50m if=/Users/j/Downloads/2016-03-18-raspbian-jessie-lite.img of=/dev/disk2
```

***Note*** Ctrl T to check progress

2. Configure the raspberryPi
### ssh
This is an easy task done the in the pi's config app ```sudo raspi-config```
under advanced options.
Current guide is [here](https://www.raspberrypi.org/documentation/remote-access/ssh/)

### wifi

https://learn.adafruit.com/adafruits-raspberry-pi-lesson-3-network-setup/setting-up-wifi-with-occidentalis

3. Install the application 'motion'
Install the packages needed to run the camera software

```
  sudo apt-get update
  sudo apt-get install -y motion libv4l-0 uvccapture vim git curl
```  

4. Configure the IP Camera App

The configuration for motion is located in etc/motion/motion.conf. You can use
the default, or make changes to suite your requirements. My configuration is
included here and copied over the default.

```
git clone https://github.com/jnyryan/raspberryPi-ipcamera.git
cp ./raspberryPi-ipcamera/motion.conf etc/motion/motion.conf
```

edit /etc/default/motion and set "start_motion_daemon" to yes

```
/etc/init.d/motion start
```

[reference](https://www.raspberrypi.org/forums/viewtopic.php?t=18314)
