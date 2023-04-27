# FYSETC-Voron-0.2-Pro

This is a project from the VORON community, VORON 0.2. We made a little upgrade and improvement on the basis of this project, and provided a complete set of information. Thanks to the open source materials and support provided by the VORON community, and hope you like it. You can find Voron official information below.

1.VORON 0.2 Official website：https://vorondesign.com/voron0.2

2.VORON 0.2 Official Github：https://github.com/VoronDesign/Voron-0

![](https://github.com/FYSETC/FYSETC-Voron-0.2/blob/main/VORON02.jpg)

## 1. Kit advantages:

1.VORON 0 1.3-inch OLED display

2.One-piece CNC hotbed holder 

3.Tophat cover (you can lift the top cover at any time for more convenient maintenance)

4.Sensorless Homing 

5.Upgrade MINI Stealthburner head

6.CNC Lightweight Gantry

7.Print surface: high-quality powder PEI steel plate, good adhesion, flexibility, easy to take molds; platform: MIC6 aluminum finishing, flatness up to 0.05, attached to high-temperature soft magnetic, and additionally designed positioning pillars, which can be fast Place the steel plate in place and not easily move.

8.Tornado hotend, check the features [here](https://github.com/FYSETC/FYSETC-Voron-0/blob/main/Tornado_hotend.md). (Please installation guide on our [youtube](https://www.youtube.com/watch?v=a5HArBp4h3s))

9.Provide a complete set of crimped terminal Teflon wires, suitable in length, plug and play, and easy to use.

10.It adopts high-precision Stainless steel 440c linear guide, precise position and stable operation

11.Imported silicone thermal mattress, high temperature resistance, built-in over-temperature fuse, high power 24V 75W, fast heating.

12.High-quality motors.

13.Contains VORON V0 UMBILICAL FRAME and VORON V0 UMBILICAL TOOL HEAD

14.Use Klipper firmware
Running on Cheetah v3.0 and Raspberry Pi 4 2GB, it can achieve higher printing speed, provide Web control (via WiFi or Ethernet), can connect to a camera.

## 2. BOM

Check [here](https://github.com/FYSETC/FYSETC-Voron-0.2/blob/main/BOM.md).

## 3. Modified STLs (2023.03.03)



So we modify these STLs base on the originals. You can find them in our `github` or `gitee`.

`FramePCBCover X1.stl` : For VORON V0 UMBILICAL FRAME[github](https://github.com/FYSETC/FYSETC-Voron-0.2/blob/main/STL/ADD/FramePCBCover%20X1.STL)

`ToolheadSpacer_with_StrainRelief X1`:For VORON V0 UMBILICAL TOOL HEAD [github](https://github.com/FYSETC/FYSETC-Voron-0.2/blob/main/STL/ADD/ToolheadSpacer_with_StrainRelief%20X1.STL)

`VORON0.1 X2.stl` :For CNC Lightweight Gantry [github](https://github.com/FYSETC/FYSETC-Voron-0.2/blob/main/STL/ADD/VORON0.1%20X2.stl)

`LJY-B01 X1.stl`:For One-piece CNC hotbed holder [github](https://github.com/FYSETC/FYSETC-Voron-0.2/blob/main/STL/ADD/LJY-B01%20X1.STL)

`Drag Chain Spacer X1.stl`:For One-piece CNC hotbed holder Chain [github](https://github.com/FYSETC/FYSETC-Voron-0.2/blob/main/STL/ADD/Drag%20Chain%20Spacer%20X1.STL)


## 4. Installation Guide

### 4.1 VORON Assembly manual

Check it [here](https://github.com/VoronDesign/Voron-0/tree/Voron0.2/Manuals).

### 4.2 Tornado Hotend installation

Please check it on our [youtube](https://www.youtube.com/watch?v=a5HArBp4h3s).

## 5. Wiring

### 5.1 Pro kit

Following is our Cheetah v3.0 board wiring diagram for VORON 0.2 pro kit.

![](https://github.com/FYSETC/FYSETC-Voron-0.2-Pro/blob/main/Fysetc%20Voron%20V0.2%20umbilical%20Wiring.png)

## 6. Firmware&OS


After you finish assembling and inspecting, be sure to wire according to the wiring diagram, and make sure that all positive and negative poles are not reversed before powering on. If you have a multimeter, it is best to check again that the power input port is not short-circuited.
Next we start configuring the firmware:
### 6.1. Install the Raspberry Pi

There is a Micro SD Card with the mainsail OS system burned in our kit. The capacity is 16GB. You need to insert it into the card slot of the Raspberry Pi, and connect the Raspberry Pi to the main board with a USB cable and a power cable (it is a 6-core Dupont cable, which contains a serial port, but the power supply is made by default, and the serial port is a spare).

If you need to reinstall the system, you can refer to the following link:
https://docs-os.mainsail.xyz/getting-started/raspberry-pi-os-based

### 6.2. Configure the Cheetah Board

Use SSH software to connect to your Raspberry Pi and enter the following command:
```
lsusb
```
You should see the device as shown below:
![Image01.png](./Docs/Maunal/Image01.png)
If not, please go back and check the power supply and wiring of the motherboard to ensure that each power indicator light is on.
![b0b11e53b1c7c9934983083631e95df1.png](en-resource://database/1856:1)


Enter the following command to get the board ID:
```
ls /dev/serial/by-id
```
Copy the ID with Crtl+C
![5bbf203144212eed07b432f400ad4a0e.png](en-resource://database/1858:1)


Use the browser to enter the IP address of the Raspberry Pi to enter the mainsail interface
Click on MACHINE
Click printer.cfg in the list to enter the editing interface
![3d369e7bf9beca125dcf7af544db77db.png](en-resource://database/1864:1)

Replace the ID in the [mcu] section
![63e00fd5cd6aafbb8f8f5369ac4adac8.png](en-resource://database/1862:1)

Click SAVE & RESTART

If it goes well, the system will automatically jump to Dashboard, and you can see the temperature curve


## 7. Community

[Voron community](https://discord.gg/voron)

[FYSETC Facebook group](https://www.facebook.com/groups/238970713918171)

## 8. Buy link

[Aliexpress](https://www.aliexpress.us/item/3256805148633512.html?spm=a2g0o.store_pc_allProduct.8148356.5.7ec130ddrDKLzx&pdp_npi=2%40dis%21USD%21US%20%24450.12%21US%20%24369.10%21%21%21%21%21%402133f17c16793803412868250ef06b%2112000032671170252%21sh&gatewayAdapt=glo2usa&_randl_shipto=US)
