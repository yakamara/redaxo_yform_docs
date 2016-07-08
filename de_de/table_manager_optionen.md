# Table Manager: Optionen
 
Um Tabellen im Table Manager zu bearbeiten, gibt es 3 verschiedene Möglichkeiten:

* Sie können eine neue [Datenbank-Tabelle erstellen](#tabelle-erstellen).
* Sie können eine vorhandene Datenbank-Tabelle in den [Table Manager migrieren](#tabelle-migrieren)
* Sie können eine neue Datenbank-Tabelle einschließlich aller benötigten Felder anhand eines [Tablesets imporiteren](#tableset-importieren).

<a name="tabelle-erstellen"></a>
## Tabelle erstellen

So fügen Sie dem Table Manager eine neue Tabelle hinzu:

* Im Menü auf YForm klicken,
* Table Manager öffnen,
* über das +-Symbol eine neue Tabelle hinzufügen.

Anschließend können der Tabelle folgende Optionen zugewiesen werden:

Option | Erläuterungen
------ | ------
Priorität | Legt fest, an welche Position sich die neue Tabelle zwischen bestehenden Tabellen einreiht, bspw. im Menü.
Name | Der Name der Datenbank-Tabelle, wie sie in MySQL heißt und über SQL-Querys aufgerufen wird.
Bezeichnung | Der Name der Tabelle, wie sie im Menü aufgelistet wird.
Beschreibung | Informationen zur Tabelle, zum Beispiel eine Kurzanleitung für den Kunden oder Informationen über den Aufbau der Tabelle als Merkhilfe. Die Beschreibung wird angezeigt, wenn Sie eine Tabelle direkt aufrufen.
aktiv | Legt fest, ob die Tabelle bearbeitet werden kann oder nicht.
Datensätze pro Seite | Legt fest, ab wievielen Datensätzen die Tabellen-Übersicht in Seiten unterteilt wird.
Standardsortierung Feld | Legt fest, nach welchem Feld die Tabellen-Übersicht zu Beginn sortiert wird.
Stadndardsortierung Richtung |  Legt fest, ob das gewählte Feld auf- oder absteigend sortiert wird.
Suche aktiv | Zeigt die Schaltfläche "Datensatz suchen" in der Tabellen-Übersicht an.
In der Navigation versteckt | Legt fest, ob die Tabelle auch im Menü angezeigt wird. oder nur im Table Manager. (Hilfreich, um bspw. relationale Datenbank-Tabellen auszublenden.)
Export der Daten erlauben | Zeigt die Schaltfläche "Datensätze exportieren" in der Tabellen-Übersicht an.
Import von Daten erlauben | [Zeigt die Schaltfläche "Datensätze importieren" in der Tabellen-Übersicht an.

> **Hinweis:**
>Solange die Tabelle über keine Felder verfügt, kann hier nur `id` ausgewählt werden. Sie können zunächst die Standard-Sortierung nach id-Feld belassen, dann neue Felder hinzufügen und anschließend die Sortierung der Tabelle neu festlegen. Zum Beispiel nach Name, Datum oder den von Ihnen festgelegten Feldern.

> **Hinweis:** 
>Wenn die Struktur der Tabelle bereits Alternativ kann auch ein vorhandenes Tableset importiert werden.
Klicken Sie abschließend auf hinzufügen, um die Datenbank-Tabelle zu erstellen.

> **Tipp:** 
>Wenn Die Datenbank über Import/Export oder über einen Backup-Crobjob gesichert werden soll, sollte die Tabelle den Präfix `rex_` behalten. Zur besseren Übersicht empfiehlt es sich, der Tabelle einen eigenen Projekt-Präfix zu geben, z.B. `rex_kunde_projekte` oder `rex_kunde_mitarbeiter`.


<a name="tabelle-migrieren"></a>
## Tabelle migrieren

Der Migrationsmanager erstellt aus einer vorhandenen Tabelle, eine, die über den Table Manager verwaltet werden kann. Dazu ist in der Tabelle ein Autoinkrement-Feld mit dem Namen `id` nötig. Ohne dieses Feld funktioniert der Tablemanager nicht.

So migrieren Sie eine vorhandene Tabelle in den Table Manager:

* Im Menü auf YForm klicken,
* Table Manager öffnen,
* den Button "Tabelle migrieren" anklicken,
* vorhandene Datenbank-Tabelle auswählen und
* mit Abschicken bestätigen.

> **Hinweis:** Falls die Datenbank-Tabelle über kein id-Feld verfügt, können Sie die Option "id-Feld konvertieren falls nicht vorhanden" benutzen.

<a name="tableset-importieren"></a>
## Tableset importieren / exportieren

Seit Redaxo 5 gibt es eine neue Möglichkeit, eine Tabelle im Table Manager zu erstellen: Den Import via Tableset.

* Im Menü auf YForm klicken,
* Table Manager öffnen,
* die Schaltfläche "Tableset importieren" anklicken,
* JSON-Datei auswählen und 
* mit Abschicken bestätigen.

Anschließend wird die Tabelle einschließlich aller in der JSON-Datei hinterlegten Felder, Parameter und Standard-Werten importiert.
