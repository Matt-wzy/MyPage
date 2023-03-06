---
layout: post
title: 在esxi上运行openwrt的笔记
date: 2023-03-06
author: Matt-wzy
tags: [ESXI,运维,笔记]
comments: true
toc: true
pinned: false
---

步骤很简单，1下载2修复3上传转换

<!-- more -->

# 下载x86的openwrt vmdk文件

基于 [GitHub - SuLingGG/OpenWrt-Rpi: Raspberry Pi &amp; NanoPi R2S/R4S &amp; G-Dock &amp; x86 OpenWrt Compile Project. (Based on Github Action / Daily Update)](https://github.com/SuLingGG/OpenWrt-Rpi) 项目，从[64 release](https://openwrt.cc/releases/targets/x86/64/) 处下载vmdk镜像（此处推荐squashfs，ext4格式的请使用者自行尝试），[下载链接](https://openwrt.cc/releases/targets/x86/64/immortalwrt-x86-64-generic-squashfs-combined-efi.vmdk)

。下载好后请使用DiskGenius修复一下文件，然后再上传到esxi服务器的储存中。

# 转换文件到esxi支持的格式，并修复文件大小

上传到储存库对应位置后，找到并记录储存库的位置，如下图所示。后续用到。

[![2ao9.md.png](https://cdn-p.freejishu.com/img/2023/03/06/2ao9.md.png)](https://img.freejishu.com/image/2ao9)

如果ESXI尚未开启安全ssh，请在操作-服务-启用安全ssh处打开

![](C:\Users\wwwa_\AppData\Roaming\marktext\images\2023-03-06-20-41-11-image.png)

[![6gRF.png](https://cdn-p.freejishu.com/img/2023/03/06/6gRF.png)](https://img.freejishu.com/image/6gRF)

使用ssh连接后，cd到vmdk对应的文件夹下，并执行后续命令（我们假设您上传的vmdk文件名为immortalwrt-x86-64-generic-squashfs-combined-efi.vmdk test.vmdk）,只展示用户需要输入的部分。其中如果要照抄代码的话请确保您的vmdk文件占用空间小于1000M

```bash
vmkfstools -X 1000M immortalwrt-x86-64-generic-squashfs-combined-efi.vmdk
vmkfstools -d thin -i  immortalwrt-x86-64-generic-squashfs-combined-efi.vmdk openwrtdisk.vmdk

```

此时，我们已经对文件进行大小的矫正以及格式的转换。，后续可以使用openwrtdisk.vmdk直接作为虚拟机的磁盘。

# 创建虚拟机

此处使用纯文本描述。

新建虚拟机： 
- 新建虚拟机✔

- 从OVF或OVA文件部署虚拟机

- 注册现有虚拟机

选择名称或操作系统：

    - 名称：输入虚拟机名称，例如mattopenwrt

    - 兼容性：保持默认

    - 客户机操作系统系列：Linux

    - 客户机操作系统版本：其他4.x或更高版本的linux(64位)

选择储存：随便选

自定义配置：

    - CPU、内存等：自己选好

    - 硬盘：此时可以不新增，若不新增则点右侧的叉，但请之后手动新增，此处新增也可。

    - 添加硬盘： 现有硬盘 -> 找到对应的文件位置并选中。

    - 网络适配器：选择对应的网口

    - CD：右边的叉点一下删除

    在虚拟机选项处 选择引导选项，展开，取消启用uefi安全引导

创建完成，可以开机检查了~

请注意，进行下一步前，您最好保证除了系统盘以外还有另一块空硬盘被分配到虚拟机中(EXT4用户不需要)

# 配置openwrt

如果您跑ESXI的设备有多个网口，建议您给openwrt单独分配一个空网口并分配给openwrt，这样可以避免openwrt的DHCP对当前网络环境造成冲突影响。

如果是那样的话，openwrt开机后，你就可以使用一根网线插入对应的网口并直接访问openwrt的管理界面了（或许是192.168.1.1）。进入openwrt后，首先建议配置磁盘，将空的磁盘创建分区并格式化后挂载到/overlay下，这样可以避免其文件系统产生奇奇怪怪的故障。

上述内容操作完毕后，请重启，重启后再进行其他配置。

如果是旁路由的配置方式，请将br-lan配置成ip地址192.168.1.XXX（不要和主路由冲突且和当前网络在同一个网段），并将其网关设置为主路由的网关地址，同时将下方的DHCP关闭，所有ipv6有关的功能禁用或者关闭，这样就可以实现旁路由的功能了。DHCP/DNS处可以关闭唯一授权选项。

配置确认无误保存应用后，openwrt的网络ip就会变动，此时可以接入原有网络的交换机中。

如果需要配置共享打印机，请在esxi界面将打印机设备添加到openwrt上，在 网络储存-USB打印服务处添加打印机，然后启用即可。

