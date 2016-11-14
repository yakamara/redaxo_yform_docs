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

	
	
	
	
###be_link

#####Definition
	Ein Redaxo-Feld, um einen Redaxo-Artikel auszuwählen.
	
#####Beispiel PHP
	$yform->setValueField('be_link', array("link","Link zu Artikel"));
		
#####Beispiel Pipe
	be_link|link|Link zu Artikel|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="link"]
		
	
	
	
		
###be_manager_relation

#####Definition
	Ein Auswahlfeld / Popup, um ein oder mehrere Datensätze mit denen einer fremden Tabelle zu verknüpfen, z.B. über einen Fremdschlüssel (1:n) oder eine Relationstabelle (m:n).
		
#####Beispiel PHP
	$yform->setValueField('be_manager_relation', array("manager_relation","Beispiel","rex_yf_messages","","0","0","","","","rex_yf_employees"));
		
#####Beispiel Pipe
	be_manager_relation|manager_relation|Beispiel|rex_yf_messages||0|0||||rex_yf_employees|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="manager_relation"]
	

	
	
	
	
		
###be_media

#####Definition
	Ein Redaxo-Feld, um eine einzelne Medienpool-Datei auszuwählen.
	
#####Beispiel PHP
	$yform->setValueField('be_media', array("image","Bild","1","0","general","jpg,gif,png,jpeg"));
		
#####Beispiel Pipe
	be_media|image|Bild|1|0|general|jpg,gif,png,jpeg|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="image"]

	
	
	
	
	
	
		
###be_select_category

#####Definition
	Ein Redaxo-Feld, um ein oder mehrere Kategorien aus der Struktur auszuwählen.
	
#####Beispiel PHP
	$yform->setValueField('be_select_category', array("be_select_category","Select Category","1","1","1","","1","0"));
		
#####Beispiel Pipe
	be_select_category|be_select_category|Select Category|1|1|1||1|0|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="be_select_category"]

	
	
	
	
	
###be_table

#####Definition
	Eine Reihe von Eingabefeldern, um tabellarische Daten einzugeben.
	
#####Beispiel PHP
	$yform->setValueField('be_table', array("table","Tabelle","Menge,Preis,Gewicht"));
		
#####Beispiel Pipe
	be_table|table|Tabelle|Menge,Preis,Gewicht|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="table"]

	
	
	
	
	
	
		
###checkbox

#####Definition
	Eine Checkbox mit vordefinierten Werten.
	
#####Beispiel PHP
	$yform->setValueField('checkbox', array("checkbox","Checkbox","0,1","1"));
		
#####Beispiel Pipe
	checkbox|checkbox|Checkbox|0,1|1|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="checkbox"]

	
	
	
	
		
###checkbox_sql

#####Definition
	Ein oder mehrere Checkbox-Felder mit Werten, die aus einer SQL-Abfrage stammen.
	
#####Beispiel PHP
	$yform->setValueField('checkbox_sql', array("checkbox_sql","Checkbox SQL","SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio"));
		
#####Beispiel Pipe
	checkbox_sql|checkbox_sql|Checkbox SQL|SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="checkbox_sql"]

	
	
	
	
		
###date

#####Definition
	Eine Reihe von Auswahlfeldern, in der ein Datum (Tag, Monat, Jahr) ausgewählt wird.
	
#####Beispiel PHP
	$yform->setValueField('date', array("date","Datum","2016","+5","DD/MM/YYYY","1","","select"));
		
#####Beispiel Pipe
	date|date|Datum|2016|+5|DD/MM/YYYY|1||select|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="date"]

	
	
	
	
	
###datestamp

#####Definition
	Ein unsichtbares Feld, in das ein Zeitstempel gespeichert wird, wenn der Datensatz hinzugefügt oder bearbeitet wird.
	
#####Beispiel PHP
	$yform->setValueField('datestamp', array("datestamp","Datestamp","","","0"));
		
#####Beispiel Pipe
	datestamp|datestamp|Datestamp|||0|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="datestamp"]

	
	
	
	
		
###datetime

