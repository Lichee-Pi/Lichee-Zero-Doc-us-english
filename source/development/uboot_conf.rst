Uboot 配置
===================================

.. contents:: directory

Content source： :menuselection:`贡献投稿篇 --> 投稿文章精选 --> Zero u-boot编译和使用指南`

Uboot Configuration command
-----------------------------------

   ``make ARCH=arm menuconfig``

.. figure:: https://box.kancloud.cn/c0bc403f54d5c23409af3dda76c6eb1e_1167x606.png
  :align: center

| ---Press Enter to select the current menu
| ------- Press Y for the config option to select
| ------- Press N to deselect this option
| -------- Press M to compile the driver into *.ko. After the system is booted, load it when the driver needs it.
| </>---------Press / to find some option
| ---------exit
| <*> ----------state which is selected by pressing Y 

**There are several common configuration options here. We can look at it:**

1. Architecture select , no doubt this is ARM architecture
2. ARM architecture This option is more important，Mainly configure common configuration functions under the ARM framework and parameters such as LCD

.. figure:: https://box.kancloud.cn/e6935388a45eb157a0267b5e0f566414_654x362.png
  :width: 500px
  :align: center

DDR configuration
-----------------------------------

.. code-block:: bash
   
   ...
   Target select (Support sunxi (Allwinner) SoCs)   Choose sunxi Soc series chip
   ...
   [*] Sunxi SoC Variant     This is the   choice of the chip Soc, we can see the config option `sun8i (Allwinner V3s)
   (360) sunxi dram clock speed            Config the clock rate of the dram
   (14779) sunxi dram zq value             Config the ZQ value of the dram to dynamically enhance DDR3.
   -*- Board uses DDR2 DRAM                Using DDR2 DRAM

LCD configuration
-----------------------------------

.. figure:: https://box.kancloud.cn/e3c46cc8756651c4cd7943b824939964_745x364.png
  :width: 500px
  :align: center

.. code-block:: bash
   
   [*] Enable graphical uboot console on HDMI, LCD or VGA                                       
   [ ] VGA via LCD controller support             Enable LCD controllers to support VGA through, it is the controller required for LCD and VAG conversion   
   (x:800,y:480,depth:18,pclk_khz:33000,le:87,ri:40,up:31,lo:13,hs:1,vs:1,sync:3,vmode:0) LCD pane
   > This option is the config option to configure the resolution of the LCD.Click Enter to change it.                      
   (1)   LCD panel display clock phase            This is the display clock phase of the LCD. 
   ()    LCD panel power enable pin               
   ()    LCD panel reset pin                                
   (PB4) LCD panel backlight pwm pin                    This should be the pin PB4 which can adjust brightness
   [*]   LCD panel backlight pwm is inverted            
   [ ]   LCD panel needs to be configured via i2c                        
       LCD panel support (Generic parallel interface LCD panel)  --->     Choose a supported LCDpanel
               (X) Generic parallel interface LCD panel                   
               ( ) Generic lvds interface LCD panel                       
               ( ) MIPI 4-lane, 513Mbps LCD panel via SSD2828 bridge chip 
               ( ) eDP 4-lane, 1.62G LCD panel via ANX9804 bridge chip    
               ( ) Hitachi tx18d42vm LCD panel                            
               ( ) tl059wv5c0 LCD panel         
   (0) GMAC Transmit Clock Delay Chain        

Clock frequency configuration
-----------------------------------

``Boot images --->(1008000000) CPU clock frequency``

Here sets the clock frequency of the CPU

Boot delay setting
-----------------------------------

``delay in seconds before automatically booting``

This is the number of seconds of waiting time when uboot is power on. It can be changed. The default is 2s.

SPL Configuration
-----------------------------------

.. code-block:: bash
   
   SPL / TPL ---> 
   [*]   MMC raw mode: by sector                     
   (0x50)  Address on the MMC to load U-Boot from 
   [*] Support GPIO                              
   [*] Support I2C                                
   [*] Support common libraries                   
   [*] Support disk paritions                     
   [*] Support generic libraries                  
   [*] Support MMC                                
   [*] Support power drivers                  
   [*] Support serial                               
   