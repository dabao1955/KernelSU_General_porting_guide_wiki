# KernelSU简介
### 什么是 KernelSU?
KernelSU 是 Android GKI 设备的 root 解决方案，它工作在内核模式，并直接在内核空间中为用户空间应用程序授予 root 权限。
### KernelSU的功能？
KernelSU 运行在内核空间， 所以它可以提供我们以前从未有过的内核接口。 例如，我们可以在内核模式下为任何进程添加硬件断点；我们可以在任何进程的物理内存中访问，而无人知晓；我们可以在内核空间拦截任何系统调用; 等等。

KernelSU 还提供了一个基于 overlayfs 的模块系统，允许您加载自定义插件到系统中。它还提供了一种修改 /system 分区中文件的机制。
### KernelSU与Magisk的区别？
KernelSU运行在内核空间，Magisk运行在用户空间。

KernelSU会集成在kernel中，Magisk会集成在ramdisk上。

KernelSU隐蔽性更强，Magisk更容易安装。