# STM32F4 LwIP TCP/IP
Development of an application running Internet communication based on a STM32F4 Discovery kit.

## Development Environment  
The exact processor version mounted on the kit is a STM32F407VG. This version comes packed in a 100 pins LQFP and has 1 M (bytes) of flash. My current kit's are marked with a sticker that says C-01 and I assume that this indicates revision C.1.  

It is possible to develop C and C++ code for STM32F4 by the use of [GNU ARM Eclipse](http://gnuarmeclipse.github.io/install/ "GNU ARM Eclipse"). This environment is used for this project.  

Toolchain version used is [gcc-arm-none-eabi-4_9-2015q3](https://launchpad.net/gcc-arm-embedded/+download "gcc-arm-none-eabi-4_9-2015q3"). 

## LwIP Configuration  
All LwIP based projects contain a configuration file named lwipopts.h. Any missing option from this configuration file can be imported (copy/paste) from a file called opt.h.  
