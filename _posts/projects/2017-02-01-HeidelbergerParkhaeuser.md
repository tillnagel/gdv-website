---
layout: page
title:  "Heidelberger Parkhäuser (CPU)"
subheadline: Vergleichende Visualisierung der Heidelberger Parkhäuser
teaser: "Parkhausauslastungen werden in drei unterschiedlichen Sichten dargestellt"
header: no
show_meta: false
categories:
    - projects
image:
    title: HeidelbergerParkhaeuser/teaser.gif
    caption: Heidelberger Parkhäuser (CPU)
author: Büsra Keles, Asim Bababalim, Ömer Sagsöz, Pascal Perle &amp; Patrick Domscheid

gallery:
    - image_url: HeidelbergerParkhaeuser/Skizze-1.jpg
    - image_url: HeidelbergerParkhaeuser/Skizze-2.png
    - image_url: HeidelbergerParkhaeuser/Skizze-3.jpg
gallery2:
    - image_url: HeidelbergerParkhaeuser/AbsRel.gif
    - image_url: HeidelbergerParkhaeuser/Hover.gif
    - image_url: HeidelbergerParkhaeuser/SelectDate.gif
---

# Abstract
CPU (car park utilization) ist eine vergleichende visuelle Analyse der urbanen Parkhausauslastung in Heidelberg. Ziel des Projektes war es, eventuelle Verhaltensmuster zu identifizieren und neue Erkenntnisse zu gewinnen. Die Resultate wurden anschließend mit unseren Hypothesen verglichen und analysiert. <br/>
Die Auslastungen werden in drei unterschiedlichen Sichten dargestellt. Diese wurden so gestaltet, dass sie schrittweise von Small Multiples über Stacked Chart hin zur georäumlichen Visualisierung werden. Im Rahmen des Projektes wurde der Zeitraum vom 19.11. bis zum 25.12.2016 betrachtet. 

## Einführung / Konzept
Autos gehören nach wie vor zu den wichtigsten Fortbewegungsmitteln in unserem Alltag. In den letzten Jahren haben viele Städte ihre Parkplatzkapazitäten in urbanen Bezirken erhöht. <br/>
Wir haben uns für die Stadt Heidelberg entschieden, da sie zu den Hauptattraktionen Deutschlands zählt und mit 19 Parkhäusern insgesamt über 4200 Parkplätze besitzt. <br/>
Folgende Fragen ergeben sich aus dem Kontext:

* Besteht der Bedarf die Kapazität der Parkhäuser auszubauen? 
  * Welche Stationen sollten in diesem Fall ausgebaut werden?
* Zu welchen Zeiten werden die Service am meisten/wenigsten in Anspruch genommen?
  * Von welchen Faktoren hängt das ab?
* Sind manche Parkhäuser gegen Mittag und andere eher gegen Abend ausgelastet?


## Daten / Auswertung

