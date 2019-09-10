# YForm-Modul: Values

> **Hinweis:** 
> Dieser Abschnitt der Doku ist noch nicht fertig. Du kannst dich auf [GitHub](https://github.com/yakamara/redaxo_yform_docs/) an der Fertigstellung beteiligen.

- [Zweck der Values](#zweck-der-values)
- [Value-Klassen](#value-klassen)

<a name="zweck-der-values"></a>
## Zweck der Values

Mit diesen Klassen werden alle sichtbaren und verstecken Felder definiert.

> Die Value-Klassen sind hier zu finden:  
> `src/addons/yform/lib/yform/values/`


Beispiele (Schreibweisen): **yForm Formbuilder** und **PHP**

Die PHP-Beispiele können in diesem Formular getestet/eingesetzt werden:

	<?php
	$yform = new rex_yform();
	$yform->setObjectparams('form_action', rex_getUrl(REX_ARTICLE_ID,REX_CLANG_ID));

	$yform->setValueField('text', array("wert1","Wert 1"));

	
	echo $yform->getForm();
	?>


<a name="value-klassen"></a>
## Value-Klassen

	
	
	
	
### be_link

##### Definition
	Ein Redaxo-Feld, um einen Redaxo-Artikel auszuwählen.
	
##### Beispiel PHP
	$yform->setValueField('be_link', array("link","Link zu Artikel"));
		
##### Beispiel Pipe
	be_link|link|Link zu Artikel|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="link"]
		

### be_manager_relation

##### Definition
	Ein Auswahlfeld / Popup, um ein oder mehrere Datensätze mit denen einer fremden Tabelle zu verknüpfen, z.B. über einen Fremdschlüssel (1:n) oder eine Relationstabelle (m:n).
		
##### Beispiel PHP
	$yform->setValueField('be_manager_relation', array("manager_relation","Beispiel","rex_yf_messages","","0","0","","","","rex_yf_employees"));
		
##### Beispiel Pipe
	be_manager_relation|manager_relation|Beispiel|rex_yf_messages||0|0||||rex_yf_employees|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="manager_relation"]
	

	

### be_media

##### Definition
	Ein Redaxo-Feld, um eine einzelne oder mehrere Medienpool-Datei/en auszuwählen.
	
##### Beispiel PHP
	$yform->setValueField('be_media', array("image","Bild","1","0","general","jpg,gif,png,jpeg"));
		
##### Beispiel Pipe
	be_media|image|Bild|1|0|general|jpg,gif,png,jpeg|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="image"]

	
	
	

### be_select_category

##### Definition
	Ein Redaxo-Feld, um ein oder mehrere Kategorien aus der Struktur auszuwählen.
	
##### Beispiel PHP
	$yform->setValueField('be_select_category', array("be_select_category","Select Category","1","1","1","","1","0"));
		
##### Beispiel Pipe
	be_select_category|be_select_category|Select Category|1|1|1||1|0|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="be_select_category"]

	
	
	
	
	
### be_table

##### Definition
	Eine Reihe von Eingabefeldern, um tabellarische Daten einzugeben.
	
##### Beispiel PHP
	$yform->setValueField('be_table', array("table","Tabelle","Menge,Preis,Gewicht"));
		
##### Beispiel Pipe
	be_table|table|Tabelle|Menge,Preis,Gewicht|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="table"]


### captcha
		
##### Definition
	captcha|Beschreibungstext|Fehlertext
	
##### Beispiel Formbuilder
	_
	
##### Beispiel PHP
	_


### captcha_calc

##### Definition
	captcha_calc|Beschreibungstext|Fehlertext
	
##### Beispiel Formbuilder
	_
	
##### Beispiel PHP
	_


### reCaptcha

##### Definition
Nutzt den Google-Service reCAPTCHA v2.  
Für den API-Key ist eine Registrierung bei Google unter https://www.google.com/recaptcha notwendig.  
**Achtung:** Es muss die reCAPTCHA Version 2 (v2) verwendet werden.   
Eine Nutzung der Versionen v1 und v3 ist derzeit nicht möglich.  

