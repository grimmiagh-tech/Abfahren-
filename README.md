# Abfahrten Berlin

Echtzeit-Abfahrten des Berliner ÖPNV (S-Bahn, U-Bahn, Tram, Bus, Fähre, Regio) im Stil einer Abfahrtstafel.
Wie der Finanzindex: eine einzelne `index.html`, kein Build-Schritt, kein eigener Server – läuft auf GitHub Pages.

## Funktionen
- **Mehrere Tafeln** gleichzeitig (z. B. U8 vom Alexanderplatz, S-Bahn vom Ostkreuz, Bus vor der Haustür), jede mit
  - **Abfahrt von**: Haltestelle per Suche oder 📍 (in der Nähe per GPS)
  - **Richtung**: nur Fahrten, die über eine bestimmte Haltestelle fahren
  - **Verkehrsmittel** und **Linien** (z. B. nur U8 oder M4 + M5)
  - **Anzahl Abfahrten** (1–20) und optionalem Namen
- Zwei Designs: **LED** (bernsteinfarbener BVG-Anzeiger) und **Modern** (Bahnsteiganzeige mit Linienfarben), Spalten Auto/1/2/3
- Verspätung (`+4`), Ausfälle, Störungsmeldungen als Laufschrift; Aktualisierung alle 30 s

## Dauerbetrieb (Wandtablet)
- Alle Tafeln werden automatisch so skaliert, dass sie ohne Scrollen auf den Bildschirm passen
- Bildschirm wach halten (Screen Wake Lock API, braucht HTTPS – GitHub Pages passt)
- Nachts dimmen (Uhrzeiten einstellbar)
- Tägliches Neuladen um 4 Uhr (Speicher aufräumen, neue App-Version übernehmen)
- Anzeige verschiebt sich alle 3 Minuten um wenige Pixel (gegen Einbrennen)
- Bedienknöpfe und Mauszeiger blenden sich nach 6 s aus, Tippen holt sie zurück
- Bei Verbindungsabbruch bleibt der letzte Stand sichtbar („offline · Stand 18:32“), neuer Versuch alle 30 s

Einstellungen liegen im `localStorage` des Tablets. Favoriten aus der ersten Version werden beim ersten Start automatisch zu Tafeln.

## Daten
[`v6.bvg.transport.rest`](https://v6.bvg.transport.rest) – freie REST-API auf Basis der BVG-Echtzeitdaten, kein API-Schlüssel nötig.
Community-Dienst ohne Garantie, Limit ca. 100 Anfragen/Minute.

## Vorschau / Demo
`index.html?demo` zeigt Beispieldaten (ohne Netz), Screenshots liegen in `vorschau/`.
Der Demo-Modus nutzt einen eigenen Speicherbereich, echte Favoriten bleiben unberührt.