#####Definition
	Eine Reihe von Auswahlfeldern, in der Datum und Uhrzeit (Tag, Monat, Jahr, Stunden, Minuten, Sekunden) ausgewählt wird.
	
#####Beispiel PHP
	$yform->setValueField('datetime', array("datetime","Datetime","2016","+5","00,15,30,45","DD/MM/YYYY HH:ii","0","","select"));
		
#####Beispiel Pipe
	datetime|datetime|Datetime|2016|+5|00,15,30,45|DD/MM/YYYY HH:ii|0||select|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="datetime"]

	
	
	
	
		
###email

#####Definition
	Ein einfaches Eingabefeld für E-Mail-Adressen.
	
#####Beispiel PHP
	$yform->setValueField('email', array("email","E-Mail-Adresse"));
		
#####Beispiel Pipe
	email|email|E-Mail-Adresse|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="email"]

	
	
	
	
		
###emptyname

#####Definition
	Ein Feld ohne Eingabemöglichkeit.
	
#####Beispiel PHP
	$yform->setValueField('emptyname', array("emptyname","Emptyname"));
		
#####Beispiel Pipe
	emptyname|emptyname|Emptyname|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="emptyname"]
	
	
	
	
		
###fieldset

#####Definition
	Ein Fieldset gruppiert Formularfelder.
	
#####Beispiel PHP
	$yform->setValueField('fieldset', array("fieldsest","Fieldset"));
		
#####Beispiel Pipe
	fieldset|fieldsest|Fieldset|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="fieldsest"]

	
	
	
	
		
###float

#####Definition
	Ein einfaches Eingabefeld für Gleitkomma-Zahlen.
	
#####Beispiel PHP
	$yform->setValueField('float', array("float","Float","1"));
		
#####Beispiel Pipe
	float|float|Float|1|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="float"]

	
	
			
	
	
	
		
###hashvalue

#####Definition
	Ein Feld, das aus dem Wert eines anderen Feldes einen Hashwert erzeugt.
	
#####Beispiel PHP
	$yform->setValueField('hashvalue', array("hashvalue","Hashvalue"));
		
#####Beispiel Pipe
	hashvalue|hashvalue|Hashvalue|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="hashvalue"]

	
	
	
	
		
###hidden
definiert ein versteckes Feld

#####Definition
	hidden|name|(default)value||[no_db]
	 	
#####Beispiel Formbuilder
	hidden|name|(default)value||[no_db]
	hidden|name|(default)value|REQUEST|[no_db]
	
#####Beispiel PHP
	$yform->setValueField('hidden', array("name", "<h1>Headline</h1>"));

	
	
	
	
		
###html

#####Definition
	Gibt HTML-Code an der gewünschten Stelle des Eingabe-Formulars aus.
	
#####Beispiel PHP
	$yform->setValueField('html', array("html","HTML","<p>Hallo Welt!</p>"));
		
#####Beispiel Pipe
	html|html|HTML|<p>Hallo Welt!</p>|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="html"]

	
	
	
	
		
###index

#####Definition
	Ein Feld, das einen Index / Schlüssel über mehrere Felder erzeugt.
	
#####Beispiel PHP
	$yform->setValueField('index', array("index","Index"));
		
#####Beispiel Pipe
	index|index|Index|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="index"]

	
	
	
	
		
###integer

#####Definition
	Ein einfaches Eingabefeld für ganze Zahlen.
	
#####Beispiel PHP
	$yform->setValueField('integer', array("int","Integer"));
		
#####Beispiel Pipe
	integer|int|Integer|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="int"]

	

	
	
	
	
		
###mediafile

#####Definition
	Ein Upload-Feld, mit dem eine Datei in den Medienpool hochgeladen wird.
	
#####Beispiel PHP
	$yform->setValueField('mediafile', array("media","Bilder","5000",".jpg,.gif,.png,.jpeg","","","","1"));
		
#####Beispiel Pipe
	mediafile|media|Bilder|5000|.jpg,.gif,.png,.jpeg||||1|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="media"]
	
	
	
	
	
	
		
###php


#####Definition
	Führt PHP-Code an der gewünschten Stelle des Eingabe-Formulars aus.
	
