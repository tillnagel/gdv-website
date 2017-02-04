---
layout: page
title:  "LateConnections"
subheadline: So schränken uns Verspätungen der ÖPNV ein
teaser: "Sehen Sie sich die Auswirkungen von Verspätungen an"
header: no
show_meta: false
categories:
    - projects
image:
    title: LateConnections/main.png
    caption: Verspätungsansicht
author: Manuel Bäuerle &amp; Dennis Kern &amp; Dimitry Nagorny &amp; Philip Pregler &amp; Ugur Tunali
---


## Zusammenfassung
<div class="flex-video"><iframe width="640" height="360" src="https://www.youtube.com/embed/5QNCZmBAl5M" frameborder="0" allowfullscreen></iframe></div>
LateConnections ist ein Visualisierungsprojekt, welches zeigt wie uns die Verspätungen der ÖPNV in unserem Bewegungsradius einschränken. Das Projekt wurde an der Hochschule Mannheim, im Rahmen von Prof. Dr. Till Nagel's Vorlesung "Grundlagen der Visualisierung" im WS16/17 entwickelt. Die unterliegenden Daten stammen von den öffentlichen Quellen des RNV. LateConnections bietet Visualisierungen über Live-Verspätungen, Isochrones zur Anzeige eines bestimmbaren Bewegungsradius, sowie die Verknüpfung der Livedaten mit den Isochrones, um einen eingeschränkten Bewegungsradius aufgrund der Verspätungen zu visualisieren. Außerdem zeigt LateConnections die Wahrscheinlichkeit für eine pünktliche oder verspätete Bahn. Durch die zugrunde liegende Karte, inklusive diversen Points of Interests, wird eine Orientierung für den Nutzer ermöglicht. Die Verwendung von Ionic in der Entwicklung erlaubt es LateConnections sowohl als Webseite, als auch als Smartphone App zu fungieren. Das Ergebnis der Arbeit zeigt, dass eine visualisierbare Einschränkung des Bewegungsradius durch Verspätungen der ÖPNV besteht.


## Konzeptidee
LateConnections wurde entwickelt um zu visualisieren wie Verspätungen der ÖPNV unseren Bewegungsbereich in einem bestimmbaren Zeitfenster einschränken.
Zu den Fragen die LateConnections beantwortet gehören unter anderem:

- Hat meine Bahn aktuell Verspätung und um wie viele Minuten handelt es sich?
- In wie fern wirkt sich diese Verspätung auf meinen Bewegungsradius aus?
- Wie wahrscheinlich ist es dass meine Bahn sich verspätet und handelt es sich eher um kürzere oder längere Verspätungen?


## Daten

