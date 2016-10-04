# Geo-Plugin

Mit dem Geo-Plugin hat man ein neues Feld im Manager zur Verfügung "google_geocode". MIt diesem Feld kann man Positionen verwalten. Mit dem entsprechenden API-Key von Google bekommt man im entsprechenden Datensatz eine Karte angezeigt und kann dort die Markierung positionieren. Weiterhin kann man über "Names Postionsfindung" verschiedene Felder des Datensatzes definieren (kommasepariert) um damit über die Google Api aus einem Adresssatz eine Position zu bekommen.

Die entsprechende Position wird folgendermaßen gespeichert: lat,lng

Eingaben bei Names Positionsfindung sind abhängig von den vorhandenen Datenfeldern, aber folgendes Beispiel wir sicher oft auftauchen

    country, city,street
