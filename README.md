To install gale on OpenWRT:

    # cd ~
    # svn co svn://svn.openwrt.org/openwrt/trunk/ openwrt
    # cd openwrt
    # cp ./feeds.conf.default ./feeds.conf
    # echo 'src-git gale git://github.com/nandub/gale-openwrt.git' >> ./feeds.conf
    # ./scripts/feeds update -a
    # ./scripts/feeds install gale

Then configure for your system:

    # make menuconfig

Select your system type and the options you want and choose:

    Application ---> [*] gale

Then save and close the configuration menu, then allow OpenWRT to resolve dependencies:

    # make defconfig

Then build:

    # make

If you have a multicore processor, you can build faster using `-j`,
however the OpenWRT build process is not highly parallelized so your milage may vary.

    # make -j 4

To update the version of gale:

    # rm ./dl/gale-*
    # ./scripts/feeds update gale
    # make

