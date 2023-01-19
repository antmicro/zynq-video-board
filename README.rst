================
Zynq Video Board
================

Copyright (c) 2018-2023 `Antmicro <https://www.antmicro.com>`_

.. image:: Images/zvb.png
   :scale: 40%

Overview
========

This repository contains open hardware design files required to build the Zynq Video Board.
The board was designed as a custom carrier board for `Enclustra Mars SoC Modules <https://www.enclustra.com/en/products/system-on-chip-modules>`_.
It has been tested with `Mars ZX2 <https://www.enclustra.com/en/products/system-on-chip-modules/mars-zx2/>`_ and `Mars ZX3 <https://www.enclustra.com/en/products/system-on-chip-modules/mars-zx3/>`_ with the `Xilinx Zynq 70xx <https://www.xilinx.com/products/silicon-devices/soc/zynq-7000.html>`_ All Programmable SoC devices.

It can be used for interfacing MIPI CSI compatible image sensors.
It can also act as a simple evaluation kit for educational purposes.

Key features
============

* SO-DIMM connector supporting Enclustra Mars family
* Gigabit Ethernet RJ45 connector
* Micro SD connector
* USB 2.0 hub with two downstream ports exposed
* HDMI output interface
* Debug micro USB connector (supporting serial console and JTAG)
* JTAG connector supporting Xiling Platform Cable
* 2x MIPI CSI-2 camera interfaces (2 lanes) exposed on FPC connector
* onboard D-PHY receiver circuitry connected to the FPGA fabric
* 2x Digilent Pmod (TM) connectors for external accessories

The PCB project files were prepared in Altium Designer 14.1.

Getting started
===============

The board can be produced and assembled using the provided design files.
Please take a look at the mechanical layers for more information regarding the PCB stackup recommended for fabrication.
It is recommended to use a 12V 2A DC supply to power the board.
By default the device boots from an SD card.
The boot mode could be changed into booting from QSPI flash by removing the ``R7`` resistor and assembling ``R8``.

Preparing the software
----------------------

The Zynq Video Board is compatible with Enclustra Mars modules which are natively supported by the `Enclustra Build Environment <https://github.com/enclustra-bsp/bsp-xilinx>`_ (EBE) which is developed by Antmicro for Enclustra.
Please refer to the EBE documentation and Zynq Video Board schematics in order to prepare the software that could support your hardware configuration.
Also, please note that Mars ZX2 and Mars ZX3 differ in FPGA ball assignment so they require different constraint files for bitstream generation.

Debug UART connection
---------------------

Most of the debug messages are provided through the serial console.
The board is equipped with a multichannel FTDI chip offering both JTAG and UART interfaces to the host PC.
Please refer to the schematic sheets for more details.
After connecting the micro USB debug port to the host PC you should see four new ``/dev/ttyUSBx`` devices in your system.
The default debug UART channel is accessible through ``/dev/ttyUSB2`` (assuming that there are no other FTDI units connected to your PC).
The default baudrate for serial debug connection is 115200 baud with 8-bit transmission, 1 stop bit and with no flow control.

License
=======

`Apache-2.0 <LICENSE>`_
