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
![Image01.png](https://github.com/FYSETC/FYSETC-Voron-0.2-Pro/blob/main/Docs/Manuals/Image01.png)
If not, please go back and check the power supply and wiring of the motherboard to ensure that each power indicator light is on.
![Image02.png](https://github.com/FYSETC/FYSETC-Voron-0.2-Pro/blob/main/Docs/Manuals/Image02.png)


Enter the following command to get the board ID:
```
ls /dev/serial/by-id
```
Copy the ID with Crtl+C
![Image03.png](https://github.com/FYSETC/FYSETC-Voron-0.2-Pro/blob/main/Docs/Manuals/Image03.png)


Use the browser to enter the IP address of the Raspberry Pi to enter the mainsail interface
Click on MACHINE
Click printer.cfg in the list to enter the editing interface
![Image04.png](https://github.com/FYSETC/FYSETC-Voron-0.2-Pro/blob/main/Docs/Manuals/Image04.png)

Replace the ID in the [mcu] section
![Image05.png](https://github.com/FYSETC/FYSETC-Voron-0.2-Pro/blob/main/Docs/Manuals/Image05.png)

Click SAVE & RESTART

If it goes well, the system will automatically jump to Dashboard, and you can see the temperature curve

## 6.3.1 Build Firmware Image


* Login to the Raspberry Pi via ssh
* Run the following:

   ```
   cd ~/klipper
   make clean
   make menuconfig
   ```

* In the menu structure there are a number of items to be selected.
  * Select "Enable extra low-level configuration options"
  * Set the micro-controller architecture is set to `STMicroelectronics STM32`
  * Set the Processor model to `STM32F446`
  * **Many people have been unable to connect to the MCU because of the bootloader problem, so we recommends choosing a mode without a bootloader.**
  * Set the Clock Reference to `12 MHz crystal`
  * Set the Communication interface to `USB (on PA11/PA12)`  

   ![9b3101cfbb31b68bd3cda3e6878cf448.png](en-resource://database/1882:1)
   

* Once the configuration is selected, press `q` to exit, and "Yes" when  asked to save the configuration.

* Run the command `make`
* The `make` command, when completed, creates a firmware file **klipper.bin** which is stored in the folder `/home/pi/klipper/out`.  

## 6.3.2 Firmware Installation

* Requires a USB connection
* Requires the installation of an extra jumper on the Cheetah V3 ( short the 3V3 and BT0)
* Does NOT require a microSD card

1. Power off the Cheetah V3
2. Install a jumper between BT0 and 3V3
3. 
![8bb85aaaaf1bed3609ff19f9f13fac75.png](en-resource://database/1890:0)

3. Connect Cheetah V3 & Pi via USB
4. Power on Cheetah V3
5. From your ssh session, run
    ```
    cd ~/klipper
    ```
    to make sure you are in the correct directory
6. Run 
    ```
     lsusb
    ```
    and find the ID of the DFU device.
    
    ![efb145905fa37660bb29c28affcc7027.png](en-resource://database/1886:1)
    
7. Run 
    ```
     make flash FLASH_DEVICE=0483:df11
    ```
    In general, the DFU mode of STM32 is this ID, if not, replacing 0483:df11 with the ID from the previous step
 8. If everything goes well, you will see the words SUCCESSFUL.
 9. 
 ![d300f8722e45ba04aae9e33dfda1b90c.png](en-resource://database/1888:1)
 
    
8. Power off the Cheetah V3

9. Move the jumper to BT0 & GND (When the STM32 is turned on, BT0 should be at a low level, and it is also possible to hang it in the air, but in order to avoid unpredictable problems, it is better to short-circuit BT0 and GND here, which is more secure.)

![3132e64b7c567b0084b277cb47473bed.png](en-resource://database/1892:0)


10. Power up the Cheetah V3

11. You can confirm that the flash was successful by running `ls /dev/serial/by-id`.  If the flash was successful, this should now show a klipper device, similar to:
 
     ![10e22edf56283ce3aa5eae4333bda754.png](en-resource://database/1884:1)
  

   (note: this test is not applicable if the firmware was compiled for UART, rather than USB)


**Important:** If the Cheetah V3 is not powered with 12-24V, Klipper will be unable to communicate with the TMC drivers via UART and the Cheetah V3 will automatically shut down.


## 7. Community

[Voron community](https://discord.gg/voron)

[FYSETC Facebook group](https://www.facebook.com/groups/238970713918171)

## 8. Buy link

[Aliexpress](https://www.aliexpress.us/item/3256805148633512.html?spm=a2g0o.store_pc_allProduct.8148356.5.7ec130ddrDKLzx&pdp_npi=2%40dis%21USD%21US%20%24450.12%21US%20%24369.10%21%21%21%21%21%402133f17c16793803412868250ef06b%2112000032671170252%21sh&gatewayAdapt=glo2usa&_randl_shipto=US)
