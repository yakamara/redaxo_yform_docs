# Yform: Formbuilder

> ## Inhalt
> - [Installation des Formbuilder-Moduls](#installation)
> - [Verwendung](#verwendung)
> 	- [Value-Felder](#value)
> 	- [Validate-Felder](#validate)
> 	- [Action-Felder](#action)
> - [Syntax](#syntax)
> - [PHP-Schreibweise](#php-schreibweise)
> - [Kurzer Blick in die Modulausgabe](#blick-modulausgabe)

<a name="installation"></a>
## Installation des Formbuilder-Moduls

Innerhalb von YForm gibt es im Menüpunkt `Übersicht` unter `Setup` den Button `Modul "YForm Formbuilder installieren"`. Damit wird das betreffende Modul angelegt.

<a name="verwendung"></a>
## Verwendung

In der Eingabe des Formbuilders kann man die Values, Validierungen und Aktionen direkt eintragen. Die genaue Syntax aller Komponenten ist im Modul zu finden.

<a name="value"></a>
### Value-Felder
Value-Felder sind die am häufigstgen verwendeten Felder, die normalerweise im Formular direkt auftauchen: einfache Textfelder, Selectfelder, Checkboxen, aber ebenso auch versteckte Felder, Geburtsdaten, Datenbank-Selectfelder, etc.

<a name="validate"></a>
### Validate-Felder
Mit Validate-Feldern werden die Werte der Value-Felder überprüft. Das heißt, damit wird z.B. valdiert, ob ein Wert eingetragen wurde (`empty`) oder ob ein `String`, `Integer` oder sonstiger Wert eingetragen wurde. Es kann aber auch überprüft werden, ob ein Datenbankfeld mit diesem Wert überhaupt schon existiert.

<a name="action"></a>
### Action-Felder
Action-Felder sind für spätere Verwendungen wichtig: Soll z.B. eine E-Mail verschickt werden und/oder ein Eintrag in die Datenbank geschehen?

<a name="syntax"></a>
## Syntax

Im Normalfall folgt die Syntax folgendem Schema: Zuerst kommt der Feldtyp, dann der Name, dann die Optionen, jeweils durch einen Trennstrich (Pipe) voneinander abgetrennt.

**Beispiel:** Hier erscheint zunächst ein Textfeld, dann wird validiert, ob ein Wert eingetragen wurde. In der Zeile darunter wird ein Selectfeld definiert, danach folgt eine Aktion, um die Daten in die Datenbank "adressen" zu speichern:

	text|name|Nachname
	validate|empty|name|Bitte einen Nachnamen eingeben
	select|anrede|Anrede|Anrede=,Frau=w,Herr=m
	action|db|adressen|

Die vollständigen Optionen für jedes Feld kann man direkt im YForm-Modul ersehen. Beim Textfeld finden sich beispielsweise folgende Optionen:

	text|name|label|defaultwert|[no_db]|cssclassname

- **text:** Dies definiert den Feldtyp
- **name:** der interne Feld-Name
- **label:** das vor dem Feld sichtbare Label (Feldbeschriftung)
- **defaultwert:** Damit kann man einen Standardwert in das Feld setzen
- **no_db:** Speichert eine Aktion die Felddaten in die Datenbank, so gibt es hin und wieder Felder, die man nicht gespeichert haben will, z.B. den Wert eines Submit-Buttons
- **cssclassname:** Damit kann man dem Feld eine individuelle CSS-Klasse zuweisen

<a name="php-schreibweise"></a>
## PHP-Schreibweise

Um ein Formular mit YForm-Methoden zu generieren, muss nicht das Formbuilder-Modul genutzt werden. Man kann alles auch direkt in PHP schreiben:

**So sieht das obige Beispiel in PHP aus:**

	action|db|adressen|
	$yform = new rex_yform();
	// $yform->setDebug(TRUE);
	// auskommentieren, um Probleme zu finden
	$yform->setValueField('text', array("name","Nachname"));
	$yform->setValidateField('empty', array("name","Bitte einen Nachnamen eingeben"));
	$yform->setValueField('select', array("anrede","Anrede","Anrede=,Frau=w,Herr=m"));
	$yform->setActionField('db', array('adressen'));
	echo $yform->getForm();

> **Tipp:** Bei einer mit dem Table Manager angelegten Tabelle kann man sich den Formular-Code in den Versionen PHP (hilfreich bei eigenen Anpassungen), PIPE (im YForm-Modul verwendet) und E-MAIL (für den Versand mit Email-Templates) generieren lassen.

<a name="blick-modulausgabe"></a>
## Kurzer Blick in die Modulausgabe

Wenn man sich den Eingabe- und Ausgabe-Code des YForm-Moduls ansieht, hilft dies, das Prinzip von YForm besser zu verstehen. In der Modulausgabe findet sich z.B. Folgendes:

	$yform = new rex_yform;
	$form_data = 'REX_VALUE[3]';
	$form_data = trim(str_replace("<br />","",rex_yform::unhtmlentities($form_data)));
	$yform->setObjectparams('form_action', rex_getUrl(REX_ARTICLE_ID,REX_CLANG_ID));
	$yform->setFormData($form_data);

Zunächst wird ein neues rex_yform-Objekt erzeugt.
Dann werden bei den im Textarea-Feld eingetragenen Felder die `<br>`-Tags herausgefiltert, als Standard-Zieladresse nach dem Abschicken die aktuelle Seite in der aktuellen Sprache definiert und die Felddefinitionen dem Objekt zur Verarbeitung übergeben.

Ebenfalls in der Modulausgabe kann man erkennen (hier nicht als Beispiel aufgelistet), wie die vordefinierten Aktionen aufgebaut sind. So wird beispielsweise im Modul-Output der nach dem Abschicken sichtbare Text und das Anzeige-Format definiert oder der E-Mail-Versand konfiguriert.  
Alle diese Aktionen lassen sich auch leicht in eigenem PHP-Code auslösen; das YForm-Builder-Modul erleichtert lediglich diese Arbeit.
