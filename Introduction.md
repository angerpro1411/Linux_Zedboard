# Deploying a Linux Distribution on the ZedBoard (Digilent)

## Objective
The objective of this tutorial is to deploy Linux distribution to **_Zedboard_** -a Digilent developpement board :
	- Create a simple project and implemented it on the FPGA
	- Use a Linaro(Ubuntu-base) root filesystem (ROOTFS)
	- Control our peripheral from software
	
	
## INTRODUCTION

The __Zedboard__ is a developpment kit who includes Xilinx Zynq-7000 SoC - a chip that contains dual-core ARM processor along with integrated peripherals as DDR controller, Ethernet, UART, DMA,...

## What makes Zynq special ?
What makes Zynq platform special compared to traditional Embedded Computers is the combination of an operating system on one side and the ability to develop custom hardware design on the other. 
Thanks to the AXI interface, we can use operating system to control pre-design IPs(provided by Xilinx) or even our custom hardware modules.
Another major advantage of Zynq over older FPGAs (as Nexys) is that we no longer need to use a portion of FPGA fabric to implement soft processor (a processor built using logic). This approach 
consumes logic resources,is typically less efficient than a hard processor (physically embedded in silicon) and hard to debug someways. 

## Linux - why ?
Linux supports multitasking, so even when we develop in C, the dual-core processor allows us to run two threads concurrently. More importantly, Linux comes with wide range of pre-build drivers(USB, Ethernet, I2C,...), fast time-to-market and allow us to focus on our main application. This approach minimizes reliance on Xilinx-specific APIs, which often change annually and lead to compatibility issues(an application that works in 2024 but not in 2025). 

## Petalinux - an option ?
Yes, Petalinux is a valid option to build our linux under Zedboard with full options of Xilinx and a lot of package to support PL as well as PS. However in this tutorial, we focus on minimal custom Linux  build for Zedboard.

## Linaro - why ?
According to the article "_Getting started with Embedded Linx - Zedboard (January 13, 2013)_" published by Digilent (manufacturer of Zedboard), the board currently supports two different Linux file systems, a BusyBox ramdisk and a Linaro Ubuntu distribution". So instead of using ramdisk who won't save any changes after power down Zedboard. We choose Linaro, the Linaro file system is a complete Linux distribution based on Ubuntu. It includes a graphical desktop that displays via the onboard HDMI port. Linaro executes from a separate partition on the SD card, and all changes made are written to memory. The utility of Linaro is that it will save files even after you power down and reboot the ZedBoard.
> ⚠️ _Note: Although Linaro supports a graphical desktop via HDMI, I have not successfully enabled it as of 27-07-2025._

## Next Steps
1. Develop hardware - Device tree file - FSBL(First stage boot loader)
2. Setup/Cross-compiling U-Boot
3. Setup/Cross-compiling the Linux kernel
4. Creating the bootfs
5. Setup BOOTFS - ROOTFS in SD card
6. Linaro - ubuntu for ROOTFS
