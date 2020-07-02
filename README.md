# linux-gpib

Notes:

On Linux Mint  19.3 (Ubuntu 18.04 LTS)

Download linux-gpib-4.3.3 at https://linux-gpib.sourceforge.io/

sudo apt-get install build-essential texinfo texi2html  libcwidget-dev tcl-dev tk-dev libncurses5-dev libx11-dev binutils-dev bison flex libusb-1.0-0 libusb-dev libmpfr-dev libexpat1-dev tofrodos subversion autoconf automake libtool python-dev

mkdir MYFOLDER
cd MYFOLDER

tar xvzf linux-gpib-kernel-4.3.3.tar.gz linux-gpib-kernel-4.3.3/
tar xvzf linux-gpib-user-4.3.3.tar.gz linux-gpib-user-4.3.3/

sudo cp -R linux-gpib-kernel-4.3.3/* /usr/src/linux-gpib-4.3.3/
sudo nano /usr/src/linux-gpib-4.3.3/dkms.conf

copy dkms.conf from this repo

sudo dkms add -m linux-gpib -v 4.3.3
sudo dkms build -m linux-gpib -v 4.3.3
sudo dkms install -m linux-gpib -v 4.3.3

sudo modprobe ni_usb_gpib

cd MYFOLDER
cd linux-gpib-user-4.3.3/
./bootstrap
./configure --sysconfdir=/etc
make
sudo make install


