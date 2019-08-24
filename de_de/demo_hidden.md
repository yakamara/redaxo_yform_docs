# Tutorial: Versteckte Werte übergeben (Hidden-Fields)

Gelegentlich besteht die Anforderung, einem Formular Parameter mitzugeben, die der Nutzer nicht sehen soll oder verändern darf.

YForm bietet dieses Möglichkeit auf zwei Wege: Serverseitig über das YForm-Value "hidden" - oder clientseitig über ein YForm Text-Eingabefeld `<input type="hidden" />`.

> **Hinweis**: Wir empfehlen, im Zweifel immer die serverseitige Variante zu wählen, damit der Benutzer keine Manipulation vornehmen kann. 

Sensible Daten sollten niemals an den Besucher übergeben werden. Daten wie die Summe eines Warenkorbs sollten bei einem Bestellformular immer serverseitig berechnet und überprüft werden und nicht über ein ausgeblendetes Eingabefeld eines Formulars. 

Andere Daten wie bspw. die Anzahl der Produkte in einem Warenkorb können auch über ein clientseitiges hidden-Feld übertragen werden.

## Voraussetzung

Wenn die Formulardaten in einer Datenbanktabelle gespeichert werden sollen, kann im Table Manager ein beliebiges Feld angelegt werden, z.B. ein Textfeld. Je nachdem, was für ein Wert gespeichert werden soll, kann aber auch ein anderes Feld sinnvoll sein. In diesem Beispiel wird ein Feld mit dem Namen `summe` benötigt.

## serverseitige Lösung

### Fest definierter Wert in Feld `summe` schreiben

**PHP-Schreibweise** 

    $yform->setHiddenField("summe", 150);

**Formbuilder Pipe-Schreibweise**

    hidden|summe|150|

### Wert aus Variable in Feld `summe` schreiben

**PHP-Schreibweise** 

    $yform->setHiddenField("summe", $bestellung_summe);

**Formbuilder Pipe-Schreibweise**

    // nicht möglich

### Wert aus dem GET-Parameter lesen

    // www.domain.de/meinformular/?q=Foo
    $yform->setValueField('hidden', array("suche", "q", REQUEST));

**Formbuilder Pipe-Schreibweise**

    // www.domain.de/meinformular/?q=Foo
    hidden|suche|q|REQUEST

Schreibt den Wert `Foo` des GET-Parameters `q` in das Feld `suche`.

> **Wichtig** Der GET-Parameter wird immer aus dem *abgesendeten* Formular geholt und nicht aus der URL des Formulars. Ggf. muss der Objekt-Parameter von YForm `form_action` den GET-Parameter enthalten.

## clientseitige Lösung

### Wert im Formular mit ausgeben

**PHP-Schreibweise** 

    $yform->setValueField('text', array('anzahl','Anzahl','0','0','{"type":"hidden"}'));

**Formbuilder Pipe-Schreibweise**

    text|anzahl|Anzahl|0|0|{"type":"hidden"}|

Erzeugt im Formular Eingabefeld, das bspw. per Javascript verändert werden kann:

    `<input class="form-control" name="FORM[...]" type="hidden" id="yform-data_edit-..." value="0">`

## Weitere Möglichkeiten

Das YForm-Objekt verfügt über zwei weitere Objekt-Methoden `setHiddenField()` und `setHiddenFields()`, die jedoch ihre Werte nicht in den sog. `value_pool` ablegen, sondern als Objektparameter unter dem key `form_hiddenfields` - d.h. diese Werte sind nicht für Aktionen wie `tpl2email` oder `db` sichtbar und werden demzufolge nicht an ein E-Mail-Template oder die Datenbank übergeben.

    $yform->setHiddenField('versteckt', 1);
    $yform->setHiddenFields(["a" => "b","c" => "d"]);

Auslesen über die Methode `getObjectparams()`

    $yform->getObjectparams('form_hiddenfields')['versteckt'];
    $yform->getObjectparams('form_hiddenfields')['a'];
    $yform->getObjectparams('form_hiddenfields')['c'];

## Credits

Alexander Walther, @alexplusde
