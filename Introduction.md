The objective of this tutorial is to deploy Linux distribution to **_Zedboard_** - Digilent card :
	- Create a simple project and implemented in FPGA
	- a Linaro(Ubuntu base) ROOTFS
	- Then control our peripheral from software
	
	
# INTRODUCTION

__Zedboard__ is a developpment kit who includes SoC Xilinx Zynq-7000, a chip has inside double cores ARM processor and also the peripherals as DDR controller, Ethernet, UART, DMA,...

The special of Zynq compares to Embedded Computer that we have operating system in one side, and another side, we can develop our matertial design. 
Thanks to AXI interface, we can use operating system to control available material design(by Xilinx) or even our design.
And another advantage of Zynq compares to old FPGA(Nexys), instead of using a part of FPGA to create soft processor (processor created by code), 
so we will lose logic resources but even less efficient than hard processor (real processor inlcuded on board) and hard to debug someways. 

# Linux - why ?
Linux supports multitasking so even when we develop in C, with 2 cores inside Zedboard, allows us to run 2 threads concurrently. But the best is Linux comes with wide range of pre-build drivers(USB, Ethernet, I2C,...), fast time-to-market and focus on our big application(not reli too much on Xilinx APIs - who changes every year and our last application who runs at 2024 but not 2025). 

# Linaro - why ?
Base on the article "Getting started with Embedded Linx - Zedboard (January 13, 2013)" of Digilent who fabrique Zedboard instead of Xilinx, "The ZedBoard currently supports two different Linux file systems, a BusyBox ramdisk and a Linaro Ubuntu distribution". So instead of using ramdisk who won't save any changes after power down Zedboard. We choose Linaro, the Linaro file system is a complete Linux distribution based on Ubuntu. It includes a graphical desktop that displays via the onboard HDMI port(I haven't succedded to do it 27-07-2025). Linaro executes from a separate partition on the SD card, and all changes made are written to memory. The utility of Linaro is that it will save files even after you power down and reboot the ZedBoard.

