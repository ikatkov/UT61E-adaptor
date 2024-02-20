# UNI-T UT61E RS232 serial interface cable to USB

## Instructions
Connect RTS to ground(Pin 5 and Pin 7), DTR to 5V or 3.3V and invert the output with 74hc14 and you have TTL output. This will work at 5V and 3.3V.

<img src="USB-to-TTL-Serial.png" width="200"/>
<img src="RS232-9-pin-pinout.jpg" width="200"/>

## Schematic
<img src="schematic.jpg" width="500"/>

## Enclosure
<img src="enclosure.jpg" width="500"/>

## Assembly
<img src="assembly.jpg" width="500"/>

## Windows Software
* Install CH430 driver
* reboot
* install [UNI-T-61E-ver-41.zip]
* Launch
* Connect to the right COM* port in the UI

## Mac / Python 

```
cd <to project folder>
python3 -m venv venv
source venv/bin/activate
pip install ut61e
```

UT61E communication config: `19200, 7 bits, odd parity, 1 stop bit`

Plug the multimeter and turn it on. Look up the serial port with `ls /dev/cu.usbserial*`

On Mac/Linux pipe the serial port to `es51922` with

`(stty speed 19200 cs7 parenb -cstopb >/dev/null && cat) </dev/cu.usbserial-1440 |  es51922`

Parameters
```
    cs8                  Use 8 character bits
    parenb               Use a parity bit
    -cstopb              Don't use 2 stopbits, but just the regular 1
```

Output looks like

```
23:39:55.027797 0 V
23:39:55.027918 0.0006 V
23:39:55.027982 0.0006 V
23:39:55.469333 0.0002 V
23:39:55.969201 0.0002 V
23:39:56.469036 0.0001 V
23:39:56.968968 0.0001 V
23:39:57.468980 0.0001 V
23:39:57.969000 0.0014 V
23:39:58.469146 0.0008 V
23:39:58.969176 0.0008 V
23:40:00.068802 55.05 mV
23:40:00.568895 115.32 mV
23:40:01.068662 157.1 mV
23:40:01.568860 179.99 mV
23:40:02.068693 192.64 mV
23:40:02.568551 204.68 mV
23:40:03.068395 225.4 mV
23:40:03.568472 -121.83 mV
23:40:04.068386 -89.45 mV
```