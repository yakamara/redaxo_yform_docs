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

Als Beispiel nehmen wir dazu eine Tabelle mit News-Einträgen und einer Tag-Tabelle, für beide Tabellen erstellen wir dazu in gewohnter Manier per yForm Table-Manager die gewünschten Felder. Zusätzlich erstellen wir die Verknüpfungen zwischen den Tabellen.

Im ersten Teil des Tutorials möchten wir den News-Beiträgen jeweils ein Tag zuweisen können (One to Many, 1:n). 

Im zweiten Teil möchten wir einem News-Beitrag mehrere Tags zuweisen können (Many to Many, m:n). Dies lässt sich zwar auch mit einem One to Many bewerkstelligen, birgt aber mehrere Nachteile. 

> Ergänzen mit Vor- und Nachteilen

Eine Many to Many Konfiguration ist vor allem in der Wartung flexibler und zukunftssicherer, ist aber auch beim Abfragen der Einträge flexibler und einfacher. Obwohl wir in diesem Beispiel nur einem Beitrag mehrere Tags zuweisen, könnten wir zusätzlich auch den Tags selbst mehrere Beiträge zuweisen (also als Zusatz den umgekehrten Weg bieten). Das Prinzip ist dasselbe und wer Interesse daran hat, kann das ja quasi als Hausaufgabe angehen. 

<a name="one-to-many"></a>
## One to Many (1:n) ##

<a name="one-to-many-step-1"></a>
### Schritt 1 - Tabellen erstellen ###

Als erstes erstellen wir mit dem Table-Manager folgende Tabellen: 

> **Wichtig** 
> Fiese Tabellen dienen nur der Veranschaulichung des Vorgangs. (Eine echte News-Tabelle würde voraussichtlich noch weitere Felder bzw. Spalten beinhalten)
> Es wird hier nur auf das/die Feld/er mit dem Typ be_relation eingegangen. Die Einstellungsmöglichkeiten für die anderen Feld-Typen werden hier genauer erläutert: [Table Manager: Feldtypen](table_manager_feldtypen.md)

#### Tabelle News-Tags news_tag ####

Feld-Name | Feld-Typ
------ | ------
`name` | `text`

#### Tabelle News-Beiträge news_beitrag ####

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
Ziel Tabellenfeld(er) zur Anzeige oder Zielfeld | `name` bzw. den Inhalt den man bei erfassen sehen möchte. Da wir beim Erfassen eines News-Eintrags die Namen der vorhandenen Tags sehen und auswählen können möchten, geben wir hier den Namen des entsprechendes Feldes aus der Tag-Tabelle an. 
Mehrfachauswahl | `select (single)` optional auch `popup (single)` möglich
Als Suchfeld aufnehmen | deaktivieren

<a name="one-to-many-step-2"></a>
### Schritt 2 - Frontend-Ausgabe ###

Wenn man nun einen News-Beitrag erfasst oder editiert, findet man zuunterst das Feld "Tag" mit einem SELECT-Feld wo die zuvor erfassten Tags drinstehen. Speichert man den Datensatz ab, wird in der News-Tabelle in das Feld id_tag fest die zugeordnete Tag-ID gespeichert und kann im Frontend ausgelesen werden. 

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

Als erstes erstellen wir mit dem Table-Manager folgende Tabellen. 

> **Wichtig** 
> Fiese Tabellen dienen nur der Veranschaulichung des Vorgangs. (Eine echte News-Tabelle würde voraussichtlich noch weitere Felder bzw. Spalten beinhalten)
> Es wird hier nur auf das/die Feld/er mit dem Typ be_relation eingegangen. Die Einstellungsmöglichkeiten für die anderen Feld-Typen werden hier genauer erläutert: [Table Manager: Feldtypen](table_manager_feldtypen.md)

#### Tabelle News-Tags news_tag ####

Feld-Name | Feld-Typ
------ | ------
`name` | `text`

#### Tabelle News-Beiträge news_beitrag ####

Feld-Name | Feld-Typ
------ | ------
`titel` | `text`
`text` | `textarea`

#### Tabelle News-Tags-zu-Beitrag news_tag_beitrag ####

Feld-Name | Feld-Typ
------ | ------
`id_tag` | `be_relation`
`id_beitrag` | `be_relation`

Das Feld id_tag wird wie folgt konfiguriert (nicht erwähnte Optionen bleiben unverändert):

Option | Erläuterung
------ | ------
Priorität | Kann beliebig gesetzt werden. Der Default-Wert ist in diesem Fall passend.
Name | `id_tag`
Bezeichnung | `Tag ID`
Ziel Tabelle | `[rex_news_tag]`
Ziel Tabellenfeld(er) zur Anzeige oder Zielfeld | `id`
Mehrfachauswahl | `select (single)`
Als Suchfeld aufnehmen | deaktivieren

Das Feld id_beitrag wird wie folgt konfiguriert (nicht erwähnte Optionen bleiben unverändert):

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

Um die Verknüpfung fertigzustellen, wechseln wir jetzt zurück in zur Tabelle News-Beiträge (news_beitrag) und legen dort am Ende der Tabelle ein weiteres be_relation Feld an mit folgenden Einstellungen (nicht erwähnte Optionen bleiben unverändert):

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

Wenn man nun einen News-Beitrag erfasst oder editiert, findet man zuunterst das Feld "Tags", entweder mit einem Multi-SELECT-Feld oder einem Rex-Widget mit Popup, wo die zuvor erfassten Tags drinstehen und davon mehrere ausgewählt werden können. Speichert man den Datensatz ab, wird in der News-Beitrag-Tabelle (news_tag_beitrag) die Zuordnung von eine Beitrag zu den entsprechenden Tags gespeichert. Der Table-Manager ist dabei klug genug, diese Tabelle entsprechend zu verwalten wenn ein Tag oder ein Beitrag gelöscht wird.

Im Frontend kann das ganze zum Beispiel so ausgelesen werden:

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
> die Query ist hier im Dienste der Lesbarkeit auf mehrere Zeilen aufgeteilt. Dass muss natürlich nicht sein ;) 

[GitHub-Diskussion zum Thema Filter](https://github.com/yakamara/redaxo_yform_docs/issues/3)
