---
layout: post
title: zsh及oh-my-zsh安装与配置
---

zsh简介以及我为何选择zsh
------------------------

　　zsh被称作是终极的Shell。在设计上借鉴了以往的shell的设计思路，细细查阅网上资料时发现zsh的评价相当不错。zsh相较于bash有很多好的改进。但其中比较令我动心的主要有两点：

+ 兼容bash

　　zsh对于bash全面兼容，因此，切换成本较低。很多已有的脚本都可以兼容，这样就免去了很多后顾之忧。

+ 自动补齐功能较为方便 

　　个人是个非常懒的人。因此对于方便的自动补齐很是依赖。而zsh恰恰提供了这一点。可以补齐命令参数，并且支持更聪明的目录补齐，这无疑很吸引笔者。恰巧笔者的Bash补齐配置得非常不好，索性就直接切换到bash了。

　　更多的比较可以参考这篇《使用Zsh的九个理由》(http://www.linuxeden.com/html/develop/20120928/130477.html)

zsh以及oh-my-zsh的安装
----------------------

　　zsh在Gentoo下的安装较为简单直接按照wiki的指示输入命令就好：

    sudo emerge --ask zsh zsh-completion

　　此时最好再设置一下全局的USE标记，将zsh-completion加进去，这样以后会较为方便。之后就开始安装oh-my-zsh。oh-my-zsh是一个zsh主题、插件等的集合，包含了超过120个插件和各种主题，据说还可以自动更新。根据其主页(http://ohmyz.sh/)上的说明，只需输入如下命令即可安装：

    wget --no-check-certificate http://install.ohmyz.sh -O - | sh

　　安装完成后，会根据模板自动创建一个.zshrc文件。之后根据模板的说明自行设定就好了。

