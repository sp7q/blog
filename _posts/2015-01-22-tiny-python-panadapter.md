---
published: false
title: "Tiny Python Panadapter"
date: 2015-01-22T19:36:00.001Z
layout: post
---

<div class="separator" style="clear: both; text-align: center;">
</div>
<div class="separator" style="clear: both; text-align: center;">
<img border="0" src="/images/iq.jpg" height="266" width="400" /></div>
Jedną z naprawdę nieocenionych funkcji Elecrafra KX-3 jest dostarczanie sygnału I/Q. Możemy wykorzystać go na wiele sposobów, np. do budowy prostego <a href="http://en.wikipedia.org/wiki/Radio_spectrum_scope" target="_blank">PANADAPTERA</a>. Dzięki temu będziemy wiedzieli co dzieję się wokół naszej częstotliwości pracy, jak i łatwiej ocenimy aktywność na paśmie. Może nie jest to PX3, ale daje spore udogodnienie za niewielką kasę. Program napisany przez <a href="http://qrz.com/db/aa6e" target="_blank">Martina AA6E</a>&nbsp;może współpracować nie tylko z KX3, także z popularnym donglem na chipsecie RTL możemy uzyskać analizator widma z szerokością pasma nawet do 2 MHz. Sterowanie syntezy Si570 i współpraca z innymi SDR-ami także nie przysporzy mu większych problemów.<br />
<br />
Większość niezbędnych informacji znajdziemy na stronie autora :<br />
<br />
<a href="http://www.aa6e.net/wiki/Tiny_Python_Panadapter">http://www.aa6e.net/wiki/Tiny_Python_Panadapter</a><br />
<br />
Niezbędne pliki pobieramy z <a href="http://sourceforge.net/projects/tinypythonpanadapter/" target="_blank">sourceforge-a</a>&nbsp;używając go tego narzędzia git<br />
<br />
<span style="background-color: #38761d; color: white; font-family: Courier New, Courier, monospace;">git clone git://git.code.sf.net/p/tinypythonpanadapter/code tinypythonpanadapter-code</span><br />
<span style="background-color: lime; font-family: Courier New, Courier, monospace;"><br /></span>
Jeśli&nbsp;<span style="font-family: inherit;">nie posiadasz środowiska python, wystarczy szybko doinstalować dwa pakiet, w przypadku&nbsp;</span><a href="http://www.linuxmint.com/" style="font-family: inherit;" target="_blank">MINT</a><span style="font-family: inherit;">-a/UBUNTU :</span><span style="background-color: lime; font-family: Courier New, Courier, monospace;"><br /></span><br />
<span style="font-family: inherit;"><span style="background-color: white;"><br /></span></span>
<span style="background-color: #38761d; color: white; font-family: Courier New, Courier, monospace;">sudo apt-get install python-pygame python-libhamlib2 python-pyaudio</span><br />
<br />
Główna część oprogramowania to <b>iq.py</b> odpalamy go i cieszymy się funkcją Panadaptera.<br />
<br />
<br />
<img border="0" src="/images/IQ.PY%2Bv.%2B0.3.6%2Bde%2BAA6E_002.png" height="332" width="400" />
<br />
<div class="separator" style="clear: both; text-align: center;">
<br /></div>
<br />
Wszystko działa bezproblemowo, ja przynajmniej na żadne nie natrafiłem.Na razie używam softu na laptopie, ale w sieci można znaleźć wiele realizacji na RaspberryPi + LCD i docelowo na pewno taki wykonam.Jedną z realizacji możecie znaleźć np tutaj :
<br />
<br />
<a href="https://tigerstyleheavyindustries.wordpress.com/2014/04/20/aa6es-tiny-python-panadapter-on-a-raspberry-pi/">https://tigerstyleheavyindustries.wordpress.com/2014/04/20/aa6es-tiny-python-panadapter-on-a-raspberry-pi/</a><br />
<br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<img border="0" height="300" src="/images/20140420-203947.jpg?w=700" width="400" /></div>
<span style="font-family: inherit;"><span style="background-color: white;"><br /></span></span>
<span style="font-family: inherit;"><span style="background-color: white;"><br /></span></span>