##### Beispiel Pipe
	recaptcha|Sicherheitsüberprüfung|<PUBLIC_KEY>|<PRIVATE_KEY>|Die Sicherheitsüberprüfung schlug fehl.|1|
	

### checkbox

##### Definition
	Eine Checkbox mit vordefinierten Werten.
	
##### Beispiel PHP

*Syntax*

	$yform->setValueField('checkbox', array("checkbox","Checkbox","0 or 1"));
	
*Beispiel*

Eine Checkbox die bereits gecheckt ist.

	$yform->setValueField('checkbox', array("checkbox","Checkbox","1"));
		
##### Beispiel Pipe
	checkbox|checkbox|Checkbox|1|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="checkbox"]

	

### checkbox_sql (nicht mehr empfohlen - statt dessen choice verwenden)

##### Definition
	Ein oder mehrere Checkbox-Felder mit Werten, die aus einer SQL-Abfrage stammen.
	
##### Beispiel PHP
	$yform->setValueField('checkbox_sql', array("checkbox_sql","Checkbox SQL","SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio"));
		
##### Beispiel Pipe
	checkbox_sql|checkbox_sql|Checkbox SQL|SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="checkbox_sql"]


### choice

##### **Definition**
Erzeugt eine Selectbox, eine Radiobutton Auswahl oder ein Checkbox-Feld. Wahlweise mit Multiple Auswahl oder Gruppiert (optgroup). Das Feld choice ersetzt mit der YFORM Version 3.0 die Felder checkbox_sql, radio, radio_sql, select und select_sql.
Die Options können entweder als kommaseparierte Liste `label1=val1,label2=val2...`, als JSON `{"Europa": {"Dänemark": "DK", "Deutschland": "DE", "Österreich": "AT", "Schweiz": "CH"}, "Südamerika": {"Bolivien": "BO"}}` oder als SQL Query `SELECT id AS value, name AS label FROM country` bzw. `SELECT a.id AS value, a.name AS label, b.name AS group_label FROM country AS a LEFT JOIN continent AS b ON a.continent_id = b.id` angegeben werden. SQL muss die Felder `value` und `label` sowie `group_label` für gruppierte Felder zurückgeben. Der Alias `group_label` kann frei gewählt werden und muss beim Parameter `group_by` angegeben werden (Siehe Beispiel 6). Mit der Syntax als kommaseparierte Liste sind keine gruppierten Felder (optgroups) möglich.

*Hinweis*
Die SQL Syntax unterscheidet sich zur früheren Syntax! Es werden nun die Felder `label` und `value` statt `id` und `name` erwartet.

*Feldtyp*
Wenn beim Parameter `expanded` 1 oder true angegeben wird, so wird ein Checkboxfeld oder Radiobuttons erzeugt. Bei 0 oder false wird ein Selectfeld erzeugt. Wenn beim Parameter `multiple` 1 oder true angegeben wird, so wird ein Multiselectfeld bzw. ein Checkboxfeld erzeugt.

    Select:       expanded = 0   multiple = 0
    Multiselect:  expanded = 0   multiple = 1
    Radiobuttons: expanded = 1   multiple = 0
    Checkboxfeld: expanded = 1   multiple = 1

*Attribute*

Der Parameter `group_attributes`, `choice_attributes` und `attributes` können entweder als ausführbare Befehle (callable) (z.B. `foo::bar($attributes)` oder `foo($attributes)`) oder als JSON (z.B. `{"class": "group-item"}`) angegeben werden.
Beim Parameter `choice_attributes` sind bei einer Funktion drei Werte möglich: `foo($attributes, $value, $label)`.


##### **Beispiele PHP**

