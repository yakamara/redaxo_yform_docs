# E-Mail-Templates erstellen

- [Zweck der E-Mail-Templates](#zweck-der-email-templates)
- [Handhabung](#handhabung)

	
	
## Zweck der E-Mail-Templates

Will man eine E-Mail aus einem yForm-Formular versenden, kann man mit Hilfe eines E-Mail-Templates, diese E-Mails gestalten und mit Platzhaltern aus dem Formular versehen.

Über die E-Mail-Template-Verwaltung kann ein Template angelegt werden. Dabei muss zuerst ein Key erstellt werden, sowie Absender und der Ansender-E-Mail-Name. 

Danach folgen die Eingaben für den E-Mail-Body, in Plain und HTML.




## Handhabung

Über die Aktion **tpl2email** kann eine E-Mail über den angebenen **Key** eines E-Mail-Templates gesendet werden. Über das Formular können zb die Werte der beiden Eingabefelder des Formular über das E-Mail-Template ausgeben werden.


#####Beispiel Formbuilder

	text|vorname|Vorname|
	text|name|Name|
	text|email|E-Mail-Adresse|

	validate|email|email|Das Feld enthält keine korrekte E-Mail-Adresse!
	validate|empty|email|Das Feld enthält keine korrekte E-Mail-Adresse!
	
	action|tpl2email|testtemplate|email


#####E-Mail-Template-Key

	testtemplate


#####Beispiel E-Mail-Template Body
	
	Hallo,
	REX_YFORM_DATA[field="vorname"] REX_YFORM_DATA[field="name"]
	
#####Beispiel E-Mail-Template Body (Html)
	
	Hallo,<br />
	REX_YFORM_DATA[field="vorname"] REX_YFORM_DATA[field="name"]
	
	
	
Es kann auch PHP-Code intergriert werden, um zb Formular-Eingabe zu prüfen und die Ausgabe in dem E-Mail zu verändern.
	
	
	Hallo,<br />
	<?php 
	if ("REX_YFORM_DATA[field="anrede"]" == "w") echo "Frau";
	else echo "Herr";
	?> REX_YFORM_DATA[field="vorname"] REX_YFORM_DATA[field="name"]
	
	

Die Action **tpl2email** kann auch mehrfach im Formular eingesetzt werden. So könnten E-Mails mit unterschiedlichen Templates versendet werden.





	
	
