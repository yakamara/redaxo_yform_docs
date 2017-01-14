# Tools-Plugin

> Dieses Plugin hilft bei bestimmten Eingabearten. Datumsfelder, DatumZeit-Felder und Textfelder die bestimmte Eingaben verlangen, die man bereits bei der Eingabe erzwingen möchte.

Dabei werden die entsprechenden Bibliotheken bei der Aktivierung der AddOn bereits installiert und initialisiert. D.h. man muss die gewünschten Funktionen nur durch Definition von CSS Attributen zuweisen.

## select2

diese Bibliothek [https://select2.github.io/](https://select2.github.io/) hilft dabei, Selectfelder zu vereinfachen und entsprechend des Typs verschiedene Varianten zu aktivieren.

Dabei muss hier das select-Feld folgendes Attribut bekommen:

	data-yform-tools-select2 = ""

Das kann man im Manager über das Attibutefeld innerhalb von z.B. select oder select_sql so setzen:

	{"data-yform-tools-select2": "", "placeholder": "My Placeholder"}

Eine weitere Variante wäre der Tag-Mode

	{"data-yform-tools-select2": "tags", "placeholder": "My Placeholder"}


## inputmask

diese Bibliothek [https://github.com/RobinHerbots/Inputmask](https://github.com/RobinHerbots/Inputmask) dient dazu, bestimmte Eingabeformate vorzugeben um somit Fehler zu vermeiden. Z.B. kann ein bestimmtes Datumsformat erzwungen werden.

Dabei wird auch hier ein Attribute im Textfeld gesetzt:

    data-yform-tools-inputmask = ""

Man muss einen Wert angeben, damit dem Textfeld klar ist, wie die Überprüfung auszusehen hat. z.B.

    dd/mm/yyyy

oder

    99-99-9999

oder

    9-a{1,3}9{1,3}


Das kann man im Manager über das Attibutefeld innerhalb von z.B. text so setzen:

    {"data-yform-tools-inputmask":"dd/mm/yyyy"}

## daterangepicker

diese Bibliothek [http://www.daterangepicker.com/](http://www.daterangepicker.com/) dient für die Auswahl von Datumsfeldern oder Datumzeiträumen. Dabei kann auch eine Uhrzeit selektiert werden.

Dabei muss das Textfeld folgendes Attribut bekommen:

    data-yform-tools-datepicker = ""

oder

    data-yform-tools-datetimepicker = ""

und auch mit Formaten versehen werden. Z.b. Beim Datepicker

    DD-MM-YYYY

oder beim Datetimepicker

    YYYY-MM-DD HH:ii

kann man im Manager über das Attibutefeld innerhalb von z.B. date mit input:text so setzen:

    {"data-yform-tools-datetimepicker":"YYYY-MM-DD HH:ii"}
