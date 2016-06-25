# Table Manager: Feldtypen

* Alle Feldtypen auflisten
* Informationen zu den einzelnen Parametern
* Beispiele bei den einzelnen Parametern (Klassen, Vorauswahl, etc.)
* Keine zu ausführlichen Beispiele zu be_relation, dafür eine Extra-Seite

<a name="be_link"></a>
## be_link

Feld zur Auswahl eines Redaxo-Artikels.

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

Feld zur Zuordnung anderer Datensätze über einen Fremdschlüssel (1:n) oder eine Relationstabelle (m:n).

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
Höhe der Auswahlbox | Höhe der Auswahlbox, wenn Mehrfachauswahl als select-Feld gewählt wurde. 
Filter | ###todo###
Relationstabelle | [optional] Name der Tabelle, in der die m:n-Beziehungen abgelegt sind, bspw. `rex_project_news_tags`
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

Wert in der Datenbank: 
* id des verknüpften Datensatzes, bspw. `1`, `5`, `20` oder
* ids der verknüpften Datensätze als `SET`, bspw. `1,5,20`, `4,8,12`, `7,10,42` oder
* leer, wenn eine Relationstabelle angegeben wurde.

> Tipp für Anfänger: Um die verknüpften Datensätze im Frontend auszugeben, wird eine SELECT-Abfrage mit einem `JOIN` benötigt.

> Tipp: Da die Einstellungsmöglichkeiten sehr umfangreich sind, haben wir ein zusätzliches Tutorial mit Anwendungsbeispielen bereitgestellt. ###todo###

<a name="be_media"></a>
## be_media

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

<a name="be_select_category"></a>
## be_select_category

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein. 
Name | 
Bezeichnung | 
Query mit "select id, name from .."  | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="date"></a>
## date

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnung | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="fieldset"></a>
## fieldset

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnung | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="float"></a>
## float

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Name | 
HTML | 
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
Name | 
PHP Code | 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="prio"></a>
## prio

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
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
