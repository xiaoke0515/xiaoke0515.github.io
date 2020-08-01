---
layout: post
title: GEM5- GEM5 中 VectorPort 的用法
categories: GEM5
tags:
    - "GEM5"
    - "simulator"
    - "cycle accurate"
---

我的需求用到不确定个数的 port ，看了源码搞清了应该怎么用。

1. 在 SimObject 的 py 文件中添加：
    ```python
    masterports = VectorMasterPort('master ports')
    slaveports = VectorSlavePort('slave ports')
    ```

1. 在 SimObject 的 hh 文件中添加 port 的 vector 变量：

    ```c++
    std::vector<XXXMasterPort> m_ps;
    std::vector<XXXSlavePort> s_ps;
    ```

1. SimObject 类中重写 getPort 函数：

    ```c++
    Port &
    HyperTr::getPort(const std::string &if_name, PortID idx){

        // This is the name from the Python SimObject declaration (SimpleMemobj.py)
        if (if_name == "masterports") {
            return m_ps[idx];
        } else if (if_name == "slaveports") {
            return s_ps[idx];
        } else {
            // pass it along to our super class
            return SimObject::getPort(if_name, idx);
        }
    }
    ```

1. 在 c++ class 的构造函数中添加 vector ports：

    port_xxx_connection_count 是自动生成的参数，是编译器根据 config.py 文件中连接了多少 port 确定的。
    在构造函数中，我们需要按照这个数量添加 port。
    ```c++
    for (int i = 0; i < params->port_masterports_connection_count; i ++){
        m_ps.push_back(XXXMasterPort(params->name + ".m_port:" + std::to_string(i), this));
    }
    for (int i = 0; i < params->port_slaveports_connection_count; i ++){
        s_ps.push_back(XXXSlavePort(params->name + ".s_port:" + std::to_string(i), this));
    }
    ```


为了表示哪几个名字必须一样，哪几个名字不必一样，我特意将 c++ class 中 port 的名字与 python 中 port 的名字设置的不同。

另：啰嗦一句
其实重点在于 getPort 函数，这个函数用于定义 python 文件中的 port 名字与 c++ class 中的哪个 port 对应
c++ class 中的 port 可能不必定义成一个 vector 。
只要能让 gem5 编译器找到对应的 port 即可。