*Syntax*

    $yform->setValueField('choice',["fieldname","Label",Options,expanded,multiple,default,group_by,preferred_choices,placeholder,group_attributes,choice_attributes,attributes,notice,[no_db]);

*Beispiele*

1. Select, Options als kommaseparierte Liste

        $yform->setValueField('choice',["selectfield","Verkehrsmittel","Auto,Bus,Fahrrad,Schiff,Rollschuhe,Zug",0,0]);

2. Gruppiertes Checkboxfeld, Options als JSON

        $yform->setValueField('choice',["mycheckboxfield","Vor- und Nachspeisen",'{"Vorspeisen": {"Gemischter Salat":"insalata_mista","Tagessuppe":"piatto_del_giorno"},"Dessert":{"Spaghettieis":"spaghetti_di_ghiaccio","Tiramisu":"tiramisu"}}',1,1]);

		
##### **Beispiel Pipe**
*Syntax*

    choice|name|label|choices|[expanded type: boolean; default: false]|[multiple type: boolean; default: false]|[default]|[group_by]|[preferred_choices]|[placeholder]|[group_attributes]|[choice_attributes]|[attributes]|[notice]|[no_db]

*Beispiele*

3. Select, Options als kommaseparierte Liste

        choice|colors|Farben|Blau,Rot,Grün,Gelb,Lila|0|0|
	
4. Checkboxfeld, Options als kommaseparierte Liste mit Vorauswahl

        choice|colors|Farben|Blau,Rot,Grün,Gelb,Lila|1|1|Rot,Grün
	
5. Gruppierte Radiobutton, Options als JSON

        choice|drinks|Trinken|{"Kalte Getränke": {"Apfelschorle":"01","Orangensaft":"02"},"Warme Getränke":{"Kaffee":"11","Tee":"12"}}|1|0|

6. Select aus SQL, gruppiert mit Leeroption und bevorzugter Auswahl

        choice|artikel|Artikel|SELECT name label, id value, catname FROM rex_article ORDER BY catname|0|0||catname|8,5|--- bitte auswählen ---

    Die Datensätze mit der Id 8 und 5 stehen am Anfang des Select (preferred choices).
	

### date

##### Definition
	Eine Reihe von Auswahlfeldern, in der ein Datum (Tag, Monat, Jahr) ausgewählt wird.
	
##### Beispiel PHP
	$yform->setValueField('date', array("date","Datum","2016","+5","DD/MM/YYYY","1","","select"));
		
##### Beispiel Pipe
	date|date|Datum|2016|+5|DD/MM/YYYY|1||select|
	validate|type|Datum|date|Bitte geben Sie das Datum ein.|[1 = Feld darf auch leer sein]

##### Beispiel E-Mail
	REX_YFORM_DATA[field="date"]

	
	
	
	
	
### datestamp

##### Definition
	Ein unsichtbares Feld, in das ein Zeitstempel gespeichert wird, wenn der Datensatz hinzugefügt oder bearbeitet wird.
	
##### Beispiel PHP
	$yform->setValueField('datestamp', array("createdate","Zeitstempel","mysql","","0"));
		
##### Beispiel Pipe
	datestamp|createdate|Zeitstempel|mysql||0|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="createdate"]

	

### datetime

##### Definition
	Eine Reihe von Auswahlfeldern, in der Datum und Uhrzeit (Tag, Monat, Jahr, Stunden, Minuten, Sekunden) ausgewählt wird.
	
##### Beispiel PHP
	$yform->setValueField('datetime', array("datetime","Datetime","2016","+5","00,15,30,45","DD/MM/YYYY HH:ii","0","","select"));
		
##### Beispiel Pipe
	datetime|datetime|Datetime|2016|+5|00,15,30,45|DD/MM/YYYY HH:ii|0||select|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="datetime"]

	

### email

##### Definition
	Ein einfaches Eingabefeld für E-Mail-Adressen.
	
##### Beispiel PHP
	$yform->setValueField('email', array("email","E-Mail-Adresse"));
		
##### Beispiel Pipe
	email|email|E-Mail-Adresse|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="email"]

	

### emptyname

##### Definition
	Ein Feld ohne Eingabemöglichkeit.
	
##### Beispiel PHP
	$yform->setValueField('emptyname', array("emptyname","Emptyname"));
		
