# Table Manager: Validierungen

* Analog zur Seite Felder
*  ###frage### Validierungsbeispiele für Custom Function bereitstellen... welche Parameter erhält die Funktion, wie erfolgt die Rückgabe?
*  ###frage### i18n der Fehlermeldungen?

<a name="compare"></a>
## compare

Zum Vergleichen zweier Felder, bspw. "E-Mail-Adresse" und "E-Mail-Adresse bestätigen". ###todo### nützliche Beispiele?

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
1. Feldname | Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `password`, `email`
2. Feldname | Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `password2`, `email_verified`
Vergleichsart | Operator, wie `Feld 1` und `Feld 2` vergleichen werden sollen, bspw. `!=`, `!=`, `>`, `<` 
Fehlermeldung | Hinweis, der erscheint, wenn der Vergleich beider Felder `false` ergibt.

<a name="compare_value"></a>
## compare_value

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
1. Feldname | Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `checkbox_agb`, `newsletter_consent`
Vergleichswert | Fest definierter Wert, der für den Vergleich herangezogen wird, z.B. `1` (bei Checkboxen) 
Vergleichsart |  Operator, wie `Feld 1` und `Vergleichswert` vergleichen werden sollen, bspw. `!=`, `!=`, `>`, `<` 
Fehlermeldung | Hinweis, der erscheint, wenn der Vergleich `false` ergibt.

<a name="customfunction"></a>
## customfunction

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name | 
Name der Funktion | 
Weitere Parameter | 
Fehlermeldung | 

<a name="email"></a>
## email

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name |  Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `email`, `contact`
Fehlermeldung | Hinweis, der erscheint, wenn keine gültige E-Mail-Adresse angegeben wurde.

 ###todo### wie findet die Prüfung statt? RFC-Standardkonform oder einfach nur nach @-Zeichen?

> Hinweis: Falls das E-Mail-Feld ein Pflichtfeld ist, muss auch die Validierung `empty` hinzugefügt werden, da ein leeres Feld eine keine ungültige E-Mail-Adresse darstellt.

<a name="empty"></a>
## empty

Option | Erläuterung
------ | ------
Priorität | Reihenfolge des Feldes in der Feldübersicht und beim Abarbeiten der Validierungen.
Name |  Name des Tabellenfeldes, das für die Überprüfung herangezogen wird, z.B. `email`, `name`
Fehlermeldung | Hinweis, der erscheint, wenn das Feld leer ist.

<a name="intfromto"></a>
## intfromto

Option | Erläuterung
------ | ------
Prioritaet | 
Name | 
Von | 
Bis | 
Fehlermeldung | 

<a name="size"></a>
## size

Option | Erläuterung
------ | ------
Prioritaet | 
Name | 
Anzahl der Zeichen | 
Fehlermeldung | 

<a name="size_range"></a>
## size_range

Option | Erläuterung
------ | ------
Prioritaet | 
Name | 
Minimale Anzahl der Zeichen (opt) | 
Maximale Anzahl der Zeichen (opt) | 
Fehlermeldung | 

<a name="type"></a>
## type

Option | Erläuterung
------ | ------
Prioritaet | 
Name | 
Prüfung nach | 
Fehlermeldung | 
Feld muss nicht ausgefüllt werden | 

<a name="unique"></a>
## unique

Option | Erläuterung
------ | ------
Prioritaet | 
Name | 
Fehlermeldung | 
Tabelle [opt] |  
