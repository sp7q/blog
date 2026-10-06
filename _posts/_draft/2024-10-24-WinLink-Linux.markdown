---
published: false
published: false
layout: post
title:  "Winlink + Linux + IC-705"
date:   2024-10-24 12:00:00 +0200
categories: Hamradio
tags: winlink IC705 HF linux
---

(Not quite) Great fun and frustration (: - unfortunately, most users are Windows-based and that is who the WinLink software is targeted at. It took me a bit of time to put it all together into a working whole. I was also motivated to push the topic forward by the purchase of a Banana Pi M4 Zero - which outclasses its raspberry-branded competitor. The 705 + a small SBC means we have a powerful tool in our hands for radio experiments with whatever modes come to mind.

Linux has a great, minimalist Winlink client = PAT.

You can find the project page here: https://getpat.io/

Installation on Armbian is the classic:

sudo apt-get install pat

After installation, you need to configure the client:

pat-winlink configure

I connect to the client via HTTP. It's also worth noting that the default setting is "http_addr": "localhost:8080", meaning the client only accepts connections from our Banana Pi. To be able to log in from the outside, you need to set "http_addr": ":8080".

Let's fire up the client:

pat-winlink http

The client is accessible via a web browser at http://your_device_ip:8080

Telnet session example:

Time to tackle the radio part.
First, we need to compile the modem ourselves. You can download the sources from: https://github.com/hamarituc/ardop

The modem supported by WinLink is ARDOPC

cd ARDOPC
make
sudo cp arcopc /usr/local/bin (Note: arcopc is likely a typo in the original text for ardopc)

Let's check what sound cards we have available:

arecord -l

In my case it is:

**** List of CAPTURE Hardware Devices ****
card 0: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

We create an .asoundrc file in the home directory and add:

pcm.ARDOP {
  type rate
  slave {
    pcm "plughw:0,0"
    rate 48000
  }
}
Let's fire up ardop:

The modem is waiting for a connection on its standard port 8515, which we configured earlier in PAT.

We also need to control the radio, this is where rigctl comes in handy:

rigctld -m 3085 -s 115200 -r /dev/ttyACM0 -t 4532

We are ready for our first radio session!

Our session: