---
layout: post
title: 空教室查询器后端搭建
date: 2023-02-04
author: Matt-wzy
tags: [建站]
comments: true
toc: true
pinned: false
---

步骤很简单，1下载2运行3内网穿透

<!-- more -->

# 空教室查询器

[GitHub - Annihilatexv/qlu-cr: 查询齐鲁工业大学校内空教室](https://github.com/Annihilatexv/qlu-cr.git) 此项目基于齐鲁工业大学的教务系统（系统服务提供商：湖南强智科技发展有限公司）的`/jsxsd/kbcx/kbxx_classroom_ifr` 接口，获取全校上课数据，从而进行空课教室查询。

理论上支持全部同服务商的教务系统后端。

## 后端源码下载

两个项目二选一 https://github.com/Annihilatexv/qlu-cr.git [GitHub - Matt-wzy/qlu-cr: 查询齐鲁工业大学校内空教室](https://github.com/Matt-wzy/qlu-cr.git) 本人在原作者的fork中增删了部分不可用教室的内容。对于图书馆空座查询部分功能增加了session鉴权，防止被当做恶意流量拦截。（当被请求量大时概率拦截，不加鉴权也没问题）

## 运行

> 本部分需要您提前安装好python 

[Python Release Python 3.11.1  Python.org](https://www.python.org/downloads/release/python-3111/)（后续新版本或以前版本也可以，此版本测试过可以正常运行）

在文件夹内部使用命令行打开，若不了解的请在文件夹目录部分输入`cmd` 并回车。在其弹出的黑色窗口操作。[![此处输入cmd并回车](https://cdn-p.freejishu.com/img/2023/02/04/20ut.th.png)](https://img.freejishu.com/image/20ut) 

`pip install -r requirements.txt ` 回车，等待环境安装成功后，使用文本编辑工具或者ide（如果有ide的话）打开 `get_course_on_table.py`文件，第11行cookie处换成你的cookie，如果你并非本校的同学请在第16行左右的`url`处将教务系统域名变更为贵校域名，然后运行 （或在上述命令窗口中执行`python get_course_on_table.py`）若没有报错且`/data/course_on_table.json`内容有变动说明更新成功。

更新成功后，可执行`python run.py`即可在http://127.0.0.1/ （作者原项目） 或 http://127.0.0.1:5000/ （本人项目）访问查询功能。

## 端口转发/内网穿透

> 本部分如果你事先有个域名就可以免费操作，虽然说github student pack能免费给你俩一年域名，但好多人懒得申请，如果不想自己搞个域名的话那就只有付费且带宽低的方案了，如果你能拿到公网ipv4地址的话可以跳过这个部分。

内容施工中，请过段时间再来或者下方评论区催更。

本方案基于cloudflare 的cloudflare tunnel，需要你事先有一个域名并且可以将ns解析转移到cloudflare。

使用tunnel教程请参考 此链接 


