---
title: Chiamare il runtime Java
titleSuffix: SQL Server Language Extensions
description: Informazioni su come chiamare le classi Java da stored procedure di SQL Server usando le estensioni del linguaggio di SQL Server.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bdff924b63b11eda850378987498e8601367d3fe
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "73658890"
---
# <a name="how-to-call-the-java-runtime-in-sql-server-language-extensions"></a>Come chiamare il runtime Java nelle estensioni del linguaggio di SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Le [estensioni del linguaggio di SQL Server](../language-extensions-overview.md) usano la stored procedure di sistema [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) come interfaccia per chiamare il runtime Java. 

Questo articolo illustra i dettagli di implementazione per le classi e i metodi Java eseguiti in SQL Server.

## <a name="where-to-place-java-classes"></a>Dove inserire le classi Java

Esistono due metodi per chiamare le classi Java in SQL Server:

1. Inserire i file con estensione **class** o **jar** nel [classpath Java](#classpath). 

2. Caricare le classi compilate in un file con estensione **jar** e altre dipendenze nel database usando il DDL della [libreria esterna](#external-library). 

> [!NOTE]
> Come raccomandazione generale, usare file con estensione **jar** e non singoli file con estensione **class**. Si tratta di una pratica comune in Java che renderà più semplice l'esperienza complessiva. Vedere anche [Come creare un file con estensione jar dai file di classe](create-a-java-jar-file-from-class-files.md).

<a name="classpath"></a>

## <a name="use-classpath"></a>Usare Classpath

### <a name="basic-principles"></a>Principi di base

Di seguito sono riportati alcuni principi di base per l'esecuzione di Java in SQL Server.

* Le classi Java personalizzate compilate devono esistere nei file con estensione **class** o **jar** nel classpath Java. Il [parametro CLASSPATH](#set-classpath) fornisce il percorso dei file Java compilati. 

* Il metodo Java che si sta chiamando deve essere specificato nel parametro **script** nella stored procedure.

* Se la classe appartiene a un pacchetto, è necessario specificare **packageName**.

* **params** viene usato per passare i parametri a una classe Java. La chiamata a un metodo che richiede argomenti non è supportata. Pertanto, i parametri sono l'unico modo per passare i valori degli argomenti al metodo. 

> [!NOTE]
> Questa nota riporta le operazioni supportate e non supportate specifiche di Java in SQL Server 2019 Release Candidate 1.
> * Nella stored procedure sono supportati i parametri di input, a differenza dei parametri di output.

### <a name="call-java-class"></a>Chiamare la classe Java

La stored procedure di sistema [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) è l'interfaccia usata per chiamare il runtime Java. L'esempio seguente illustra un `sp_execute_external_script` che usa l'estensione Java e i parametri per specificare il percorso, lo script e il codice personalizzato.

> [!NOTE]
> Si noti che non è necessario definire il metodo da chiamare. Per impostazione predefinita, viene chiamato un metodo denominato **execute**. Ciò significa che è necessario seguire [Extensibility SDK per Java in SQL Server](extensibility-sdk-java-sql-server.md) e implementare un metodo execute nella classe Java.

```sql
DECLARE @param1 int
SET @param1 = 3

EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'<packageName>.<ClassName>'
, @input_data_1 = N'<Input Query>'
, @param1 = @param1
```

<a name="set-classpath"></a>

### <a name="set-classpath"></a>Impostare CLASSPATH

Dopo aver compilato la classe o le classi Java e aver creato un file con estensione jar nel classpath Java, sono disponibili due opzioni per specificare il classpath per l'estensione Java di SQL Server:

1. Usare librerie esterne

    L'opzione più semplice consiste nel far sì che SQL Server trovi automaticamente le classi creando librerie esterne e facendo puntare la libreria a un file con estensione jar. [Usare librerie esterne per Java](#external-library)

2. Registrare una variabile di ambiente di sistema

    È possibile creare una variabile di ambiente di sistema e specificare i percorsi del file con estensione jar contenente le classi. Creare una variabile di ambiente di sistema denominata **CLASSPATH**.

<a name="external-library"></a>

## <a name="use-external-library"></a>Usare una libreria esterna

In SQL Server 2019 Release Candidate 1 è possibile usare librerie esterne per il linguaggio Java in Windows e Linux. È possibile compilare le classi in un file con estensione jar e caricare il file jar e altre dipendenze nel database usando il DDL [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

Esempio di come caricare un file con estensione jar con la libreria esterna:

```sql 
CREATE EXTERNAL LIBRARY myJar
FROM (CONTENT = '<local path to .jar file>') 
WITH (LANGUAGE = 'Java'); 
GO
```

Creando una libreria esterna, SQL Server avrà automaticamente accesso alle classi Java e non sarà necessario impostare autorizzazioni speciali per il classpath.

Esempio di chiamata di un metodo in una classe da un pacchetto caricato come libreria esterna:

```sql
EXEC sp_execute_external_script
  @language = N'Java'
, @script = N'MyPackage.MyCLass'
, @input_data_1 = N'SELECT * FROM MYTABLE'
with result sets ((column1 int))
```

Per altre informazioni, vedere [CREATE EXTERNAL LIBRARY](https://docs.microsoft.com/sql/t-sql/statements/create-external-library-transact-sql).

## <a name="next-steps"></a>Passaggi successivi

+ [Esercitazione: cercare una stringa usando espressioni regolari in Java](../tutorials/search-for-string-using-regular-expressions-in-java.md)