#####Beispiel PHP
	$yform->setValueField('php', array("php","PHP","<?
echo 'hallo welt';
?>"));
		
#####Beispiel Pipe
	php|php|PHP|<?
echo 'hallo welt';
?>|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="php"]

	
	
	
	
		
###prio

#####Definition
	Ein Auswahlfeld, um Datensätze in eine bestimmte Reihenfolge zu sortieren.
	
#####Beispiel PHP
	$yform->setValueField('prio', array("prio","Reihenfolge"));
		
#####Beispiel Pipe
	prio|prio|Reihenfolge|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="prio"]
	



	
		
###radio

#####Definition
	Ein Auswahlfeld, um Datensätze in eine bestimmte Reihenfolge zu sortieren.
	
#####Beispiel PHP
	$yform->setValueField('radio', array("radio","Radio","schlecht=-1,ok=0,gut=1","0"));
		
#####Beispiel Pipe
	radio|radio|Radio|schlecht=-1,ok=0,gut=1|0|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="radio"]


	
	
	
		
###radio_sql

#####Definition
	Ein oder mehrere Auswahlfelder als Radio-Buttons.
	
#####Beispiel PHP
	$yform->setValueField('radio_sql', array("radio_sql","Radio SQL","SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio"));
		
#####Beispiel Pipe
	radio_sql|radio_sql|Radio SQL|SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="radio_sql"]
	
		
	
	
	
		
###select

#####Definition
	Ein Auswahlfeld mit vordefinierten Werten.
	
#####Beispiel PHP
	$yform->setValueField('select', array("select","Select","schlecht=-1,ok=0,gut=1","","0","0"));
		
#####Beispiel Pipe
	select|select|Select|schlecht=-1,ok=0,gut=1||0|0|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="select"]


	
	
	
	
		
###select_sql

#####Definition
	Ein Auswahlfeld mit Werten, die aus einer SQL-Abfrage stammen.
	
#####Beispiel PHP
	$yform->setValueField('select_sql', array("select_sql","Select SQL","SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio","","","0","","0"));
		
#####Beispiel Pipe
	select_sql|select_sql|Select SQL|SELECT id, name FROM rex_yf_table WHERE name = paul ORDER BY prio|||0||0|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="select_sql"]

	
	
	
	
	
	
###submit

#####Definition
	Ein oder mehrere Submit-Buttons zum Absenden des Formulars.
	
#####Beispiel PHP
	$yform->setValueField('submit', array("submit","Submit"));
		
#####Beispiel Pipe
	submit|submit|Submit|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="submit"]


	
	
	
###text

#####Definition
	Input-Feld zur Eingabe eines Textes.
	
#####Beispiel PHP
	$yform->setValueField('text', array("text","Text"));
		
#####Beispiel Pipe
	text|text|Text|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="text"]


	
	
	
	
	
###textarea

#####Definition
	Ein mehrzeiliges Eingabefeld für Text.

#####Beispiel PHP
	$yform->setValueField('textarea', array("textarea","Textarea"));
		
#####Beispiel Pipe
	textarea|textarea|Textarea|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="textarea"]


	
	
	
	
	
###time

#####Definition
	Eine Reihe von Auswahlfeldern, in der die Uhrzeit (Stunden, Minuten, Sekunden) ausgewählt wird.
	
#####Beispiel PHP
	$yform->setValueField('time', array("time","Zeit","","00,15,30,45","HH:ii","","select"));
		
#####Beispiel Pipe
	time|time|Zeit||00,15,30,45|HH:ii||select|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="time"]



	
	
	
	
	
###upload

#####Definition
	Ein Upload-Feld, mit dem eine Datei in die Datenbank oder ein Verzeichnis hochgeladen wird.
	
#####Beispiel PHP
	$yform->setValueField('upload', array("upload","Upload","",".jpg,.gif,.png,.jpeg"));
		
#####Beispiel Pipe
	upload|upload|Upload||.jpg,.gif,.png,.jpeg|

#####Beispiel E-Mail
	REX_YFORM_DATA[field="upload"]


	
	