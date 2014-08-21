This is a port of Realtek's own 8192CU driver for USB WiFi devices on Ubuntu 13.10 and later.

Installation
============

This package is include by linux-image-ev3dev. It should already be installed on ev3dev-jessie.

Troubleshooting
===============

There is a known issue with power management on some hardware. If your WiFi connection drops after a few minutes, edit the following module setting file to disable power management in your WiFi interface:

    /etc/modprobe.d/8192cu-disable-power-management.conf

And remove the comment from the following line:

    options 8192cu rtw_power_mgnt=0 rtw_enusbss=0

And then reboot.

Current status
==============

As it currently stands, the driver doesn't populate /proc with informational data from the driver. The API for /proc has changed in recent kernels, and the driver hasn't yet been ported to the new API.

This driver is known to work with some RTL8192CU devices like the Belkin N300, and should work with some 8188CUS, RTL8188CE-VAU and RTL8188RU devices as well. However, it is known not to work well with devices using dual antennas, such as the TP-Link WN8200ND, due to an incomplete MIMO implementation in the upstream driver.

Credits
=======

This repository was initially based on Timothy Phillips's work as published here: https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/, though no longer.

Thanks go to Saqib Razaq (@s-razaq) for the power management workaround.
