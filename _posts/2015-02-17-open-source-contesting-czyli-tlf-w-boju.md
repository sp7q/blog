---
published: false
title: "Open source contesting czyli TLF w boju."
date: 2015-02-17T13:29:00Z
layout: post
---

<div class="separator" style="clear: both; text-align: center;">
<img border="0" src="/images/mc%2B%5Bsp7q%40sp7q-desktop%5D%3A%7E-zawody-pga%2Bluty_002.png" height="213" width="320" /></div>
Od zawsze chciałem przesiąść się zupełnie na wolne oprogramowanie. Od dłuższego czasu nie mam w domu żadnej maszyny z Łindoł$sem. Praca na wolnym oprogramowaniu ma szereg zalet, niestety nie ma róży bez kolców, czasem trudno znaleźć jakieś oprogramowanie lub go po prostu brak. Pod systemy linuxopochodne jest sporo programów logujących, lecz praktycznie żaden nie skupia się na zawodach. Wyjątkiem jest TLF, projekt który rozpoczął Reinus Couperus PA0RCT. Program obsługuje większość zawodów międzynarodowych , ale nie jesteśmy do tego ograniczenie, można spokojnie dostosować go do naszych potrzeb. Uparłem się i wystartowałem w PGA-TEST, oczywiście popełniłem szczeniacki błąd i wszystko robiłem w nocy przed zawodami co w połączeniu z moim brakiem treningów ostatnio, brakiem dokładnej znajomości programu logującego dało mi zaszczytne ostatnie miejsce :-).<br />
<br />
Do rzeczy. Konsolowy program który każdy bezproblemowo opanuje w kilkanaście minut. Posiada wszystko co powinien mieć porządny program logujący.<br />
<br />
Podstawowe funkcje :<br />
<br />
Informacje widoczne w logu ciągle;<br />
<br />
-Wyjście klucza<br />
-prędkość kluczowania i opóźnienie<br />
-status klucza<br />
-Keyboard/CQ/S&amp;P/Auto<br />
-ostatnie 5 linii logu<br />
-czas UTC<br />
-Dane WWV<br />
-Informacje dla aktywnego znaku<br />
<br />
Informacje w oddzielnych oknach :<br />
<br />
-duplikaty<br />
-wynik<br />
-dx cluster<br />
-podpowiedź znaku<br />
-zaliczone podmioty<br />
-diagram propagacji<br />
<br />
Współpraca z cwdaemonem<br />
Obłsuga CAT przez HAMLIB<br />
<br />
Więcej informacji możecie nzaleźć np tu :<br />
<br />
<a href="http://home.iae.nl/users/reinc/tlf/tlfdoc-0.9.9/tlfdoc.html">http://home.iae.nl/users/reinc/tlf/tlfdoc-0.9.9/tlfdoc.html</a><br />
<br />
W przypadku systemów Ubuntu i pochodnych zaczynamy od instalacji :<br />
<br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;sudo apt-get install tlf libhamlib2 cwdaemon xplanet xplanet-images</span><br />
<br />
No i mamy wszystko co potrzebne. Teraz konfiguracja pod zawody.<br />
<br />
Tworzymy katalog gdzie chcemy trzymać logi u mnie po prostu katalog zawody<br />
<br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;mkdir zawody</span><br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;cd zawody</span><br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">#Następnie katalog na konkretne zawody :</span><br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;mkdir pgatest</span><br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;cd pgatest</span><br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;mkdir rules</span><br />
<br />
Przenosimy niezbędne pliki.<br />
<br />
<span style="background-color: #274e13;"><span style="color: white; font-family: Courier New, Courier, monospace;">cp /usr/share/tlf/logcfg.dat /home/twoja nazwa użytkownika/zawody/pgatest</span></span><br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">cp /usr/share/tlf/rules/contest / /home/twoja nazwa użytkownika/zawody/pgatest/rules/pga</span><br />
<br />
Plik konfiguracyjny a także plik zawodów powinniśmy przystosować do własnych potrzeb.<br />
<br />
Przykłady można pobrać z :<br />
<br />
<a href="https://www.dropbox.com/sh/95y628yekbbyqj2/AAC96ZtVyFwlnaBwaIKkzOf3a?dl=0">https://www.dropbox.com/sh/95y628yekbbyqj2/AAC96ZtVyFwlnaBwaIKkzOf3a?dl=0</a><br />
<br />
Do katalogu pgatest pobieramy sobie także plik callmaster dzięki któremu program będzie podpowiadał znak korespondenta oraz gminę.<br />
<br />
TLF współpracuje także z programem xplanet, który wyświetli nam ostatnie 8 spotów z dx klastra, może w zawodach PGA to bezsensowne, ale przy innych może bardzo się przydać. Xplanet już wcześniej zainstalowaliśmy, teraz tylko kilka prostych zabiegów.<br />
<br />
<pre><span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;cd
&gt;mkdir -p .xplanet/config
&gt;touch .xplanet/config/default</span></pre>
<pre>
</pre>
<pre>Edytujemy plik default i dodajemy linie :</pre>
<pre>
</pre>
<pre><span style="font-family: Courier New, Courier, monospace;">[earth]
marker_file=/home/twoja nazwa użytkownika/.xplanet/tlfmarkers</span>
</pre>
<pre>
</pre>
<pre>W pliku konfiguracyjnym logu logcfg.dat edytujemy linię by wyglądała tak :</pre>
<pre>
</pre>
<pre><span style="font-family: Courier New, Courier, monospace;">MARKERS=/home/twoja nazwa użytkownika/.xplanet/tlfmarkers</span></pre>
<pre>
</pre>
<pre>Czas zacząć zabawę, odpalamy cwdaemon-a, xplanet oraz log.</pre>
<pre>
</pre>
<pre><span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;sudo cwdaemon -d ttyS0</span></pre>
<pre><span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;xplanet -window -geometry 1400x700 -longitude 19 -latitude 51 -fontsize 13 </span></pre>
<div>
<pre><span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">-projection rectangular -wait 5</span></pre>
<pre>
</pre>
<pre>Dodatkowe parametry xplanet to odpowiednio :</pre>
<pre>-window odpala program w oknie, czasem pod fluxboxem używam bez tego parametru i wyświetla się jako tło pulpitu.</pre>
<pre>-geometry określa rozmiar okna</pre>
<pre>-longitude/latitude punkt na jakim centruje mapę</pre>
<pre>-fontsize rozmiar czcionki</pre>
<pre>-projection rodzaj projekcji i tu możemy dać:</pre>
<pre>
</pre>
<pre style="text-align: center;"><b><span style="font-size: large;">RECTANGULAR</span></b></pre>
<div class="separator" style="clear: both; text-align: center;">
<img border="0" src="/images/Xplanet%2B1.3.0_004.png" height="329" width="640" /></div>
<div class="separator" style="clear: both; text-align: center;">
<span style="font-size: large;"><b>ANCIENT</b></span></div>
</div>
<div class="separator" style="clear: both; text-align: center;">
<img border="0" src="/images/Xplanet%2B1.3.0_005.png" height="330" width="640" /></div>
<div class="separator" style="clear: both; text-align: center;">
<b><span style="font-size: large;">AZIMUTHAL</span></b></div>
<div class="separator" style="clear: both; text-align: center;">
<img border="0" src="/images/Xplanet%2B1.3.0_006.png" height="330" width="640" /></div>
<div>
<br /></div>
Więcej możemy poczytać tutaj :<br />
<br />
<a href="http://xplanet.sourceforge.net/README">http://xplanet.sourceforge.net/README</a><br />
<br />
Na koniec wchodzimy do katalogu zawodów :<br />
<br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;cd /home/twoja nazwa użytkownika/zawody/pgatest</span><br />
<span style="background-color: #274e13; color: white; font-family: Courier New, Courier, monospace;">&gt;tlf</span><br />
<br />
I możemy startować w zawodach, u mnie wygląda to tak :<br />
<br />
<div class="separator" style="clear: both; text-align: center;">
<img border="0" src="/images/Obszar%2Broboczy%2B1_001.png" height="360" width="640" /></div>
<br />
<br />
Polecam dokładnie przeczytać dokumentację jak i podejrzeć jak wygląda moja konfiguracja, pozwoli to uniknąć błędu jaki ja popełniłem. Program ułatwia pracę np dzięki różnemu zachowaniu klawicza Enter, w zależności w jakim trybie jesteśmy Auto/CQ/S&amp;P<br />
<br />
Więcej tutaj :<br />
<br />
<a href="http://home.iae.nl/users/reinc/tlf/tlfdoc-0.9.9/tlfdoc.html#Operation">http://home.iae.nl/users/reinc/tlf/tlfdoc-0.9.9/tlfdoc.html#Operation</a><br />
<br />
Jeśli znajdzie się więcej zainteresowanych manualem w języku ojczystym to coś sklecę na poczekaniu. Do usłyszenia w zawodach !<br />
<br />