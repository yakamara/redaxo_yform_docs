# Table Manager: Feldtypen

> ##Inhalt
> - [be_link](#be_link)
> - [be_manager_relation](#be_manager_relation)
> - [be_media](#be_media)
> - [be_medialist](#be_medialist)
> - [be_select_category](#be_select_category)
> - [be_table](#be_table)
> - [checkbox](#checkbox)
> - [checkbox_sql](#checkbox_sql)
> - [date](#date)
> - [datestamp](#datestamp)
> - [datetime](#datetime)
> - [email](#email)
> - [emptyname](#emptyname)
> - [fieldset](#fieldset)
> - [float](#float)
> - [hashvalue](#hashvalue)
> - [html](#html)
> - [index](#index)
> - [integer](#integer)
> - [mediafile](#mediafile)
> - [php](#php)
> - [prio](#prio)
> - [radio](#radio)
> - [select](#select)
> - [select_sql](#select_sql)
> - [submits](#submits)
> - [text](#text)
> - [textarea](#textarea)
> - [time](#time)
> - [upload](#upload)
> - [ycom_auth_password](#ycom_auth_password)

<a name="be_link"></a>
## be_link

Ein Redaxo-Feld, um einen <b>Redaxo-Artikel</b> auszuwählen.

> **Wert in der Datenbank:**  
> id des Redaxo-Artikels, z.B. `1`, `5`, `20`

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `article_id`, `page_id`, `link_id`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Redaxo-Artikel`, `Seite`, `Link`
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben. 
In der Liste verstecken | Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen | Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.


<a name="be_manager_relation"></a>
## be_manager_relation

Ein Auswahlfeld / Popup, um ein oder mehrere <b>Datensätze</b> mit denen einer fremden Tabelle zu <b>verknüpfen</b>, z.B. über einen Fremdschlüssel (1:n) oder eine Relationstabelle (m:n).

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein. 
Name | Name des Felds in der Datenbank, z.B. `article_id`, `person_id`, `link_id`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. die Bezeichnung der Ziel-Tabelle
Ziel-Tabelle | Name der Tabelle, deren Datensätze referenziert werden.
Ziel Tabellenfeld(er) zur Anzeige oder Zielfeld | Feldname der Tabelle, dessen Werte als Select-Box oder im Popup angezeigt werden, z.B. `name`, `prename, ' ', name` oder `name, '(', id, ')'` [Erläuterungen auf GitHub](https://github.com/yakamara/redaxo_yform_docs/issues/12)
Mehrfachauswahl | Gibt an, ob ein (1:n) oder mehrere (m:n) Datensätze ausgewählt werden können, entweder in einem select-Feld oder als Popup-Fenster 
Mit "Leer-Option" | Gibt an, ob "keine Auswahl" erlaubt ist.
Fehlermeldung, wenn "Leer-Option" nicht aktiviert ist | Fehlermeldung, die dem Nutzer mitteilt, dass eine Auswahl getroffen werden muss. 
Höhe der Auswahlbox | Höhe der Auswahlbox, wenn `Mehrfachauswahl` als select-Feld aktiviert wurde. 
Filter | Zusätzliche Angaben in einer speziellen Syntax, die in [be_relation-Tutorial](table_manager_feldtypen_be-relation.md) erläutert werden.
Relationstabelle | [optional] Name der Tabelle, in der die m:n-Beziehungen abgelegt sind, z.B. `rex_project_news_tags`
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben. 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Wert in der Datenbank:**
> ID des verknüpften Datensatzes, z.B. `1`, `5`, `20` oder
> IDs der verknüpften Datensätze als `SET`, z.B. `1,5,20`, `4,8,12`, `7,10,42` oder
> leer, wenn eine Relationstabelle angegeben wurde.

> **Hinweise:**
> **Tipp für Anfänger:** Um die verknüpften Datensätze im Frontend auszugeben, wird eine SELECT-Abfrage mit einem `JOIN` benötigt.
> **Tipp:** Details zu den umfangreichen Einstellungsmöglichkeiten gibt's im [be_relation-Tutorial](table_manager_feldtypen_be-relation.md).

<a name="be_media"></a>
## be_media

Ein Redaxo-Feld, um eine einzelne <b>Medienpool-Datei</b> auszuwählen.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `image`, `attachment`, `file`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Bild`, `Anhang`, `Datei`
Defaultwert | Datei aus dem Medienpool, mit der das Eingabefeld vorausgefüllt wird, z.B. `mueller.jpg`, `preisliste.pdf` 
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Wert in der Datenbank:**  
Dateiname der Medienpool-Datei, z.B. `mueller.jpg`, `preisliste.pdf`


<a name="be_medialist"></a>
## be_medialist

Ein Redaxo-Feld, um ein oder mehrere <b>Medienpool-Dateien</b> auszuwählen.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `images`, `attachments`, `files`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Bilder`, `Anhänge`, `Dateien`
Preview (0/1) (opt) | Zeigt eine Bildvorschau an, wenn die Datei in der `be_medialist` markiert wird.
Medienpool Kategorie (opt) | ID der Medienpool-Kategorie, die bei der Auswahl der Dateien voreingestellt ist.
Types (opt) | Filtert die Dateiauswahl im Medienpool anhand der Dateiendung, z.B. `.jpg,.jpeg,.png,.gif` oder `.pdf,.docx,.doc`
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben. 
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Wert in der Datenbank:**  
> Dateinamen der Medienpool-Dateien als SET, z.B. `mueller.jpg,mayer.jpg`, `preisliste.pdf,agb.pdf`

<a name="be_select_category"></a>
## be_select_category

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `category_id`, oder `category_ids`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Kategorie`, `Kategorien`, `Navigationspunkt`
Ignoriere Offline-Kategorien  | Gibt an, ob Offline-Kategorien aus dem Auswahl-Dialogfeld ausgeschlossen werden. 
Prüfe Rechte  | ###todo###
Füge "Homepage"-Eintrag (Root) hinzu  | Gibt an, ob im Auswahl-Dialogfeld die oberste Ebene auswählbar ist.
Root-ID | Startpunkt der Auswahl-Dialogfelds, z.B. die ID einer Unterkategorie.
Sprache | ###todo###
Mehrere Felder möglich | Gibt an, ob ein oder mehrere Kategorien ausgewählt werden können.
Höhe der Auswahlbox | Höhe der Auswahlbox, wenn `Mehrere Felder möglich` aktiviert wurde. 
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="be_table"></a>
## be_table

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `table`, `features`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Info-Tabelle`, `Eigenschaften`
Anzahl Spalten |  Anzahl der Spalten, die bei der Eingabe zur Verfügung stehen.
Bezeichnung der Spalten (Menge,Preis,Irgendwas)  | Kopfzeile der Tabelle, z.B., `Leistung,Aufpreis`, `Vorname,Name`, `Artikelnummer,Größe,Preis` 
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Wert in der Datenbank:**  
> String / CSV. Felder werden mit Komma abgetrennt, Zeilen mit Semikolon.

> **Hinweis:**  
> Um die Werte wieder aufzutrennen, kann z.B. `explode(";" $rows)` und `$explode("," $row)` verwendet werden.

<a name="checkbox"></a>
## checkbox

Eine <b>Checkbox</b> mit vordefinierten Werten.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `active`, `online`, `visible`, `hidden`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `aktiviert`, `online`, `sichtbar?`, `ausgeblendet?`
Werte (0,1) (nicht angeklickt,angeklickt)  | Wert, der in die Datenbank geschrieben wird, z.B. `0,1`, `nein,ja`
Defaultstatus | Gibt an, ob die Checkbox vorausgewählt ist oder nicht.
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Wert in der Datenbank:**  
Status der Checkbox als Zahl oder String (je nach angegebenen Wert), z.B. `0` oder `1`, `nein` oder `ja`

<a name="checkbox_sql"></a>
## checkbox_sql

Eine **Checkbox** mit Werten, die aus einer **SQL-Abfrage** stammen.  
todo: handelt es sich nicht dabei um eine Liste an Checkboxes?

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein. 
Name | Name des Felds in der Datenbank, z.B. `active_languages`, `tags`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Sichtbar in Sprachen`, `Schlagwörter`
Query mit "select id, name from .."  | SQL-Abfrage, um die Checkbox-Werte abzurufen, z.B. `SELECT id, name FROM rex_clang ORDER BY name`, `SELECT id, tag AS name FROM rex_project_tags ORDER BY id`
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Wert in der Datenbank:** 
> todo

> **Tipp:**  
> Mit checkbox_sql kann man z.B. in einer News-Tabelle einer News die Sprachen zuordnen, in der sie angezeigt werden sollen. 

<a name="date"></a>
## date

Eine Reihe von Auswahlfeldern, in der ein <b>Datum</b> (Tag, Monat, Jahr) ausgewählt wird.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `date`, `date_begin`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Datum`, `Beginn der Veranstaltung`
[Startjahr] | Gibt an, mit welchem Jahr das Auswahlfeld beginnt, z.B. `1980`, `2014`
[Endjahr] oder [+5] | Gibt an, mit welchem Jahr das Auswahlfeld endet, z.B. `2020` oder `+3`, um immer 3 Jahre über der aktuellen Jahreszahl anzugeben.
[Anzeigeformat###Y###-###M###-###D###]] | Reihenfolge der Auswahlfelder für Tag, Monat und Jahr beim bearbeiteten eines Datensatzes, z.B. `am ###D###.###M###.###Y###`
Aktuelles Datum voreingestellt | Gibt an, ob das aktuelle Datum vorausgewählt ist.
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> Wert in der Datenbank:**  
Das Datum im todo-Format ...

<a name="datestamp"></a>
## datestamp

Ein unsichtbares Feld, in das ein **Zeitstempel** gespeichert wird, wenn der Datensatz hinzugefügt oder bearbeitet wird.

**todo**: Optionen überprüfen, hier müsste doch was anderes stehen?

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `datestamp`, `date_created`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Zeitstempel`, `Beginn der Veranstaltung`
[Anzeigeformat###Y###-###M###-###D###]] | Reihenfolge der Auswahlfelder für Tag, Monat und Jahr beim bearbeiteten eines Datensatzes, z.B. `am ###D###.###M###.###Y###`
Aktuelles Datum voreingestellt | Gibt an, ob das aktuelle Datum vorausgewählt ist. 
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="datetime"></a>
## datetime

Eine Reihe von Auswahlfeldern, in der **Datum und Uhrzeit** (Tag, Monat, Jahr, Stunden, Minuten, Sekunden) ausgewählt wird.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `date`, `date_begin`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Datum`, `Beginn der Veranstaltung`
[Startjahr] | Gibt an, mit welchem Jahr das Auswahlfeld beginnt, z.B. `1980`, `2014`
[Endjahr] oder [+5] | Gibt an, mit welchem Jahr das Auswahlfeld endet, z.B. `2020` oder `+3`, um immer 3 Jahre über der aktuellen Jahreszahl anzugeben.
[Anzeigeformat###Y###-###M###-###D###]] | ###todo### Reihenfolge der Auswahlfelder für Tag, Monat und Jahr beim bearbeiteten eines Datensatzes, z.B. `am ###D###.###M###.###Y###`
Aktuelles Datum voreingestellt | Gibt an, ob das aktuelle Datum vorausgewählt ist.
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="email"></a>
## email

Ein einfaches Eingabefeld für **E-Mail-Adressen.**

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `email`, `contact`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `E-Mail`, `Kontakt-Mail-Adresse`
Defaultwert | E-Mail-Adresse, mit der das Eingabfeld vorausgefüllt wird, z.B. `max@mustermann.de`, `jane@smith.com` 
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
cssclassname | CSS-Klasse(n), die dem Input-Element zugewiesen werden.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Wert in der Datenbank:**  
> String.

<a name="emptyname"></a>
## emptyname

Ein Feld **ohne** Eingabemöglichkeit.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank
Bezeichnung | 
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="fieldset"></a>
## fieldset

Ein Fieldset gruppiert Formularfelder.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `fieldset_product`, `fieldset_details`,
Bezeichnung | Titel des Fieldsets, das im `<legend />`-Tag notiert wird. z.B. `Produktinfos`, `Details`
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Wert in der Datenbank:** 
> leer

> **Hinweis:**  
> Das Feld wird nur aus technischen Gründen angelegt. Das Feld wird nicht mit einem Wert gefüllt.

<a name="float"></a>
## float

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `price`, `fee`.
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Preis in EUR`, `Gebühr`
Nachkommastellen | Anzahl der erlaubten Stellen nach dem Komma, z.B. `1`, `5`, `42`
Defaultwert | Zahl, mit der das Eingabfeld vorausgefüllt wird, z.B. `0,1234`, `5` 
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Tipp:**  
> Dieses Feld eignet sich besser für Zahlen als das Feld `text`, weil Dezimalzahlen mit `,` als Trennzeichen automatisch in `float`-Zahlen mit `.` als Trennzeichen umgewandelt werden.

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
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="html"></a>
## html

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein. 
Name | Name des Felds in der Datenbank, z.B. `info`, `code`.
HTML | HTML-Code, der vor, zwischen oder nach anderen Feldern im Frontend oder Backend eingefügt wird.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="index"></a>
## index

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Felder | 
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Opt. Codierfunktion | 
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="integer"></a>
## integer

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `price`, `quantity`.
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Preis in EUR`, `Anzahl`
Defaultwert | Zahl, mit der das Eingabfeld vorausgefüllt wird, z.B. `1`, `5`, `42` 
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
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
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Mediakategorie ID | 
Mediapool User (createuser/updateuser) | 
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="php"></a>
## php

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `php`, `code`.
HTML | PHP-Code, der vor, zwischen oder nach anderen Feldern im Frontend oder Backend eingefügt wird.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="prio"></a>
## prio

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `prio`, `ranking`, `order`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Priorität`, `Rang`, `Reihenfolge`
Anzeige | Feld(er), die in der Auswahl-Box angezeigt werden, z.B. `name`, `title`, `isbn`
Beschränkung | Feld(er), die die Auswahlmöglichkeiten in der Auswahl-Box beschränken, z.B. `category_id` 
Am Anfang | Vorauswahl, ob ein neuer Datensatz am Anfang oder am Ende angelegt wird. 
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Hinweis:**  
> Wenn eine Beschränkung ausgewählt wurde, kann es vorkommen, dass ein Datensatz zunächst gespeichert werden muss, damit die Beschränkung greifen kann. Dadurch lässt sich z.B. eine Reihenfolge pro Kategorie festlegen.

<a name="radio"></a>
## radio

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnung | 
Selectdefinition, kommasepariert | 
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Defaultwert | 
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
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
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Defaultwert | 
Mehrere Felder möglich |
Höhe der Auswahlbox | 
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
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
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Leeroption  |
Text bei Leeroption (Bitte auswählen) |
Mehrere Felder möglich | 
Höhe der Auswahlbox |  
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Tipp:**  
> Ein select_sql-Feld kann ähnlich wie be_relation dazu benutzt werden, um Datensätze fremder Tabellen in einer 1:1- oder 1:n-Beziehung zu verknüpfen.

<a name="submits"></a>
## submits

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnungen (kommasepariert) | 
Werte (optional, kommasepariert) | 
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Defaultwert | 
CSS Klassen (kommasepariert) |
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Tipp:**  
> Mit mehreren Submits kann man auf unterschiedliche Absichten mit dem gleichen Formular reagieren, z. B. zwei Buttons namens `Bestellen` und `Angebot anfragen`.

<a name="text"></a>
## text

Input-Feld zur Eingabe eines Textes.

Option | Erläuterung
------ | ------ 
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `name`, `prename`, `title`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Name`, `Vorname`, `Titel`
Defaultwert | Wert, der beim Aufruf des Formulars eingetragen ist, z.B. `Musterfirma`, `Paul`, `Musterprojekt`
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
cssclassname | Zusätzliche CSS-Klasse(n), die dem Feld zugeordnet werden, z.B., um das Feld im Frontend oder Backend gesondert zu formatieren.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken | Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen | Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

> **Wert in der Datenbank:**  
> String, z.B. `Musterfirma`, `Paul`, `Musterprojekt`

<a name="textarea"></a>
## textarea

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. "text", "description", "message"
Bezeichnung |  Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. "Text", "Beschreibung", "Nachricht"
Defaultwert | Wert, der beim Aufruf des Formulars eingetragen ist, z.B. `Geben Sie hier Ihre Nachricht ein`
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
classes | Zusätzliche CSS-Klasse(n), die dem Feld zugeordnet werden, z.B., um das Feld im Frontend oder Backend gesondert zu formatieren.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="time"></a>
## time

Eine Reihe von Auswahlfeldern, in der die <b>Uhrzeit</b> (Stunden, Minuten, Sekunden) ausgewählt wird.

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | Name des Felds in der Datenbank, z.B. `time`, `time_begin`
Bezeichnung | Name des Felds, wie er im Frontend oder Backend angezeigt wird, z.B. `Uhrzeit`, `Beginn der Veranstaltung`
[Stundenraster] | optional: Kommagetrennte Liste an Stunden, die für den Nutzer zur Auswahl stehen sollen, z.B. `0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23`
[Minutenraster] | optional: Kommagetrennte Liste an Minuten, die für den Nutzer zur Auswahl stehen sollen, z.B. `0,15,30,45`, `0,10,20,30,40,50`
[Anzeigeformat ###H###h ###I###m] |  Reihenfolge der Auswahlfelder für Stunde und Minute beim bearbeiteten eines Datensatzes, z.B. `um ###H###:###I### Uhr`
Nicht in Datenbank speichern | Gibt an, ob das Feld nur angezeigt werden soll oder der Wert auch in der Datenbank gespeichert werden soll.
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
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
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.

<a name="ycom_auth_password"></a>
## ycom_auth_password

Option | Erläuterung
------ | ------
Priorität | Ordnet das Feld zwischen anderen Feldern in der Tabelle ein.
Name | 
Bezeichnung | 
Notiz | Hinweis unterhalb des Feldes, um dem Nutzer zusätzliche Instruktionen zur Eingabe mitzugeben.
In der Liste verstecken |  Versteckt das Feld in der Tabellen-Übersicht.
Als Suchfeld aufnehmen |  Zeigt das Feld in den Suchoptionen an, sofern die Option "Suche aktiv" in den Tabellen-Optionen aktiviert wurde.
