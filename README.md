# raspberry-pi4-yocto
raspberry pi4 with yocto

Setup:
1) Install the following packages:
sudo apt-get install \
     gawk wget git-core diffstat unzip texinfo gcc-multilib \
     build-essential chrpath socat cpio \
     python python3 python3-pip python3-pexpect \
     xz-utils debianutils iputils-ping \
     python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev xterm

2) Poky & OpenEmbedded
Clone the poky and meta-openembedded
$ git clone -b dunfell git://git.yoctoproject.org/poky.git
$ git clone -b dunfell git://git.openembedded.org/meta-openembedded    

3) Meta layer for Raspberry pi
$git clone -b dunfell git://git.yoctoproject.org/meta-raspberrypi

4)Project Structure
$YOCTO_PI=/home/pabitra/workspace/raspberry-pi4-yocto
$YOCTO_PI/
    -layers/
        -poky
        -meta-openembedded
        -meta-raspberrypi

5) Source poky environment to build pi image
$source layers/poky/oe-init-build-env rasp4-build

This will create a directory called rasp4-build in $YOCTO_PI/rasp4-build

The content of the rasp4-build:
conf/
    -bblayers.conf
    -local.conf

6) add the base layers into bblayers.conf using 
$bitbake-layers add-layer ../layers/meta-openembedded/meta-oe
$bitbake-layers add-layer ../layers/meta-openembedded/meta-multimedia
$bitbake-layers add-layer ../layers/meta-openembedded/meta-networking
$bitbake-layers add-layer ../layers/meta-openembedded/meta-python
$bitbake-layers add-layer ../layers/meta-raspberrypi