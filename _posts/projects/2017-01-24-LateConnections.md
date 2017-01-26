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
LateConnections ist ein Visualisierungsprojekt, welches zeigt wie uns die Verspätungen der ÖPNV in unserem Bewegungsradius einschränken. Das Projekt wurde an der Hochschule Mannheim, im Rahmen von Prof. Dr. Till Nagel's Vorlesung "Grundlagen der Visualisierung" im WS16/17 entwickelt. Die unterliegenden Daten stammen von den öffentlichen Quellen des RNV. LateConnections bietet Visualisierungen über Live-Verspätungen, Isochrones zur Anzeige eines bestimmbaren Bewegungsradius, sowie die Verknüpfung der Livedaten mit den Isochrones, um einen eingeschränkten Bewegungsradius aufgrund der Verspätungen zu visualisieren. Außerdem zeigt LateConnections die Wahrscheinlichkeit für eine pünktliche oder verspätete Bahn. Durch die zugrunde liegende Karte, inklusive diversen Points of Interests, wird eine Orientierung für den Nutzer ermöglicht. Die Verwendung von Ionic in der Entwicklung erlaubt es LateConnections sowohl als Webseite, als auch als Smartphone App zu fungieren. Das Ergebnis der Arbeit zeigt, dass eine visualisierbare Einschränkung des Bewegungsradius durch Verspätungen der ÖPNV besteht.


## Einführung / Konzept
LateConnections wurde entwickelt um zu visualisieren wie Verspätungen der ÖPNV unseren Bewegungsbereich in einem bestimmbaren Zeitfenster einschränken.
Zu den Fragen die LateConnections beantwortet gehören unter anderem:
- Hat meine Bahn aktuell Verspätung und um wie viele Minuten handelt es sich?
- In wie fern wirkt sich diese Verspätung auf meinen Bewegungsradius aus?
- Wie wahrscheinlich ist es dass meine Bahn sich verspätet und handelt es sich eher um kürzere oder längere Verspätungen?


- Einführung: Was ist die Motivation hinter Ihrem Projekt?
- Konzept: Was ist die Grundidee, Hauptfrage, wichtigste Hypothese?


## Daten / Auswertung

### Daten
Quellen, Erhebung, Parsing, Aggregation, ...

Wir haben die Daten von ... genutzt, ...

### Prozess
Sinnvolle Auswahl relevanter Experimente.

<figure>
  <img src="{{ site.urlimg }}/LateConnections/history.png" />
  <figcaption >Historienverlauf einer Haltestelle</figcaption>
</figure>

## Prototyp / Ergebnisse

### Visualisierung
Ergebnisse, Design, Prototyp. Darstellungen echter oder ausgewählter Daten.

### Erkenntnisse
Was haben Sie herausgefunden? Können Sie ein/zwei Aussagen oder Stories hervorheben?

### Implementierung
Wie haben Sie die Visualisierung umgesetzt? Welche Tools haben Sie für welche Schritte eingesetzt?


```javascript
function setup() {
  Data data = loadData();
  doSomeVisualization(data);
}
```


## Fazit
- Reflektion: Haben Sie erreicht, was sie wollten? Ist Ihr Ergebnis hilfreich?
- Ausblick: Welche weiteren Ideen haben Sie? Was könnten interessante
nächste Schritte sein?
