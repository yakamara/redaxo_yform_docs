# Table Manager: Validierungen

* Analog zur Seite Felder
*  ###frage### Validierungsbeispiele für Custom Function bereitstellen... welche Parameter erhält die Funktion, wie erfolgt die Rückgabe?
*  ###frage### i18n der Fehlermeldungen?

<a name="compare"></a>
## compare

Vergleicht zwei Eingabe-Werte <b>miteinander</b>. ###todo### nützliche Beispiele?

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
1. Feldname | Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `password`, `email`
2. Feldname | Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `password2`, `email_verified`
Vergleichsart | Operator, wie `Feld 1` und `Feld 2` vergleichen werden sollen, bspw. `!=`, `!=`, `>`, `<` 
Fehlermeldung | Hinweis, der erscheint, wenn der Vergleich beider Felder `false` ergibt.

<a name="compare_value"></a>
## compare_value

Vergleicht einen Eingabe-Wert mit einem <b>fest definierten Wert</b>.

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
1. Feldname | Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `checkbox_agb`, `newsletter_consent`
Vergleichswert | Fest definierter Wert, der für den Vergleich herangezogen wird, z.B. `1` (bei Checkboxen) 
Vergleichsart |  Operator, wie `Feld 1` und `Vergleichswert` vergleichen werden sollen, bspw. `!=`, `!=`, `>`, `<` 
Fehlermeldung | Hinweis, der erscheint, wenn die Überprüfung `false` ergibt.

<a name="customfunction"></a>
## customfunction

Ruft eine eigene <b>PHP-Funktion</b> für einen Vergleich auf.

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name | Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `name`, `email`, `phone`, `zip`
Name der Funktion | Funktion, die den Wert überprüfen soll, bspw. `project_is_customer` ruft `project_is_customer($value)` auf. ###todo### überprüfen
Weitere Parameter | ###todo###
Fehlermeldung | Hinweis, der erscheint, wenn die Funktion `false` als Rückgabewert liefert.

 ###todo### Wo werden solche Funktionen üblicherweise abgelegt?
 ##todo### Codebeispiele
 
<a name="email"></a>
## email

Überprüft, ob der Eingabe-Typ eine <b>E-Mail-Adresse</b> ist.

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name |  Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `email`, `contact`
Fehlermeldung | Hinweis, der erscheint, wenn keine gültige E-Mail-Adresse angegeben wurde.

 ###todo### wie findet die Prüfung statt? RFC-Standardkonform oder einfach nur nach @-Zeichen?

> Hinweis: Falls das E-Mail-Feld ein Pflichtfeld ist, muss auch die Validierung `empty` hinzugefügt werden, da ein leeres Feld eine keine ungültige E-Mail-Adresse darstellt.

<a name="empty"></a>
## empty

Überprüft, ob ein Eingabe-Wert <b>vorhanden</b> ist.

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name |  Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `email`, `name`
Fehlermeldung | Hinweis, der erscheint, wenn die Eingabe leer ist.

<a name="intfromto"></a>
## intfromto

Überprüft, ob der Eingabe-Wert <b>zwischen zwei Zahlen</b> liegt.

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name |  Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `email`, `name`
Von | Wert, der mindestens eingegeben werden muss, bspw. `0`, `5`, `1000`
Bis | Wert, der höchstens eingegeben werden darf, bspw. `5`,`10`,`2030`
Fehlermeldung | Hinweis, der erscheint, wenn die Eingabe nicht im erlaubten Bereich liegt.

<a name="size"></a>
## size

Überprüft, ob der Eingabe-Wert eine <b>bestimmte Anzahl von Zeichen</b> hat.

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name |  Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, bspw. `customer_id`, `pin`
Anzahl der Zeichen | Anzahl der Zeichen, die eingegeben werden sollen, bspw. `5`,`10`,`42`
Fehlermeldung | Hinweis, der erscheint, wenn die Eingabe die festgelegte Anzahl von Zeichen unter- oder überschreitet.

<a name="size_range"></a>
## size_range

Überprüft, ob die <b>Länge</b> des Eingabe-Werts <b>zwischen zwei Zahlen</b> liegt.

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name |  Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, bspw. `customer_id`, `password`
Minimale Anzahl der Zeichen (opt) | Anzahl der Zeichen, die mindestens werden sollen, bspw. `0`, `5`, `7`
Maximale Anzahl der Zeichen (opt) | Anzahl der Zeichen, die höchstens werden sollen, bspw. `5`,`10`,`15`
Fehlermeldung | Hinweis, der erscheint, wenn die Eingabe den festgelegten Bereich an Zeichen unter- oder überschreitet.

<a name="type"></a>
## type

Überprüft, ob <b>der Typ</b> des Eingabe-Werts korrekt ist.

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name |  Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, bspw. `zip`, `phone`, `name`, `email`, `website`
Prüfung nach | Typ, der überprüft werden soll, bspw. `int`, `float`, `numeric`, `string`, `email`, `url`, `date`, `hex`]
Fehlermeldung | Hinweis, der erscheint, wenn die Eingabe nicht dem festgelegten Typ entspricht.
Feld muss nicht ausgefüllt werden | Gibt an, ob die Validierung erfolgreich ist, wenn keine Eingabe stattfindet. 

<a name="unique"></a>
## unique

Überprüft ob der Eingabe-Wert <b>noch nicht in anderen Datensätzen vorhanden</b> ist.

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name |  Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, bspw. `id`, `customer_id`, `email`
Fehlermeldung | Hinweis, der erscheint, wenn die Eingabe bereits in einem anderen Datensatz existiert.
Tabelle [opt] |  ###todo###