##### Beispiel Pipe
	emptyname|emptyname|Emptyname|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="emptyname"]
	

### fieldset

##### Definition
	Ein Fieldset gruppiert Formularfelder.
	
##### Beispiel PHP
	$yform->setValueField('fieldset', array("fieldsest","Fieldset"));
		
##### Beispiel Pipe
	fieldset|fieldsest|Fieldset|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="fieldsest"]

	

### float (deprecated)

##### Definition
	Ein einfaches Eingabefeld für Gleitkomma-Zahlen.
	
##### Beispiel PHP
	$yform->setValueField('float', array("float","Float","1"));
		
##### Beispiel Pipe
	float|float|Float|1|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="float"]


		
### generate_key

##### Definition
	Generiert ein nicht sichtbares Feld mit zufälligem 32-stelligem Schlüssel, bestehend aus Zahlen und Kleinbuchstaben.
		
##### Beispiel Pipe
	generate_key|name|[no_db]
	
##### Beispiel PHP
	_


### hashvalue

##### Definition
	Ein Feld, das aus dem Wert eines anderen Feldes einen Hashwert erzeugt.
	
##### Beispiel PHP
	$yform->setValueField('hashvalue', array("hashvalue","Hashvalue"));
		
##### Beispiel Pipe
	hashvalue|hashvalue|Hashvalue|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="hashvalue"]

	

### hidden
definiert ein Feld, das nur serverseitig befüllt wird und nicht ausgegeben wird.

> Hinweis: Für ein unsichtbares Eingabefeld wird nicht dieses hidden-Feld verwendet, sondern bspw. ein reguläres Eingabefeld (`text`), das zusätzlich das Attribut type="hidden" bekommt.

##### Definition
	hidden|name|(default)value||[no_db]
	 	
##### Beispiel Formbuilder
	hidden|name|(default)value||[no_db]
	hidden|name|(default)value|REQUEST|[no_db]
	
##### Beispiel PHP
	$yform->setValueField('hidden', array("name", "Max Muster"));
	
	// oder
	
	$ycom_user = rex_ycom_auth::getUser();
	if($ycom_user) {
		$yform->setValueField('hidden', array("user", $ycom_user()->getId()));
	}

	

### html

##### Definition
	Gibt HTML-Code an der gewünschten Stelle des Eingabe-Formulars aus.
	
##### Beispiel PHP
	$yform->setValueField('html', array("html","HTML","<p>Hallo Welt!</p>"));
		
##### Beispiel Pipe
	html|html|HTML|<p>Hallo Welt!</p>|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="html"]

	

### index

##### Definition
	Ein Feld, das einen Index / Schlüssel über mehrere Felder erzeugt.
	
##### Beispiel PHP
	$yform->setValueField('index', array("index","Index"));
		
##### Beispiel Pipe
	index|index|Index|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="index"]

	

### integer

##### Definition
	Ein einfaches Eingabefeld für ganze Zahlen.
	
##### Beispiel PHP
	$yform->setValueField('integer', array("int","Integer"));
		
##### Beispiel Pipe
	integer|int|Integer|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="int"]

	
### ip
übergibt die IP des Users.

##### Definition
	ip|name|[no_db]
	
##### Beispiel Formbuilder
	ip|ip	

##### Beispiel PHP
	$yform->setValueField('ip', array("ip"));


### mediafile

##### Definition
	Ein Upload-Feld, mit dem eine Datei in den Medienpool hochgeladen wird.
	
##### Beispiel PHP
	$yform->setValueField('mediafile', array("media","Bilder","5000",".jpg,.gif,.png,.jpeg","","","","1"));
	$yform->setValueField('mediafile', array("name","label","[min_size,max_size]/max_size","[allowed extensions]","[required 0,1]","min_err,max_err,type_err,empty_err","[no_db]","media_cat_id","mediapool_user"));	
	
##### Beispiel Pipe
	mediafile|media|Bilder|5000|.jpg,.gif,.png,.jpeg||||1|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="media"]
	

