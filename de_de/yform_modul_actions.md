# YForm-Modul: Actions

- [Zweck der Aktionen](#zweck-der-aktionen)
- [Aktionen-Klassen](#aktionen-klassen)

	

## Zweck der Aktionen

mit Aktionen definert man, was nach dem Versenden mit den Formulardaten passieren soll.
Versand einer E-Mail über E-Mail-Templates oder Speicherung der Daten in einer Tabelle.

Die Klassen sind hier zu finden

	src/addons/yform/lib/yform/actions/



## Actions-Klassen

###abstrakt
..

#####Definition
	

	_
#####Beispiel
	
--

###callback
..

#####Definition
	

	_
#####Beispiel
	
--

###copy_value
..

#####Definition
	

	_
#####Beispiel
	
--

###createdb
..

#####Definition
	

	_
#####Beispiel
	
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
	

	_
#####Beispiel
	
--

###email
..

#####Definition
	

	_
#####Beispiel
	
--

###encrypt_value
..

#####Definition
	

	_
#####Beispiel
	
--

###fulltext_value
..

#####Definition
	

	_
#####Beispiel
	
--

###html
..

#####Definition
	

	_
#####Beispiel
	
--

###readtable
..

#####Definition
	

	_
#####Beispiel
	
--

###redirect
..

#####Definition
	

	_
#####Beispiel
	
--

###showtext
..

#####Definition
	

	_
#####Beispiel
	
--

###wrapper_value
..

#####Definition
	

	_
#####Beispiel
	
--
