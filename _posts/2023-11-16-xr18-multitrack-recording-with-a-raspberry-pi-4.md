---
title: "XR18 multitrack recording with a Raspberry PI 4"
date: 2023-11-16
layout: post
tags: [dev]
---

During the summer I had the chance to be able to buy one of those wonderful [XR18](https://www.behringer.com/product.html?modelCode=P0BI8) (18 input/12 bus portable audio mixer) and I'm very excited about it !

The main reason I bought this little gem is to be able to make multitrack live concert recordings. The fact that it's compatible with [OSC](https://opensoundcontrol.stanford.edu) is a great advantage too.

So, I decided to record a live concert of one of my Blues Band ([Blue Time Shakers](https://www.facebook.com/bluetimeshakers)) during the famous [braderie de Lille](https://en.wikipedia.org/wiki/Braderie_de_Lille) as we were playing oi the street on that day.
The XR18 outputs multi-channels audio using USB-Audio protocol. I first thought of bringing a PC to record the multichannel stream, but it's not very comfortable, especially as we were playing in the street, and the probability that someone quite drunk come around the hardware was quite big ! After a quick search I've seen that someone had succeeded using a Raspberry Pi 3 to record 16 tracks in WAV format, but this was [limited to 8 minutes](https://github.com/danielappelt/caPiture/issues/3), after what problems started to appears.

Long story in short: I started form this [caPiture](https://github.com/danielappelt/caPiture) project and optimized it in some points to make recording more stable:
- using [systemd]() instead of `.profile` greatly improve the global stability of the recording subprocess
- recording in [FLAC format](https://xiph.org/flac) decrease the writes rates to the SD card (bottleneck of the multitrack recording process). The Raspberry PI 4 can handle this 16-tracks FLAC compression very sweet, as it haves 4 cores and [jack_capture](https://github.com/kmatheussen/jack_capture) makes advantage of parallelization

I was very happy to be able to use my tiny little Pi mini computer as a portable multitrack recorder, and the overall sound quality is more than satisfying !

![](/assets/images/XR18-1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
