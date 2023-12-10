# ebus2usb - 1TE DIN Rail eBUS to USB Type-C Interface

eBUS is a serial 2-wire serial data-bus, often used in heating, solar energy, and other building automation systems. This project provides an interface to access an eBUS via USB.
It uses a series transistor regulator circuit with a low IZT zener diode to extract the operating voltage from the eBUS, an ADuM1201 for the galvanic isolation, and a STM32 microcontroller for the UART to USB conversion.
Power consumption on the eBUS side is between 475uA (eBUS low/8V) and 750uA (eBUS idle high/24V), making the interface qualify as a class 0 device with respect to the eBUS specification.
It has been designed to fit into an [CNMB/1/2](https://www.camdenboss.com/camden-boss/cnmb12-din-rail-module-box%2c-polycarbonate-enclosure%2c-industrial-iot-electronics-housing/c-23/p-18541) 1TE DIN rail enclosure by CAMDENBOSS. The interface is intended to be used with [ebusd](https://github.com/john30/ebusd/). Note that the firmware is currently just a proof-of-concept and only implements a basic uart to USB bridge. Support for the ebusd enhanced protocol is planned for the near future.

![Images](ebus2usb-img-v1.0.jpg)

## Schematic

![Schematic](./ebus2usb-sch.png)

## PCB Layout

![PCB Layout](./ebus2usb-pcb.png)

When ordering at JLCPCB, remove the mouse bites and cut the boards yourself. Otherwise JLCPCB will charge you for two designs.

## BOM

|Designator|Footprint|Quantity|Value|LCSC Part #
|:---|:---|:---|:---|:---
|C1, C2, C7|C0805|3|10u|C15850
|C10, C3, C4, C5, C6, C8, C9|C0603|7|100n|C14663
|C11, C12|C0805|2|1u|C28323
|D1, D2, D4|SOT-23-3|3|BAV99|C2500
|D3|SOD-123|1|5V6, Onsemi MMSZ4690*|C152307
|D5|SOD-123|1|24V/1W, KDZVTR24B, MM1W24|C209605, C438336
|D6|SOD-123|1|7V5/1W, KDZVTR7.5B, MM1W7V5|C209594, C382950
|D7|LED_0603|1|LED|C72043
|D8, D9, D10|D3.0mm|3||[CHANZON 3mm diffused LED](https://www.aliexpress.com/item/1936229691.html)
|J1|MSTBA_2,5_2-G-5,08|1|MSTBA 2,5/2-G-5,08|C3697
|J2, J6|Molex_PicoBlade_53047-0210|2|Molex 53047-0210|C114130
|J3, J7|Molex_PicoBlade_53047-0410|2|Molex 53047-0410|C504989
|J5|HRO_TYPE-C-31-M-12|1|HRO TYPE-C-31-M-12|C165948
|J8|PinHeader_1x02_P1.27mm|1|Harwin M50-3530242|C2881948
|Q1, Q2|SOT-23-3|2|BC817-40, S9013J3|C52801, C6749
|R1, R2, R3|R0603|3|100K|C25803
|R10|R0603|1|47K|C25819
|R12, R13|R0603|2|5K1|C23186
|R14|R0805|1|100K|C149504
|R15, R16|R0805|2|15K|C17475
|R4|R0603|1|4K7|C23162
|R5|R0603|1|300K|C23024
|R6|R0603|1|51K|C23196
|R7|R0603|1|2M|C22976
|R8|R0603|1|10K|C25804
|R9|R0603|1|0R|C21189
|U1|SO08|1|AZV3002, TSX3702|C5123396, C2970396
|U2|SO08|1|ADuM1201, π122U31|C9669, C471590
|U5|SOT-23-6L|1|SRV05-4|C85364
|U6|SOT-23-3|1|XC6206P332MR|C5446
|U7|LQFP-32|1|STM32L412KBT6, STM32F042K6T6|C529438, C69216

\* Low IZT of 50uA is required. Other manufacturers than Onsemi may not qualify. For example, MMSZ4690 from Jiangsu Changjing Elec. Tech. is not recommened.