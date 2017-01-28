---
layout: page
title:  "Radwege in Zürich"
subheadline: "Untersuchung der Radweglänge im Verhältnis der Einwohnerzahl in Zürich"
teaser: ""
header: no
show_meta: false
categories:
    - projects
image:
    title: radwegezuerich/wr_teaser.png
author: Hunar Mawlod &amp; Giang Pham &amp; Timon Vogler &amp; Mahmoud Abou El Azm
---

### Abstract
Dieses Projekt beschäftigt sich mit der Länge der Radwege und Radstreifen in den einzelnen Quartieren der Stadt Zürich.
Es wird untersucht durch welche Faktoren die Verteilung der Radwege beeinflusst werden. In diesem Fall handelt es sich um den Faktor Einwohnerzahl.
Ein Zusammenhang zwischen Radwegen und Einwohnerzahl wird vielleicht auf den ersten Blick vermutet, dennoch ist es interessant, eventuelle Ausreißer zu entdecken und die Vermutung zu bestätigen bzw. zu widerlegen.


## Einführung / Konzept
Mit diesem Projekt wurde das Verhältnis zwischen Radweglänge und die Einwohnerzahl der jeweiligen Quartiere untersucht. Die Antworten und Erkenntnisse sind auf verschiedenen Arten visuell dargestellt worden.

Hinweis:
In den Daten gab es sowohl Radwege als auch Radstreifen. Radstreifen sind auf der Straße eingezeichnete Wege, wobei Radwege getrennt von der Strasse sind und eigens für Fahrräder gebaut sind. In diesem Projekt wurde jedoch festgelegt, dass nicht qualitativ zwischen Radwegen und Radstreifen unterschieden wird. Außerdem umfasst in den folgenden Abschnitten das Wort „Radwege“ die „Radwege und Radstreifen“.

Die Motivation des Projekts war zum einen, dass wir die Möglichkeit hatten mit neuen Visualisierungstools zu arbeiten und die Idee, die wir zu unserem Projekt hatten visuell darzustellen.

Die These die von uns aufgestellt worden ist lautet:
Je mehr Einwohner in einem Quartier wohnen, desto mehr Radwege gibt es auch. Außerdem haben wir uns die Frage gestellt, ob die Einwohnerzahl der Quartiere einen Zusammenhang mit der Länge der Radwege hat?
Diese These sollte bestätigt oder widerlegt werden.Die Vermutung hat sich größtenteils bestätigt, dass es tatsächlich einen Zusammenhang zwischen Einwohnerzahl und Radweglänge gibt, wobei es auch Quartiere gibt, die aus dem Muster fallen.

## Daten / Auswertung

