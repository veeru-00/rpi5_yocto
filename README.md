Reference Documentation (Yocto)
##################################
https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html
https://docs.yoctoproject.org/ref-manual/variables.html
https://layers.openembedded.org/layerindex/branch/master/layers/


Reference Documentation (Raspberry Pi)
########################################
https://www.raspberrypi.com/documentation/
https://datasheets.raspberrypi.com/rp1/rp1-peripherals.pdf

Preliminary Steps
#############################

$ sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 python3-subunit zstd liblz4-tool file locales libacl1
$ sudo locale-gen en_US.UTF-8

Download Poky
######################

git clone git://git.yoctoproject.org/poky -b scarthgap

Building Software Package Example
######################################

. oe-init-build-env
bitbake dropbear

Cloning Additional Layers
##############################

Use https://layers.openembedded.org/layerindex/branch/master/layers/ to pick layer

cd poky/
git clone <layer_git> -b <branch_name>


Cooking (bitbake'ing) the image recipe
################################
bitbake core-image-minimal

Serial communication
######################
ls /dev/tty*
sudo minicom -s

Limit cores and threads from local.conf
###########################################
BB_NUMBER_THREADS="10"
PARALLEL_MAKE="-j 2"

Cook application SDK
#########################
bitbake meta-toolchain
or
bitbake meta-toolchain-qt6
or
bitbake meta-toolchain-moz

Install application SDK
#########################
Execute the script from tmp/deploy/sdk/*toolchain

Use the application SDK
###########################
. /opt/poky/5.0.1/environment-setup-cortexa76-poky-linux
