Uboot compilation
===================================

.. contents:: directory

compilation
-----------------------------------

Install cross compiler
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

address ：https://releases.linaro.org/components/toolchain/binaries/latest/arm-linux-gnueabihf/

.. code-block:: bash

   wget https://releases.linaro.org/components/toolchain/binaries/latest/arm-linux-gnueabihf/gcc-linaro-6.3.1-2017.05-x86_64_arm-linux-gnueabihf.tar.xz
   tar xvf gcc-linaro-6.3.1-2017.05-x86_64_arm-linux-gnueabihf.tar.xz
   mv gcc-linaro-6.3.1-2017.05-x86_64_arm-linux-gnueabihf /opt/
   vim /etc/bash.bashrc
   # add: PATH="$PATH:/opt/gcc-linaro-6.3.1-2017.05-x86_64_arm-linux-gnueabihf/bin"
   source /etc/bash.bashrc
   arm-linux-gnueabihf-gcc -v
   sudo apt-get install device-tree-compiler

Download and compile Uboot
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
   
.. code-block:: bash

   git clone https://github.com/Lichee-Pi/u-boot.git -b v3s-current
   #or git clone https://github.com/Lichee-Pi/u-boot.git -b v3s-spi-experimental
   cd u-boot
   make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- LicheePi_Zero_800x480LCD_defconfig
   #or make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- LicheePi_Zero480x272LCD_defconfig
   #or make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- LicheePi_Zero_defconfig
   make ARCH=arm menuconfig
   time make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- 2>&1 | tee build.log

After the compilation, u-boot-sunxi-with-spl.bin is generated in the current directory, which can be burned to the 8K offset.。

Uboot directory Structure introduction 
-----------------------------------------


:: 

   ├── api                Store the API interface functions provided by uboot
   ├── arch               Platform related parts, we only need to care about the ARM folder in this directory
   │   ├──arm
   │   │   └──cpu
   │   │   │   └──armv7
   │   │   └──dts	
   │   │   │   └──*.dts   Store the dts of device, which is the device configuration related pin information.
   ├── board              Code for the development board for different platforms
   ├── cmd                Most of the implement of commands  are under this folder.
   ├── common             Public code
   ├── configs            The corresponding configuration files for each board are inside, and our Lichee configuration is also inside.
   ├── disk               Some operations on the disk are in this folder, such as partitions.
   ├── doc                there are a lot of usage documents related to the platform.
   ├── drivers            A wide variety of driver files are in it
   ├── dts                A tree structure (device tree) ,this should be uboot new syntax
   ├── examples           Some sample programs given by the official
   ├── fs                 File system, some file systems that uboot will use
   ├── include            Header file, all header files are under this folder
   ├── lib                Some commonly used library files are under this folder
   ├── Licenses           It is a statement of some licenses.
   ├── net                Small network protocol stack
   ├── post               Power-on self-test program
   ├── scripts            Compile scripts and Makefiles
   ├── spl                second program loader
   ├── test               Small unit test program.
   └── tools              There are a lot of tools commonly used by uboot.

Understand the basic structure of uboot, we can know where some related configurations are.。

- Lichee's uboot configuration file is placed under the confgs-file-directory，called

:: 

   LicheePi_Zero_480x272LCD_defconfig 
   LicheePi_Zero_800x480LCD_defconfig 
   LicheePi_Zero_defconfig

These 3 configurations are configured according to different Zero display devices. You can use one of them to execute commands in the uboot directory.

   ``make LicheePi_Zero_defconfig``

The configuration will take effect.
