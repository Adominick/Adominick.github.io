---
layout: post
title: "cygwin的安装与设置"
description: "ssh远程访问你的windows端"
category: 技术
tags: [远程, cygwin, windows]
---
 
{% include JB/setup %}
_文/<a href="{{site.url}}/zcontact.html" style="color:grey">甄谨言</a>_ 习惯在 shell 中工作的朋友一定也回捣鼓在 windows 环境中也能运行，于是推荐使用 Cygwin，windows 端安装 Cygwin 后又想能够 ssh 到 windows 端，那么就可以用 Cygwin 提供的 SSH 服务，这东西实在是方便，所以特别来记录下安装过程。<!-- more -->
 
<a name="t"></a>
 
---
本文目录
 
1.  <a href="#t1">Cygwin的安装</a>
 
2.  <a href="#t2">openssh的安装</a>
 
3.  <a href="#t3">ssh 的配置</a>
 
---

## <a name="t1"></a>1.Cygwin 的安装
 
 - 32位电脑[下载地址](http://cygwin.com/setup-x86.exe)
 - 64位电脑[下载地址](http://cygwin.com/setup-x86_64.exe)
 
 下载注意事项：
 
 - 选择中国地镜像**.cn
 - 如果需要Cygwin能够编译程序，需要安装gcc，用鼠标点开组件列表中的“Devel”分支，在该分支下，有很多组件， 选择：binutils，gcc，gcc-mingw，gdb
 
 然后就是漫长的等待安装完毕吧。本文假设你配置在 d 盘，即 D:/cygwin
 
## <a name="t2"></a>2.apt-cyg 和openssh 的安装

在 Cygwin 的 terminal 中安装apt-cyg：

<pre><code>wget http://apt-cyg.googlecode.com/svn/trunk/apt-cyg -P /bin
chmod.exe +x /bin/apt-cyg</code></pre>
 
apt-cyg安装源为ftp://mirror.mcs.anl.gov，设置改为网易镜像源。
 
<pre><code>apt-cyg -m http://mirrors.163.com/cygwin/</code></pre>

直接在 Cygwin 中输入安装 openssh：

<pre><code>apt-cyg install openssh</code></pre>


## <a name="t3"></a>3.ssh 的配置
 
 设置环境变量，把 'D:/cygwin/bin;D:/cygwin/usr/bin' 加入到系统环境变量的Path中
 
 打开cygwin，输入 ssh-host-config
 
  一路点 yes
  
  当询问about the value of CYGWIN environment variable enter 时输入 ntsec tty
  
  输入 `cygrunsrv --start sshd` 或者 `net start sshd`启动sshd，
  
  输入`cygrunsrv --stop sshd` 或者 `net stop sshd`停止sshd
 
  在 terminal 中输入：
  
  <pre><code>cd ~/.ssh 
cat id_rsa.pub >> authorized_keys</code></pre>

测试 ssh 设置是否成功`ssh localhost`

 下面展示一张远程登录成功初始界面提示：
 
 ![登录界面](http://7u2ofy.com1.z0.glb.clouddn.com/cygwin_ssh.png)
 

<div align="right"><a href="#t">返回目录</a></div>