### Daten
Alle Daten zu den Haltestellen, Streckenverläufen und den Live-Daten kommen von [RNV OpenData](https://opendata.rnv-online.de/datensaetze) bzw. [RNV API](https://opendata.rnv-online.de/startinfo-api).
Des Weiteren haben wir Historiendaten der Linie 1 von Anfang Dezember 2016 bis Mitte Januar 2017 angelegt.

### Prozess
Zuerst wollten wir erreichen, dass auf der von uns eingebundenen Karte alle Haltestellen angezeigt werden. Im laufenden Projekt, das nur sehr klein sein sollte, wurde uns aber klar das das zu viele Daten sind. Deshalb entschieden wir uns die Visualisierung nur für die Linie 1 der RNV anzufertigen, da diese den studenten der HS Mannheim bekannt sein würde und durch die Mannheimer Innenstadt verläuft.

Im weitern Verlauf haben wir uns überlegt wie wir die Verspätung dargestellt bekommen. Hierzu haben wir zunächst ein Scribble angefertigt.

Zum Schluss kam noch die Visualisierung der angelegten Historiendaten. Hierfür unterteilten wir anhand der Richtlinien der RNV, ab wann für die eine Bahn als verspätet gilt. Wir nahmen letztlich eine Unterteilung von vier Rubriken vor. Das Endergebnis ist hier zu sehen:


## Ergebnisse

### Visualisierung
Damit die folgenden Visualisierungen verstanden werden hier die Legende dazu:
<figure>
  <img src="{{ site.urlimg }}/LateConnections/legend.png" />
  <figcaption >Legende</figcaption>
</figure>

<figure>
  <img src="{{ site.urlimg }}/LateConnections/main_alt.png" />
  <figcaption >Platzhalter für Gesamtansicht</figcaption>
</figure>

Hier eines unserer ersten Scribbles, bei dem wir versucht haben uns vorzustellen wie die Visualisierung später aussehen kann und wie diese dann auch auf einem Tablet wirkt:
<figure>
  <img src="{{ site.urlimg }}/LateConnections/scribble.png" />
  <figcaption >Experimentelles Scribble</figcaption>
</figure>


<figure>
  <img src="{{ site.urlimg }}/LateConnections/history.png" />
  <figcaption >Historienverlauf einer Haltestelle</figcaption>
</figure>


### Erkenntnisse
Durchschnittliche Verspätung der Linie 1 lag zum Zeitraum der Projektvorstellung im Schnitt bei 16%. 
Täglicher Zeitverlust durch Visualisierung greifbar gemacht. Wir haben erkannt, dass auch schon kleine Verspätungen eine große Wirkung auf uns haben können.

### Implementierung
Bei diesem Projekt wurden verschiedene Technologien zur Erstellung verwendet. Dabei möchten wir 	im Folgenden genauer auf die Aufgaben der eingesetzten Tools eingehen und wie diese verwendet wurden. 

Beginnend mit dem Grundgerüst unserer Applikation haben wir Ionic verwendet. Ionic ist ein hybrides Framework zur Erstellung nativer Applikationen für iOS und Android. Vorteil dieser Technologie ist, dass der geschriebene Code mit HTML, CSS und dem Framework AngularJS (ein Framework für JavaScript) ebenso einfach als Webseite verwendet werden kann. Aufgrund der vielseitigen Einsatzmöglichkeiten können demnach alle potenziellen Nutzer angesprochen werden.

Um aus unserem Grundgerüst ein erstes Konzept zu entwickeln haben wir Leaflet verwendet. Leaflet bot uns die Möglichkeit, Karten einzubinden und mithilfe der bereitgestellten Funktionalitäten eigene an das Projekt angepasste Funktionen dem Endnutzer anzubieten. Beispiele hierfür sind Setzern der Haltestellen oder das Zeichnen der Linien zwischen der Haltestellen, um nur einige zu nennen. 
	
Spannender wird es bei D3. D3 wurde verwendet, um unser Dashboard zu verwirklichen. Das Kreisdiagramm wird von unserer Seite aus nur noch mit Werten gefüllt und zeigt im Anschluss direkt 	ein perfektes Ergebnis an. Mit D3 sind in Zukunft auch viele andere Möglichkeiten der Darstellung gegeben.

Da das Hauptaugenmerk auf den sogenannten „Isochrones“ liegt, wurden wir auf eine API von r360 aufmerksam. Um die API zu verwenden, musste eine Datei eingebunden werden. An unsere GET-Anfragen mussten Koordinaten des Startpunktes und bis zu 3 Zeiten (also Zeitintervalle) angeben. Die Rückgabe war dann ein komplettes Set an Daten zur Erstellung der Isochrones, welche wir lediglich auf der Karte mit Leaflet „gemalt“ haben.

Mapbox half uns weitere Designvorstellungen für die Karte zu verwirklichen. Anpassung der Farben und der Kartenarten waren damit kein Problem.

Hier der Codeabschnitt der uns die leaflet Karte inklusive der Mapbox-Styles erzeugt:
```javascript
map = new L.Map('map', {
	doubleClickZoom: false,
	zoomControl: false
}).setView(new L.LatLng(49.485, 8.475), 13);
L.control.zoom({position: 'bottomleft'}).addTo(map);

//Put mapbox style tiles
L.tileLayer('https://api.mapbox.com/styles/v1/2good4u/cixsr1ojr001c2rplwt50xg0s/tiles/256/{z}/{x}/{y}?access_token=OURTOKEN', {
	maxZoom: 19
}).addTo(map);
```

Hier der Codeabschnitt wie mit Hilfe von [r360°]() die Isochrones erzeugt werden:
```javascript
$scope.showPolygons = function(sourceMarker, walkTime, lateness, type) {
	var blackOptions = r360.travelOptions();
	blackOptions.setIntersectionMode('Union');
	blackOptions.addSource(sourceMarker);
	blackOptions.setTravelTimes([walkTime]);
	blackOptions.setTravelType(type);
	blackOptions.setServiceKey('OURTOKEN');
	blackOptions.setServiceUrl('https://service.route360.net/germany/');
	
	r360.PolygonService.getTravelTimePolygons(blackOptions, function(polygons) {
		blackLayer.clearAndAddLayers(polygons, false);
		blackLayer.setColors([
			{ 'time': walkTime, opacity : 1 },
		]);
	});
	
	var travelOptions = r360.travelOptions();
	travelOptions.setIntersectionMode('Union');
	travelOptions.addSource(sourceMarker);
	travelOptions.setTravelTimes([(walkTime - lateness), walkTime]);
	travelOptions.setTravelType(type);
	travelOptions.setServiceKey('OURTOKEN');
	travelOptions.setServiceUrl('https://service.route360.net/germany/');

	r360.PolygonService.getTravelTimePolygons(travelOptions, function(polygons) {
		polygonLayer.clearAndAddLayers(polygons, false);
		polygonLayer.setColors([
			{ 'time': walkTime, opacity : 0, 'color': '#aa0000' },
			{ 'time': (walkTime - lateness), opacity : 0.1, 'color': '#CAFF70'},
		]);
	});
}
```

### Verwendete Technologien
<figure>
  <img src="{{ site.urlimg }}/LateConnections/technos.png" />
  <figcaption >Unsere verwendeten Technologien</figcaption>
</figure>


## Fazit
Wir haben mit LateConnections unser Ziel, die Einschränkungen unseres Bewegungsradius durch Verspätungen der ÖPNV, zu visualisieren erreicht. LateConnections erhielt von Studenten/Professoren ein positives Feedback. Einzelne äußerten bereits den Wunsch LateConnections als App auf ihrem Smartphone zu installieren, da sie die Anwendung als durchaus hilfreich ansahen.

### Einschätzung
Die geplanten Ziele für dieses Projekt wurden erreicht. Der Nutzer erkennt, ob die Straßenbahn pünktlich oder zu spät ist. Ihm wird visuell dargestellt, welche Reichweite an der gewählten Zielhaltestelle aufgrund einer Verspätung nicht mehr zu erreichen ist.
Durch eine Donutchart, wird die Verspätungshisterio der jeweiligen Linie an der Halstelle visuell gut und auf einem Blick erkennbar angezeigt.

### Ausblick
Das Projekt LateConnections stellt aktuelle Ergebnisse nur für die Linie 1 dar. Es ist aber möglich, die Ergebnisse auf die anderen Linien auzuweiten. Als Erweiterung für dieses Projekt ist ein Routing möglich. Dem Nutzer soll ermöglicht werden, während der Fahrt mit der Straßenbahn auf einem Blick zu sehen, ob die Anschlussbahn rechtzeitig erreichbar ist. Ist die Straßenbahn nicht rechtzeitig zu erreichen, soll er zur nächsten Bushaltestelle navigiert werden, wenn dort ein Bus zum gewünschten Ziel fährt.
Der Nutzer soll seine Zieleingabe anhand von Points of Interests (z.B. Arztpraxis, Bibliothek...) tätigen können.
Die Points of Interests sollen beim laufendem Routing nur in den Isolines dargestellt werden, und nicht außerhalb.