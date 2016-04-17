Single Channel LoRaWAN Gateway
==============================
This repository contains a proof-of-concept implementation of a single
channel LoRaWAN gateway.

It has been tested on the Raspberry Pi platform, using a Semtech SX1272
transceiver (HopeRF RFM92W), and SX1276 (HopeRF RFM95W).

Also, [NiceRF LoRa1276 modules](http://goo.gl/CqBBWU) supported

The code is for testing and development purposes only, and is not meant 
for production usage. 

Part of the source has been copied from the Semtech Packet Forwarder 
(with permission).

Maintainer: Thomas Telkamp <thomas@telkamp.eu>

Features
--------
- listen on configurable frequency and spreading factor
- SF7 to SF12
- status updates
- can forward to two servers

Not (yet) supported:
- PACKET_PUSH_ACK processing
- SF7BW250 modulation
- FSK modulation
- downstream messages (tx)

Dependencies
------------
- SPI needs to be enabled on the Raspberry Pi (use `raspi-config`)
- WiringPi: a GPIO access library written in C for the BCM2835 
  used in the Raspberry Pi.
  `sudo apt-get install wiringpi`
  see http://wiringpi.com
- Run packet forwarder as root
  `sudo ./single_chan_pkt_fwd`

Connections
-----------

Raspberry Pi | pin | SX1276
| :---:| :---: | :---: |
3.3v | 1  | VCC
GND  | 6  | GND
SPI0 MOSI | 19 | MOSI
SPI0 MISO | 21 | MISO
SPI0 SCLK | 23 | SCK
SPI0 CE0  | 24 | NSS
WiringPi GPIO0| 11 | RESET
WiringPi GPIO2| 13 | TXEN
WiringPi GPIO3| 15 | RXEN
WiringPi GPIO4| 16 | DIO0

Configuration
-------------

Defaults:

- LoRa:   SF7 at 868.1 Mhz
- Server: 54.72.145.119, port 1700  (The Things Network: croft.thethings.girovito.nl)

Edit source node (main.cpp) to change configuration (look for: "Configure these values!").

Please set location, email and description.

License
-------
The source files in this repository are made available under the Eclipse
Public License v1.0, except for the base64 implementation, that has been
copied from the Semtech Packet Forwader.
