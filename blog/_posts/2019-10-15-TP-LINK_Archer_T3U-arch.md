---
layout: post
author: Bruno
title: TP-LINK Archer T3U in Arch Linux
---

Recently I bought the [TP-LINK Archer T3U](http://en.techinfodepot.shoutwiki.com/wiki/TP-LINK_Archer_T3U) Wifi usb key (2357:012d). The [driver](https://github.com/jeremyb31/rtl8822bu) is not included in my current kernel (5.1.4-arch1-1-ARCH) so I tried to install it:

```sh
sudo pacman -S core/linux-headers gcc
yay -S aur/rtl8822bu-dkms-git
```

I came across [the problem described here](https://forum.manjaro.org/t/rtl8822bu-problem-installing-driver/104130)

The good news is that its works well for me with `5.3.6.arch1` kernel.
