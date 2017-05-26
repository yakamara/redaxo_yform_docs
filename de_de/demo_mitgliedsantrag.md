Entwurf

# Tutorial Mitgliedsantrag

In diesem Tutorial geht es darum, ein Formular zu entwerfen, mit dem Besucher einer Website verbindlich und sicher einen Mitgliedsantrag ausfüllen können.

## Voraussetzungen und Anforderungen

*Double-Opt-In*
Damit nicht wildfremde Menschen das Formular ausfüllen, soll eine E-Mail an den Antragssteller gesendet werden, in der sich ein Link zur Bestätigung befindet. Hierzu muss ein zufälliger Validierungs-Code erstellt werden, sodass nicht Fremde die Bestätigung über einen Link vornehmen können.

*Datenschutz*
E-Mails werden noch immer oft unverschlüsselt gesendet. Deshalb ist es notwendig, sensible Daten wie bspw. IBAN, vor dem Versand der Bestätinungs-E-Mail an den Antragssteller zu maskieren. Generell ist empfohlen, dass das Formular nur verschlüsselt (https) übertragen wird.

*Einfache Handhabung*
Das Formular soll, sofern möglich, auf die Autofill-Funktion des Browsers zugreifen können. Hierzu müssen die Feldnamen richtig benannt werden.

*Schutz vor unvollständigen Eingaben*
Das Formular soll erst abgesendet werden können, wenn die Pflichtfelder ordnungsgemäß ausgefüllt wurden. Dazu werden die Formular-Eingaben clientseitig (im Browser, via HTML5) validiert - und zusätzlich serverseitig (via YForm).

Für das Tutorial werden demzufolge benötigt:

* Der Table Manager zum Erstellen der Datenbanktabelle und der Formularfelder 
* Das YForm Formbuilder-Modul, das im Frontend das Formular ausgibt
* Die E-Mail-Templates, um Bestätigungs-Mails an Antragssteller und Betreiber informiert
* Ein Modul, das die Bestätigung des Nutzers entgegen nimmt und den Antrag freischaltet

## Schritt 1: Tabelle anlegen

1. Im Menü auf `YForm > Table Manager` klicken
2. Auf das `+`-Zeichen klicken, um eine neue Tabelle hinzuzufügen. 
   * Im Tutorial wird `rex_yf_member` verwendet.

## Schritt 2: Formular-Felder anlegen

1. Im Menü auf `YForm > Table Manager` klicken
2. An der Tabelle `rex_yf_member` auf `Felder hinzufügen` klicken
3. Die gewünschten Felder hinzufügen:

