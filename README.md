# STM32F4 LwIP TCP/IP
Development of an application running Internet communication based on a STM32F4 Discovery kit.

## Development Environment  
The exact processor version mounted on the kit is a STM32F407VG. This version comes packed in a 100 pins LQFP and has 1 M (bytes) of flash. My current kit's are marked with a sticker that says C-01 and I assume that this indicates revision C.1.  

It is possible to develop C and C++ code for STM32F4 by the use of [GNU ARM Eclipse](http://gnuarmeclipse.github.io/install/ "GNU ARM Eclipse"). This environment is used for this project.  

Toolchain version used is [gcc-arm-none-eabi-4_9-2015q3](https://launchpad.net/gcc-arm-embedded/+download "gcc-arm-none-eabi-4_9-2015q3"). 

## Blocking VS Non-Blocking
A socket can be setup to be either blocking or non-blocking.  

A socket set to blocking will not take control of the system and not release it until some event happens. For example when you call receive to read from a stream, control isn't returned to your program until at least one byte of data is read from the remote site. This process of waiting for data to appear is referred to as "blocking".  

A socket placed in non-blocking mode, means that we are free to do other things without having to stop and wait for an operation to complete.

## LwIP Configuration  
All LwIP based projects contain a configuration file named lwipopts.h. Any missing option from this configuration file can be imported (copy/paste) from a file called opt.h.  
