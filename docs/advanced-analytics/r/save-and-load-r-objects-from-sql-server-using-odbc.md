---
title: Salvare e caricare oggetti R tramite ODBC
description: Il pacchetto RevoScaleR include nuove funzioni di serializzazione e deserializzazione che migliorano notevolmente le prestazioni e archiviano gli oggetti in modo più compatto.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 98a14848db4854c0bcb19167e7fcf7d43eca5f2e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "73727400"
---
# <a name="save-and-load-r-objects-from-sql-server-using-odbc"></a>Salvare e caricare oggetti R da SQL Server tramite ODBC
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server R Services può archiviare oggetti R serializzati in una tabella e quindi caricare l'oggetto dalla tabella in base alle necessità, senza dover eseguire nuovamente il codice R o ripetere il training del modello. La possibilità di salvare gli oggetti R in un database è fondamentale per gli scenari di training e salvataggio di un modello e quindi per un uso successivo per l'assegnazione dei punteggi o l'analisi.

Per migliorare le prestazioni di questo passaggio critico, il pacchetto **RevoScaleR** ora include nuove funzioni di serializzazione e deserializzazione che migliorano notevolmente le prestazioni e archiviano l'oggetto in modo più compatto. Questo articolo descrive queste funzioni e come usarle.

## <a name="overview"></a>Panoramica

Il pacchetto **RevoScaleR** ora include nuove funzioni che rendono più semplice salvare gli oggetti R in SQL Server e quindi leggere gli oggetti dalla tabella di SQL Server. Ogni chiamata di funzione usa in genere un archivio di valori chiave semplice, in cui la chiave è il nome dell'oggetto e il valore associato alla chiave è l'oggetto R varbinary da spostare all'interno o all'esterno dalla tabella.

Per salvare gli oggetti R in SQL Server direttamente da un ambiente R, è necessario:

+ Stabilire una connessione a SQL Server tramite l'origine dati *RxOdbcData*.
+ Chiamare le nuove funzioni tramite la connessione ODBC
+ Facoltativamente, è possibile specificare che l'oggetto non deve essere serializzato. Scegliere quindi un nuovo algoritmo di compressione da usare al posto dell'algoritmo di compressione predefinito.

Per impostazione predefinita, qualsiasi oggetto chiamato da R per lo spostamento in SQL Server viene serializzato e compresso. Al contrario, quando si carica un oggetto da una tabella SQL Server da usare nel codice R, l'oggetto viene deserializzato e decompresso.

## <a name="list-of-new-functions"></a>Elenco di nuove funzioni

- `rxWriteObject` scrive un oggetto R in SQL Server usando l'origine dati ODBC.

- `rxReadObject` legge un oggetto R da un database di SQL Server usando un'origine dati ODBC.

- `rxDeleteObject` elimina un oggetto R dal database di SQL Server specificato nell'origine dati ODBC. Se sono presenti più oggetti identificati dalla combinazione chiave/versione, vengono eliminati tutti.

- `rxListKeys` elenca tutti gli oggetti disponibili come coppie chiave-valore. Ciò consente di determinare i nomi e le versioni degli oggetti R.

Per informazioni dettagliate sulla sintassi di ogni funzione, usare la Guida di R. I dettagli sono disponibili anche nelle [informazioni di riferimento per ScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler).

## <a name="how-to-store-r-objects-in-sql-server-using-odbc"></a>Come archiviare gli oggetti R in SQL Server tramite ODBC

Questa procedura illustra come è possibile usare le nuove funzioni per creare un modello e salvarlo in SQL Server.

1. Impostare la stringa di connessione per SQL Server.
   ```R
   conStr <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. Creare un oggetto origine dati *rxOdbcData* in R usando la stringa di connessione.
   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr)
   ```

3. Eliminare la tabella se esiste già e non si vuole tenere traccia delle versioni precedenti degli oggetti.

   ```R
   if(rxSqlServerTableExists(ds@table, ds@connectionString)) {
       rxSqlServerDropTable(ds@table, ds@connectionString)
       }
   ```
   
4. Definire una tabella che può essere usata per archiviare oggetti binari.

   ```R
   ddl <- paste(" CREATE TABLE [", ds@table, "] 
      (","  [id] varchar(200) NOT NULL,
       "," [value] varbinary(max),
       "," CONSTRAINT unique_id UNIQUE (id))", 
       sep = "") 
   ```
5. Aprire la connessione ODBC per creare la tabella e quando l'istruzione DDL è stata completata, chiudere la connessione.

   ```R
    rxOpen(ds, "w") 
    rxExecuteSQLDDL(ds, ddl) 
    rxClose(ds)
    ```
6. Generare gli oggetti R che si vuole archiviare.

   ```R
   infertLogit <- rxLogit(case ~ age + parity + education + spontaneous + induced, 
     data = infert)
   ```
6. Usare l'oggetto *RxOdbcData* creato in precedenza per salvare il modello nel database.

   ```R
   rxWriteObject(ds, "logit.model", infertLogit)
   ```

## <a name="how-to-read-r-objects-from-sql-server-using-odbc"></a>Come leggere gli oggetti R da SQL Server tramite ODBC

Questa procedura illustra come è possibile usare le nuove funzioni per caricare un modello da SQL Server.

1. Impostare la stringa di connessione per SQL Server.

   ```R
   conStr2 <- 'Driver={SQL Server};Server=localhost;Database=storedb;Trusted_Connection=true'
   ```
2. Creare un oggetto origine dati *rxOdbcData* in R usando la stringa di connessione.

   ```R
   ds <- RxOdbcData(table="robjects", connectionString=conStr2)
   ```
3. Leggere il modello dalla tabella specificandone il nome di oggetto R.

   ```R
    infertLogit2 <- rxReadObject(ds, "logit.model")
   ```
