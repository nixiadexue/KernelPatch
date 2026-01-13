# KernelPatch

**Patching and hooking the Linux kernel with only stripped Linux kernel image.**

``` shell
 _  __                    _ ____       _       _     
| |/ /___ _ __ _ __   ___| |  _ \ __ _| |_ ___| |__  
| ' // _ \ '__| '_ \ / _ \ | |_) / _` | __/ __| '_ \ 
| . \  __/ |  | | | |  __/ |  __/ (_| | || (__| | | |
|_|\_\___|_|  |_| |_|\___|_|_|   \__,_|\__\___|_| |_|

```

- Obtain all symbol information without source code and symbol information.
- Inject arbitrary code into the kernel. (Static patching the kernel image or Runtime dynamic loading).
- Kernel function inline hook and syscall table hook are provided.
- Additional SU for Android.

If you are using Android, [APatch](https://github.com/bmax121/APatch) would be a better choice.

## Requirement

CONFIG_KALLSYMS=y  

## Supported Versions

Currently only supports arm64 architecture.  

Linux 3.18 - 6.6 (theoretically)  

## Get Involved

## More Information

[Documentation](./doc/)

## Credits

- [vmlinux-to-elf](https://github.com/marin-m/vmlinux-to-elf): Some ideas for parsing kernel symbols.
- [android-inline-hook](https://github.com/bytedance/android-inline-hook): Some code for fixing arm64 inline hook instructions.
- [tlsf](https://github.com/mattconte/tlsf): Memory allocator used for KPM. (Need another to allocate ROX memory.)

## License

KernelPatch is licensed under the **GNU General Public License (GPL) 2.0** (<https://www.gnu.org/licenses/old-licenses/gpl-2.0.html>).

## Build
linux 下载编译工具链 https://developer.arm.com/downloads/-/arm-gnu-toolchain-downloads
1、当前下载使用 https://developer.arm.com/-/media/Files/downloads/gnu/13.3.rel1/binrel/arm-gnu-toolchain-13.3.rel1-x86_64-aarch64-none-elf.tar.xz
2、解压tar包到/opt/ 
3、echo "\nexport PATH=$PATH:/opt/arm-gnu-toolchain-13.3.rel1-x86_64-aarch64-none-elf/bin" >> /etc/profile
4、source /etc/profile

export ARCH=arm64
export CROSS_COMPILE=aarch64-linux-android-
export TARGET_COMPILE=aarch64-none-elf-

make