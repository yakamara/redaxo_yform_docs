# be_manager_relation

-   [One to Many (1:n)](#one-to-many)
    - [Schritt 1 - Tabellen anlegen](#one-to-many-step-1)
    - [Schritt 2 - Frontend-Ausgabe](#one-to-many-step-2)
-   [Many to Many (m:n)](#many-to-many)
    - [Schritt 1 - Tabellen anlegen](#many-to-many-step-1)
    - [Schritt 2 - Hilfstabelle verknüpfen](#many-to-many-step-2)
    - [Schritt 3 - Frontend-Ausgabe](#many-to-many-step-3)

> **Hinweis:**  
> Dieser Abschnitt der Doku ist noch nicht fertig. Du kannst dich auf [GitHub](https://github.com/yakamara/redaxo_yform_docs/) an der Fertigstellung beteiligen.

In diesem Tutorial wird die Anwendung des be_relation Feld-Typs erklärt.

Als Beispiel für das Tutorial dient dazu eine Tabelle mit News-Einträgen und einer Tag-Tabelle, für beide Tabellen werden per yForm Table-Manager die gewünschten Felder erstellt. 

Das Ziel des ersten Teils des Tutorials ist, den News-Beiträgen jeweils ein Tag zuweisen zukönnen (One to Many, 1:n). 

Im zweiten Teil soll man einem News-Beitrag mehrere Tags zuweisen können (Many to Many, m:n). Dies lässt sich zwar auch mit One to Many bewerkstelligen, birgt aber diverse Nachteile. 

> Ergänzen mit Vor- und Nachteilen

Eine Many to Many Relation hingegen ist in der Wartung flexibler und zukunftssicherer. Obwohl im folgendem Beispiel nur abgehandelt wird, wie einem Beitrag mehrere Tags zugewiesen werden können, gäbe es auch die Möglichkeit, den Tags ebenfalls mehrere Beiträge zuzuweisen (also quasi der Umgekehrte Weg). Das Prinzip ist aber dasselbe und wer Lust hat, kann das selber als eine Art Hausaufgabe angehen. 

<a name="one-to-many"></a>
## One to Many (1:n) ##

<a name="one-to-many-step-1"></a>
### Schritt 1 - Tabellen erstellen ###

Als erstes werden per Table-Manager folgende Tabellen erstellt: 

> **Wichtig** 
> Diese Tabellen dienen ausschliesslich der Veranschaulichung des Vorgangs (eine echte News-Tabelle würde voraussichtlich weitere Felder bzw. Spalten beinhalten).

> Es wird ausschliesslich das Feld mit dem Typ be_relation genauer erklärt. Die Konfiguration anderer Feld-Typen wird hier genauer erläutert: [Table Manager: Feldtypen](table_manager_feldtypen.md)

#### Tabelle News-Tags `news_tag` ####

Feld-Name | Feld-Typ
------ | ------
`name` | `text`

#### Tabelle News-Beiträge `news_beitrag` ####

Feld-Name | Feld-Typ
------ | ------
`titel` | `text`
`text` | `textarea`
`id_tag` | `be_relation`

Das Feld id_tag wird wie folgt konfiguriert (nicht erwähnte Optionen bleiben unverändert):

Option | Erläuterung
------ | ------
Priorität | Kann beliebig gesetzt werden. Der Default-Wert ist in diesem Fall passend.
Name | `id_tag`
Bezeichnung | `Tag`
Ziel Tabelle | `[rex_news_tag]` bzw. die Tabelle, die man mit der aktuellen verknüpfen möchte
Ziel Tabellenfeld(er) zur Anzeige oder Zielfeld | `name` bzw. den Inhalt den man bei erfassen sehen möchte. Da man beim Erfassen eines News-Eintrags die Namen der vorhandenen Tags sehen und auswählen können möchte, gibt man hier den Namen des entsprechendes Feldes aus der Tag-Tabelle an. 
Mehrfachauswahl | `select (single)` optional auch `popup (single)` möglich
Als Suchfeld aufnehmen | deaktivieren

<a name="one-to-many-step-2"></a>
### Schritt 2 - Frontend-Ausgabe ###

Wenn man nun einen News-Beitrag erfasst oder editiert, findet man zuunterst das Feld "Tag", ein  SELECT-Feld welches die zuvor erfassten Tags beinhaltet. Speichert man den Datensatz ab, wird in das Feld `id_tag` (in der Tabelle `news_beitrag`) die gewählte Tag-ID geschrieben und kann so im Frontend schliesslich ausgelesen werden. 

Zum Beispiel so:

```
<?php
$sql = rex_sql::factory()
$query = 'SELECT * FROM ' . rex::getTable('news_beitrag') . ' JOIN ' . rex::getTable('news_tag') . ' ON ' . rex::getTable('news_beitrag') . '.id_tag = ' . rex::getTable('news_tag') . '.id ';
$sql->setQuery($query);
foreach($sql->getArray as $row) {
	echo '<h1>' . $row['titel'] . '</h1>';
	echo '<p>' . $row['text'] . '</p>';
	echo '<p>Tag: ' . $row['name'] . '</p>';
}
?>
```
<a name="many-to-many"></a>
## Many to Many (m:n) ##

<a name="many-to-many-step-1"></a>
### Schritt 1 - Tabellen erstellen ###

Als erstes werden per Table-Manager folgende Tabellen erstellt. 

> **Wichtig** 
> Diese Tabellen dienen ausschliesslich der Veranschaulichung des Vorgangs (eine echte News-Tabelle würde voraussichtlich noch weitere Felder bzw. Spalten beinhalten).
> Es wird ausschliesslich das Feld mit dem Typ be_relation genauer erklärt. Die Konfiguration anderer Feld-Typen wird hier genauer erläutert: [Table Manager: Feldtypen](table_manager_feldtypen.md)

#### Tabelle News-Tags `news_tag` ####

Feld-Name | Feld-Typ
------ | ------
`name` | `text`

#### Tabelle News-Beiträge `news_beitrag` ####

Feld-Name | Feld-Typ
------ | ------
`titel` | `text`
`text` | `textarea`

#### Tabelle News-Tags-zu-Beitrag `news_tag_beitrag` ####

Feld-Name | Feld-Typ
------ | ------
`id_tag` | `be_relation`
`id_beitrag` | `be_relation`

Das Feld `id_tag` wird wie folgt konfiguriert (nicht erwähnte Optionen bleiben unverändert):

Option | Erläuterung
------ | ------
Priorität | Kann beliebig gesetzt werden. Der Default-Wert ist in diesem Fall passend.
Name | `id_tag`
Bezeichnung | `Tag ID`
Ziel Tabelle | `[rex_news_tag]`
Ziel Tabellenfeld(er) zur Anzeige oder Zielfeld | `id`
Mehrfachauswahl | `select (single)`
Als Suchfeld aufnehmen | deaktivieren

Das Feld `id_beitrag` wird wie folgt konfiguriert (nicht erwähnte Optionen bleiben unverändert):

Option | Erläuterung
------ | ------
Priorität | Kann beliebig gesetzt werden. Der Default-Wert ist in diesem Fall passend.
Name | `id_beitrag`
Bezeichnung | `Beitrag ID`
Ziel Tabelle | `[news_beitrag]`
Ziel Tabellenfeld(er) zur Anzeige oder Zielfeld | `id`
Mehrfachauswahl | `select (single)`
Als Suchfeld aufnehmen | deaktivieren

<a name="many-to-many-step-2"></a>
### Schritt 2 - Hilfstabelle verknüpfen ###

Um die Verknüpfung abzuschliessen, geht's zurück zur Tabelle News-Beiträge `news_beitrag` wo am Ende der Tabelle ein weiteres be_relation Feld angelegt wird und zwar mit folgenden Einstellungen (nicht erwähnte Optionen bleiben unverändert):

Option | Erläuterung
------ | ------
Priorität | Kann beliebig gesetzt werden. Der Default-Wert ist in diesem Fall passend.
Name | `tags`
Bezeichnung | `Tags`
Ziel Tabelle | `[rex_news_tag]`
Ziel Tabellenfeld(er) zur Anzeige oder Zielfeld | `name`
Mehrfachauswahl | `select (multiple)` oder `popup (multilple)`
Relationstabelle | `news_tag_beitrag`
Als Suchfeld aufnehmen | deaktivieren

<a name="many-to-many-step-3"></a>
### Schritt 3 - Frontend-Ausgabe ###

Wenn man nun einen News-Beitrag erfasst oder editiert, findet man ganz am Ende der Eingabemaske ein Feld mit Namen "Tags", entweder mit einem Multi-SELECT-Feld oder einem Rex-Widget mit Popup. Speichert man den Datensatz ab, wird in der News-Beitrag-Tabelle `news_tag_beitrag` die Zuordnung vom jeweiligen Beitrag zu den entsprechenden Tags gespeichert. 

Im Frontend kann das ganze dann beispielsweise so abgefragt werden:

```
<?php
$sql = rex_sql::factory()
$query = 'SELECT ' . rex::getTable('news_beitrag') . '.*, GROUP_CONCAT(news_tag.name SEPARATOR ',') AS tags ';
$query.= 'FROM ' . rex::getTable('news_beitrag') . ' ';
$query.= 'JOIN ' . rex::getTable('news_tag_beitrag') . ' ON ' . rex::getTable('news_beitrag') . '.id = ' . rex::getTable('news_tag_beitrag') . '.id_beitrag ';
$query.= 'JOIN ' . rex::getTable('news_tag') . ' ON ' . rex::getTable('news_tag') . '.id = ' . rex::getTable('news_tag_beitrag') . '.id_tag ';
$query.= 'GROUP BY news_beitrag.id';
$sql->setQuery($query);
foreach($sql->getArray as $row) {
	echo '<h1>' . $row['titel'] . '</h1>';
	echo '<p>' . $row['text'] . '</p>';
	echo '<p>Tags: ' . $row['tags'] . '</p>';
}
?>
```
> die Query ist hier im Dienste der Lesbarkeit auf mehrere Zeilen aufgeteilt. Dass muss natürlich nicht zwingend so sein

[GitHub-Diskussion zum Thema Filter](https://github.com/yakamara/redaxo_yform_docs/issues/3)
