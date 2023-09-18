# Bug修复

此文本旨在ksu核心工作正常后对其不工作的地方(例如模块)进行修复，文章部分内容节选自[此](https://github.com/tiann/KernelSU/discussions/956)

### 能安装模块但是不工作

修改`security/selinux/hooks.c `

参考[此提交](https://github.com/sticpaper/android_kernel_xiaomi_msm8998-ksu/commit/646d0c836053ffa8743519c39fcabaecb258f00b)

### 低于安卓10的设备KernelSU显示工作但是SU授权无法正常使用且模块页面显示不支持Overlay_FS

KernelSU不兼容安卓10以下设备，所以无法正确处理低于安卓10的init。那么结果即使就会遭到SELinux的拦截。

1.修改selinux(不推荐)

```
--- a/security/selinux/selinuxfs.c
+++ b/security/selinux/selinuxfs.c  

	length = -EINVAL;
	if (sscanf(page, "%d", &new_value) != 1)
		goto out;


+  	new_value = 0;

	if (new_value != selinux_enforcing) {
		length = task_has_security(current, SECURITY__SETENFORCE);

```

~~2.修改init变量~~

~~需要手动修改KernelSU源码,参考[此提交](https://github.com/longhuan1999/KernelSU/commit/56ca12d550875efe7cac45b3a16d9dce678a8b85)~~



