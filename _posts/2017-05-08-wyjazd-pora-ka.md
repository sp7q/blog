---
title: "Wyjazd 'porażka'."
date: 2017-05-08T09:36:00.001Z
layout: post
---

<br />
Wyjazd zapowiadał się wyśmienicie. Toboły spakowane, rodzinka w komplecie. Radiostacja zmieściła się wraz z anteną do małej podręcznej torby. K1, 10m RG58 i dublet. Niestety jakie było moje rozczarowanie kiedy na miejscu okazało się że niestety nie bardzo będzie możliwe powieszenie dubletu. Porażka w tytule jest w cudzysłowiu, gdyż sam wyjazd był wyśmienity, Kaszuby to przepiękne miejsce do wypoczynku, niestety radiowo dałem ciała, QSO w logu 0. Jednak nie należy załamywać rąk, każda porażka daje ważną lekcję. Dublet to bardzo skuteczna antena, dlatego często ze mną wędruje, niestety awaryjnie należy zawsze mieć ze sobą jakiegoś ENDFED-a. Choć posiadam w domu tuner do anten półfalowych zasilanych z końca (FUCHS), to staram się zawsze zminimalizować ilość gratów zabranych ze sobą i wykorzystać potencjał skrzynki drzemiącej w K1.<br />
<br />
Najbardziej rozpowszechnioną "partyzancką" anteną jest <a href="http://www.arrl.org/random-wires" target="_blank">Random Wire</a>, czyli po prostu przypadkowej długości drut. Zaletą takiego rozwiązania jest możliwość w mniej lub bardziej przypadkowy sposób rozwieszenie jej w każdych warunkach.<br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<img border="0" height="220" src="/images/Zaznaczenie_066.png" width="400" /></div>
<br />
<br />
Skrzynka w K1 z założenia jest projektowana dla takich anten, jednakże instrukcja jednoznacznie wspomina o unikaniu wielokrotności pół fali.<br />
<br />
<blockquote class="tr_bq">
Random-Length Antennas
The KAT1 is optimized for use with long, random-length wire antennas, since these are the easiest
antennas to set up in the field (you just toss the wire in a nearby tree). In most cases you can connect such
an antenna (and a few ground radials) directly to the K1, with no feedline. However, watch for RF
problems, especially if the wire is exactly a half-wavelength long or any multiple thereof on a given band.
The KAT1 also works with loops. An untuned loop of wire 30 feet long (or longer), formed into any shape,
can be matched on most bands. A loop may work well even if you can’t lay out a lot of ground radials.</blockquote>
<br />
Ponieważ większość skrzynek antenowych nie lubi wysokich impedacji powinniśmy ich unikać. Z pomocą przyszła strona Michaela <a href="http://www.qrz.com/db/ab3ap" target="_blank">AB3AP</a>&nbsp;pod adresem <a href="http://udel.edu/~mm/ham/randomWire/">http://udel.edu/~mm/ham/randomWire/</a><br />
. Napisał on prosty kod w C, który wylicza strefy wysokiej impedancji. Dostosowałem ten kod odrobinę do swoich wymagań. Po pierwsze moje K1 posiada pasma 40-30-20-17m i tylko te były polem zainteresowania dla mnie, po drugie nie lubię się męczyć więc zmieniłem jednostkę na metryczną.<br />
<br />
Oto kod :<br />
<br />
<span style="background-color: black; color: lime;">/*</span><br />
<span style="background-color: black; color: lime;">&nbsp;* Simple calculations of half wavelengths of ham bands.</span><br />
<span style="background-color: black; color: lime;">&nbsp;*</span><br />
<span style="background-color: black; color: lime;">&nbsp;* Mike Markowski AB3AP</span><br />
<span style="background-color: black; color: lime;">&nbsp;* Thu Jun 28 07:01:26 EDT 2012</span><br />
<span style="background-color: black; color: lime;">&nbsp;*/</span><br />
<span style="background-color: black; color: lime;"><br /></span>
<span style="background-color: black; color: lime;">#include <stdio .h=""></stdio></span><br />
<span style="background-color: black; color: lime;"><br /></span>
<span style="background-color: black; color: lime;">main() {</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>printHalfwaves();</span><br />
<span style="background-color: black; color: lime;">}</span><br />
<span style="background-color: black; color: lime;"><br /></span>
<span style="background-color: black; color: lime;">/*</span><br />
<span style="background-color: black; color: lime;">&nbsp;* Print ranges of half wavelengths for ecah ham band.</span><br />
<span style="background-color: black; color: lime;">&nbsp;*/</span><br />
<span style="background-color: black; color: lime;">printHalfwaves() {</span><br />
<span style="background-color: black; color: lime;"><br /></span>
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>rw(7000., 7300.); &nbsp; &nbsp; &nbsp; /* 40m */</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>rw(10100., 10150.); &nbsp; &nbsp; /* 30m */</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>rw(14000., 14350.); &nbsp; &nbsp; /* 20m */</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>rw(18068., 18168.); &nbsp; &nbsp; /* 17m */</span><br />
<span style="background-color: black; color: lime;">}</span><br />
<span style="background-color: black; color: lime;"><br /></span>
<span style="background-color: black; color: lime;">/*</span><br />
<span style="background-color: black; color: lime;">&nbsp;* For a given frequency range, calculate the half wavelength range and print</span><br />
<span style="background-color: black; color: lime;">&nbsp;* it. &nbsp;In addition, print up to 4th multiples of each range up to the length</span><br />
<span style="background-color: black; color: lime;">&nbsp;* of 160m half wavelength.</span><br />
<span style="background-color: black; color: lime;">&nbsp;*</span><br />
<span style="background-color: black; color: lime;">&nbsp;* Comments are also printed out, assuming that the output will saved to a file,</span><br />
<span style="background-color: black; color: lime;">&nbsp;* and that file used by gnuplot for plotting.</span><br />
<span style="background-color: black; color: lime;">&nbsp;*/</span><br />
<span style="background-color: black; color: lime;">rw(double min_kHz, double max_kHz) {</span><br />
<span class="Apple-tab-span" style="background-color: black; white-space: pre;"><span style="color: lime;"> </span></span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>double lambda0_ft, lambda1_ft;</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>double loFreq_MHz = 7;</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>double lambdaMax_ft = 2 * 468 / loFreq_MHz; /* Max wavelength in band. */</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>int n;</span><br />
<span style="background-color: black; color: lime;"><br /></span>
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>double qtr_ft = 300 / loFreq_MHz / 2;</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>printf("# %.3f to %.3f kHz, too short for %f MHz\n",</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">  </span>min_kHz, max_kHz, loFreq_MHz);</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>printf("%.3f 0\n%.3f 1\n%.3f 1\n%.3f 0\n\n",</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">  </span>0., 0+(1e-3), qtr_ft, qtr_ft+(1e-3));</span><br />
<span class="Apple-tab-span" style="background-color: black; white-space: pre;"><span style="color: lime;"> </span></span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>n = 1; /* First multiple. */</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>do {</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">  </span>lambda0_ft = n * 300 / (max_kHz * 1e-3);</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">  </span>lambda1_ft = n * 300 / (min_kHz * 1e-3);</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">  </span>/* Print in format gnuplot expects. */</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">  </span>printf("# %.3f to %.3f kHz, multiple %d\n",</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">   </span>min_kHz, max_kHz, n);</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">  </span>printf("%.3f 0\n%.3f 1\n%.3f 1\n%.3f 0\n\n",</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">   </span>lambda0_ft-(1e-3), lambda0_ft,</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">   </span>lambda1_ft, lambda1_ft+(1e-3));</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">  </span>/* Prepare for next multiple. */</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;">  </span>n++;</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>/* Change '5' in next line to max number of multiples to calculate. */</span><br />
<span style="background-color: black; color: lime;"><span class="Apple-tab-span" style="white-space: pre;"> </span>} while (lambda1_ft &lt; lambdaMax_ft &amp;&amp; n &lt; 5);</span><br />
<span style="background-color: black; color: lime;">}</span><br />
<br />
Dalej było już prosto, szybka kompilacja :<br />
<br />
<span style="background-color: black; color: lime;">$gcc rw.c -o rw</span><br />
<br />
Wykonanie progranu :<br />
<span style="background-color: black; color: lime;">$rw &gt; f</span><br />
<br />
Teraz by ładnie zwizualizować wyniki obliczeń z pomocą przyjdzie gnuplot. Na początek polecam utworzyć plik konfiguracyjny rw.gnu :<br />
<br />
<span style="background-color: black; color: lime;">set xtics 5</span><br />
<span style="background-color: black; color: lime;">unset ytics</span><br />
<span style="background-color: black; color: lime;">set grid</span><br />
<span style="background-color: black; color: lime;">set xlabel 'Wire Length (m)'</span><br />
<span style="background-color: black; color: lime;">set title 'Random Wire Lengths to Avoid'</span><br />
<span style="background-color: black; color: lime;">set term png size 1500,300</span><br />
<span style="background-color: black; color: lime;">set output 'f.png'</span><br />
<span style="background-color: black; color: lime;">plot [:][:1] 'f' with filledcurves notitle</span><br />
<br />
Odpalamy gnuplot:<br />
<br />
<span style="background-color: black; color: lime;">$gnuplot rw.gnu</span><br />
<br />
<br />
Otrzymujemy piękny wykres :<br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<img border="0" height="40" src="/images/f.png" width="400" /></div>
<br />
<div class="separator" style="clear: both; text-align: center;">
</div>
<br />
Oczywiście na własne potrzeby możecie zmodyfikować kod po swojemu. Im więcej pasm tym więcej będzie występowało stref których należy unikać.<br />
<br />
<b>Należy także pamiętać że jedną z ważniejszych rzeczy jest przeciwwaga. Należy użyć co najmniej jednej przeciwwagi o długości 1/4 na najniższe pasmo jakiego będziemy używać.&nbsp;</b><br />
<br />
Uwagę o przeciwwadze podają praktycznie wszystkie źródła na jakie natrafiłem.<br />
<br />
Teraz czas na testy !!! Już niedługo c.d.n.<br />
<br />