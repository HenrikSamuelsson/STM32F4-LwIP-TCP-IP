# STM32F4 LwIP TCP/IP
Development of an application running Internet communication based on a STM32F4 Discovery kit.

## Development Environment  
The exact processor version mounted on the kit is a STM32F407VG. This version comes packed in a 100 pins LQFP and has 1 M (bytes) of flash. My current kit's are marked with a sticker that says C-01 and I assume that this indicates revision C.1.  

It is possible to develop C and C++ code for STM32F4 by the use of [GNU ARM Eclipse](http://gnuarmeclipse.github.io/install/ "GNU ARM Eclipse"). This environment is used for this project.  

Toolchain version used is [gcc-arm-none-eabi-4_9-2015q3](https://launchpad.net/gcc-arm-embedded/+download "gcc-arm-none-eabi-4_9-2015q3"). 

## Sockets  
A network socket is an endpoint of an inter-process communication across a computer network. Today, most communication between computers is based on the Internet Protocol; therefore most network sockets are Internet sockets.  

A socket API is an application programming interface (API), usually provided by the operating system, that allows application programs to control and use network sockets. Internet socket APIs are usually based on the Berkeley sockets standard.  

A socket address is the combination of an IP address and a port number, much like one end of a telephone connection is the combination of a phone number and a particular extension. Based on this address, internet sockets deliver incoming data packets to the appropriate application process or thread.  

## Blocking VS Non-Blocking
A socket can be setup to be either blocking or non-blocking.  

A socket set to blocking will not take control of the system and not release it until some event happens. For example when you call receive to read from a stream, control isn't returned to your program until at least one byte of data is read from the remote site. This process of waiting for data to appear is referred to as "blocking".  

A socket placed in non-blocking mode, means that we are free to do other things without having to stop and wait for an operation to complete.  

## LwIP API's
LwIP offers three different API's designed for different purposes:  
1. Raw API is the core API of LwIP. This API aims at providing the best performances while using a minimal code size. Events are handled asynchronously by the use of callbacks. When using the Raw API in a mufti-threaded environment, beware that there is no protection against concurrent access. Consequently, all the network part of the application must remain in a single thread context.  
2. Netconn API is a sequential API built on top of the Raw API. It allows mufti-threaded operation and therefore requires an operating system. It is easier to use than the Raw API at the expense of lower performances and
increased memory footprint.  
3. BSD Socket API is a Berkeley like Socket implementation (Posix/BSD) built on top of the Netconn API. Its interest is portability. It shares the same drawback than the Netconn API.  

## LwIP Configuration  
All LwIP based projects contain a configuration file named lwipopts.h. Any missing option from this configuration file can be imported (copy/paste) from a file called opt.h.  
