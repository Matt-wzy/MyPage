---
layout: post
title: 打包python程序笔记
date: 2023-08-29
author: Matt-wzy
tags: [python,打包]
comments: true
toc: true
pinned: false
---



<!-- more -->

把大象装进冰箱，总共分几步？

<!-- more -->

# 前期准备

`pip install pyinstaller`

在环境中安装好项目中需要的包

哦对了，如果你的电脑中有多个python软件或者虚拟环境，请找到对应的pip命令进行执行。

# 打包

如果你的项目比较简单，或者引用的第三方库自动打包时不会出现故障，则直接运行`pyinstaller -F xxx.py`即可将指定的python文件进行打包。

打包完成之后的目录结构大致如下：

```
dir:
|	xxx.py
|	xxx.spec
|-build
|	└-xxx
|		some files here
└-dist
	└-xxx.exe
```

其中dist文件夹下既是打包生成的文件

如果此时运行xxx.exe没有报错程序正常运行的话，那么恭喜你，你已经完成任务啦~

但是你如果遇上xxx not found之类的错误提示，那么就说明部分运行库或者环境没有成功地被自动识别上，需要我们手动加载，我们以修复使用ddddcor的项目为例。

找到对应的spec文件，并在pathex，datas写入如下内容：

```
# -*- mode: python ; coding: utf-8 -*-


block_cipher = None


a = Analysis(
    ['run.py'],
    pathex=[r'C:\Users\username\AppData\Roaming\Python\Python311\site-packages'],
    binaries=[],
    datas=[(r'C:\Users\username\AppData\Roaming\Python\Python311\site-packages\onnxruntime\capi\onnxruntime_providers_shared.dll','onnxruntime\\capi'),(r'C:\Users\username\AppData\Roaming\Python\Python311\site-packages\ddddocr\common.onnx','ddddocr')],
    hiddenimports=[],
    hookspath=[],
    hooksconfig={},
    runtime_hooks=[],
    excludes=[],
    win_no_prefer_redirects=False,
    win_private_assemblies=False,
    cipher=block_cipher,
    noarchive=False,
)
pyz = PYZ(a.pure, a.zipped_data, cipher=block_cipher)

exe = EXE(
    pyz,
    a.scripts,
    a.binaries,
    a.zipfiles,
    a.datas,
    [],
    name='run',
    debug=False,
    bootloader_ignore_signals=False,
    strip=False,
    upx=True,
    upx_exclude=[],
    runtime_tmpdir=None,
    console=True,
    disable_windowed_traceback=False,
    argv_emulation=False,
    target_arch=None,
    codesign_identity=None,
    entitlements_file=None,
)

```

需要注意的是，缺失的文件目录需要根据你电脑上的实际情况进行编写。编辑完成后，删掉已经打包出来的 `dist build __pycache__` 这三个文件夹，运行`pyinstaller xxx.spec`即可完成打包。

# 加密

> 想peach呢？写python代码还想着要加密？

啊，这……其实是能加的，只能加一点点，根据[这篇文章](https://zhuanlan.zhihu.com/p/109266820)，安装  ~~pycrypto pip install pycrypto~~  (考虑到pycrypto 安装不上，应该是不需要的) `pip install tinyaes` ，然后`pyinstaller.exe -F --key 123456 xxx.py`，则**依赖库**里面的内容就能被加密啦，需要注意的是依赖库并不代表所有内容，程序的主函数还是能被反编译出来的。








