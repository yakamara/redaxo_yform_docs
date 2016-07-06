# Table Manager: Feldtypen


- [be_link](#be_link)
- [be_manager_relation](#be_manager_relation)
- [be_media](#be_media)
- [be_medialist](#be_medialist)
- [be_select_category](#be_select_category)
- [be_table](#be_table)
- [checkbox](#checkbox)
- [checkbox_sql](#checkbox_sql)
- [date](#date)
- [datestamp](#datestamp)
- [datetime](#datetime)
- [email](#email)
- [emptyname](#emptyname)
- [fieldset](#fieldset)
- [float](#float)
- [hashvalue](#hashvalue)
- [html](#html)
- [index](#index)
- [integer](#integer)
- [mediafile](#mediafile)
- [php](#php)
- [prio](#prio)
- [radio](#radio)
- [select](#select)
- [select_sql](#select_sql)
- [submits](#submits)
- [text](#text)
- [textarea](#textarea)
- [time](#time)
- [upload](#upload)
- [ycom_auth_password](#ycom_auth_password)

<a name="be_link"></a>
## be_link

Ein Redaxo-Feld, um einen <b>Redaxo-Artikel</b> auszuwählen.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `article_id`, `page_id`, `link_id`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Redaxo-Artikel`, `Seite`, `Link`
In der Liste verstecken | Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen | Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: id des Redaxo-Artikels, bspw. `1`, `5`, `20`

<a name="be_manager_relation"></a>
## be_manager_relation

Ein Auswahlfeld / Popup, um ein oder mehrere <b>Datensätze</b> mit denen einer fremden Tabelle zu <b>verknüpfen</b>, bspw. über einen Fremdschlüssel (1:n) oder eine Relationstabelle (m:n).

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein. 
Name | Name des Felds in der Datenbank, bspw. `article_id`, `person_id`, `link_id`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. die Bezeichnung der Ziel-Tabelle
Ziel-Tabelle | Name der Tabelle, deren Datensätze referenziert werden.
Ziel Tabellenfeld(er) zur Anzeige oder Zielfeld | Feldname der Tabelle, dessen Werte als Select-Box oder im Popup angezeigt werden, bspw. `name`, `title AS name` oder `CONCAT('id', ' ', 'name') AS name`
Mehrfachauswahl | Gibt an, ob ein (1:n) oder mehrere (m:n) Datensätze ausgewählt werden können, entweder in einem select-Feld oder als Popup-Fenster 
Mit "Leer-Option" | Gibt an, ob "keine Auswahl" erlaubt ist.
Fehlermeldung, wenn "Leer-Option" nicht aktiviert ist | Fehlermeldung, die dem Nutzer mitteilt, dass eine Auswahl getroffen werden muss. 
Höhe der Auswahlbox | Höhe der Auswahlbox, wenn `Mehrfachauswahl` als select-Feld aktiviert wurde. 
Filter | Zusätzliche Angaben in einer speziellen Syntax, die in [be_relation-Tutorial](table_manager_feldtypen_be-relation.md) erläutert werden.
Relationstabelle | [optional] Name der Tabelle, in der die m:n-Beziehungen abgelegt sind, bspw. `rex_project_news_tags`
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: 
* id des verknüpften Datensatzes, bspw. `1`, `5`, `20` oder
* ids der verknüpften Datensätze als `SET`, bspw. `1,5,20`, `4,8,12`, `7,10,42` oder
* leer, wenn eine Relationstabelle angegeben wurde.

> Tipp für Anfänger: Um die verknüpften Datensätze im Frontend auszugeben, wird eine SELECT-Abfrage mit einem `JOIN` benötigt.

> Tipp: Details zu den umfangreichen Einstellungsmöglichkeiten gibt's im [be_relation-Tutorial](table_manager_feldtypen_be-relation.md).

<a name="be_media"></a>
## be_media

*Funktion:* Ein Redaxo-Feld, um eine einzelne <b>Medienpool-Datei</b> auszuwählen.
*Wert in der Datenbank:* Dateiname der Medienpool-Datei, bspw. `mueller.jpg`, `preisliste.pdf`

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `image`, `attachment`, `file`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Bild`, `Anhang`, `Datei`
Defaultwert | Datei aus dem Medienpool, mit der das Eingabfeld vorausgefüllt wird, bspw. `mueller.jpg`, `preisliste.pdf` 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.


<a name="be_medialist"></a>
## be_medialist

Ein Redaxo-Feld, um ein oder mehrere <b>Medienpool-Dateien</b> auszuwählen.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `images`, `attachments`, `files`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Bilder`, `Anhänge`, `Dateien`
Preview (0/1) (opt) | Zeigt eine Bildvorschau an, wenn die Datei in der be_medialist markiert wird.
Medienpool Kategorie (opt) | ID der Medienpool-Kategorie, die bei der Auswahl der Dateien voreingestellt ist.
Types (opt) | Filtert die Dateiauswahl im Medienpool anhand der Dateiendung, bspw. `.jpg,.jpeg,.png,.gif` oder `.pdf,.docx,.doc`
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: 
* Dateinamen der Medienpool-Dateien als SET, bspw. `mueller.jpg,mayer.jpg`, `preisliste.pdf,agb.pdf`

<a name="be_select_category"></a>
## be_select_category

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `category_id`, oder `category_ids`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Kategorie`, `Kategorien`, `Navigationspunkt`
Ignoriere Offline-Kategorien  | Gibt an, ob Offline-Kategorien aus dem Auswahl-Dialogfeld ausgeschlossen werden. 
Prüfe Rechte  | ###todo###
Füge "Homepage"-Eintrag (Root) hinzu  | Gibt an, ob im Auswahl-Dialogfeld die oberste Ebene auswählbar ist.
Root-ID | Startpunkt der Auswahl-Dialogfelds, bspw. die ID einer Unterkategorie.
Sprache | ###todo###
Mehrere Felder möglich | Gibt an, ob ein oder mehrere Kategorien ausgewählt werden können.
Höhe der Auswahlbox | Höhe der Auswahlbox, wenn `Mehrere Felder möglich` aktiviert wurde. 
Nicht in Datenbank speichern | ###todo###
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="be_table"></a>
## be_table

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `table`, `features`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Info-Tabelle`, `Eigenschaften`
Anzahl Spalten |  Anzahl der Spalten, die bei der Eingabe zur Verfügung stehen.
Bezeichnung der Spalten (Menge,Preis,Irgendwas)  | Kopfzeile der Tabelle, bspw., `Leistung,Aufpreis`, `Vorname,Name`, `Artikelnummer,Größe,Preis` 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: 
* ###todo### was ist das? JSON? Eigenes Format? 

> ###todo### Hinweis: Wie kommt man an die einzelnen Werte wieder ran?

<a name="checkbox"></a>
## checkbox

Eine <b>Checkbox</b> mit vordefinierten Werten.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `active`, `online`, `visible`, `hidden`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `aktiviert`, `online`, `sichtbar?`, `ausgeblendet?`
Werte (0,1) (nicht angeklickt,angeklickt)  | Wert, der in die Datenbank geschrieben wird, bspw. `0,1`, `nein,ja`
Defaultstatus | Gibt an, ob die Checkbox vorausgewählt ist oder nicht.
Nicht in Datenbank speichern |  ###todo###
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: 
* Status der Checkbox als Zahl oder String (je nach angegebenen Wert), z.B. `0` oder `1`, `nein` oder `ja`

<a name="checkbox_sql"></a>
## checkbox_sql

Eine <b>Checkbox</b> mit Werten, die aus einer <b>SQL-Abfrage</b> stammen.
###todo### handelt es sich nicht dabei um eine Liste an Checkboxes?

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein. 
Name | Name des Felds in der Datenbank, bspw. `active_languages`, `tags`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Sichtbar in Sprachen`, `Schlagwörter`
Query mit "select id, name from .."  | SQL-Abfrage, um die Checkbox-Werte abzurufen, bspw. `SELECT id, name FROM rex_clang ORDER BY name`, `SELECT id, tag AS name FROM rex_project_tags ORDER BY id`
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: 
* ###todo###

> Tipp: Mit checkbox_sql kann man bspw. in einer News-Tabelle einer News die Sprachen zuordnen, in der sie angezeigt werden sollen. 

<a name="date"></a>
## date

Eine Reihe von Auswahlfeldern, in der ein <b>Datum</b> (Tag, Monat, Jahr) ausgewählt wird.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `date`, `date_begin`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Datum`, `Beginn der Veranstaltung`
[Startjahr] | Gibt an, mit welchem Jahr das Auswahlfeld beginnt, bspw. `1980`, `2014`
[Endjahr] oder [+5] | Gibt an, mit welchem Jahr das Auswahlfeld endet, bspw. `2020` oder `+3`, um immer 3 Jahre über der aktuellen Jahreszahl anzugeben.
[Anzeigeformat###Y###-###M###-###D###]] | Reihenfolge der Auswahlfelder für Tag, Monat und Jahr beim bearbeiteten eines Datensatzes, bspw. `am ###D###.###M###.###Y###`
Aktuelles Datum voreingestellt | Gibt an, ob das aktuelle Datum vorausgewählt ist.
Nicht in Datenbank speichern | ###todo###
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: 
* Das Datum im ###todo###-Format, z.B.  ``, ``

<a name="datestamp"></a>
## datestamp

Ein unsichtbares Feld, in das ein <b>Zeitstempel</b> gespeichert wird, wenn der Datensatz hinzugefügt oder bearbeitet wird.

###todo### Optionen überprüfen, hier müsste doch was anderes stehen?

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `datestamp`, `date_created`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Zeitstempel`, `Beginn der Veranstaltung`
[Anzeigeformat###Y###-###M###-###D###]] | Reihenfolge der Auswahlfelder für Tag, Monat und Jahr beim bearbeiteten eines Datensatzes, bspw. `am ###D###.###M###.###Y###`
Aktuelles Datum voreingestellt | Gibt an, ob das aktuelle Datum vorausgewählt ist. 
Nicht in Datenbank speichern | ###todo###
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="datetime"></a>
## datetime

Eine Reihe von Auswahlfeldern, in der <b>Datum und Uhrzeit</b> (Tag, Monat, Jahr, Stunden, Minuten, Sekunden) ausgewählt wird.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `date`, `date_begin`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Datum`, `Beginn der Veranstaltung`
[Startjahr] | Gibt an, mit welchem Jahr das Auswahlfeld beginnt, bspw. `1980`, `2014`
[Endjahr] oder [+5] | Gibt an, mit welchem Jahr das Auswahlfeld endet, bspw. `2020` oder `+3`, um immer 3 Jahre über der aktuellen Jahreszahl anzugeben.
[Anzeigeformat###Y###-###M###-###D###]] | ###todo### Reihenfolge der Auswahlfelder für Tag, Monat und Jahr beim bearbeiteten eines Datensatzes, bspw. `am ###D###.###M###.###Y###`
Aktuelles Datum voreingestellt | Gibt an, ob das aktuelle Datum vorausgewählt ist.
Nicht in Datenbank speichern | ###todo###
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="email"></a>
## email

Ein einfaches Eingabefeld für <b>E-Mail-Adressen.</b>
*Wert in der Datenbank:* String.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `email`, `contact`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `E-Mail`, `Kontakt-Mail-Adresse`
Defaultwert | E-Mail-Adresse, mit der das Eingabfeld vorausgefüllt wird, bspw. `max@mustermann.de`, `jane@smith.com` 
Nicht in Datenbank speichern  | ###todo###
cssclassname | CSS-Klasse(n), die dem Input-Element zugewiesen werden.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="emptyname"></a>
## emptyname

Ein Feld *ohne* Eingabemöglichkeit.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank
Bezeichnung | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="fieldset"></a>
## fieldset

Ein Fieldset gruppiert Formularfelder.
*Wert in der Datenbank:* **leer**.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `fieldset_product`, `fieldset_details`,
Bezeichnung | Titel des Fieldsets, das im `<legend />`-Tag notiert wird. bspw. `Produktinfos`, `Details`
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> Hinweis: Das Feld wird nur aus technischen Gründen angelegt. Das Feld wird nicht mit einem Wert gefüllt.

<a name="float"></a>
## float

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `price`, `fee`.
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Preis in EUR`, `Gebühr`
Nachkommastellen | Anzahl der erlaubten Stellen nach dem Komma, bspw. `1`, `5`, `42`
Defaultwert | Zahl, mit der das Eingabfeld vorausgefüllt wird, bspw. `0,1234`, `5` 
Nicht in Datenbank speichern | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> Tipp: Dieses Feld eignet sich besser für Zahlen als das Feld `text`, weil Dezimalzahlen mit `,` als Trennzeichen automatisch in `float`-Zahlen mit `.` als Trennzeichen umgewandelt werden.

<a name="hashvalue"></a>
## hashvalue

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnung | 
Input-Feld | 
Algorithmus | 
Salt | 
Nicht in Datenbank speichern  |
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="html"></a>
## html

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein. 
Name | Name des Felds in der Datenbank, bspw. `info`, `code`.
HTML | HTML-Code, der vor, zwischen oder nach anderen Feldern im Frontend oder Backend eingefügt wird.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="index"></a>
## index

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Felder | 
Nicht in Datenbank speichern | 
Opt. Codierfunktion | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="integer"></a>
## integer

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `price`, `quantity`.
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Preis in EUR`, `Anzahl`
Defaultwert | Zahl, mit der das Eingabfeld vorausgefüllt wird, bspw. `1`, `5`, `42` 
Nicht in Datenbank speichern  | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="mediafile"></a>
## mediafile

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Label | 
Bezeichnung | 
Maximale Größe in Kb oder Range 100,500 | 
Welche Dateien sollen erlaubt sein, kommaseparierte Liste. ".gif,.png" | 
Pflichtfeld  | 
min_err,max_err,type_err,empty_err |
Nicht in Datenbank speichern | 
Mediakategorie ID | 
Mediapool User (createuser/updateuser) | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="php"></a>
## php

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `php`, `code`.
HTML | PHP-Code, der vor, zwischen oder nach anderen Feldern im Frontend oder Backend eingefügt wird.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="prio"></a>
## prio

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `prio`, `ranking`, `order`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Priorität`, `Rang`, `Reihenfolge`
Anzeige | Feld(er), die in der Auswahl-Box angezeigt werden, bspw. `name`, `title`, `isbn`
Beschränkung | Feld(er), die die Auswahlmöglichkeiten in der Auswahl-Box beschränken, bspw. `category_id` 
Am Anfang | Vorauswahl, ob ein neuer Datensatz am Anfang oder am Ende angelegt wird. 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> Hinweis: Wenn eine Beschränkung ausgewählt wurde, kann es vorkommen, dass ein Datensatz zunächst gespeichert werden muss, damit die Beschränkung greifen kann. Dadurch lässt sich bspw. eine Reihenfolge pro Kategorie festlegen.

<a name="radio"></a>
## radio

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnung | 
Selectdefinition, kommasepariert | 
Nicht in Datenbank speichern | 
Defaultwert | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="select"></a>
## select

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnung | 
Selectdefinition, kommasepariert | 
Nicht in Datenbank speichern | 
Defaultwert | 
Mehrere Felder möglich |
Höhe der Auswahlbox | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="select_sql"></a>
## select_sql

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnung | 
Query mit "select id, name from .." | 
Defaultwert (opt.) | 
Nicht in Datenbank speichern  | 
Leeroption  |
Text bei Leeroption (Bitte auswählen) |
Mehrere Felder möglich | 
Höhe der Auswahlbox |  
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> Tipp: Ein select_sql-Feld kann ähnlich wie be_relation dazu benutzt werden, um Datensätze fremder Tabellen in einer 1:1- oder 1:n-Beziehung zu verknüpfen.

<a name="submits"></a>
## submits

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnungen (kommasepariert) | 
Werte (optional, kommasepariert) | 
Nicht in Datenbank speichern | 
Defaultwert | 
CSS Klassen (kommasepariert) |
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="text"></a>
## text

Input-Feld zur Eingabe eines Textes.

Option | Erläuterung
------ | ------ 
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `name`, `prename`, `title`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Name`, `Vorname`, `Titel`
Defaultwert | Wert, der beim Aufruf des Formulars eingetragen ist, bspw. `Musterfirma`, `Paul`, `Musterprojekt`
Nicht in der Datenbank speichern |
cssclassname | Zusätzliche CSS-Klasse(n), die dem Feld zugeordnet werden, bspw., um das Feld im Frontend oder Backend gesondert zu formatieren.
In der Liste verstecken | Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen | Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: String, bspw. `Musterfirma`, `Paul`, `Musterprojekt`

<a name="textarea"></a>
## textarea

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. "text", "description", "message"
Bezeichnung |  Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. "Text", "Beschreibung", "Nachricht"
Defaultwert | Wert, der beim Aufruf des Formulars eingetragen ist, bspw. `Geben Sie hier Ihre Nachricht ein`
Nicht in Datenbank speichern | ###todo###
classes | Zusätzliche CSS-Klasse(n), die dem Feld zugeordnet werden, bspw., um das Feld im Frontend oder Backend gesondert zu formatieren.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="time"></a>
## time

Eine Reihe von Auswahlfeldern, in der die <b>Uhrzeit</b> (Stunden, Minuten, Sekunden) ausgewählt wird.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. `time`, `time_begin`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. `Uhrzeit`, `Beginn der Veranstaltung`
[Stundenraster] | optional: Kommagetrennte Liste an Stunden, die für den Nutzer zur Auswahl stehen sollen, bspw. `0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23`
[Minutenraster] | optional: Kommagetrennte Liste an Minuten, die für den Nutzer zur Auswahl stehen sollen, bspw. `0,15,30,45`, `0,10,20,30,40,50`
[Anzeigeformat ###H###h ###I###m] |  Reihenfolge der Auswahlfelder für Stunde und Minute beim bearbeiteten eines Datensatzes, bspw. `um ###H###:###I### Uhr`
Nicht in Datenbank speichern | ###todo###
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="upload"></a>
## upload

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Label | 
Bezeichnung | 
Maximale Größe in Kb oder Range 100,500 | 
Welche Dateien sollen erlaubt sein, kommaseparierte Liste. ".gif,.png" | 
Pflichtfeld | 
min_err,max_err,type_err,empty_err,delete_file_msg |
Speichermodus | 
`database`: Dateiname wird gespeichert in Feldnamen |
Eigener Uploadordner [optional] |
Dateiprefix [optional] |
Defaultfile |
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="ycom_auth_password"></a>
## ycom_auth_password

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnung | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.
