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

<a name="be_manager_relation"></a>
## be_manager_relation

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Ziel-Tabelle | 
Ziel Tabellenfeld(er) zur Anzeige oder Zielfeld | 
Mehrfachauswahl | 
Mit "Leer-Option" | 
Fehlermeldung, wenn "Leer-Option" nicht aktiviert ist | 
Höhe der Auswahlbox | 
Filter | 
Relationstabelle | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="be_media"></a>
## be_media

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Defaultwert | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="be_medialist"></a>
## be_medialist

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Preview (0/1) (opt) | 
Medienpool Kategorie (opt) | 
Types (opt) | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="be_select_category"></a>
## be_select_category

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Ignoriere Offline-Kategorien  | 
Prüfe Rechte  | 
Füge "Homepage"-Eintrag (Root) hinzu  | 
Root-ID | 
Sprache | 
Mehrere Felder möglich  | 
Höhe der Auswahlbox | 
Nicht in Datenbank speichern |
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="be_table"></a>
## be_table

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Anzahl Spalten  | 
Bezeichnung der Spalten (Menge,Preis,Irgendwas)  | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="checkbox"></a>
## checkbox

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Werte (0,1) (nicht angeklickt,angeklickt)  | 
Defaultstatus |
Nicht in Datenbank speichern | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="checkbox_sql"></a>
## checkbox_sql

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Query mit "select id, name from .."  | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="date"></a>
## date

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
[Startjahr] |
[Endjahr] oder [+5] |
[Anzeigeformat###Y###-###M###-###D###]] |
Aktuelles Datum voreingestellt |
Nicht in Datenbank speichern |
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="datestamp"></a>
## datestamp

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
[Startjahr] |
[Endjahr] oder [+5] |
[Anzeigeformat###Y###-###M###-###D###]] |
Aktuelles Datum voreingestellt |
Nicht in Datenbank speichern |
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="datetime"></a>
## datetime

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
[Startjahr] |
[Endjahr] oder [+5] |
[Minutenformate] | 
[Anzeigeformat###Y###-###M###-###D###]] |
Aktuelles Datum voreingestellt |
Nicht in Datenbank speichern |
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="email"></a>
## email

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Defaultwert | 
Nicht in Datenbank speichern  | 
cssclassname | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="emptyname"></a>
## emptyname

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="fieldset"></a>
## fieldset

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="float"></a>
## float

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Nachkommastellen | 
Defaultwert | 
Nicht in Datenbank speichern | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="hashvalue"></a>
## hashvalue

Option | Erläuterung
------ | ------
Priorität | 
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
Priorität | 
Name | 
HTML | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="index"></a>
## index

Option | Erläuterung
------ | ------
Priorität | 
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
Priorität | 
Name | 
Bezeichnung | 
Defaultwert | 
Nicht in Datenbank speichern  | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="mediafile"></a>
## mediafile

Option | Erläuterung
------ | ------
Priorität | 
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
Priorität | 
Name | 
PHP Code | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="prio"></a>
## prio

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Tabellenfelder zur Anzeige | 
Tabellenfelder zur Beschränkung | 
Defaultwert | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="radio"></a>
## radio

Option | Erläuterung
------ | ------
Priorität | 
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
Priorität | 
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
Priorität | 
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

<a name="submits"></a>
## submits

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
##### | 
##### | 
##### | 
##### |
##### | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="text"></a>
## text

Input-Feld zur Eingabe eines Textes.

Option | Erläuterung
------ | ------ 
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, bspw. "name", "prename", "title"
Bezeichnung |  Name des Felds, wie er im Frontend oder Backend angezeigt wird, bspw. "Name", "Vorname", "Titel"
Defaultwert | Wert, der beim Aufruf des Formulars eingetragen ist, bspw. "Musterfirma", "Paul", "Musterprojekt"
Nicht in der Datenbank speichern | ###todo### Wan benötigt man das?
cssclassname | Zusätzliche CSS-Klasse(n), die dem Feld zugeordnet werden, bspw., um das Feld im Frontend oder Backend gesondert zu formatieren.
In der Liste verstecken | Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen | Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: String, bspw. "Musterfirma", "Paul", "Musterprojekt"

<a name="textarea"></a>
## textarea

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
Defaultwert | 
Nicht in Datenbank speichern | 
classes | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="time"></a>
## time

Option | Erläuterung
------ | ------
Priorität | 
Name | 
Bezeichnung | 
[Stundenraster] | 
[Minutenraster] | 
[Anzeigeformat ###H###h ###I###m] | 
Nicht in Datenbank speichern |
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="upload"></a>
## upload

Option | Erläuterung
------ | ------
Priorität | 
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
Priorität | 
Name | 
Bezeichnung | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.