Die Informationen zu den Radwegen und Quartieren stammen aus dem [Open Data Portal Zürich](
https://data.stadt-zuerich.ch)

Folgende Daten standen in dem Open Data Portal zur Verfügung:
* Geokoordinaten der Quartiere (Stadtteile von Zürich)
* Geokoordinaten der Radwege
* Einwohnerzahl der Quartiere

Die Gesamtlänge der Radwege in den einzelnen Quartieren waren nicht in den Daten vorhanden, daher mussten die Längen ausgerechnet werden. Dazu wurde das Tool QGIS verwendet, in das die Koordinaten der Radwege und Quartiere importiert wurden.
Die selbst ausgerechneten Daten und die aus den anderen Dateien wurden dann zu einer Datei zusammengefasst.

## Prototyp / Ergebnisse
### Visualisierung
Die erste Visualisierungen fanden mit QGIS statt. Durch QGIS gab es eine Übersicht der Quartieren mit den eingezeichneten Radwegen.

<figure>
  <img src="{{ site.urlimg }}/radwegezuerich/blau.png" />
</figure>

Anhand der Einfärbung der einzelnen Quartieren haben wir mit Unfolding versucht die Länge der Radwege durch Farbabstufungen hervorzuheben. Das Beispiel zeigt die ersten Versuche mit Zufallswerten der Radweglänge.

<figure>
  <img src="{{ site.urlimg }}/radwegezuerich/rot.png" />
</figure>

Bevor wir mit der Programmierung angefangen haben, wurde mit Numbers und Excel Streudiagramme erstellt, um erste Erkenntnisse zu gewinnen.

<figure>
  <img src="{{ site.urlimg }}/radwegezuerich/scatterplot.png" />
</figure>

Wie im obigen Diagramm zu erkennen, hängt die Radweglänge tatsächlich mit der Einwohnerzahl zusammen. Die Punkte ergeben zwar keine exakt gerade Linie, dennoch lässt sich ein Muster erkennen, bei dem mit steigender Einwohnerzahl auch die Radweglänge zunimmt.

### Erkenntnisse

Interessant sind die Quartiere Escher Wyss und Enge, die man als Ausreisser bezeichnen kann, da sie vom Muster abweichen.

Beim Quartier Escher-Wyss handelt es sich um ein Industriegebiet, das  auch viele öffentliche Gebäuden wie Museen, Theater und Hotels besitzt.

<figure>
  <img src="{{ site.urlimg }}/radwegezuerich/escherwyss.png" />
</figure>

Beim Quartier Enge fällt auf, dass auf der gleichen Straße entlang des Flusses drei Radwege eingezeichnet sind. Es besteht der Verdacht, dass die redundanten Linien in die Berechnungen einflossen. Diese Linien sind in der Mitte der nachfolgenden Abbildung zu sehen.

<figure>
  <img src="{{ site.urlimg }}/radwegezuerich/enge.png" />
</figure>

### Überblick der verwendeten Tools

Um ein interaktives Tool für die Darstellung unserer Ergebnisse zu entwickeln, wurden folgende Tools und Bibliotheken benutzt:

[Eclipse](https://eclipse.org/) - Entwicklungsumgebung für das [Umsetzen des Tools
[Processing](https://processing.org/) - generell zum umsetzen von Visualisierungen
[Unfolding](http://unfoldingmaps.org/) - zur Erstellung von interaktiven Karten/Maps
[giCentre](http://www.gicentre.net/) - Bibliothek für die Erstellung des Scatterplots
[QGIS](https://www.qgis.org/) - durchführen von Geo-Berechnungen
[Git](https://github.com/) - um als Gruppe an der Implementierung zu arbeiten

### Ergebnis der Visualisierung

Um den Zusammenhang zwischen Radwegen und Einwohner darzustellen, sind verschiedene Ansichten gestaltet worden.

* ein Choropleth, zeigt die farbliche Abstufungen für die Radweglänge der Quartiere
* ein Scatterplot/Streudiagramm zeigt das Verhältnis der Radwege zur Einwohnerzahl der einzelnen Quartiere
* Mini Map mit eingezeichneten Radwegen (Radwege: rot, Radstreifen: blau)
* Details über die Radweglänge und Einwohnerzahl, im Vergleich zum Quartier mit der höchsten Einwohnerzahl und Radweglänge, dargestellt in einem Balkendiagramm
* Zusatzinformationen über Besonderheiten der einzelnen Quartiere

Interaktionsmöglichkeiten: Hover und Auswahl der Quartiere über Scatterplot und Choropleth

<figure>
  <img src="{{ site.urlimg }}/radwegezuerich/tool_final.png" />
</figure>

## Resümee und Ausblick 
Es konnte tatsächlich die These belegt werden, dass es einen Zusammenhang zwischen der Einwohnerzahl und der Radweglänge gibt. Durch die Visualisierung, konnten auch unerwartete und interessante Auffälligkeiten entdeckt werden. 

Das Projekt kann weitergeführt werden, indem weitere Faktoren betrachtet werden, die mit der Verteilung der Radwege zusammenhängen könnten.
Möglichkeiten sind zum Beispiel, dass untersucht wird, ob es mehr Radwege in Quartieren gibt, in denen viele junge Familien oder generell junge Menschen leben. Auch denkbar ist zu prüfen ob mehr Radwege in der Nähe von öffentlichen Gebäuden (Supermärkte, Schulen etc.) existieren.
