# YForm-Modul: YForm erweitern

YForm lässt sich an verschiedenen Stellen erweitern - durch eigene Feldtypen, Templates und mittels Extension Points.

## eigene Values, Validates und Actions verwenden

Values, Validates und Actions werden von YForm automatishc aufgenommen. Dupliziere dazu bspw. eine Validierung aus `/redaxo/src/addons/yform/lib/yform/validate` kopieren, anpassen und unter `/redaxo/src/addons/project/lib/` ablegen.

> **Tipp:** Das Theme-Addon für REDAXO bringt bereits eine Struktur mit, in der eigene YForm-Erweiterungen abgelegt werden können.

## ein eigenes Template / Framework für Formularcode verwenden

Standardmäßig werden Formularcodes von YForm mit Bootstrap-3-Syntax ausgegeben. Mit dem Parameter `form_ytemplate` lassen sich eigene Templates laden, die das Template komplett, oder auch teilweise überschreiben.

Dazu bspw. in die boot.php des `project`-Addons folgende Zeile aufnehmen:

```php
rex_yform::addTemplatePath($this->getPath('ytemplates'));
```

und anschließend die gewünschten Ausgabe-Templates von `/redaxo/src/addons/yform/ytemplates/bootstrap/` nach `/redaxo/src/addons/project/ytemplates/dein_template/` kopieren und anpassen.

Zu guter Letzt über den Parameter `form_ytemplate` das zusätzliche Template für die Ausgabe wählen.

**Pipe-Schreibweise**

```text
objparam|form_ytemplate|dein_template,bootstrap
```

> **Tipp:** Es genügt, einzelne Template-Dateien abzuändern und ggf. zu überschreiben - alle Template-Dateien, die nicht in `dein_template` abgelegt sind, werden automatisch von `bootstrap` überschrieben.

## Extension Points in YForm

In YForm gibt es verschiedene Extension Points, wie z.B. `YFORM_DATA_LIST_SQL`, der die Darstellung der Tabelle und der Datensätze im Table Manager beeinflusst. Hilf mit, diese Liste zu vervollständigen und werde Teil des Doku-Teams!

### Die E-Mail-Adresse in der Table-Manager-Übersicht verlinken

Ein Trick von @steri-rex unter https://github.com/yakamara/redaxo_yform_docs/issues/117

In die boot.php vom `project`-Addon folgenden Code mit aufnehmen, um am Beispiel des `ycom`-Addons die E-Mail-Adresse zu verlinken. Es muss ein Feld `email` in der Tabelle existieren.

```php
function format_email($ep)
{
return '<a href="mailto:###email###">###email###</a>'; // email ist der Platzhalter für den VALUE von Spalte email
}

rex_extension::register('YFORM_DATA_LIST','my_rex_list_tweaks');

function my_rex_list_tweaks($ep)

{
 $list = $ep->getSubject();
//if ($ep->getParam('table')->getTableName() == 'rex_ycom_user') { // optional wenn nur bestimmte Tabelle verändert werden soll
 $list->setColumnFormat('email','custom','format_email'); // email ist die Spalte welche editiert werden soll
//}

}
```