#### Number 
##### Beispiel Formbuilder
    number|name|label|precision|scale|defaultwert|[no_db]|[unit]|[notice]
	number|zahl|Zahl|6|2|5||cm|Hinweis Number

precision ist die Anzahl der signifikanten Stellen. Der Bereich von precision liegt zwischen 1 und 65.

scale ist die Anzahl der Stellen nach dem Dezimalzeichen. Der Bereich von scale ist 0 und 30. MySQL erfordert, dass scale kleiner oder gleich (<=) precision ist.

In diesem Beispiel kann die Spalte 6 Stellen mit 2 Dezimalstellen speichern. Daher reicht der Bereich der Betragsspalte von 9999,99 bis -9999,99.


##### Beispiel PHP

	


### !!password

##### Beispiel Formbuilder
	password|name|label|default_value
	
##### Beispiel PHP
	$yform->setValueField('password', array("name","label", "default_value"));


### php


##### Definition
	Führt PHP-Code an der gewünschten Stelle des Eingabe-Formulars aus.
	
##### Beispiel PHP
	$yform->setValueField('php', array("php","PHP","<? echo 'hallo welt'; ?>"));
		
##### Beispiel Pipe
	php|php|PHP|<? echo 'hallo welt'; ?>|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="php"]

> **Hinweis**: Zusammen mit dem Upload-Feld lassen sich komfortabel [E-Mails mit Anhang versenden](demo_email-attachments.md).
	

### prio

##### Definition
	Ein Auswahlfeld, um Datensätze in eine bestimmte Reihenfolge zu sortieren.
	
##### Beispiel PHP
	$yform->setValueField('prio', array("prio","Reihenfolge"));
		
##### Beispiel Pipe
	prio|prio|Reihenfolge|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="prio"]
	




### radio (nicht mehr empfohlen - statt dessen choice verwenden)

##### Definition
	Ein Auswahlfeld, um Datensätze in eine bestimmte Reihenfolge zu sortieren.
	
##### Beispiel PHP
	$yform->setValueField('radio', array("radio","Radio","schlecht=-1,ok=0,gut=1","0"));
		
##### Beispiel Pipe
	radio|radio|Radio|schlecht=-1,ok=0,gut=1|0|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="radio"]

### readtable
liest einen Datensatz und übergibt die ausgelesenen Werte in den E-mail value_pool, die einem E-Mail-Template über Platzhalter werden können.

##### Definition
	readtable|tablename|feldname|label
	Ein Auswahlfeld, um Datensätze in eine bestimmte Reihenfolge zu sortieren.
	
##### Beispiel Formbuilder
	text|name|Name
	readtable|rex_user|name|name
	action|tpl2email|testtemplate||info@mustermann.de


##### Beispiel PHP
	$yform->setValueField('text', array("name","Name"));
	$yform->setValueField('readtable', array("rex_user","name","name"));
	$yform->setActionField('tpl2email', array("testtemplate","","info@mustermann.de"));

liest aus der Tabelle **rex_user** einen Datensatz 

	SELECT * FROM rex_user WHERE name='[eingabe feld name]'

und sendet eine E-Mail mit dem E-Mail-Template "testtemplate" and die E-Mail-Adresse:



### radio_sql (nicht mehr empfohlen - statt dessen choice verwenden)

##### Definition
	Ein oder mehrere Auswahlfelder als Radio-Buttons.
	
##### Beispiel PHP
	$yform->setValueField('radio_sql', array("radio_sql","Radio SQL","SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio"));
		
##### Beispiel Pipe
	radio_sql|radio_sql|Radio SQL|SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="radio_sql"]

### resetbutton
definiert einen Reset-Button, mit dem Eingaben zurückgesetzt werden können.


##### Definition
	resetbutton|name|label|value|cssclassname
	
##### Beispiel Formbuilder
	resetbutton|reset|reset|Reset

### !!uniqueform

##### Definition
	uniqueform|name|table|Fehlermeldung
	
##### Beispiel Formbuilder
	_
	
