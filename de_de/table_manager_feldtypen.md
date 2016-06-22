# Table Manager: Feldtypen

* Alle Feldtypen auflisten
* Informationen zu den einzelnen Parametern
* Beispiele bei den einzelnen Parametern (Klassen, Vorauswahl, etc.)
* Keine zu ausführlichen Beispiele zu be_relation, dafür eine Extra-Seite


be_link

Feld zur Auswahl eines Redaxo-Artikels.

Optionen:
* Priorität: Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
* Name: Name des Felds in der Datenbank, bspw. "article_id", "page_id", "link_id"
* Bezeichnung: Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. "Redaxo-Artikel", "Seite", "Link"
* In der Liste verstecken: Versteckt das Feld in der Tabellen-Übersicht.
* Als Suchfeld aufnehmen: Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: id des Redaxo-Artikels, bspw. "1", "5", "20"

be_manager_relation

be_media

be_medialist

be_select_category

be_table

checkbox

checkbox_sql

date

datestamp

datetime

email

emptyname

fieldset

float

hashvalue

html

index

integer

mediafile

php

prio

radio

select

select_sql

submits

text

Input-Feld zur Eingabe eines Textes.

Optionen:
* Priorität: Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
* Name: Name des Felds in der Datenbank, bspw. "name", "prename", "title"
* Bezeichnung: Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. "Name", "Vorname", "Titel"
* Defaultwert: Wert, der beim Aufruf des Formulars eingetragen ist, bspw. "Musterfirma", "Paul", "Musterprojekt"
* Nicht in der Datenbank speichern: ###todo### Wan benötigt man das?
* cssclassname: Zusätzliche CSS-Klasse(n), die dem Feld zugeordnet werden, bspw., um das Feld im Frontend oder Backend gesondert zu formatieren.
* In der Liste verstecken: Versteckt das Feld in der Tabellen-Übersicht.
* Als Suchfeld aufnehmen: Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: String, bspw. "Musterfirma", "Paul", "Musterprojekt"

textarea

time

upload
