# Yorm ORM

- [Arbeiten ohne eigene Model class](#ohne-model-class)
- [Eigene Model class verwenden](#eigene-model-class)
- [Methoden](#methoden)
- [Query debuggen](#query-debuggen)
    
<a name="ohne-model-class"></a>
## Arbeiten ohne eigene Model class

Hole alle Daten der Tabelle `rex_my_table`

```
$items = rex_yform_manager_table::get('rex_my_table')->query()->find();
```



<a name="eigene-model-class"></a>
## Eigene Model class verwenden

Nicht zwingend erforderlich, vereinfacht das Ansprechen der Tabelle mittels der OO-Notation.

### Klasse erstellen

Zunächst wird eine Klasse erstellt und in das `project` AddOn im Ordner `lib` abgelegt
```
<?php
class MyTable extends \rex_yform_manager_dataset
{
}
```

### Klasse registrieren
Jetzt muss die erstellte Klasse noch registiert werden. Dazu öffnet man die Datei `boot.php` des `project` AddOns und fügt nachfolgenden Code ein. Wird das theme-Addon verwendet, den Code in die Datei `functions.php` einfügen.

```
rex_yform_manager_dataset::setModelClass('rex_my_table', MyTable::class);
```

Nun kann man alle Daten wie folgt holen

```
$items = MyTable::query()->find();
```

#### weitere Beispiele

```
$items = MyTable::query()
            ->alias('t')
            ->joinRelation('relation_id', 'r')
            ->select('r.name', 'relation_name')
            ->where('t.status', '1')
            ->orderBy('t.name')
            ->find();
```

<a name="methoden"></a>
## Methoden

### query Methoden

- Alias
    - alias
    - getTableAlias
- count
- exists (liefert true oder false zurück. Optimal für große Abfragen.)
- Find
    - find
    - findId
    - findIds
    - findOne (liefert einen Datensatz als Objekt zurück.)
- Get
    - get
    - getAll
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

### Beispiel ###
```
$pager = new rex_pager(10);
$table = rex_yform_manager_table::get('rex_table_name');
$ergebnisse = $table->query()
    ->paginate($pager);
$fragment = new rex_fragment();
$fragment->setVar('urlprovider', rex_article::getCurrent());
$fragment->setVar('pager', $pager);
echo $fragment->parse('core/navigations/pagination.php');

foreach ($ergebnisse as $erg) {
echo "ID: ".$erg->id;
}
echo $pager->getRowCount();
echo $pager->getCurrentPage();
echo $pager->getLastPage();
echo $pager->getPageCount();
```

- Query
    - query
    - queryOne
- save
- Select
    - resetSelect
    - select
    - selectRaw (lässt individuelle Argumente zu, wie z.B. `CONCAT, SUM`)
- Table
    - getTable
    - getTableName
- Where
    - resetWhere
    - setWhereOperator
    - where
    - whereNested
    - whereRaw

### dataset Methoden

- get
- getData (liefert Felder als Array zurück)
- getForm (liefert Formular zurück - EXPERIMENTELL!)
- getId
- getMessages
- getRaw
- getRelatedCollection
- getRelatedDataset
- getTable
- getTableName
- getValue
- hasValue
- isValid
- loadData


<a name="query-debuggen"></a>
## Query debuggen

Temporär, wird gelöscht wenn besseres Handling vorhanden ist

### Variante A

Wichtig ist nur der Part mit `rex_sql`

```
$query = MyTable::query();
$query
    ->alias('t')
    ->joinRelation('relation_id', 'r')
    ->select('r.name', 'relation_name')
    ->where('t.status', '1')
    ->orderBy('t.name')
$items = rex_sql::factory()->setDebug()->getArray($query->getQuery(), $query->getParams());
$items = $query->find();
``` 

### Variante B

Datei `/redaxo/src/addons/yform/plugins/manager/lib/yform/manager/dataset.php` und die Variable `private static $debug = false;` auf `true` setzen

## Beispiele

```
<?php

$table = rex_yform_manager_table::get('rex_data_product');

$products = $table->query()
    ->joinRelation('category_id', 'c') // Join auf rex_data_product_category gemäß Relationsfeld category_id, mit Alias "c" für weitere Verwendung
    ->select('c.name', 'category_name') // Aus der gejointen Tabelle den Kategorienamen mit auslesen mit Alias "category_name"
    ->where('status', 1)
    ->find();

foreach ($products as $product) {
    echo $product->name;
    echo $product->category_name; // Value aus der gejointen Tabelle, siehe oben

    // Alternativ das komplette Objekt für die Kategorie auslesen
    $category = $product->getRelatedDataset('category_id');
    echo $category->name;
}
```
