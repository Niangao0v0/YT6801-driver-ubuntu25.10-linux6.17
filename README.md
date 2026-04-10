# YT6801 驱动在 Ubuntu 25.10 / Linux 6.17 上的兼容性修复

此仓库内所有内容均为免费文件。若您获取副本时，被以任何形式地收费过，请与我联系。

**联系方式**  
Email：gaochuhan1455@outlook.com

---

## 问题描述

YT6801 官网驱动在 Ubuntu 25.10 编译安装时会遇到报错，与 Linux 6.17 的 

`timer.h` 头文件发生更改有关。  

本仓库存储了一个替换文件，用于兼容新的 Linux 内核。

---

## 替换步骤

1. **下载官方驱动**  
   前往 [MotorComm 官网](https://www.motor-comm.com/cn/index/pageview/kw/yt6801/catid/55/wd/1/tp/1/p/1.html](https://www.motor-comm.com/download?kw=&category=744&wd=1&tp=1) 下载  
   `yt6801-linux-driver-1.0.31.zip`

2. **解压**
   
   解压 ``yt6801-linux-driver-1.0.31.zip``

   并继续解压其中的 ``yt6801-1.0.31.tar.gz``

3. **替换``.c``文件**
   
   将该仓库提供的.c文件替换掉  /yt6801-linux-driver-1.0.31/yt6801-1.0.31  中的相关文件。  
   文件下载地址：[v1.0.31Alpha2](https://github.com/Niangao0v0/YT6801-driver-ubuntu25.10-linux6.17/releases/tag/v1.0.31Alpha2)

4. **替换``.sh``文件**
   
   将该仓库提供的.sh文件替换掉  /yt6801-linux-driver-1.0.31  中的相关文件。

5. **安装编译依赖**  
   确保系统已安装编译所需依赖（如

   `build-essential`  `linux-headers-$(uname -r)`
   等）。

6. **切换到 root 用户**  
   ```bash
   sudo -i
   ```

7. **进入驱动源码目录**
   ```bash
   cd 你的源码路径   # 该路径下应包含 .sh 文件
   ```

8. **执行安装脚本**
   ```bash
   ./yt_nic_install.sh
   ```
