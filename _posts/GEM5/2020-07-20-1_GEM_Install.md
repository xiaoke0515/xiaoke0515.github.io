---
layout: post
title: GEM5- GEM5 的用户安装
categories: GEM5
tags:
    - "GEM5"
    - "simulator"
    - "virtuoso"
---

没写完，待补充。
<!--->
这篇是好久之前总结的，觉得网上没有相关的资料于是就把这个放上来了。算是比较详细，该踩的坑都踩了。


需求：gem5仿真器要安装scons，需要无sudo权限使用python-dev；先试着求助anaconda，但无果
大致思路是用源码编译python，之后安装pip，再安装scons

	1. 编译python
		scons对python版本需求是python2.7，下安装python2.7.17
		a. 源码地址： https://www.python.org/downloads/source/
		b. config：
		./configure --enable-optimizations --prefix=~/.local/python2.7/（安装路径）
		c. make：
		make & make install
		d. 将python路径添加到.bashrc中：
		export PATH="路径:$PATH"
	2. 编译安装pip和setuptools
		a. 源码地址： https://pypi.org/project/setuptools/#files 和 https://pypi.org/project/pip/#files
		b. 直接 python setup.py install
	3. 修改pip源
		PYPI国内源路径
		
		    阿里云 http://mirrors.aliyun.com/pypi/simple/
		
		    豆瓣(douban) http://pypi.douban.com/simple/
		
		    清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/
		
		    中国科学技术大学 http://pypi.mirrors.ustc.edu.cn/simple/
		在～/.pip/pip.conf文件中追加：
			[global]
index-url=http://pypi.douban.com/simple
[install]
trusted-host=pypi.douban.com
	4. 安装scons:
		a. 源码地址 https://github.com/SCons/scons github上有安装步骤
		b. bootstrap： 
		python bootstrap.py build/scons
		c. install：
		cd build/scons
python setup.py install
	5. 安装gem5需要的其他包：
		a. M4等： 见 https://blog.csdn.net/qq_30549833/article/details/72955881 ，下面的源网站可以根据情况改成最新的版本，四个都要安装在同一个文件夹下，建议~/.local
			i. 安装m4
				1)  地址 http://mirrors.kernel.org/gnu/m4/m4-1.4.13.tar.gz 
				2) ./configure –prefix=/usr/local（或其他安装路径，下同）
				3) make && make install
			ii. 安装autoconf
				1) 地址 http://mirrors.kernel.org/gnu/autoconf/autoconf-latest.tar.gz
				2) ./configure –prefix=/usr/local
				3) make && make install
			iii. 安装automake
				1) 地址 http://mirrors.kernel.org/gnu/automake/automake-1.11.tar.gz 
				2) ./configure –prefix=/usr/local
				3) make && make install
			iv. 安装libtool
				1) 地址 http://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz 
				2) ./configure –prefix=/usr/local
				3) make && make install
		b. Protobuf:
			i. 源码地址： https://github.com/protocolbuffers/protobuf.git
			ii. Update ： 
			git submodule update --init --recursive
			iii. autogen：
			./autogen.sh
			iv. Install
			 ./configure --prefix = {your_path}
			make
make check
(sudo ) make install
			v. 添加路径在.bashrc文件中
			vi. 添加python依赖：
				1) 添加python路径：
				export PYTHONPATH="{your_path}/lib/python2.7/site-packages/:$PYTHONPATH"
				2) 编译安装
				python setup.py build 
python setup.py test 
python setup.py install --prefix={your_path} 
				3) 测试
				import google.protobuf
	6. 编译gem5：
		scons bulid/X86/gem5.opt -j9

<--->