##### Beispiel PHP
	-

##### Beispiel PHP
	$yform->setValueField('resetbutton', array("reset","reset","Reset"));
	

### select (nicht mehr empfohlen - statt dessen choice verwenden)

##### Definition
	Ein Auswahlfeld mit vordefinierten Werten.
	
##### Beispiel PHP
	$yform->setValueField('select', array("select","Select","schlecht=-1,ok=0,gut=1","","0","0"));
		
##### Beispiel Pipe
	select|select|Select|schlecht=-1,ok=0,gut=1||0|0|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="select"]


	

### select_sql (nicht mehr empfohlen - statt dessen choice verwenden)

##### Definition
	Ein Auswahlfeld mit Werten, die aus einer SQL-Abfrage stammen.
	
##### Beispiel PHP
	$yform->setValueField('select_sql', array("select_sql","Select SQL","SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio","","","0","","0"));
		
##### Beispiel Pipe
	select_sql|select_sql|Select SQL|SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio|||0||0|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="select_sql"]

	
	
	
### submit

##### Definition
	Zeigt einen Wert in der Ausgabe.
	
##### Beispiel PHP
		
##### Beispiel Pipe
	showvalue|name|label|defaultwert|notice
	
	
	
### submit

##### Definition
	Ein oder mehrere Submit-Buttons zum Absenden des Formulars.
	
##### Beispiel PHP
	$yform->setValueField('submit', array("submit","Submit"));
	Als Standard werden die Klassen "btn" & "btn-primary" definiert. Für zusätzliche Klassen gilt:
	$yform->setValueField('submit', array('submit','Anfrage senden','','','','btn-secondary'));
		
##### Beispiel Pipe
	submit|submit|Submit|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="submit"]


	
	
	
### text

##### Definition
	Input-Feld zur Eingabe eines Textes.
	
##### Beispiel PHP
	$yform->setValueField('text', array("text","Text"));
		
##### Beispiel Pipe
	text|text|Text|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="text"]


	
	
	
	
	
### textarea

##### Definition
	Ein mehrzeiliges Eingabefeld für Text.

##### Beispiel PHP
	$yform->setValueField('textarea', array("textarea","Textarea"));
		
##### Beispiel Pipe
	textarea|textarea|Textarea|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="textarea"]


	
	
	
### time

##### Definition
	Eine Reihe von Auswahlfeldern, in der die Uhrzeit (Stunden, Minuten, Sekunden) ausgewählt wird.
	
##### Beispiel PHP
	$yform->setValueField('time', array("time","Zeit","","00,15,30,45","HH:ii","","select"));
		
##### Beispiel Pipe
	time|time|Zeit||00,15,30,45|HH:ii||select|

##### Beispiel E-Mail
	REX_YFORM_DATA[field="time"]



	
	
### !!uniqueform

##### Definition
	uniqueform|name|table|Fehlermeldung
	
##### Beispiel Formbuilder
	_
	
##### Beispiel PHP
	-

	
	
	
	
	
### upload

##### Definition
	Ein Upload-Feld, mit dem eine Datei in die Datenbank oder ein Verzeichnis hochgeladen wird.
	
##### Beispiel PHP
	$yform->setValueField('upload', array("upload","Upload","",".jpg,.gif,.png,.jpeg"));
		
##### Beispiel Pipe
	upload|upload|Upload||.jpg,.gif,.png,.jpeg|

	upload|name | label | Maximale Größe in Kb oder Range 100,500 | endungenmitpunktmitkommasepariert | pflicht=1 | min_err,max_err,type_err,empty_err,delete_file_msg | Speichermodus(upload/database/no_save) | `database`: Dateiname wird gespeichert in Feldnamen | Eigener Uploadordner [optional] | Dateiprefix [optional] |

##### Beispiel E-Mail
	REX_YFORM_DATA[field="upload"]

> **Hinweis**: Zusammen mit dem PHP-Feld lassen sich komfortabel [E-Mails mit Anhang versenden](demo_email-attachments.md).
