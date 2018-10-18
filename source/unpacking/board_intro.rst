Board introduction
=========================================

.. contents:: Directory

LicheePi Zero Introduction
-----------------------------------------

Lichee pi Zero (hereafter referred to as Zero) is a delicate mini **Cortex-A7** core board/development board, which can be used for beginners to learn Linux or for product development.
Zero offers a wealth of peripherals (LCD, ETH, UART, SPI, I2C, PWM, SDIO...) and powerful performance (~24M~1.2G, 64MB DDR**) on a slightly longer SD card size (~ **45x26mm**).

Zero uses a compact PCB design that makes development and use very convenient:

- Inline breadboard
- Inline 40P RGB LCD
- Use OTG port for power supply and data transmission (virtual serial port, virtual Ethernet, etc.)
- Networking with stacked WiFi modules
- Direct patch

Zero provides **Mainline Linux** support. You can use any programming you are familiar with on Linux.

Zero prompt
-----------------------------------------

For the fresh man  that has just have zero, please see the following basic instructions first.：

1. Zero needs a card to start (or solder spi flash), please don't ask why plug in usb does not respond
#. The TF card slot is a rectangular slot above the lichee pi logo in the figure below.
#. After receiving the Zero, if you saw that there is a tin-connection on the main chip. Please don’t panic. This is the design (they use the same power pin)，Please see `schematic diagram <http://lichee.jicm.cn/doc/SCH_PCB/lichee_zero.pdf>`_
#. Zero's system debug serial port is UART0, which is the two pins labeled "U0T R" at the bottom right of the figure below.
#. The LED on the front of Zero is not flashing when it is powered on. Please don’t think that the LED is not bright after power-on is bad.
#. Zero's usb is OTG usb, which can supply power and communicate(such as usb virtual network port `sharing a network with a computer <http://bbs.ilichee.cc/t/tutorial-pc-share-network-to-zero-via-usb/55>`_)
#. The “G 5V” pin under the Zero usb port can be used as a power input, and can be powered by a 5V or lithium battery on the serial port.
#. The recommended method of soldering the two side pins is to solder down. The “G 5V” pin is recommended for up welding.
#. The recommended underlying debugging method is: usb to serial port small board connected to "U0T R" and "G 5V".
#. Recommended networking method：`usb virtual network port <http://bbs.ilichee.cc/t/tutorial-pc-share-network-to-zero-via-usb/55>`_ or `tf wifi <https://www.kancloud.cn/lichee/lpi0/327885>`_ ；Or use the `usb transfer network port HUB <https://item.taobao.com/item.htm?id=538814529688>`_ in Taobao shop
#. After all, Zero is the Cortex-A7 processor with G frequency, and the running temperature is 40~60°C. Please don't think that the chip's temperature in this range is short circuit.
#. Zero runs Linux with no-load current of about 100mA, full-load current of about 150~180mA, and LCD current of about 200~300mA. No card power-on current is about 50~60mA。

If you have any other questions after receiving the board, please add official  `TG group <https://t.me/joinchat/HH5CKkoLTnnxtdIl2U1Psg>`_. The answer to the group verification is... Please pick up the board and look at the silkscreen logo of the above chip, thank you.


Design block diagram
-----------------------------------------

.. figure:: https://box.kancloud.cn/fb63cd12ae1def9dd50710d2a32dc5c1_1095x740.png
  :width: 500px
  :align: center

Zero Physical photo
-----------------------------------------

.. figure:: https://box.kancloud.cn/aa69c26a162e043a1831f6693ec059d7_1024x768.jpg
  :width: 500px
  :align: center

.. figure:: https://box.kancloud.cn/f66b91d12d8a68d6fd65a70274205b19_1024x768.jpg
  :width: 500px
  :align: center

HDK
-----------------------------------------

Hardware parameter
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

- **CPU：** Allwinner V3S， ARM Cortex-A7, fastest 1.2GHz
- **RAM：** integrated 64MB DDR2
- Memory：
   + ReservedSOP8 SPI FlashPad（customizable patch 8~32MB SPI Nor Flash,128MB Nand Flash）;
   + On-board half-slot TF card holder, can be started by TF。
- Display：
   + General 40P RGB LCD FPC holder

      - Inline 40P 4.3/5/7 Inch screen（on-board backlight driver），50P 7/9 inchscreen can be inserted through the adapter plate
      - Resolution support 272x480, 480x800,1024x600 etc.
      - On-board resistive touch screen chip,support resistive screen
   + On-board RGB LED
- Communication Interface
   + SDIO x2,Can be used with the matching SDIO WiFi+BT module
   + SPI x1
   + I2C x2
   + UART x3
   + 100M Ether x1（include EPHY）
   + OTG USB x1
   + MIPI CSI x1
- Other interface
   + PWM x2
   + LRADC x1
   + Speakerx2 + Mic x1
- Electrical characteristics
   + Micro USB 5V power supply ； 2.54mm Pin 3.3V~5Vpower supply； 1.27mm stamp hole power supply 
   + output 3.3V 和 3.0V（AVCC），Optional input RTC voltage
   + 1GHz linux no-load operating current 90~100mA， full-load operating current ~180mA
   + storage temperature -40~125℃，Operating temperature -20~70℃

data sheet
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

| Download link：
| netdisc address：
| datasheet：
| schematic：
| package library：
   

Pin definition
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. figure:: https://box.kancloud.cn/cff378c6c891e69aa4a1b0ea02fe7f97_1063x638.png
  :width: 500px
  :align: center

.. note:: In the figure, TX RX of UART0 is reversed, which is subject to the silk screen on the board.。

