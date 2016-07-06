# YForm-Modul: Actions

- [Zweck der Aktionen](#zweck-der-aktionen)
- [Aktionen-Klassen](#aktionen-klassen)

	

## Zweck der Aktionen

mit Aktionen definert man, was nach dem Versand des Formulars, mit den Formulardaten passieren soll. zb der Versand einer E-Mail über ein E-Mail-Template oder die Speicherung der Daten in einer Tabelle.


Die Klassen sind hier zu finden

	src/addons/yform/lib/yform/actions/


Beispiele (Schreibweisen) gibt es für **yForm Formbuilder** und **PHP**

Die PHP-Beispiele können in diesem Formular getestet/eingesetzt werden:

	<?php
	$yform = new rex_yform();
	$yform->setObjectparams('form_action', rex_getUrl(REX_ARTICLE_ID,REX_CLANG_ID));
	
	$yform->setValueField('text', array("wert1","Wert 1"));
	$yform->setValidateField('empty', array("wert1","Bitte geben Sie einen Namen an!"));
	
	echo $yform->getForm();
	?>
	
	
	

## Actions-Klassen


###callback
ruf eine Funktion oder Klasse auf

#####Definition
	action|callback|mycallback / myclass::mycallback

#####Beispiel Formbuilder
	
#####Beispiel PHP





-

###copy_value
kopiert Eingaben von Feld mit Label [label_from] in Feld mit Label [label_to]

#####Definition
	action|copy_value|label_from|label_to
	
#####Beispiel Formbuilder
	hidden|user
	text|name|Name
	action|copy_value|name|user
	
	action|db|rex_warenkorb
	action|html|Daten gespeichert	
	
	
#####Beispiel PHP	
	$yform->setValueField('hidden', array("user"));
	$yform->setValueField('text', array("name","Name"));
	$yform->setActionField('copy_value', array("name","user"));
	
	$yform->setActionField('db', array("rex_warenkorb"));
	$yform->setActionField('html', array("Daten gespeichert"));






-
###createdb
erstellt Datenbank-Tabelle. Formular-Labels werden dabei als Feldnamen in der neue Tabellen gespeichert. Die neuen Tabelle erscheibt dabei **nicht** in der Redaxo-Tabelle-Struktur.

#####Definition
	action|createdb|tblname

	_
#####Beispiel Formbuilder
	text|vorname|Vorname
	text|name|Name
	
	action|createdb|shop_user
	
#####Beispiel PHP
	$yform->setValueField('text', array("vorname","Vorname"));
	$yform->setValueField('text', array("name","Name"));

	$yform->setActionField('createdb', array("shop_user"));






-
###db
speichert oder aktualisiert Formulardaten in Tabelle. Dabei werden die Labels und deren Eingaben in die gleichnamigen Tabellenfelder gespeichert.

#####Definition
	action|db|tblname|[where(id=2)/main_where]

#####Beispiel Formbuilder
	text|vorname|Vorname
	text|name|Name
	text|plz|PLZ
	text|ort|Ort

	action|db|rex_warenkorb
	action|html|Daten gespeichert	

#####Beispiel PHP
	$yform->setValueField('text', array("vorname","Vorname"));
	$yform->setValueField('text', array("name","Name"));
	$yform->setValueField('text', array("plz","PLZ"));
	$yform->setValueField('text', array("ort","Ort"));

	$yform->setActionField('db', array("rex_warenkorb"));
	$yform->setActionField('html', array("Daten gespeichert"));






-
###db_query
führt einen Query aus

#####Definition
	action|db_query|query|Fehlermeldung

	_
#####Beispiel Formbuilder
	action|db_query|query|Fehlermeldung
	
#####Beispiel PHP
	$yform->setActionField('db_query', array("query", "Fehlermeldung"));





-
###email
sendet E-Mail mit Betreff und Body an angegebene E-Mail-Adresse. Eingaben aus dem Formular können als Platzhalter im Mailbody verwendet werden. 

#####Definition
	action|email|from@email.de|to@email.de|Mailsubject|Mailbody###name###
	
#####Beispiel Formbuilder
	text|name|Name
	action|email|from@mustermann|to@mustermann.de|Test|Hallo ###name###
	

#####Beispiel PHP
	$yform->setValueField('text', array("name","Name"));
	$yform->setActionField('email', array("from@mustermann", "to@mustermann.de", "Test", "Hallo ###name###"));






-
###!encrypt_value (wird nicht mehr fortgeführt)
verschlüsselt Eingabe in Feld mit Label

#####Definition
	action|encrypt|label[,label2,label3]|md5|[save_in_this_label]

#####Beispiel Formbuilder
	text|pass|Password
	action|encrypt_value|pass|md5

	action|db|rex_warenkorb
	action|html|Daten gespeichert	
	
#####Beispiel PHP
	$yform->setValueField('text', array("pass", "Password"));
	$yform->setActionField('encrypt_value', array("pass", "md5"));	
	$yform->setActionField('db', array("rex_warenkorb"));
	$yform->setActionField('html', array("Daten gespeichert"));



-
###!fulltext_value (wird nicht mehr fortgeführt)
..

#####Definition
	action|fulltext_value|label|fulltextlabels with ,

	_
#####Beispiel Formbuilder
	
#####Beispiel PHP





-
###html
gibt html Code aus

#####Definition
	action|html|[html]

	_
#####Beispiel Formbuilder
	action|html|<b>fett</b>
	
#####Beispiel PHP
	$yform->setActionField('html', array("<b>fett</b>"));





-
###readtable
liest aus Tabelle aus dem Feld [feldname] mit der Eingabe aus dem Formular-Feld [label] den gefundenen Datensatz. Das gesuchte Tabellen-Feld muss im Formular als Label vorhanden sein. 

#####Definition
	action|readtable|tablename|feldname|label

#####Beispiel Formbuilder
	text|name|Name
	action|readtable|shop_user|fname|name
	
#####Beispiel PHP
	$yform->setValueField('text', array("name","Name"));
	$yform->setActionField('readtable', array("shop_user", "fname", "name"));




-
###redirect
	

#####Definition
	action|redirect|Artikel-Id oder Externer Link|request/label|field

#####Beispiel Formbuilder
	//Umleitung auf internen Artikel 32
	action|redirect|32  	
	
#####Beispiel PHP
	$yform->setActionField('redirect', array("32"));



-
###showtext
Gibt einen Antworttext zurück, der als Plaintext, HTML oder über Textile ausgegeben werden kann.

#####Definition
	action|showtext|Antworttext|<p>|</p>|0/1/2 (plaintext/html/textile)

	_
#####Beispiel Formbuilder
	action|showtext|Hallo das ist Redaxo|<p>|</p>|0
	action|showtext|Hallo das ist *Redaxo*|||2
	
	
#####Beispiel PHP
	$yform->setActionField('showtext', array("Hallo das ist Redaxo", "<p>", "</p>", "0"));
	$yform->setActionField('showtext', array("Hallo das ist *Redaxo*", "", "", "2"));


#####Ausgabe nach Submit
	<p>Hallo das ist Redaxo</p>	
	<p>Hallo das ist <strong>Redaxo</strong></p>
	






-
###tpl2email (plugin email)
versendet eine E-Mail über ein yform-E-Mail-Template. Der Parameter **emailtemplate** ist der Key des E-Mail-Templates.

#####Definition
	action|tpl2email|emailtemplate|emaillabel|[email@domain.de]

#####Beispiel Formbuilder
	text|email|E-Mail-Empfänger
	action|tpl2email|emailtemplate|email

#####Beispiel PHP
	$yform->setValueField('text', array("email","E-Mail-Empfänger"));	$yform->setActionField('tpl2email', array("emailtemplate", "email"));



* wird keine E-Mail-Adresse angegeben, wird die E-Mail-Adresse bei Fehlern (System/Einstellungen) eingesetzt
* emaillabel = E-Mail-Label, Formular-Element
* wird eine E-Mail-Adresse angegeben, wird die E-Mail des Labels überschrieben
	






-
###!wrapper_value (wird nicht mehr fortgeführt)
..

#####Definition
	action|wrapper_value|label|prefix###value###suffix
	
#####Beispiel Formbuilder
	text|telefon|Telefon
	action|wrapper_value|telefon|<a href="tel:+49###value###">###value###</a>
	action|db|rex_warenkorb
	action|html|Daten gespeichert	

#####Beispiel PHP
	$yform->setValueField('text', array("telefon", "Telefon"));
	$yform->setActionField('wrapper_value', array("telefon", "<a href="tel:+49###value###">###value###</a>"));
	$yform->setActionField('db', array("rex_warenkorb"));
	$yform->setActionField('html', array("Daten gespeichert"));






--
