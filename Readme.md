#Realtek 802.11ac (rtl8812au) Linux Driver Version 4.3.8

The driver was originally from [Here](http://www.comfast.cn/upload/%E8%BD%AF%E4%BB%B6%E9%A9%B1%E5%8A%A8/%E7%BD%91%E5%8D%A1%E7%B1%BB/8812AU%20912%E3%80%817500AC/linux/RTL8812AU_linux_v4.3.8_12175.20140902.zip).  

I tweaked the Makefile a bit in order to compile it on Raspberry Pi, which is the default platform in this configuration, as well as make it compatible with dkms.

You should change the target platform in Makefile if you want to build it for different architecture.  

The driver was tested on **Raspberry Pi 2** under updated **ArchLinux ARM** for **Comfast CF-912AC**

Note that the kernel should has configuration as below[1]:
```
[*] Networking support --->
      <*>   Wireless --->
              <*>   cfg80211 - wireless configuration API
              <*>   Generic IEEE 802.11 Networking Stack (mac80211)
      <*>   RF switch subsystem support --->
    Device Drivers --->
      [*] Network device support --->
            [*]   Wireless LAN --->
                    <M>   Realtek rtlwifi family of devices --->
                            <M>   Realtek RTL8821AE/RTL8812AE Wireless Network Adapter
                            <M>   Realtek RTL8192CU/RTL8188CU USB Wireless Network Adapter
      [*] Staging drivers --->
            <M>   Support for rtllib wireless devices
            <M>     Support for rtllib CCMP crypto
            <M>     Support for rtllib TKIP crypto
            <M>     Support for rtllib WEP crypto
            <M>   Realtek RTL8723AU Wireless LAN NIC driver
            [*]     Realtek RTL8723AU AP mode
            [*]     Realtek RTL8723AU BlueTooth Coexistence
```
otherwise the driver will not be `modprobe`d properly.

#Install:
```
git clone https://github.com/meoow/dkms-rtl8812au.git

sudo cp -r dkms-rtl8812au/8812au-4.3.8 /usr/src

sudo dkms install 8812au/4.3.8
```

[1]: https://wiki.gentoo.org/wiki/AC1200_Wireless_Adapters