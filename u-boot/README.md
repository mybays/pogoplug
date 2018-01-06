#build

build stage1:
git clone https://github.com/kref/u-boot-oxnas


build u-boot:

wget http://ftp.denx.de/pub/u-boot/u-boot-2014.10.tar.bz2

tar -xvf u-boot-2014.10.tar.bz2

tar -xvf uboot-oxnas-2014.10.patch.tar.gz

cd u-boot-2014.10

cp -fr ../uboot-oxnas/src/* ./

patch -p1 < ../uboot-oxnas/patches/patch***

make ox820_defconfig

ARCH=arm CROSS_COMPILE=arm-none-eabi- make -j


upload:
setenv ipaddr 202.1.1.4

setenv serverip 202.1.1.136

setenv ethaddr aa:bb:34:34:34:43

tftp 0x65000000 oxnas/u-boot.bin

nand erase 0x40000 0x90000

nand write 0x65000000 0x40000 0x90000




