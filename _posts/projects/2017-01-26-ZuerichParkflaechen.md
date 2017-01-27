---
layout: page
title:  "Züricher Parkflächen"
subheadline: Veranschaulichung und Exploration der Züricher Natur und Parkplätze 

teaser: "Vergleich von Natur und Parkplätzen in der Grünstadt Zürich"
header: no
show_meta: false
categories:
    - projects
image:
    title: ZuerichParkflaechen/zp_teaser.png
    caption: Hauptsicht der Applikation 
author: Ahmet Ekiz, Kevin Schorpp, Klaus Hipp, Mihkail Polishuk
---

## Abstract
Die Anwendung visualisiert diverse Geodaten zu Wald-, Grünflächen und Parks in der „Grünstadt Zürich“ und ermöglicht einen Vergleich diesbezüglicher Flächenverteilung mit Parkflächen.

Gegliedert wird die Darstellung in eine Übersichts-, sowie eine Diagrammansicht und vier Detailansichten zur Veranschaulichung maximal zweier Bezirke Zürichs und deren Gegenüberstellung zum Züricher Durchschnitt.

## Einführung
Dieses kleine Datenvisualisierungsprojekt ist im Rahmen der Vorlesung "Grundlagen der Datenvisualisierung" im Wintersemester 2016/2017 entstanden. Ziel war eine interaktive Datenvisualisierung zum Thema Smart City und Urbanen Räumen.

Nach einiger Recherche zu verfügbaren Datenquellen, griffen wir eine Konzeptidee unseres Dozenten Herr Prof. Dr. Nagel auf, Parks und Parkplätze der Stadt Zürich in Relation zu setzen und festzustellen, ob besondere Ausprägungen zu erkennen sind.

## Funktionalitäten
Die Übersichtskarte <img src="{{ site.urlimg }}/ZuerichParkflaechen/zp_A.png" alt="(A)" style="width: 20px; height: 20px;" /> erlaubt das einfache Selektieren von bis zu zwei Bezirken, die in den jeweiligen Spalten zur Detailansicht <img src="{{ site.urlimg }}/ZuerichParkflaechen/zp_B.png" alt="(B)" style="width: 20px; height: 20px;" /> dargestellt werden.

Diese zeigen jeweils in zwei übereinanderliegenden Panels die Grünflächen (oben) und die verschiedenen Parkplatzarten (unten), die jeweils gefiltert werden können.

Bei fehlender Selektion oder Auswahl eines einzelnen Bezirkes wird in der rechten Spalte gesamt Zürich zum Vergleich eingeblendet.

Die Diagrammansicht <img src="{{ site.urlimg }}/ZuerichParkflaechen/zp_C.png" alt="(C)" style="width: 20px; height: 20px;" /> stellt die Gesamtflächen der visualisierten Bezirke dem Züricher Absolut und Durchschnitt gegenüber.

<figure>
  <img src="{{ site.urlimg }}/ZuerichParkflaechen/zp_functions_image.png" />
  <figcaption >Allgemeine Übersicht über die Funktionalitäten der Anwendung.</figcaption>
</figure>

## Daten / Auswertung

### Datenquellen
Wir haben folgende Datenquellen genutzt:

