---
title: 'Procedura: Recuperare i tipi di data e ora come oggetti DateTime PHP usando il driver PDO_SQLSRV | Microsoft Docs'
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as datetime objects
author: yitam
ms.author: v-yitam
manager: v-mabarw
ms.openlocfilehash: 165e91cee3b0b4592f9b746f8b35b46bc73bce50
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "68264571"
---
# <a name="how-to-retrieve-date-and-time-types-as-php-datetime-objects-using-the-pdo_sqlsrv-driver"></a>Procedura: Recuperare i tipi di data e ora come oggetti DateTime PHP usando il driver PDO_SQLSRV
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Questa funzionalità, aggiunta nella versione 5.6.0, è valida solo quando si usa il driver SQLSRV per [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

### <a name="to-retrieve-date-and-time-types-as-datetime-objects"></a>Per recuperare i tipi di data e ora come oggetti DateTime

Quando si usa PDO_SQLSRV, i tipi di data e ora (**smalldatetime**, **DateTime**, **date**, **Time**, **datetime2** e **DateTimeOffset**) vengono restituiti per impostazione predefinita come stringhe. Né l'attributo DOP::ATTR_STRINGIFY_FETCHES né l'attributo DOP::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE hanno alcun effetto. Per recuperare i tipi di data e ora come oggetti [PHP DateTime](http://php.net/manual/en/class.datetime.php), impostare l'attributo di connessione o di istruzione `PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE` su **true** (è **false** per impostazione predefinita).

> [!NOTE]
> Questo attributo di connessione o di istruzione si applica solo al recupero regolare dei tipi di data e ora perché gli oggetti DateTime non possono essere specificati come parametri di output.

## <a name="example---use-the-connection-attribute"></a>Esempio: usare l'attributo di connessione
Negli esempi seguenti viene omesso il controllo degli errori per chiarezza. In questo esempio viene illustrato come impostare l'attributo di connessione:

```php
<?php
$server = 'myserver';
$databaseName = 'mydatabase';
$username = 'myusername';
$passwd = 'mypasword';
$tableName = 'mytable';

$conn = new PDO("sqlsrv:Server = $server; Database = $databaseName", $username, $passwd);

// To set the connection attribute
$conn->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$query = "SELECT DateTimeCol FROM $tableName";
$stmt = $conn->prepare($query);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_ASSOC);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-attribute"></a>Esempio: usare l'attributo di istruzione
In questo esempio viene illustrato come impostare l'attributo di istruzione:

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");
$query = "SELECT DateTimeCol FROM myTable";
$stmt = $conn->prepare($query);
$stmt->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_NUM);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-option"></a>Esempio: usare l'opzione dell'istruzione
In alternativa, è possibile impostare l'attributo di istruzione come opzione:

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");

$dateObj = null;
$query = "SELECT DateTimeCol FROM aTable";
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => true);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateObj, PDO::PARAM_LOB);
$row = $stmt->fetch(PDO::FETCH_BOUND);
var_dump($dateObj);

unset($stmt);
unset($conn);
?>
```

## <a name="example---retrieve-datetime-types-as-strings"></a>Esempio: recuperare i tipi di data e ora come stringhe
Nell'esempio seguente viene illustrato come ottenere il contrario, che non è effettivamente necessario essendo false per impostazione predefinita:

```php
<?php
$database = "MyData";
$conn = new PDO("sqlsrv:server = (local); Database = $database");

$dateStr = null;
$query = 'SELECT DateTimeCol FROM table1';
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => false);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateStr);
$row = $stmt->fetch(PDO::FETCH_BOUND);
echo $dateStr . PHP_EOL;

unset($stmt);
unset($conn);
?>
```

## <a name="see-also"></a>Vedere anche
[Recupero di dati](../../connect/php/retrieving-data.md)

[Recuperare i tipi di data e ora come stringhe usando il driver SQLSRV](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)