# Schutz vor Spam

Von Haus aus liefert `YForm` für den Formbuilder zwei Feldtypen, um sicherzustellen, dass das Formular von einem echten Website-Besucher ausgegeben wurde und nicht von einem Spam-Bot. Es gibt jedoch noch weitere Tricks, um Bots zu erkennen und Spam zu vermeiden.

> Hinweis: Ein Captcha ist kein Sicherheitsmerkmal. Für eine sichere Übermittlung der Formular-Daten ist ein SSL-Zertifikat absolute Pflicht. Wenn die eingegebenen Daten per E-Mail versendet werden, werden diese Daten unter Umständen trotz SSL-Zertifikat unverschlüsselt übertragen.

## Captcha 

Siehe [YForm Formbuilder Values](yform_modul_values.md#captcha)

**Nachteile**

* Nicht barrierefrei
* Zusätzlicher Aufwand für den Nutzer

## Captcha Calc

Siehe [YForm Formbuilder Values](yform_modul_values.md#captcha_calc)

**Nachteile**

* Zusätzlicher Aufwand für den Nutzer

## via Zeitstempel 

**Vorgehensweise**

1. Feld vom Typ PHP anlegen: `php|validate_timer|Spamschutz|<?php echo '<input name="validate_timer" type="hidden" value="'.microtime(true).'" />' ?>|`
2. Validierung vom Typ custom_function anlegen: `validate|customfunction|validate_timer|yform_validate_timer|5|Spambots haben keine Chance|`
3. Nachfolgende Funktion hinterlegen, die via `custom_function` aufgerufen wird.

```
function xform_validate_timer($label,$microtime,$seconds)
    {
        if (($microtime + $seconds) > microtime(true)) {
            return true;
        } else {
            return false;
        }
    }
```
    
> Tipp: Die Funktion kann bspw. im projects-Addon innerhalb der boot.php hinterlegt werden.
    
**Funktionsweise**

Spambots sind kleine ungeduldige Biestlinge. Sie füllen das Formular in der Regel im Bruchteil einer Sekunde aus und haben schließlich keine Zeit zu verlieren, um den nächsten Website-Betreiber in den Wahnsinn zu betreiben.

Über PHP wird ein zusätzliches, verstecktes Feld namens `validate_timer` erstellt und bei der Ausgabe des Formulars mit dem Zeitstempel ausgefüllt. Ein Nutzer wird i.d.R. einige Sekunden brauchen, um das Formular auszufüllen. 

Dieser Zeitstempel wird beim Absenden des Formulars in der Funktion `yform_validate_timer` verglichen. Wenn der vorgegebene Zeitwert unterschritten wird (in diesem Beispiel sind es `5` Sekunden), dann ist davon auszugehen, dass das Formular von einem Spambot ausgefüllt wurde, weshalb die Validierung fehlschlägt und das Absenden unterbunden wird.

**Nachteile**

* keinen

## via hidden E-Mail-Field

**Vorgehensweise**

1. Feld vom Typ `email` anlegen, als Label `email` verwenden
2. weiteres Feld vom Typ `email` anlegen, als Label bspw. `xmail` verwenden
3. Validierung vom Typ `compare` anlegen, das Feld darf nicht `>0` sein.
4. Eingabefeld `email` via CSS verstecken.

**Funktionsweise**

Sobald Spambots das input-Feld namens `email` als Eingabe-Feld erkennen, werden sie es ausfüllen. Nur ein echter Nutzer wird das Feld nicht sehen und damit auch nicht ausfüllen. Dadurch kann man feststellen, ob ein Bot oder ein Mensch das Formular ausgefüllt hat. Für den Bot wird damit das Absenden blockiert.

**Nachteil**

* Unter Umständen wird das versteckte Feld von Browsern vorausgefüllt. Lösung: Autocomplete abschalten, indem das Eingabe-Feld via JSON das Attribut `{"autocomplete":"off"}` bekommt.
* Das korrekte E-Mail-Feld wird nicht mehr vom Browser vorausgefüllt.
* Die Lösung ist nur bedingt barrierefrei.