-   [Open Data Projekt der Grünstadt Zürich](https://data.stadt-zuerich.ch/)
-   [Overpass Turbo](https://overpass-turbo.eu/): Tool zur Datenfilterung für [OpenStreetMap](http://openstreetmap.org/)

### Daten
Aus den oben genannten Datenquellen haben wir folgenden Datensätze zusammengetragen und kombiniert:

-   Grünflächen:
    Zusammengesetzt aus [Parks](https://data.stadt-zuerich.ch/dataset/park) und [Picknickplätzen](https://data.stadt-zuerich.ch/dataset/picknickplatz) von Open Data Zürich, sowie Grünflächen, Parks und Grasflächen von Overpass Turbo.

-   Waldflächen:
    Aggregiert aus verschiedenen Wald- bzw. Waldflächen-Datensätzen von Overpass Turbo.

-   Parkplätze:
    Von Open Data Zürich - die Parkplätze unterteilen sich dabei in mehrere Unterkategorien:

    -   Weisse Parkplätze:
        Begrenzte Parkdauer mit Parkuhr von bis zu 30 Minuten und in manchen Fällen bis zu 4 Stunden.
    -   Blaue Parkplätze:
        Voraussetzung sind sogenannte "Parkkarten".
    -   Taxiparkplätze
    -   Behindertenparkplätze
    -   Lieferantenparkplätze

### Probleme mit den Datenquellen
Leider mussten wir feststellen, dass trotz Kombination unserer Datenquellen, die Daten nicht vollständig waren.
Dies macht sich besonders beim Vergleich von Satellitenaufnahmen der Stadt mit den eingetragenen Grünflächen und Parks bemerkbar.

### Prozess
Erste Exploration und Zusammenstellung der gefundenen Daten erfolgte in [QGIS](http://qgis.org/de/site/), einem Tool zur Bearbeitung, Erstellung und Exploration von Geodaten.

Die folgenden Bilder zeigen zwei unserer frühen Explorationen und Zusammenstellungen der von uns verwendeten Daten:

<figure>
  <img src="{{ site.urlimg }}/ZuerichParkflaechen/QGIS_Bezirke_GruenUndWaldflaechen.JPG" />
  <figcaption >Eine frühe Zusammenstellung, nur mit den Bezirken Zürichs und Daten der Grünflächen.</figcaption>
</figure>

<figure>
  <img src="{{ site.urlimg }}/ZuerichParkflaechen/QGIS_View.JPG" />
  <figcaption >Zusammenstellung aller von uns verwendeten Daten in QGIS.</figcaption>
</figure>

### Visualisierung

### Fragen
Wir untersuchten folgende Fragen:

-   Wie ist die Relation der Grünflächen zu den Parkplätzen in Zürich?
-   Inwiefern weichen einzelne Bezirke vom Gesamtdurchschnitt ab?
-   Gibt es Tendenzen und Abweichungen am Stadtrand oder im Zentrum?
-   Gibt es andere interessante Auffälligkeiten?

### Erkenntnisse
-   Zunahme der Grünflächen in Richtung der Stadtgrenzen.
-   Parks scheinen sich auf das Zentrum Zürichs zu konzentrieren.
-   Überwiegend zeitbegrenzte Parkplätze im Stadtkern Zürichs.
-   In der Nähe der Grünflächen gibt es zwar viele Parkplätze, die Mehrheit davon ist aber zeitbegrenzt.
-   Es gibt etwa doppelt so viele kostenpflichtige wie zeitbegrenzte Parkmöglichkeiten.

### Implementierung

#### Verwendete Tools/Libraries:
-   Java [Processing](https://processing.org/)
-   [Unfolding Maps](http://unfoldingmaps.org/) für die Karten
-   [GiCentre](http://www.gicentre.net/) für Diagramme
-   [ControlP5](http://www.sojamo.de/libraries/controlP5/) für Filter

#### Probleme bei der Implementierung:
-   Processing, sowie die ebenfalls genutzten Bibliotheken und Tools waren neu für uns, dementsprechend mussten wir viel Zeit für die erste Einarbeitung aufwenden.

-   Sehr viele Datensätze, allein die Parkplätze, umfassen ~50.000 einzelne Datenpunkte. Daraus folgen Performanceprobleme, die sich in der Applikation bemerkbar machen.

-   Die Flächen der Polygone, die wir aus Overpass Turbo generierten, konnten wir aufgrund von Fehlern im Aufbau der dort eingetragenen Daten nicht korrekt berechnen.

-   Wälder, die außerhalb eines Bezirks liegen, werden in der Flächenberechnung mit zum Bezirk gezählt und nicht abgeschnitten.

## Fazit
-   Processing in Kombination mit Unfolding Maps bietet vielseitige Möglichkeiten. Da diese jedoch auf Java aufbauen, treten bei sehr großen Datenmengen enorme Performanceeinbrüche auf.

-   Wir konnten wie erhofft die Grünflächen und Parkplätze leicht verständlich veranschaulichen.
