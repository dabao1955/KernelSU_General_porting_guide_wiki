# 集成KernelSU
KernelSU 可以被集成到非 GKI 内核中，现在它最低支持到内核 4.14 版本；理论上也可以支持更低的版本。

### 通过kprobes集成
KernelSU 使用 kprobe 机制来做内核的相关 hook，如果 kprobe 可以在你编译的内核中正常运行，那么推荐用这个方法来集成。

首先，把 KernelSU 添加到你的内核源码树，在内核的根目录执行以下命令：
```bash
curl -LSs "https://raw.githubusercontent.com/tiann/KernelSU/main/kernel/setup.sh" | bash -
```
然后，你需要检查你的内核是否开启了 kprobe 相关的配置，如果没有开启，需要编辑配置文件并添加以下内容
```bash
CONFIG_KPROBES=y
CONFIG_HAVE_KPROBES=y
CONFIG_KPROBE_EVENTS=y
CONFIG_MODULES=y
CONFIG_OVERLAYFS=Y
```
如果你在集成 KernelSU 之后手机无法启动，那么很可能你的内核中 kprobe 工作不正常，你需要修复这个 bug 或者用第二种方法。
### 手动添加kernelSU