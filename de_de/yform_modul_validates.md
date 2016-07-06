# YForm-Modul: Validierung

- [Zweck der Validierungen](#zweck-der-validierungen)
- [Validierungs-Klassen](#allgemeine-objparams)

	

## Zweck der Validierungen

mit diesen Feldklassen lassen sich Feldklassen-Values überprüfen und eine entsprechende Warnung ausgeben.
Diese Feldklassen werden wie Values und Aktionen im Formbuilder im Feld "Felddefinitonen" eingetragen.

Dabei wird von einer Feldklasse Values das Label definiert, welche validiert werden soll.

Die Klassen sind hier zu finden

	src/addons/yform/lib/yform/validate/


Beispiele (Schreibweisen) gibt es für **yForm Formbuilder** und **PHP**

Die PHP-Beispiele können in diesem Formular getestet/eingesetzt werden:

	<?php
	$yform = new rex_yform();
	$yform->setObjectparams('form_action', rex_getUrl(REX_ARTICLE_ID,REX_CLANG_ID));

	$yform->setValueField('text', array("wert1","Wert 1"));
	$yform->setValidateField('empty', array("wert1","Bitte geben Sie einen Namen an!"));
	
	echo $yform->getForm();
	?>



## Validierungs-Klassen

###compare
vergleicht zwei Felder mit Hilfe Operatoren

#####Definition
	validate|compare|label1|label2|[!=,<,>,==,>=,<=]|warning_message|

	_
#####Beispiel Formbuilder
	text|wert1|Wert 1|
	text|wert2|Wert 2|
	validate|compare|wert1|wert2|!=|Die beiden Felder haben unterschiedliche Werte|

#####Beispiel PHP
	$yform->setValueField('text', array("wert1","Wert 1"));
	$yform->setValueField('text', array("wert2","Wert 2"));
	$yform->setValidateField('compare', array("wert1","wert2","!=", "Die Felder haben unterschiedliche Werte"));
	

* [mögliche Vergleichs-Operatoren] !=, <, >, ==, >= <=

	
	
	
	
	
	
	
-
###compare_value
vergleicht Feld mit angegebenen Wert mit Hilfe Operatoren

#####Definition
	validate|compare_value|label|value|[!=,<,>,==,>=,<=]|warning_message
	
#####Beispiel Formbuilder
	text|wert1|Wert 1|
	validate|compare_value|wert1|2|<|Der Wert ist kleiner als 2!|

#####Beispiel PHP
	$yform->setValueField('text', array("wert1","Wert 1"));
	$yform->setValidateField('compare_value', array("wert1","wert2","<", "Der Wert ist kleiner als 2!"));
	

* [mögliche Vergleichs-Operatoren] !=, <, >, ==, >= <=

	
	
	
	
	
	
	
-
###customfunction
es können eigenen Überprüfungen via Funktion oder Klasse/Methode durchgeführt werden

#####Definition
	validate|customfunction|label|[!]function/class::method|weitere_parameter|warning_message
		
#####Beispiel Formbuilder

#####Beispiel PHP

	
-
###email
überprüft ob Feld eine E-Mail-Adresse ist. Ein leere Eingabe würde dabei als korrekt bewertet werden!

#####Definition
	validate|email|emaillabel|warning_message
	
#####Beispiel Formbuilder
	
	text|email|E-Mail|
	validate|email|email|Das Feld enthält keine korrekte E-Mail-Adresse!

#####Beispiel PHP
	$yform->setValueField('text', array("email","E-Mail"));
	$yform->setValidateField('email', array("email", "Das Feld enthält keine korrekte E-Mail-Adresse!"));

	
	
	
	
	
	
	
-
###empty
überprüft das Feld mit dem angegebenen Label, ob ein Wert eingetragen wurde und gibt ein Meldung aus

#####Definition

	validate|empty|label|Meldung

#####Beispiel Formbuilder

	text|name|Nachname|
	validate|empty|name|Bitte geben Sie einen Namen an!

#####Beispiel PHP

	$yform->setValueField('text', array("name","Nachname"));
	$yform->setValidateField('empty', array("name","Bitte geben Sie einen Namen an!"));

	
	
	
	
	
	
	
-
###existintable (wird nicht mehr fortgeführt)
 
#####Definition
	validate|existintable|label,label2|tablename|feldname,feldname2|warning_message
 
#####Beispiel Formbuilder
 	
 
#####Beispiel PHP
 
-
####intformto
überprüft ob **Wert** der Eingabe größer oder kleiner als die definierten Werte sind
#####Definition
	validate|intfromto|label|from|to|warning_message
	
#####Beispiel Formbuilder
	text|wert|Wert
	validate|intfromto|wert|2|4|Der Wert ist kleiner als 2 und größer als 4! 

#####Beispiel PHP
	$yform->setValueField('text', array("wert","Wert"));
	$yform->setValidateField('intfromto', array("wert","2", "4", "Der Wert ist kleiner als 2 und größer als 4! "));

	
	
	
	
	
	
	
-
###labelexist
überprüft, ob ein oder mehrere Felder weniger als den Minimal-Wert oder mehr als den Maximal-Wert enthalten
#####Definition

	validate|labelexist|label,label2,label3|[minlabels]|[maximallabels]|Fehlermeldung
	
#####Beispiel Formbuilder
	text|vorname|Vorname|
	text|name|Nachname|
	text|email|E-Mail|
	text|tel|Telefon|
	
	validate|labelexist|vorname,name,tel|1|2|Fehlermeldung


#####Beispiel PHP
	$yform->setValueField('text', array("vorname","Vorname"));
	$yform->setValueField('text', array("name","Nachname"));
	$yform->setValueField('text', array("email","E-Mail"));
	$yform->setValueField('text', array("tel","Telefon"));
	
	$yform->setValidateField('labelexist', array("vorname, name, tel","1", "2", "Fehlermeldung"));


* [minlabels] optinal, default 1
* [maximallabels] optinal, default 1000

	
	
	
	
	
	
-	
###preg_match
überprüft die Eingabe auf die hinterlegten Regeln
#####Definition
	validate|preg_match|label|/[a-z]/i|warning_message
	
#####Beispiel Formbuilder
	text|eingabe|Eingabe
	validate|preg_match|eingabe|/[a-z]+/|Es dürfen nur ein oder mehrere kleingeschriebene 	Buchstaben eingegeben werden!


#####Beispiel PHP
	$yform->setValueField('text', array("eingabe","Eingabe"));
	$yform->setValidateField('preg_match', array("eingabe","/[a-z]+/", "Es dürfen nur ein oder mehrere kleingeschriebene 	Buchstaben eingegeben werden!"));

	
	
	
	
	
	
-	
###size
überprüft die Eingabe eines Feldes auf die angegebene Zeichenlänge
#####Definition
	validate|size|plz|[size]|warning_message
	
#####Beispiel Formbuilder
	text|plz|PLZ
	validate|size|plz|5|Die Eingabe hat nicht die korrekte Zeichenlänge!

#####Beispiel PHP
	$yform->setValueField('text', array("plz","PLZ"));
	$yform->setValidateField('size', array("plz","5", "Die Eingabe hat nicht die korrekte Zeichenlänge!"));


* [size] Zahl, Zeichenlänge

	
	
	
	
	
	
-	
###size_range
überprüft die Eingabe eines Feldes auf die angegebene **Zeichenlänge**, die zwischen dem Minimal- und Maximalwert liegt
#####Definition
	validate|size_range|label|[minsize]|[maxsize]|Fehlermeldung
	
#####Beispiel Formbuilder
	text|summe|Summe
	validate|size_range|summe|3|10|Die Eingabe hat nicht die korrekte Zeichenlänge (mind. 3, max 10 Zeichen)!

#####Beispiel PHP
	$yform->setValueField('text', array("summe","Summe"));
	$yform->setValidateField('size_range', array("summe", "3", "10", "Die Eingabe hat nicht die korrekte Zeichenlänge (mind. 3, max 10 Zeichen)!"));

	
	
	
	
	
	
-	
###type
überprüft den Typ der Eingabe
#####Definition
	validate|type|label|[int,float,numeric,string,email,url,date,datetime]|Fehlermeldung|[1= Feld darf auch leer sein]	
	
#####Beispiel Formbuilder
	text|wert|Wert
	validate|type|wert|numeric|Die Eingabe ist keine Nummer!

#####Beispiel PHP
	$yform->setValueField('text', array("wert","Wert"));
	$yform->setValidateField('type', array("wert", "numeric", "Die Eingabe ist keine Nummer!"));

	
	
	
	
	
	
-	
###unique
überprüft, ob ein Datensatz mit einem Feld-Wert, in einer Tabelle bereits vorhanden ist
#####Definition
	validate|unique|dbfeldname[,dbfeldname2]|Dieser Name existiert schon|[table]
	
#####Beispiel Formbuilder
	text|email|E-Mail|
	validate|unique|email|Ein User mit dieser E-Mail-Adresse existiert schon!|rex_user

#####Beispiel PHP
	$yform->setValueField('text', array("email","E-Mail"));
	$yform->setValidateField('unique', array("email", "Ein User mit dieser E-Mail-Adresse existiert schon!|rex_user"));

	


* [table] wenn Tabellenname angegeben ist, wird der Tabellenname der im Formbuilder ausgewählt wurde übernommen.
* dbfeldname: es können mehrere Feldname überprüft werden (kommagetrennt)