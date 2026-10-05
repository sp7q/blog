---
title: "Manipulator tensoryczny cd."
date: 2020-06-29T21:57:00Z
layout: post
---

W telegrafii wszystko rozbija się o prawidłowy timing.<br />
Tutaj można znaleźć świetnie opisane relacje czasowe :&nbsp;<a href="https://morsecode.world/international/timing.html">https://morsecode.world/international/timing.html</a><br />
<br />
Przy projektowaniu klucza należałoby się zastanowić jak szybko potrzebujemy próbkować stany dźwigni.<br />
<br />
Przy ekstremalnym założeniu że ktoś pracowałby 100WPM (są tacy co odbierają takie tempa choć osobiście nie znam nikogo kto by je nadawał) jeden element (krótki dźwięk - "kropka") trwałby t=60/(50x100)=<b>12ms</b><br />
<br />
W keyerze sprawdzenie stanu czy dana łopatka jest wciśnięta nastąpi dopiero po cyklu 2t (gdzie t="kropka"), wtedy stwierdzi on czy jest ona dalej wciśnięta, zwolniona lub wciśnięty przeciwstawna łopatka.&nbsp;<br />
<br />
Niestety moja pętla programu wykonuje się&nbsp;<b>~18-19ms&nbsp;</b>&nbsp;co godnie z twierdzeniem&nbsp;&nbsp;<b style="background-color: white; color: #202122; font-family: sans-serif; font-size: 14px;"><a href="https://pl.wikipedia.org/wiki/Twierdzenie_o_pr%C3%B3bkowaniu" target="_blank">Nyquista–Shannon</a>-a&nbsp;</b>powinno dać satysfakcjonujący efekt do 60 WPM - co i tak przewyższa umiejętności 95% populacji telegrafistów.<br />
<br />
Można także spróbować wykorzystać wewnętrzny komparator ADS1115 oraz wyjście ALRT co sprowadziło by rolę mikrokontrolera jedynie do zadania wartości do rejestrów. Układ w trybie ciągłym może osiągnąć nawet 860 SPS (samples per second) co daleko wykracza poza nasze potrzeby, lecz zmusza do wykorzystania dwóch układów ADS.<br />
<br />
<b>EDIT:</b><br />
<br />
Popełniłem drobny błąd - układ defaultowo ustawiony jest na&nbsp;<b>128SPS</b>&nbsp;- co daje ok 8ms per shot, wraz z komunikacją dawało to ok&nbsp;<b>9-10ms</b> - stąd cykl dla obu łopatek wyniósł&nbsp;<b>~18-19ms</b><br />
Przestawiłem go na&nbsp;<b>860SPS</b>&nbsp;(<b>~1ms/shot</b>) - całość obecnie wykonuje się w 5-6ms&nbsp; (z czego należy pamiętać że sama część benchmarkowa również zabiera parę cykli mikrokontrolera) - co daje na tyle dużą gęstość próbek że nawet owe<b>&nbsp;100 WPM</b>&nbsp;nam nie straszne (a w zasadzie nawet 120).