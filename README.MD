# Start here if you do not have a preinstalled image
start with the latest raspbian lite (https://downloads.raspberrypi.org/raspbian_latest)

write to the micro SD card (at least 8 GB, recommended type: SanDisk)

copy "ssh" file and "wpa_supplicant.conf" to the boot disk (next to cmdline.txt)

expand file system (https://www.raspberrypi.org/documentation/configuration/raspi-config.md)

```
sudo apt-get update
sudo apt-get upgrade
```

# Start here if you have a preinstalled and properly setup image


`sudo nano /etc/dphys-swapfile`
#change the CONF_SWAPSIZE from 100 to 2048:
`CONF_SWAPSIZE=100` ->	  `CONF_SWAPSIZE=2048`

```
sudo /etc/init.d/dphys-swapfile restart swapon -s

sudo apt-get install git mc python-pip python3-pip cython3

wget https://ncs-forum-uploads.s3.amazonaws.com/ncsdk/ncsdk-02_05_00_02-full/ncsdk-2.05.00.02.tar.gz

tar -xzvf ncsdk-2.05.00.02.tar.gz

cd ncsdk-2.05.00.02
```

`nano ncsdk.conf`
#uncomment MAKE_NJOBS and change number to 2, like here:
`#MAKE_NJOBS=1` -> `MAKE_NJOBS=2`

```
sudo apt install cython

sudo -H pip3 install cython

sudo -H pip3 install numpy

sudo -H pip3 install pillow
```

`sudo nano install-opencv.sh`
#change the version to number; Go to line 55 and change from 3.3.0 to 3.4.2 (I tested only this version, might be possible it work with higher one also)

`sudo ./install-opencv.sh`
#and grab a coffee, might take a while (1-2 hours)

#if you can see this message: "OpenCV Installation Finished", then you are lucky and you can change back the swapfile:

`sudo nano /etc/dphys-swapfile`

#change the CONF_SWAPSIZE from 2048 to 100:
`CONF_SWAPSIZE=2048` ->	  `CONF_SWAPSIZE=100`

`sudo /etc/init.d/dphys-swapfile restart swapon -s`


# How to check python3 opencv installation
```
python3
import cv2
print(cv2.__version__)
```
