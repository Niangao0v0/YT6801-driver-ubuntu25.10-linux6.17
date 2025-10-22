替换步骤：
1.前往https://www.motor-comm.com/product/ethernet-control-chip
下载yt6801-linux-driver-1.0.30.zip
此时尝试按照.zip内的readme编译安装。如果你正在使用ubuntu25.10(linux6.17)或以上（未来），你可能会遇到针对fuxi-gmac-phy.c的报错。
此时将该github页面提供的fuxi-gmac-phy.c替换掉官方驱动/src/fuxi-gmac-phy.c
确保编译依赖都已经安装，应该就能编译成功。

# 注意：此次更改并不兼容linux版本<=6.16的内核。若linux version<=6.16，可直接编译运行官方驱动，请勿替换本文件。
# ubuntu25.04及以下应该都不需要替换本文件
# 当motorcomm官方驱动对linux6.17进行兼容之后，本替换文件将会停止维护。



针对fuxi-gmac-phy.c的修改说明：

1.第318行
<linux/viersion.h>头文件位置变更。
新的目录为 /usr/src/linux-headers-6.17.0-5-generic/include/generated/uapi/linux/version.h
如有需要，你可修改YT6801驱动附带的fuxi-os.h头文件（如果你希望兼容全部linux版本的话）

2.第328行
from_timer()似乎已被新内核弃用，可能应调用timer_container_of()
container_of()位于/usr/src/linux-headers-6.17.0-5-generic/include/linux/timer.h中

3.第358行
init_timer_key()似乎已被其用，可能应当调用timer_setup()
timer_setup()位于/usr/src/linux-headers-6.17.0-5-generic/include/linux/timer.h中

4.第377行
del_timer_sync()可能已被弃用，可能需要调用timer_shutdown_sync()
timer_shutdown_sync()位于/usr/src/linux-headers-6.17.0-5-generic/include/linux/timer.h中
文件中还有timer_delete_sync()


//以上不一定正确。