| Feldtyp | Feldname | Label | Weitere Optionen |
| ------- | -------- |:-----:| ----------------:|
radio|salutation|Anrede|Herr,Frau<br>{"required":"required"}|
text|firstname|Vorname|{"required":"required"}|
text|lastname|Nachname|{"required":"required"}|
text|street|Straße|{"required":"required"}|
text|zip|PLZ|{"required":"required"}|
text|city|Ort|{"required":"required"}|
text|bankname|Kreditinstitut|
text|iban|IBAN|{"required":"required"}|
text|bic|BIC|
text|email|E-Mail-Adresse|{"required":"required","type":"email"}|
index|key|key|email|md5|
hashvalue|token|Token|iban|sha512|/Ru7Vz(%tQ5VV%vkV#VYB=KhaQYAavf/?APtYpe}59ynUTybL\|
datestamp|createdate|Angemeldet am...|mysql||1|
datestamp|updatedate|Aktualisiert am|mysql||0|

** Erläuterungen **

Warum index
Warum hashvalue
Warum token
Warum datestamp
Warum required

> Hinweis: Die meisten Browser erkennen Eingabefelder anhand der Feldnamen und können so einiger Felder vorausfüllen. Beispiel hierfür sind Konventionen wie `firstname` für Vorname, `city` oder `location` für den Ortsnamen, usw.

### Validierungen

Alle required-Felder auch serverseitig validieren.

## Schritt 3: Formular im Frontend einfügen

Der Formular-Code sollte in etwa so aussehen:
```
objparams|form_ytemplate|bootstrap
objparams|form_showformafterupdate|0
objparams|real_field_names|true

radio|salutation|Anrede|Herr,Frau||{"required":"required"}|
text|firstname|Vorname|||{"required":"required"}|
text|lastname|Nachname|||{"required":"required"}|
text|street|Straße|||{"required":"required"}|
text|zip|PLZ|||{"required":"required"}|
text|city|Ort|||{"required":"required"}|
text|bankname|Kreditinstitut|
text|iban|IBAN|||{"required":"required"}|
text|bic|BIC|
text|email|E-Mail-Adresse|||{"required":"required","type":"email"}|
index|key|key|email||md5|
hashvalue|token|Token|iban|sha512|/Ru7Vz(%tQ5VV%vkV#VYB=KhaQYAavf/?APtYpe}59ynUTybL\|
datestamp|createdate|Angemeldet am...|mysql||1|
datestamp|updatedate|Aktualisiert am|mysql||0|

action|db|rex_yf_member|
action|tpl2email|member_confirm|email|
action|tpl2email|member_confirm||betreiber@domain.de
```

*Meldung bei erfolgreichem Versand* 
```
<p>Vielen Dank für Ihre Unterstützung!</p>
<p>Bitte beachten Sie: Sie erhalten in Kürze eine Mail mit einem Bestätigungs-Link. Erst, wenn Sie diesen Link anklicken, wird Ihre Mitgliedschaft verbindlich. Sie erhalten anschließend eine schriftliche Bestätigung.</p>
```

## Schritt 4: E-Mail-Templates anlegen

*E-Mail an den Antragssteller*

```
Hallo REX_YFORM_DATA[field="salutation"] REX_YFORM_DATA[field="firstname"] REX_YFORM_DATA[field="lastname"],

Sie haben auf unserer Website einen Antrag auf Mitgliedschaft ausgefüllt. Bitte bestätigten Sie Ihre Mitgliedschaft mit einem Klick auf folgenden Link:

https://www.domain.de/mitgliedschaft-aktivieren/?key=REX_YFORM_DATA[field="key"]&token=REX_YFORM_DATA[field="token"]

Sie erhalten anschließend eine schriftliche Bestätigung per Post an die von Ihnen angegebene Adresse.

Ihr Vorteil Als Mitglied: Sie erhalten ermäßigten Eintritt zu unseren Veranstaltungen. Bringen Sie dazu Ihren Mitgliedsausweis mit.

Wir bedanken uns sehr für Ihre Unterstützung und freuen uns über Ihren nächsten Besuch!

Anbei eine Kopie Ihrer Daten:
REX_YFORM_DATA[field="salutation"] REX_YFORM_DATA[field="firstname"] REX_YFORM_DATA[field="lastname"]
REX_YFORM_DATA[field="street"]
REX_YFORM_DATA[field="zip"] REX_YFORM_DATA[field="city"]

Ihre E-Mail-Adresse:
REX_YFORM_DATA[field="email"]

Bankdaten:
Name der Bank: REX_YFORM_DATA[field="bankname"]
IBAN [aus Datenschutzgründen ausgeblendet]
BIC: REX_YFORM_DATA[field="bic"]

Die Zahlungsweise erfolgt per Abbuchung, der Antrag gilt gleichzeitig als Einzugsermächtigung.
```

*E-Mail an den Betreiber*

```
Hallo Team des %Name des Betreibers%,

ein neuer Antrag auf Mitgliedschaft wurde ausgefüllt:

REX_YFORM_DATA[field="salutation"]
REX_YFORM_DATA[field="firstname"]
REX_YFORM_DATA[field="lastname"]
REX_YFORM_DATA[field="street"]
REX_YFORM_DATA[field="zip"]
REX_YFORM_DATA[field="city"]
REX_YFORM_DATA[field="email"]
REX_YFORM_DATA[field="bankname"]
REX_YFORM_DATA[field="iban"]
REX_YFORM_DATA[field="bic"]

Der Status der bestätigten Aktivierung kann eingesehen werden unter:
https://www.domain.de/redaxo/ > Tabellen > Mitglieder
```
## Schritt 5: Aktivierungs-Modul einrichten

```
    <div class="modul-wrapper">       
        <?php
$key = rex_get('key', 'string', 0);
$token = rex_get('token', 'string', 0);

if($key && $token) {
    $member = current(rex_sql::factory()->setDebug(0)->getArray('SELECT * FROM rex_yf_member WHERE key = ? AND token = ? AND status = 0 LIMIT 1', array($key, $token)));

    if(count($member)) {
        if($member['token'] == $token) {
            rex_sql::factory()->setDebug(0)->setQuery('UPDATE rex_yf_member SET token = NULL, key = NULL, status = 1, updatedate = NOW() WHERE key = ?', array($key));

        ?>
        <div class="header-message"><p>Ihre Mitgliedschaft wurde bestätigt. Vielen Dank!</p></div>
        <? 
        } else {
        ?>
        <div class="header-message warning"><p>Ihre Mitgliedschaft wurde bereits bestätigt.</p></div>
        <?
        }
    } else {
        ?>
        <div class="header-message warning"><p>Ein Antrag zur Mitgliedschaft liegt uns nicht vor.</p></div>
        <?
    }
} else {
        ?>
        <div class="header-message warning"><p>Ihre Mitgliedschaft wurde nicht beantragt oder wurde bereits aktiviert.</p></div>
        <?
}
        ?>
    </div>
```
