# RESTful API: Einführung

> ## Inhalt
> - [Erste Schritte](#erste-schritte)
> - [Konfiguration/Endpoints](#config)
>   - [Route](#config-route)
> - [Nutzung eines Endpoints](#use)
>   - [GET / Datensätze laden](#use-get)
>   - [POST](#use-post)
>   - [DELETE](#use-delete)
> - [Authentifizierung](#auth)

<a name="erste schritte"></a>
## Erste Schritte

Mit dem REST-Plugin lässt sich eine Schnittstelle aktivieren, mit der man YForm Tabellen von außen abrufen, verändern und löschen kann. Dabei wird auf die REST API gesetzt.
Die Klasse muss zunächst registriert werden siehe [YOrm](yorm.md), damit auf diese mit REST zugegriffen werden kann. Alle Übergaben und Rückgabewerte werden als JSON übertragen.

> Hinweis: Die Tabellem müssen mit YForm verwaltbar sein, da diese Felder automatisch genutzt werden.


<a name="config"></a>
## Konfiguration / Endpoints

Die Zugriff über REST muss für jeden Endpoint einzeln definiert werden. D.h. man muss für jede Tabelle und für unterschiedliche Nutzungszenarien diese fest definieren.

Die Standardroute der REST API ist auf "/rest" gesetzt, d.h. hierunter können eigene Routen definiert werden. 

Die Konfiguration wird über PHP festgelegt und sollte im project-AddOn in der boot.php abgelegt werden. Kann aber auch woanders abgelegt werden, solange diese während der Initialisierung aufgerufen wird.


Hier ein Beispiel, um YCom-User über die REST API zu verwalten:


```

// diese Zeile ist normalerweise nötig. Dieses Bespiel nutzt aber eine YCom-Tabelle, die bereits über das AddOn registriert ist.
#rex_yform_manager_dataset::setModelClass('rex_ycom_user', rex_ycom_user::class);


// Konfiguration des REST Endpoints.
$route = new \rex_yform_rest_route(
    [
        'path' => '/v1/user/',
        'auth' => \rex_yform_rest_auth_token::checkToken(),
        'type' => \rex_ycom_user::class,
        'query' => \rex_ycom_user::query(),
        'get' => [
            'fields' => [
                'rex_ycom_user' => [
                    'id',
                    'login',
                    'email',
                    'name'
                 ],
                 'rex_ycom_group' => [
                    'id',
                    'name'
                 ]
            ]
        ],
        'post' => [],
        'delete' => [],
    ]
);

// Einbinden der Konfiguration
\rex_yform_rest::addRoute($route);
```

Dieses Beispiel führt dazu, dass



<a name="config-route"></a>
### Route-Konfiguration

`path`
muss angegeben werden und bestimmt mit dem $prePath den Endpoint. In diesem Fall wird dann daraus: `/rest/v1/user`

`auth`
ist optional und kann komplett weggelassen werden, wenn man keine Authentifizerung für einen Endpoint haben möchte. Erlaubt sind callbacks und Funktionsnamen.

Beispiele

* **\rex_yform_rest_auth_token::checkToken()** für die interne Authentifizierung mit Token
* **function() { return (date("d") == 1) ? true : false }**
* **"MeineFunktion"**

Wenn man keine Authentifizierung einträgt kann jeder diese Daten entsprechend der weiteren Konfiguration nutzen. Sollte man nur bei Tabellen wie PLZ oder ähnlich offensichtlich freien Daten machen.


`table`
hier wird die entsprechend Tabelle übergeben, die in YOrm definiert ist.

Beispiel

* **\rex_ycom_user::table()**

`get`

`post`

`delete`

<a name="use"></a>
## Nutzung eines Endpoints

URL (z.B. https://domain/rest/v1/user)
In den Beispielen wird davon ausgegangen, dass es keine Authentifizierung gibt

* Fehler und Statusmeldeungen

<a name="use-get"></a>
### GET

* Filter
* Felder

<a name="use-post"></a>
### POST

* Anlegen von Datensätzen
* Update von Datensätzen
* Validierung

<a name="use-delete"></a>
### DELETE

* Filter
* Nach ID

<a name="auth"></a>
## Authentifizierung

### Standardauthentifizierung

Wenn im Model folgende Authentifizerung angegeben wurde: `\rex_yform_rest_auth_token::checkToken()` ist das die Standardauthentifizierung mit Tokens aus der YForm:Rest:Tokenverwaltung.

Ein hier erstellter Token wird entsprechend überprüft und muss im Header übergeben werden. `token=###meintoken###` Nur aktive Tokens funktionieren.
