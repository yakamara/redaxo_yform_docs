# YForm-Modul: Actions

- [Zweck der Aktionen](#zweck-der-aktionen)
- [Aktionen-Klassen](#aktionen-klassen)

	

## Zweck der Aktionen

mit Aktionen definert man, was nach dem Versand des Formulars, mit den Formulardaten passieren soll. zb der Versand einer E-Mail über ein E-Mail-Template oder die Speicherung der Daten in einer Tabelle.


Die Klassen sind hier zu finden

	src/addons/yform/lib/yform/actions/



## Actions-Klassen


###!callback
..

#####Definition
	action|callback|mycallback / myclass::mycallback

#####Beispiel
	
--

###copy_value
kopiert Eingaben von Feld mit Label [label_from] in Feld mit Label [label_to]

#####Definition
	action|copy_value|label_from|label_to
	
#####Beispiel
	hidden|user
	text|name|Name
	action|copy_value|name|user
	
	action|db|rex_warenkorb
	action|html|Daten gespeichert	
--

###createdb
erstellt Datenbank-Tabelle. Formular-Labels werden dabei als Feldnamen in der neue Tabellen gespeichert. Die neuen Tabelle erscheibt dabei **nicht** in der Redaxo-Tabelle-Struktur.

#####Definition
	action|createdb|tblname

	_
#####Beispiel
	text|vorname|Vorname
	text|name|Name
	
	action|createdb|shop_user
--

###db
speichert oder aktualisiert Formulardaten in Tabelle. Dabei werden die Labels und deren Eingaben in die gleichnamigen Tabellenfelder gespeichert.

#####Definition
	action|db|tblname|[where(id=2)/main_where]

#####Beispiel
	text|vorname|Vorname
	text|name|Name
	text|plz|PLZ
	text|ort|Ort

	action|db|rex_warenkorb
	action|html|Daten gespeichert	


###db_query
..

#####Definition
	action|db_query|query|Fehlermeldung

	_
#####Beispiel
	
--

###email
sendet E-Mail mit Betreff und Body an angegebene E-Mail-Adresse. Eingaben aus dem Formular können als Platzhalter im Mailbody verwendet werden. 

#####Definition
	action|email|from@email.de|to@email.de|Mailsubject|Mailbody###name###
	
#####Beispiel
	text|name|Name
	action|email|max@mustermann|min@mustermann.de|Test|Hallo ###name###
--


###encrypt_value
verschlüsselt Eingabe in Feld mit Label

#####Definition
	action|encrypt|label[,label2,label3]|md5|[save_in_this_label]

#####Beispiel
	text|pass|Password
	action|encrypt_value|pass|md5

	action|db|rex_warenkorb
	action|html|Daten gespeichert	
--


###!fulltext_value
..

#####Definition
	action|fulltext_value|label|fulltextlabels with ,

	_
#####Beispiel
	
--


###html
gibt html Code aus

#####Definition
	action|html|[html]

	_
#####Beispiel
	action|html|<b>fett</b>
--




###readtable
liest aus Tabelle aus dem Feld [feldname] mit der Eingabe aus dem Formular-Feld [label] den gefundenen Datensatz. Das gesuchte Tabellen-Feld muss im Formular als Label vorhanden sein. 

#####Definition
	action|readtable|tablename|feldname|label

#####Beispiel
	text|name|Name
	action|readtable|shop_user|fname|name
--


###redirect
	

#####Definition
	action|redirect|Artikel-Id oder Externer Link|request/label|field

#####Beispiel 
	Umleitung auf internen Artikel 32
	action|redirect|32  	
		
--


###showtext
Gibt einen Antworttext zurück, der als Plaintext, HTML oder über Textile ausgegeben werden kann.

#####Definition
	action|showtext|Antworttext|<p>|</p>|0/1/2 (plaintext/html/textile)

	_
#####Beispiel
	action|showtext|Hallo das ist Redaxo|<p>|</p>|0
	action|showtext|Hallo das ist *Redaxo*|||2

#####Ausgabe nach Submit
	<p>Hallo das ist Redaxo</p>	
	<p>Hallo das ist <strong>Redaxo</strong></p>
--



###tpl2email (plugin email)
versendet eine E-Mail über ein yform-E-Mail-Template. Der Parameter **emailtemplate** ist der Key des E-Mail-Templates.

#####Definition
	action|tpl2email|emailtemplate|emaillabel|[email@domain.de]

#####Beispiel
	text|email|E-Mail-Empfänger
	action|tpl2email|emailtemplate|email

* wird keine E-Mail-Adresse angegeben, wird die E-Mail-Adresse bei Fehlern (System/Einstellungen) eingesetzt
* emaillabel = E-Mail-Label, Formular-Element
* wird eine E-Mail-Adresse angegeben, wird die E-Mail des Labels überschrieben

--


###wrapper_value
..

#####Definition
	action|wrapper_value|label|prefix###value###suffix
	
#####Beispiel
	text|telefon|Telefon
	action|wrapper_value|telefon|<a href="tel:+49###value###">###value###</a>
	action|db|rex_warenkorb
	action|html|Daten gespeichert	
--
