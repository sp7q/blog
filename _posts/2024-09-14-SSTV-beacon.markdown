---
layout: post
title:  "SSTV Beacon"
date:   2024-09-14 12:00:00 +0200
categories: Hamradio
tags: SSTV
---

In a ham radio operator's drawer, there are always plenty of electronic parts lying around, often bought with some project in mind and then abandoned. Fortunately, they almost never go to waste; sooner or later, a completely different project will be created from them. That was the case this time; modules lying in the drawer, once bought for an Echolink gateway, served me for an SSTV-related project.

The Nano Pi NEO is a small SBC with dimensions of 4x4 cm; its advantage is a fully-fledged sound card with analog input and output (exactly what's needed for things like Echolink, for example).
You can find more information here, for example:
https://wiki.friendlyelec.com/wiki/index.php/NanoPi_NEO

A Chinese DRA818 module serves as the transmitting part: https://www.dorji.com/docs/data/DRA818V.pdf

Besides installing the system, we also need the imagemagick and pysstv packages.

Also, from a previous project, I already had a PCB prepared; the radio part is a typical DRA818 implementation.
As an image source, I used a simple webcam connected to a USB port; there is a plan to replace it with a camera integrated via GPIO.

We also need to define the pin that will serve as the PTT. The necessary help can be found here:
https://wiki.friendlyelec.com/wiki/index.php/WiringNP:_NanoPi_NEO/NEO2/Air_GPIO_Programming_with_C

I/O handling installation:

Bash
git clone https://github.com/friendlyarm/WiringNP
cd WiringNP/
chmod 755 build
./build
Below is the script that does all the "magic":

Bash
#!/bin/bash
echo "taking a photo"
fswebcam -r 640x480 --no-banner --no-subtitle 640x480.png
echo "changing resolution"
convert 640x480.png -resize 640x496\! nowy.png
echo "adding text"
convert nowy.png -font helvetica -pointsize 80 -fill red -draw "text 20,70 'SP7HACK'" -pointsize 40 -draw "text 20,110 'JO91RS'" -pointsize 30 -draw "text 20,145 '$(date)'" -pointsize 30 -draw "text 20,470 'Zapraszamy do Hakierspejs Łódź hs-ldz.pl'" hack.png
echo "generating SSTV"
python3 -m pysstv --mode PD120 --vox --fskid SP7HACK hack.png sp7hack.wav
echo "Setting radio to 433.4"
/bin/echo -n -e "AT+DMOSETGROUP=1,433.4000,433.4000,0000,5,0000\n\r" > /dev/ttyS1
echo "PTT ON"
/usr/local/bin/gpio mode 4 out
/usr/local/bin/gpio write 4 0
sleep 1
echo "Transmitting SSTV"
AUDIODEV=hw:2 play sp7hack.wav
echo "PTT OFF"
/usr/local/bin/gpio write 4 1
The whole thing can be used, for example, as a payload in a high-altitude balloon mission.

While visiting us at the Hackerspace, you can tune your radio to 433.400 and receive the images with a simple handheld radio and a phone app, for example: Robot36 - below are a few received images.