---
layout: post
title: "Linux回环(loop)设备和文件虚拟磁盘"
categories:
- linux
tags:
- linux命令
- linux


---


在linux系统中，/dev/loop（或称vnd (vnode disk)、lofi（循环文件接口））是一种伪设备，这种设备使得文件可以**如同块设备**一般被访问。

在使用之前，循环设备必须与现存文件系统上的文件相关联。这种关联将提供给用户一个应用程序接口，接口将允许文件视为块特殊文件（参见设备文件系统）使用。因此，如果文件中包含一个完整的文件系统，那么这个文件就能如同磁盘设备一般被挂载。

这种设备文件经常被用于光盘或是磁盘镜像。通过循环挂载来挂载包含文件系统的文件，便使处在这个文件系统中的文件得以被访问。这些文件将出现在挂载点目录。  
linux下回环设备一般是/dev/loop0,/dev/loop1,......  
如果找不到这些文件，可能是loop模块未加载，使用`modprobe loop`命令加载。

### 使用

在目录上挂载包含文件系统的文件一般需要两步，

+  用一个循环设备节点连接文件。
+  在目录上挂载该循环设备。

比如：  

	losetup /dev/loop0 example.img
	mount /dev/loop0 /home/you/dir

其中losetup连接节点和文件，mount进行挂载，回想一下挂载iso文件时的命令  
mount -o loop /path/to/file.iso /path/to/mountdir  
可以认为直接实现了这两步。

### 创建、使用img镜像文件

先用dd创建一个指定大小的文件（例子200M）

`dd if=/dev/zero of=test.img bs=1M count=20`

然后格式化，自选文件系统

`mkfs.ext4 test.img`

然后挂载，见上面挂载方法，之后就可以在挂载的目录里进行文件操作了，这样就可以把test.img当作一个磁盘来用了。



