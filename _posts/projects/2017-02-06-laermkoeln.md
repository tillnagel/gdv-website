---
layout: page
title: "Ruhezonen in Köln"
subheadline: "Entspannungspotenzial der Grünflächen in Betracht des umliegenden Lärms"
teaser: "Entspannungspotenzial der Grünflächen in Betracht des umliegenden Lärms"
header: no
show_meta: false
categories:
    - projects
image:
    title: laermkoeln/teaser.png
    caption: Finaler Prototyp
author: Christine Ernst, Deniz Kaya, Patrick Fruh, Suzy Djomo Kouamou
---

[Abstract] In diesem Dokument wird beschrieben, wie die Visualisierung des oben genannten Projektes in unserem Team umgesetzt wurde. Hierbei gehen wir auf die Daten, die Probleme und Lösungswege ein, stellen die verwendeten Tools und unsere Ergebnisse vor. Zum Schluss wird in einem Fazit unser Ergebnis kurz zusammengefasst und wir stellen weitere Ideen vor, wie das Projekt fortgeführt werden kann.

## Einführung / Konzept

Parks sind in einer Großstadt oft die einzige Möglichkeit, dem Beton und den Menschenmengen für eine kurze Weile zu entfliehen. Köln bezeichnet sich diesbezüglich als grüne Stadt. Doch wie viel Entspannungspotenzial haben diese Grünflächen in Betracht des umliegenden Lärms wirklich?
Anhand unserer Karte kann man sich davon ein Bild machen, welche besonders ruhige und welche lärmbelastete Parks sind. Bei Letzteren besteht für die Stadt Köln ein großes Potenzial, den Lärmpegel zu reduzieren und seinen Bürgern damit langfristig etwas Gutes zu tun.

Wir haben uns folgende Fragen gestellt.
- Wo befinden sich die Grünflächen in Köln?
- Welche Hauptlärmquellen sind diese ausgesetzt?
- Wie ist die Lärmbelastung der Grünflächen im Vergleich?

Unser Ziel ist es, dem Betrachter eine Exploration zu ermöglichen, die nicht nur informativ ist, sondern auch Spaß macht. Aus diesem Grund werden nicht nur die Grünflächen und der Lärmbereich in Köln angezeigt. Es besteht die Möglichkeit die Hauptlärmquellen aus- bzw. einzuschalten. So erhält man nicht nur einen Überblick darüber, wie stark die Grünfläche belastet ist, sondern auch darüber welche Teilbereich des Parks belastet sind und durch welche Lärmquellen.
Um detaillierte Informationen zu den Lärmwerten auf den Grünflächen zu liefern, werden neben dem Namen und der Größe des Parks auch die unterschiedlichen Lärmquellen aufgelistet, welche diesen Bereich beeinflussen. Darüber hinaus wird der gemessene Wert in dB angegeben.


## Daten / Auswertung

