---
layout: post
title: Gentoo Linux 折腾随笔
---

折腾了一个星期Gentoo，感觉非常High。看着自己的系统由命令行直到图形界面，由不顺手到顺手，让人有种很欣喜的感觉。突然发觉，折腾的过程渐渐被淡忘了，特此记录下来。

中文tty
-------
　　以前使用Ubuntu就有这个问题，系统挂掉，需要使用tty的时候，发现很多目录都是中文的，在tty下就是乱码，完全没法进入。当时不懂如何去google，所以没能解决。这次Google了一下，网友推荐了一个可以实现中文tty环境的软件——fbterm。

　　首先,安装fbterm和fcitx-fbterm

```
emerge fbterm
emerge fcitx-fbterm --autounmask-write
emerge fcitx-fbterm
```

　　然后在.bashrc中设置在登录tty时自动运行fbterm

```
echo "[[ $(tty) == \/dev\/tty[0-9]* ]] && fbterm" >> ~/.bashrc
```

　　最后，在~/.fbtermrc中配置输入法

```
input-method=fcitx-fbterm
```

　　切换到tty后，登录，然后就可以看到中文输出了。
　　
Ubuntu迁移到Gentoo后加密主目录问题
--------------------------------
　　Ubuntu的安装过程中有加密主目录这一选项，但到了Gentoo下发现主目录已被加密，如何才能恢复原来的状态呢？
由于是迁移到Gentoo，所以我并不希望更换用户名和密码。这种情况属于较为容易处理的情况。
　　　
　　首先，安装ecryptfs-utils

```
emerge ecryptfs-utils
```
 
 　　然后，修改pam.d/system-auth文件，然后在auth required pam_unix.so 后面写

```
auth    required        pam_ecryptfs.so unwrap
```

　　接着，在password required pam_unix.so上面添加

```
password        optional        pam_ecryptfs.so
```

　　最后，在session required pam_unix.so之后写

```
session optional        pam_ecryptfs.so
```

　　重新登录，主目录就如愿出现了！

升级系统
--------

```
emerge --sync
emerge -avuDN --newuse world
emerge --ask --depclean
revdep-rebuild
```
