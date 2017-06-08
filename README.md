# Schnee Von Morgen – Analyse
Enthält eine Dokumentation der Methodik zur Analyse der klimatischen Entwicklung im bayerischen Alpenraum in den vergangen Jahrzehnten. Diese liegt in Form einer R-Markdown-Datei vor und macht die Berechnungen somit transparent und reproduzierbar.

- **Live**: http://schnee-von-morgen.br.de

## Verwendung
1. Repository klonen `git clone https://...`
2. `analyse.Rmd` in RStudio öffnen
3. Berechnungen reproduzieren durch Knitten von `analyse.Rmd`
4. `analyse.html` enthält eine [HTML-Version](http://rpubs.com/br_data/schnee-von-morgen) des gesamten Prozesses

## Datenquelle
Die Daten stammen vom FTP-Server des Deutschen Wetterdienstes (DWD): 
ftp://ftp-cdc.dwd.de/pub/CDC/observations_germany/climate

Wir zeigen pro Jahr die Durchschnittstemperatur im Winterhalbjahr, die wir aus den mittleren Tagestemperaturen aggregiert haben.

Die Zeitreihen der Tageswerte, die an den Wetterstationen des DWD gemessen wurden, sind nicht überall vollständig. Werte von Halbjahren, in denen mehr als drei Tageswerte fehlen, markieren wir dementsprechend als nicht verfügbar. Falls maximal drei Tageswerte fehlen, wurden diese durch lineare Interpolation ergänzt.

An den Wetterstationen Wendelstein (2011) und Bad Reichenhall (2006) werden seit einiger Zeit keine Messungen mehr durchgeführt. In Reit im Winkl wurden die Messungen nach einer Unterbrechung (2003-2006) wieder aufgenommen. Da diese Stationen über eine langjährige Datenreihe seit den 60er Jahren verfügen, haben wir sie dennoch in unserer Recherche berücksichtigt.

## Statistischer Hintergrund
Den langjährigen absoluten Trend haben wir mit einer linearen Regression und der Methode der kleinsten Quadrate berechnet. Ein Trend lässt nur Rückschlüsse auf den jeweils betrachteten Zeitraum zu. Klimatische Entwicklungen zeichnen sich jedoch erst ab einer gewissen Mindestlänge ab, weshalb der Nutzer die jeweils untersuchte Zeitspanne nicht verändern kann.

Die Deutlichkeit, mit der sich der Trend aus der Variabilität der Datenreihe hervorhebt, wird mit Hilfe von sogenannten Mann-Kendall-Trendtests bestimmt. Unterschreitet der einer Datenreihe zugeordnete Signifikanzwert die Schwelle von 80% wird der Trend als statistisch nicht signifikant eingestuft (vgl. Vorgehen in [Heft 5](http://www.kliwa.de/_download/KLIWAHeft5.pdf) der KLIWA-Berichte).