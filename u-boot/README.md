#build

build stage1:


build u-boot:
wget http://ftp.denx.de/pub/u-boot/u-boot-2014.10.tar.bz2
tar -xvf u-boot-2014.10.tar.bz2
tar -xvf uboot-oxnas-2014.10.patch.tar.gz
cd u-boot-2014.10
cp -fr ../uboot-oxnas/src/* ./
patch -p1 < ../uboot-oxnas/patches/patch***
make ox820_defconfig
make -j




