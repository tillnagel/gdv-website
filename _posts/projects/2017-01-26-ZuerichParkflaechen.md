---
layout: page
title:  "Zürich Parkflächen"
subheadline: Veranschaulichung und Exploration der Züricher Natur und Parkplätze 

teaser: "Vergleich von Natur und Parkplätzen in der Grünstadt Zürich"
header: no
show_meta: false
categories:
    - projects
image:
    title: ZuerichParkflaechen/zp_teaser.jpg
    caption: Teaser
author: Ahmet Ekiz, Kevin Schorpp, Klaus Hipp, Mihkail Polishuk
---

## [Abstract]
Die Anwendung visualisiert diverse Geodaten zu Wald-, Grünflächen und Parks in der „Grünstadt Zürich“ und ermöglicht einen Vergleich diesbezüglicher Flächenverteilung mit Parkflächen.

Gegliedert wird die Darstellung in eine Übersichts-, sowie eine Diagrammansicht und vier Detailansichten zur Veranschaulichung maximal zweier Bezirke Zürichs und deren Gegenüberstellung zum Züricher Durchschnitt.


## Einführung
<!--- Einführung: Was ist die Motivation hinter Ihrem Projekt?
- Konzept: Was ist die Grundidee, Hauptfrage, wichtigste Hypothese?-->

Dieses kleine Datenvisualisierungsprojekt ist im Rahmen des Wintersemesters 2016/2017 entstanden. Ziel war es eine Interaktive Datenvisualisierung zum Thema Smart City und Urbanen Räumen.
Nach einiger Recherche zu verfügbaren Datenquellen, griffen wir eine Konzeptidee unseres Dozenten Herr Prof. Dr. Nagel auf, Parks und Parkplätze der Stadt Zürich in Relation zu setzen und festzustellen ob eine gewisse Verteilung zu erkennen ist.

## Funktionalitäten:
Die Übersichtskarte (A) erlaubt das einfache Selektieren von bis zu zwei Bezirken, die in den jeweiligen Spalten zur Detailansicht (B) dargestellt werden.
Diese zeigen jeweils in zwei übereinanderliegenden Panels die Grünflächen (oben) und die verschiedenen Parkplatzarten (unten), die jeweils gefiltert werden können.

Bei fehlender Selektion oder Auswahl eines einzelnen Bezirkes wird in der rechten Spalte gesamt Zürich zum Vergleich eingeblendet.

Die Diagrammansicht (C) stellt die Gesamtflächen der visualisierten Bezirke dem Züricher Absolut und Durchschnitt gegenüber.


<figure>
  <img src="{{ site.urlimg }}/ZuerichParkflaechen/zp_functions_image.png" />
  <figcaption >Allgemeine Übersicht über die Funktionalitäten der Anwendung</figcaption>
</figure>

- - - 

## Daten / Auswertung

### Daten
<!--Quellen, Erhebung, Parsing, Aggregation, ...-->

Genutzte Datenquellen:
[Opendata Projekt der Grünstadt Zürich](https://data.stadt-zuerich.ch/)
[Overpass Turbo](https://overpass-turbo.eu/) ein Datenfilterungs Tool für [OpenStreetMap](http://openstreetmap.org/)

### Prozess
<!--Sinnvolle Auswahl relevanter Experimente.-->

Erste Exploration und zusammenstellung der gefundenen Daten erfolge in [QGIS](http://qgis.org/de/site/) einem Tool zur Bearbeitung, Erstellung und Exploration von unteranderem Geo Daten.

Die folgenden Bilder zeigen zwei unsere frühen Explorationen und Zusammenstellungen der von uns verwendeten Daten.

<figure>
  <img src="{{ site.urlimg }}/ZuerichParkflaechen/QGIS_Bezirke_GruenUndWaldflaechen.JPG" />
  <figcaption >Eine frühe Zusammenstellung, nur mit den Bezirken Zürichs und den Daten der Grünflächen</figcaption>
</figure>

<figure>
  <img src="{{ site.urlimg }}/ZuerichParkflaechen/QGIS_View.JPG" />
  <figcaption >Zusammenstellung aller von uns verwendeten Daten in QGIS</figcaption>
</figure>


<!--## Prototyp / Ergebnisse
Hier sind einige unserer Prototypen und Entwicklungsschritte zu sehen: -->

### Visualisierung
<!--Ergebnisse, Design, Prototyp. Darstellungen echter oder ausgewählter Daten.-->

### Erkenntnisse
<!--Was haben Sie herausgefunden? Können Sie ein/zwei Aussagen oder Stories hervorheben?-->

### Implementierung
#### Verwendete Tools/Libraries:
-- Java Processing
-- Unfolding Maps für die Karten
-- GiCentre für Diagramme
-- ControlP5 für Filter

<!--Wie haben Sie die Visualisierung umgesetzt? Welche Tools haben Sie für welche Schritte eingesetzt?-->


#### Probleme bei der Implementierung:
- Processing und die anderen genutzten Bibliotheken und Tools waren neu für uns, dementsprechend mussten wir viel Zeit für die Einarbeitung aufwenden.
- Sehr viele Daten, allein die Parkplätze umfassten ~50.000 einzelne Datenpunkte.
demensprechend hatten wir mit einigen Performanceproblemen zu kämpfen.
- Eigene Marker für die Maps erstellen, wir entschieden uns schlussendlich von uns angefertigte Icons zu verwenden.
- Die Flächen der Polygone die wir aus Overpass Turbo generierten, konnten wir aufgrund von Fehlern im Aufbau der dort eingetragenen Daten nicht korrekt berechnen.
- Wälder die außerhalb eines Bezirks liegen werden mit zum Bezirk gezählt.


<!--```javascript
function setup() {
  Data data = loadData();
  doSomeVisualization(data);
}
```-->

- - - 

## Fazit
<!--- Reflektion: Haben Sie erreicht, was sie wollten? Ist Ihr Ergebnis hilfreich?
- Ausblick: Welche weiteren Ideen haben Sie? Was könnten interessante
nächste Schritte sein?-->

- Processing in Kombination mit Unfolding Maps bietet vielseitige Möglichkeiten, da diese jedoch auf Java aufbauen, treten bei sehr großen Datenmengen enorme Performance einbrüche auf. 
- Wir konnten wie erhofft die Grünflächen und Parkplätze leicht verständlich veranschaulichen.
