---
title: "virt-manager - disable guests access to public internet but preserve their access to local (samba) network drive"
date: 2024-03-04
layout: post
tags: []
---

Today I had to use a windows virtual machine but:
- disable internet access
- enable local network access (especially for Samba access)

The libvirt online documentation gives us an answer for that: [isolated-mode](https://wiki.libvirt.org/VirtualNetworking.html#isolated-mode); and hopefully virt-manager allows us to acheive it easilly (but it's not abvious IMHO)

## How to use an isolated network using virt-manager

### Step 1 - create an isolated network

From the main virt-manager window (where we can see the VMs list)
- Edit -> Connection details
    - here we can configure differents networks that are accessible by every VMs
    - the default network is `virbr0` and every VM that is connected to this network **have** access to internet (if the host is connected of course)
- click on the ![](/assets/images/virt-manager/virt-manager-1.webp) `+` button on the bottom
    - set mode to `isolated`
- from here we've another network. Select it and note the bridge name (`virbr1`) in my case

### Step 2 - use this isolated network

Now we've this network available, we can use it with any existing or new VM:

![](/assets/images/virt-manager/virt-manager-2.webp){:.centered}

- guest will connect to this network and receive an IP adress from the virtual DHCP server (192.168.100.1 in my case, that is the host IP on this network)
- on the host side, another network is created (`ifconfig` can list it on Linux). In my case it's `virbr1`
- host and guest are now able to communicate on this network (`192.168.100` in my case)
