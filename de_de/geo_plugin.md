# Geo-Plugin

Das Geo-Plugin stellt Funktionen zur Geocodierung von Adressdaten zur Verfügung. Frei festgelegte Felder können als Standortinformationen für die Geocodierung hrangezogen werden. Eine Massenbearbeitung z.B. importierter Daten ist ebefalls verfügbar. 

## Installation
Das Geo-Plugin wird in Redaxo über die Addonverwaltung installiert und aktiviert. (geo) 
Nach der Installation stehen die Funktionen des Geo-Plugins als neues Feld im Table Manager und im Reiter Geo in YForm zur Verfügung. 

## Neues Geo-Feld anlegen
- Füge im Table Manager in der gewünchten Tabelle ein neues Feld google_geocode hinzu
- Lege einen Namen und eine Bezeichnung fest
- Unter **Names Positionsfindung** trägst du kommagetrennt die Feldernamen(keys) deiner Tabelle ein, die zur Positionsfindung dienen sollen, z.B.: country, city, street. 
- Jetzt kannst du noch die **Höhe** und **Breite** deiner Map im Table Manager festlegen. 
- Hinterlege noch einen **Google-Maps-Api-Key**, diesen kann Du hier anfordern: https://developers.google.com/maps/documentation/javascript/get-api-key?hl=de
- Unter **Default** kannst du Standard-Koordination zur Map-Anzeige festlegen, wenn noch keine Koordinaten ermittelt wurden. 

## Datenformat
Das Feld speichert die Daten kommagetrennt im Format lat,lng.
  > Beispiel: 49.578502,2.761796000000004

## Massen-Geocoding 
Will man nicht alle Datensätze selbst bearbeiten, kann man sich die Geodaten automatisch generieren lassen. 
Findet das Geo-Plugin eine Tabelle mit dem Geodaten-Feld, kann man diese in YFom im Reiter **Geo** auswählen und automatisch geocodieren lassen. 

## Verwendung in der Tabelle
Ist der Google-Api-Code korrekt, zeigt das Feld in der Tabelle bereits eine Karte an. 

### Position ermitteln und bearbeiten
- Mit Click auf **Position holen** wird die Position des Standortes abgerufen. 
- Mit **Lösche Position** wird das Feld zurückgesetzt
- Die Position kann mit dem Standortmarker in der Google-Map durch drag & drop korrigiert werden. 

## Ausgabe einer Map
Eine Ausgabe der der Daten als Map stellt das Geo-Plugin nicht bereit. Nutze die Geo-Daten zur weiteren Verarbeitung  z.B. für: Google Map oder Leaflet
