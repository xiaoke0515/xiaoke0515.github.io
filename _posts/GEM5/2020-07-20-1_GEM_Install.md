---
layout: post
title: GEM5- GEM5 的非 sudo 用户安装
categories: GEM5
tags:
    - "GEM5"
    - "simulator"
    - "cycle accurate"
---

这篇是好久之前总结的，觉得网上没有相关的资料于是就把这个放上来了。算是比较详细，该踩的坑都踩了。


需求：gem5仿真器要安装 scons ，需要无sudo权限使用 python-dev ；先试着求助 anaconda ，但无果，最终选择了这种方案。

大致思路是用源码编译python，之后安装pip，再安装scons。

当然，如果有 root 权限就简单很多了，直接参考官方文档 [http://www.gem5.org/](http://www.gem5.org/) 就可以了。

## Python 和 Python-dev 的安装

1. 下载并编译python

	scons对python版本需求是 python2.7，下安装 python2.7.17

	- 源码地址： [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/)

	- config：

		```
		./configure --enable-optimizations --prefix=~/.local/python2.7/（安装路径，可自定义）
		```
	- make：
	
		```
		make & make install
		```
	- 将python路径添加到.bashrc中：

		```
		export PATH="路径:$PATH"
		```

1. 编译安装 pip 和 setuptools

	- 源码地址： [https://www.python.org/downloads/source/](https://pypi.org/project/setuptools/#files) 和 [https://pypi.org/project/pip/#files](https://pypi.org/project/pip/#files)

	- install，注意这里要确认 python 为刚刚安装的 python ，如果不是，要尝试关闭 conda 等环境。

		```
		python setup.py install
		```
		
1. 修改pip源

	几个可选的 PYPI 国内源路径:
	
	- 阿里云 [http://mirrors.aliyun.com/pypi/simple/](http://mirrors.aliyun.com/pypi/simple/)
	
	- 豆瓣(douban) [http://pypi.douban.com/simple/](http://pypi.douban.com/simple/)
	
	- 清华大学 [https://pypi.tuna.tsinghua.edu.cn/simple/](https://pypi.tuna.tsinghua.edu.cn/simple/)
	
	- 中国科学技术大学 [http://pypi.mirrors.ustc.edu.cn/simple/](http://pypi.mirrors.ustc.edu.cn/simple/)

	修改方式：在～/.pip/pip.conf文件中追加如下字段

	```
	[global]
	index-url=http://pypi.douban.com/simple
	[install]
	trusted-host=pypi.douban.com
	```

## scons 的安装

1. 安装scons:

	- 源码地址 [https://github.com/SCons/scons](https://github.com/SCons/scons) ,  github上有安装步骤，可自行参考，不赘述

	- bootstrap 的安装： 

		- python bootstrap.py build/scons

		- install：

			```
			cd build/scons
			python setup.py install
			```

## GEM5的其他依赖

1.  M4等： 此处参考 [https://blog.csdn.net/qq_30549833/article/details/72955881](https://blog.csdn.net/qq_30549833/article/details/72955881) ，下面的源网站可以根据情况改成最新的版本，四个都要安装在同一个文件夹下，建议安装在~/.local
	- 安装m4

		1. 地址:
		
			[http://mirrors.kernel.org/gnu/m4/m4-1.4.13.tar.gz](http://mirrors.kernel.org/gnu/m4/m4-1.4.13.tar.gz)

		1. Config:

			```
			./configure –prefix=~/.local（或其他安装路径，下同）
			```

		1. Install:

			```
			make && make install
			```

	- 安装autoconf

		1. 地址:
		
			[http://mirrors.kernel.org/gnu/autoconf/autoconf-latest.tar.gz](http://mirrors.kernel.org/gnu/autoconf/autoconf-latest.tar.gz)

		1. Config:

			```
			./configure –prefix=~/.local
			```

		1. Install:

			```
			make && make install
			```

	- 安装automake

		1. 地址:
		
			[http://mirrors.kernel.org/gnu/automake/automake-1.11.tar.gz](http://mirrors.kernel.org/gnu/automake/automake-1.11.tar.gz)

		1. Config:

			```
			./configure –prefix=~/.local
			```

		1. Install:

			```
			make && make install
			```

	- 安装libtool

		1. 地址:
		
			[http://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz ](http://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz )

		1. Config:

			```
			./configure –prefix=~/.local
			```

		1. Install:

			```
			make && make install
			```

1. Protobuf:

	- 源码地址： [https://github.com/protocolbuffers/protobuf.git](https://github.com/protocolbuffers/protobuf.git)

	- Update： 这个步骤省了会报错 

		```
		git submodule update --init --recursive
		```

	- autogen：

		```
		./autogen.sh
		```

	- config:

		```
		./configure --prefix = {your_path}
		```

	- install:

		```
		make
		make check
		make install
		```

	- 添加路径在.bashrc文件中，在.bashrc中追加：

		```
		export PATH="{your_path}:$PATH"
		```

	- 添加python依赖 （可选）：
		1. 添加python路径 （就是刚才安装的python路径，添加到 PYTHONPATH 环境变量中）：

			```
			export PYTHONPATH="{your_path}/lib/python2.7/site-packages/:$PYTHONPATH"
			```

		1. 编译安装

			```
			python setup.py build 
			python setup.py test 
			python setup.py install --prefix={your_path} 
			```

		1. 测试，打开一个python，输入下面代码，没有import错误就说明正确安装了


			```
			import google.protobuf
			```

## GEM5 的编译

最后就可以编译 GEM5 啦

1. 源码：

	[https://github.com/gem5/gem5.git](https://github.com/gem5/gem5.git)

1. 编译gem5：

	```
	scons bulid/X86/gem5.opt -j9
	```

	有可能会报错少一些 python module ，这个可以很轻松解决，在此不赘述。


