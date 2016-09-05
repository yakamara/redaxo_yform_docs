# Yorm ORM

- [Arbeiten ohne eigene Modal class](#ohne-modal-class)
- [Eigene Modal class verwenden](#eigene-modal-class)
- [Methoden](#methoden)
    
<a name="ohne-modal-class"></a>
## Arbeiten ohne eigene Modal class

Hole alle Daten der Tabelle `rex_my_table`

```
$items = rex_yform_manager_table::get('rex_my_table')->query()->find();
```



<a name="eigene-modal-class"></a>
## Eigene Modal class verwenden

### Klasse erstellen

Zunächst wird eine Klasse erstellt und in das `project` AddOn im Ordner `lib` abgelegt
```
<?php
class MyTable extends \rex_yform_manager_dataset
{
}
```

### Klasse registrieren
Jetzt muss die erstellte Klasse noch registiert werden. Dazu öffnet man die Datei `boot.php` des `project` AddOns und fügt nachfolgenden Code ein

```
rex_yform_manager_dataset::setModelClass('rex_my_table', MyTable::class);
```

Nun kann man alle Daten wie folgt holen

```
$items = MyTable::query()->find();
```


<a name="methoden"></a>
## Methoden (unvollständig)

- Alias
    - alias
    - getTableAlias
- count
- exists
- find
- findId
- findIds
- findOne
- get
- Group By
    - groupBy
    - groupByRaw
    - resetGroupBy
- Join
    - joinRaw
    - joinRelation
    - joinType
    - joinTypeRelation
    - leftJoin
    - leftJoinRelation
    - resetJoins
- Limit
    - limit
    - resetLimit
- Order By
    - orderBy
    - orderByRaw
    - resetOrderBy
- paginate
- Query
    - query
    - queryOne
- save
- Select
    - resetSelect
    - select
    - selectRaw
- Table
    - getTable
    - getTableName
- Where
    - resetWhere
    - setWhereOperator
    - where
    - whereNested
    - whereRaw