### Daten
Auf dem [offenen Datenportal der Stadt Köln](https://www.offenedaten-koeln.de/) erhält man unter anderem Informationen darüber, wo besonders hohe Ausschläge einiger Hauptlärmquellen gemessen wurden. Hier werden neben dem Straßenlärm und dem Schienenverkehr der DB, des KVBs und des HGKs, auch die Werte von Industrie und dem Luftverkehr über eine interaktive Webanimation bereitgestellt. Dabei werden nicht nur Informationen über die Ausprägung des Lärms innerhalb des Intervalls von 55-75dB betrachtet, man kann sich auch die Unterschiede zwischen Tag und Nacht vor Augen führen. Im vorliegenden Projekt wurden ebendiese Daten aufbereitet und in Bezug zu den Grünflächen Kölns gestellt.

OpenData Köln bietet eine REST API wodurch man mit Hilfe des "[AGStoShapefile](https://github.com/tannerjt/AGStoShapefile)" Scripts die GeoJSON Dateien erhalten kann. Zur Vereinfachung dieser Daten wurde "[Mapshaper](https://github.com/mbloch/mapshaper)" genutzt. Dieses Tool führt mehrere Dateien mit Ebenen zusammen ("merge"). So wurden aus anfänglich ca. 30 verschiedenen Dateien zu Straßenlärm eine einzelne. Nach der Zusammenführung der Dateien wurde diese "aufgelöst". Da in den Dateien eine sehr große Anzahl von Ebenen vorhanden war, mussten diese reduziert werden. Nach der Ausführung gab es zu jeder Lärmquelle nur noch eine Ebene für jede Dezibel-Größe. Zur Reduzierung der Punkte der Polygone und für eine bessere Performance, wurden die Dateien "vereinfacht". 

### Prozess
Da die Daten auf den Lärmbereich von 55-75 Dezibel beschränkt sind, kann die bei der Visualisierung als lärmfrei dargestellte Fläche tatsächlich leistungsschwächere bzw. -stärkere Lärmquellen beinhalten.
Die erste Visualisierung erfolgte in Processing, wurde aber wegen dem kurzfristigem Wechsel zu Mapbox und dem daraus resultierenden Zeitmangel nicht komplett übernommen.
Da wir zu Beginn aufgrund der großen, uns zur Verfügung stehenden Datenmenge, Performanceprobleme hatten, entschieden wir uns zunächst dafür, nur eine Auswahl an Parks darzustellen. Hierfür recherchierten wir über verschiedene Webseiten die größten und beliebtesten Parks in Köln. Diese legten wir, mithilfe von Photoshop, unter die Visualisierung unserer Daten, die es bereits von der Stadt Köln gab, um schon früh Erkenntnisse zu besonders spannenden Grünflächen zu erhalten.

Ursprünglich sollten die Buttons zum ein- bzw. ausblenden des Lärms neben dem Namen des Projektes, über die gesamte Breite des Bildes verteilt sein.

<figure>
  <img src="{{ site.urlimg }}/laermkoeln/bild1.png" />
  <figcaption>Mockup Startscreen</figcaption>
</figure>
<figure>
  <img src="{{ site.urlimg }}/laermkoeln/bild2.png" />
  <figcaption>Startscreen in Processing</figcaption>
</figure>

In der Version in Processing waren Parks anklickbar. Dabei wurde auf die geklickte Grünfläche gezoomt und es hat sich ein Detailfeld mit allen nötigen Infos zur gewählten Fläche geöffnet. Ursprünglich war geplant, dass das Kreisdiagramm sich in diesem Detailfeld befindet.

<figure>
  <img src="{{ site.urlimg }}/laermkoeln/bild3.png" />
  <figcaption>Mockup Detailansicht für Grünflächen (Parks)</figcaption>
</figure>
<figure>
  <img src="{{ site.urlimg }}/laermkoeln/bild4.png" />
  <figcaption>Detailansicht für Grünflächen in Processing (nicht vollständig umgesetzt)</figcaption>
</figure>

Um dem Betrachter Hintergrundinformationen zum Projekt zur Verfügung zu stellen, hatten wir auf der Startseite einen "Info-Button" geplant.

<figure>
  <img src="{{ site.urlimg }}/laermkoeln/bild5.png" />
  <figcaption>Anzeige der Informationen in Processing (nicht vollständig umgesetzt)</figcaption>
</figure>

## Prototyp / Ergebnisse
Bei der Darstellung der Stadt haben wir uns für eine 3D-Karte entschieden. Beim Start der Webapplikation wird Köln mitsamt aller Hauptlärmquellen und Grünflächen von oben angezeigt. Die Lärmquellen wurden in verschiedenen Farben visualisiert und können aus- und wieder eingeblendet werden, während die Grünflächen in grün dargestellt werden. Die Stärke der Lärmausprägung wird in einem Balkendiagramm angezeigt, welches die Daten aktualisiert, wenn der Mauszeiger seine Position auf der Karte ändert. Sofern sich in diesem Bereich eine Grünfläche befindet, öffnet sich ein Kreisdiagramm in dem der prozentuale Anteil der Lärmquellen sowie der lärmfreien Zone visualisiert sind. 
Der Nutzer hat die Möglichkeit näher heran zu zoomen und die Karte zu drehen, was die 3D-Ansicht erscheinen lässt. Es ist außerdem möglich wieder hinaus zu zoomen. Es ist ebenfalls möglich die Karte in alle Richtungen zu verschieben. Die Lärmquellen werden aber nur für den zur Verfügung stehenden Bereich angezeigt. Es wurden hier echte Daten verwendet, wobei Lärmquellen, die keinerlei Einfluss auf die Grünflächen haben, z.B. Flughafen-Lärm, nicht dargestellt werden.

Aufgrund der Visualisierung wurde deutlich, dass Lärm in Grünflächen weitestgehend gleich verteilt ist. Hauptlärmverursacher sind der Straßenlärm und der Zugverkehr der Deutschen Bahn. Der Industrielärm fällt hingegen nur sehr gering aus. In dem gemessenen Lärmbereich wird ziemlich deutlich, dass es kaum Parks gibt, die nicht von Lärm betroffen sind, wobei der Hauptlärm sich meist am Rand lokalisiert. 

### Processing
Die erste Implementierung erfolgte in [Processing](https://processing.org).  Processing beinhaltet eine eigene Entwicklungsumgebung welche für die Einsatzbereiche von Grafik, Simulation und Animation spezialisiert ist. Es hat den Charakter einer stark vereinfachten Version der Programmiersprache Java, ermöglicht allerdings Interaktionen und visuelle Elemente zu programmieren. Processing enthält Klassenbibliotheken welche vor allem für Videos, Grafiken, Grafikformate, Sound, Animation, Typographie, 3D, Simulation, Datenzugriff und -transfer sowie Netzwerkprotokolle beinhalten und ist somit sehr gut für die Visualisierung von Daten geeignet.

Die Benutzeroberfläche in Processing wurde mit "G4P" umgesetzt. Um die Karte darstellen zu können wurde "[Unfolding Maps](http://unfoldingmaps.org)" genutzt und zur farblichen Kennzeichnung der Lärmquellen "[giCentreUtils](http://www.gicentre.net/utils/)". Die geplante Detailansicht sollte eine Detailbox enthalten mit allen notwendigen Daten und Diagrammen zur visuellen Darstellung der Auswertung der Daten. Beides sind Elemente von "[ControlP5](http://www.sojamo.de/libraries/controlP5/)".
Zur besseren Arbeit im Team haben wir uns für [GitHub](https://github.com) entschieden. Der Programmcode konnte so zeitgleich von mehreren Personen bearbeitet werden. So ist es möglich jederzeit den aktuellen Code zu erhalten und zu bearbeiten.

Schwierigkeiten traten auf, wenn der Mauszeiger sich über einer Grünfläche befand, dies mit einem Hover-Effekt darzustellen. Da die Daten der Grünfläche in einzelnen Markern hinterlegt waren, wäre hier eine Berechnung notwendig gewesen um die Farbe aller Marker zeitgleich zu ändern. Diese Berechnung war sehr kompliziert und konnte auch nicht fehlerfrei umgesetzt werden.
Da die Daten für den Lärm in einer Datei vereinfacht hinterlegt wurden, mussten diese für die Filter-Funktion wieder separiert werden. Dadurch war es nicht so einfach wirklich alle entsprechenden Lärm-Marker ein- bzw. wieder einzublenden.
Es gab ebenfalls Probleme bei der Darstellung der Informationen für die Grünflächen im Detail. So war es in Processing sehr schwer die Daten auszuwerten, da die GeoJSON-Daten einzeln ausgelesen und verglichen werden mussten. Es konnten einige Libraries nicht eingebunden werden, so dass wir nur mit Hilfe des "GeoJSONReader" an diese Daten kamen. Allerdings war die Rückgabe eine Liste mit allen Polygonen. Diese Daten mussten nun zu einzelnen Daten zerlegt werden um diese zur Auswertung nutzen zu können.
Weitere Probleme gab es bei der Visualisierung der Diagramme in der Detailbox. Trotz aller Anstrengungen wurden diese nicht angezeigt und so war eine Weiterarbeit an diesen nicht möglich. 
Da neben den oben genannten Problemen weitere schwerwiegende bei der Performance auftragen (langsames Laden der Daten und starkes Ruckeln) und keine Libraries zur Flächenberechnung der Polygone zur Verfügung standen, haben wir uns entschieden das Projekt in Mapbox umzusetzen.

### Mapbox GL und Turf.js
Mit dem Tool [Mapbox](https://www.mapbox.com) kann man interaktive Karten bauen und ist besonders für Designer und Programmierer geeignet. Die Karten sowie die Marker können individuell gestaltet werden und es können einfach Informationen hinzugefügt werden. Durch die Library Mapbox GL ist es möglich das Programm in JavaScript zu implementieren und mit Hilfe von CSS die Darstellung zu bearbeiten.

<figure>
  <img src="{{ site.urlimg }}/laermkoeln/bild6.png" />
  <figcaption>Darstellung von Mapbox</figcaption>
</figure>
<figure>
  <img src="{{ site.urlimg }}/laermkoeln/bild7.png" />
  <figcaption>Styles in Mapbox</figcaption>
</figure>

[Turf](http://turfjs.org) ist eine Library von JavaScript mit der die Flächen berechnet und Überschneidungen von Bereichen gefunden werden können. Dies ermöglicht Daten besser analysieren und verarbeiten zu können.
Die Flächenberechnung und -auswertung mit Turf führte leider zu ein paar Problemen. So kam es bei der Berechnung ab und an zu Abstürzen des Programmes. Im Tortendiagramm, welches den Prozentualen Anteil von Lärm und Lärmfreien Bereichen darstellt, kommt es zu Überschneidungen. Da wir nur die Werte der einzelnen Lärmbereiche erhalten haben, war es (bisher) nicht möglich die tatsächlich lärmfreien Bereiche zu berechnen. Dadurch sieht es in einigen Bereichen so aus, als ob mehr Lärm vorhanden ist, als es tatsächlich der Fall ist.

## Fazit
Lärm ist nicht der einzige Aspekt, der den Entspannungsgrad einer Freizeitanlage bestimmt. Allerdings bietet eine ruhige Umgebung eine wichtige Grundlage. 
Aufgrund der bereits erwähnten Umstellung und dem daraus resultierenden Zeitmangel, mussten leider einige Visualisierungen anders oder vereinfacht dargestellt werden. So konnten wir die Vergrößerung auf die Grünfläche bei Klick, sowie die Detail-Informationen, nicht mehr umsetzen. Es war ebenfalls nicht mehr möglich, die korrekte Darstellung des Lärmbereichs im Kreisdiagramm zu realisieren.
Es besteht die Möglichkeit weitere Details zu den Grünflächen hinzuzufügen. Weiter könnten die Parks unter den Grünflächen hervorgehoben sowie anklickbar gemacht werden, damit bei Klick direkt auf diese gezoomt wird. Einen Vergleich zwischen mehreren Parks können wir uns ebenfalls gut vorstellen.