### Daten
Die Stadt Heidelberg stellt auf ihrer [Webseite](http://parken.heidelberg.de/) die aktuelle Auslastung aller Heidelberger Parkhäuser zur Verfügung. Diese Daten werden alle 3 Minuten aktualisiert.

### Erhebung
Über den betrachteten Zeitraum (19.11. - 25.12.16) wurde alle 3 Minuten die aktuelle Auslastung aller Parkhäuser in eine Datenbank gespeichert.

### Parsing
Die API lieferte die Daten in JSON-Format, welches wir aus Performancegründen zur späteren Verarbeitung in eine SQLite-Datenbank gespeichert haben.

* Beispiel für Parkhaus id=3:

```json
{
  "id": 3,
  "total": 200,
  "current": 9,
  "trend": "constant",
  "status": "closed",
  "parkinglocation": 3
}
```

### Bereinigung
Die IDs (bzw. parkinglocation) der Parkhäuser, der API, stimmen nicht mit den Parkhausnummern in der Stadt überein. Das erste Parkhaus in Heidelberg heißt P0, welches in der API die ID 1 hat. Da die ID immer eins größer, als die Nummer des Parkhauses, ist war dieses Problem einfach zu beheben.

* Parkhausnummer = ID - 1

### Aggregierung
Da die API manchmal Aussetzer hatte, d.h. keine Daten geliefert hat, haben wir uns dazu entschieden, von einem 3 Minuten Intervall zu einem 10 Minuten Intervall zu wechseln, welches das Problem gelöst hat.

### Prozess
Mittels Scribbles haben wir erste Prototypen für das Layout erstellt. Teile wie die Small Multiples, die Karte und die Stacked Chart waren von Anfang an geplant. Die Wetteransicht (dritter Quadrant) aus dem Scribbles haben wir am Ende fallen lassen, da sie keine erkenntlichen Informationen enthielt (es hat an keinem der Tage mehr als eine Stunde geregnet, weshalb wir keine Abhängigkeit vom Regen auf das Verhalten beobachten konnten).
Außerdem haben wir mittels Tableau erste Visualisierungen erstellt, um zu testen, ob unsere Vermutungen zutreffen.

{% include gallery %}


## Prototyp / Ergebnisse

### Visualisierung

<figure>
  <img src="{{ site.urlimg }}/HeidelbergerParkhaeuser/Overview.png" />
  <figcaption >Allgemeiner Aufbau</figcaption>
</figure>

<figure>
  <img src="{{ site.urlimg }}/HeidelbergerParkhaeuser/TimelineAbs.gif" />
  <figcaption >Tagesverlauf auf der Karte (absolute Ansicht)</figcaption>
</figure>

<figure>
  <img src="{{ site.urlimg }}/HeidelbergerParkhaeuser/TimelineRel.gif" />
  <figcaption >Tagesverlauf auf der Karte (relative Ansicht)</figcaption>
</figure>

{% include gallery2 %}



### Erkenntnisse
Wie vermutet, sind zu bestimmten Events, bzw. zu bestimmten Uhrzeiten z.B. mittags andere Parkhäuser in der Stadt ausgelastet als gegen Abend.

* **Black Friday (26.11.2016)** <br/>
  * An diesem Tag sind die Parkhäuser fast komplett ausgelastet, mehr als 97% der Parkplätze sind zu den Spitzenzeiten belegt.<br/>
    * Vermutung: Schnäppchenjagd
<figure>
  <img src="{{ site.urlimg }}/HeidelbergerParkhaeuser/erkenntnisse-26.png" />
  <figcaption >Black Friday (26.11.2016) - mehr als 97% der Parkplätze belegt</figcaption>
</figure>


* **Heiligabend (24.12.2016)** <br/>
  * P11 und P13 in der Nähe der Heiliggeistkirche, in der Altstadt, ist gegen 18 Uhr überdurchschnittlich ausgelastet.<br/>
    * Vermutung: Gottesdienst
<figure>
  <img src="{{ site.urlimg }}/HeidelbergerParkhaeuser/erkenntnisse-24.png" />
  <figcaption >Heiligabend (24.12.2016)- überdurchschnittlich ausgelastet gegen 18 Uhr</figcaption>
</figure>

<br/>

Wie zu Beginn vermutet, besteht Bedarf die Kapazität mancher Parkhäuser auszubauen. 
Im Durchschnitt des Beobachtungszeitraums sind in den Parkhäusern P6, P8, P9, P10, P13 und P16 zwischen 16 und 20 Uhr über 80% der Parkplätze belegt. Im Parkhaus P11 sind in diesem Zeitraum sogar über 90% der Parkplätze belegt.
<figure>
  <img src="{{ site.urlimg }}/HeidelbergerParkhaeuser/erkenntnisse-all.png" />
  <figcaption >Durchschnitt des Beobachtungszeitraums in der Small Multiples Ansicht</figcaption>
</figure>

Mittels der Kartenansicht ist leicht erkennbar, dass die Auslastung der Parkhäuser ortsabhängig ist. So sind alle Parkhäuser in der Nähe der Altstadt gegen 19 Uhr im Durchschnitt höher ausgelastet, als die außerhalb der Altstadt.
<figure>
  <img src="{{ site.urlimg }}/HeidelbergerParkhaeuser/erkenntnisse-all-map.png" />
  <figcaption >Durchschnitt des Beobachtungszeitraums (19 Uhr) in der Kartenansicht</figcaption>
</figure>

Am meisten werden die Service zwischen 11 und 20 Uhr in Anspruch genommen. Wichtige Einflussfaktoren hierfür sind Arbeitszeiten und Öffnungszeiten der Stadt.
<figure>
  <img src="{{ site.urlimg }}/HeidelbergerParkhaeuser/erkenntnisse-all-sacked.png" />
  <figcaption >Durchschnitt des Beobachtungszeitraums in der Stacked Chart Ansicht</figcaption>
</figure>

### Implementierung
Während der Datenexploration (explorativen Datenanalyse) wurde Tableau verwendet, um erste Muster in den Daten zu erkennen.
Die Visualisierung wurde in Java mit dem [Processing](https://processing.org/)-Framework, der [unfoldingmaps](http://unfoldingmaps.org/)-, sowie der [timerangeslider](https://github.com/tillnagel/timerangeslider)-Bibliothek umgesetzt.

## Fazit

### Reflektion
Mittels unserer visuellen Analyse haben wir erreicht, dass Menschen darüber diskutieren, wie man die Parkhausauslastung zu Spitzenzeiten besser verteilen kann.

### Ausblick
Während der iExpo wurden wir immer wieder darauf angesprochen, ob wir unsere Daten nicht online zur Verfügung stellen könnten, sodass sie z.B. mit einer App abgerufen werden können.
Erstens, dass man die Livedaten mit historischen Daten kombiniert, um eine Auslastungsprognose zu erstellen. Zweitens, dass man den Parkpreis pro Stunde mit anzeigt, um zu sehen, ob der Parkpreis die Auswahl des Parkhauses mit beeinflusst.

Die Ergebnisse unserer Analyse kann der Stadt Heidelberg präsentiert werden, sodass die Parkhausauslastung besser koordiniert werden kann.