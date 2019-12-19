## How to confirm that the operating system has the recognition module?

> :warning: **When you can't see the VEGA module information by following methods, please checking your BIOS settings or try replace another VEGA module.** 

### Windows 

Step 1. Open "Device Manager" and check the USB devices

Step 2. Check how many Movidius MyriadX in it

VEGA-320: **m.2** Edge AI Module with **one** Intel® Movidius™ Myriad™ X VPU onboard

![image](https://github.com/ADVANTECH-EIoT/VEGA_Workshop/blob/master/photos/status_1.png)

VEGA-330: **miniPCIe** Edge AI Module with **two** Intel® Movidius™ Myriad™ X VPUs onboard

![image](https://github.com/ADVANTECH-EIoT/VEGA_Workshop/blob/master/photos/status_4.png)

**When you excute inference engine with VEGA, the USB device name will change to "VSC Loopback Device"**

VEGA-320: **m.2** Edge AI Module with **one** Intel® Movidius™ Myriad™ X VPU onboard

![image](https://github.com/ADVANTECH-EIoT/VEGA_Workshop/blob/master/photos/status_3.png)

VEGA-330: **miniPCIe** Edge AI Module with **two** Intel® Movidius™ Myriad™ X VPUs onboard

![image](https://github.com/ADVANTECH-EIoT/VEGA_Workshop/blob/master/photos/status_2.png)

### Linux

Step 1. Use demsg command to chek the VEGA module detect or not.

![image](https://github.com/ADVANTECH-EIoT/VEGA_Workshop/blob/master/photos/status_6.png)

Step 2. Use lsusb command to chek the VEGA module detect or not.

![image](https://github.com/ADVANTECH-EIoT/VEGA_Workshop/blob/master/photos/stauts_7.png)

**You can see there a 5 Movidius chips are detected, because there are one VEGA-320 and two VEGA-330 in this system**

![image](https://github.com/ADVANTECH-EIoT/VEGA_Workshop/blob/master/photos/stauts_8.png)
