---
title: Query tra database | Microsoft Docs
ms.custom: ''
ms.date: 08/04/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 93eae89743c2a4563317614a18e4bf5f46248071
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68031979"
---
# <a name="cross-database-queries"></a>Query tra database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  A partire da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]le tabelle ottimizzate per la memoria non supportano le transazioni tra database. Non è possibile accedere a un altro database dalla stessa transazione o dalla stessa query che accede anche a una tabella ottimizzata per la memoria. Non è possibile copiare facilmente i dati da una tabella in un database a una tabella ottimizzata per la memoria in un altro database.  
  
 Le variabili di tabella non sono transazionali. Pertanto, le variabili di tabella ottimizzata per la memoria possono essere utilizzate nelle query tra database e possono quindi facilitare lo spostamento di dati da un database nelle tabelle ottimizzate per la memoria a un altro. È possibile utilizzare due transazioni. Nella prima transazione, inserire i dati della tabella remota nella variabile. Nella seconda transazione, inserire i dati nella tabella ottimizzata per la memoria locale dalla variabile.  Per altre informazioni sulle variabili di tabella ottimizzata per la memoria, vedere [Tabella temporanea più rapida e variabile di tabella tramite l'ottimizzazione per la memoria](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md).
  
## <a name="example"></a>Esempio
Questo esempio illustra un metodo per trasferire i dati da un database in una tabella ottimizzata per la memoria in un database diverso.

1. Creare oggetti di prova.  Eseguire il seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  

    ```sql

    USE master;
    GO
    
    SET NOCOUNT ON;
    
    -- Create simple database
    CREATE DATABASE SourceDatabase;
    ALTER DATABASE SourceDatabase SET RECOVERY SIMPLE;
    GO

    -- Create a table and insert a few records
    USE SourceDatabase;
    
    CREATE TABLE SourceDatabase.[dbo].[SourceTable] (
        [ID] [int] PRIMARY KEY CLUSTERED,
        [FirstName] nvarchar(8)
        );
    
    INSERT [SourceDatabase].[dbo].[SourceTable]
    VALUES (1, N'Bob'),
        (2, N'Susan');
    GO

    -- Create a database with a MEMORY_OPTIMIZED_DATA filegroup

    CREATE DATABASE DestinationDatabase
     ON  PRIMARY 
    ( NAME = N'DestinationDatabase_Data', FILENAME = N'D:\DATA\DestinationDatabase_Data.mdf',   SIZE = 8MB), 
     FILEGROUP [DestinationDatabase_mod] CONTAINS MEMORY_OPTIMIZED_DATA  DEFAULT
    ( NAME = N'DestinationDatabase_mod', FILENAME = N'D:\DATA\DestinationDatabase_mod', MAXSIZE = UNLIMITED)
     LOG ON 
    ( NAME = N'DestinationDatabase_Log', FILENAME = N'D:\LOG\DestinationDatabase_Log.ldf', SIZE = 8MB);
    
    ALTER DATABASE DestinationDatabase SET RECOVERY SIMPLE;
    GO
    
    USE DestinationDatabase;
    GO

    -- Create a memory-optimized table
    CREATE TABLE [dbo].[DestTable_InMem] (
        [ID] [int] PRIMARY KEY NONCLUSTERED,
        [FirstName] nvarchar(8)
        )
    WITH ( MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA );
    GO
    ```

2.  Provare ad eseguire query tra database. Eseguire il seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
  
    ```sql  
    INSERT [DestinationDatabase].[dbo].[DestTable_InMem]
    SELECT * FROM [SourceDatabase].[dbo].[SourceTable]
    ```  

    Dovrebbe essere visualizzato il seguente messaggio di errore:
    > Messaggio 41317, livello 16, stato 5  
    > Una transazione utente che accede alle tabelle con le tabelle con ottimizzazione per la memoria o ai moduli compilati in modo nativo non può accedere a più database utente o modelli di database e msdb e non può accedere in scrittura al database master.

3.  Creare un tipo di tabella ottimizzata per la memoria.  Eseguire il seguente [!INCLUDE[tsql](../../includes/tsql-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].

    ```sql
    USE DestinationDatabase;
    GO
    
    CREATE TYPE [dbo].[MemoryType]  
        AS TABLE  
        (  
        [ID] [int] PRIMARY KEY NONCLUSTERED,
        [FirstName] nvarchar(8)
        )  
        WITH  
            (MEMORY_OPTIMIZED = ON);  
    GO
    ```

4.  Riprovare ad eseguire query tra database.  Questa volta i dati di origine verranno prima trasferiti a una variabile di tabella ottimizzata per la memoria.  Quindi, i dati della variabile di tabella verranno trasferiti alla tabella ottimizzata per la memoria.
    ```sql
    -- Declare table variable utilizing the newly created type - MemoryType
    DECLARE @InMem dbo.MemoryType;
    
    -- Populate table variable
    INSERT @InMem SELECT * FROM SourceDatabase.[dbo].[SourceTable];
    
    -- Populate the destination memory-optimized table
    INSERT [DestinationDatabase].[dbo].[DestTable_InMem] SELECT * FROM @InMem;
    GO 
    ```
   
## <a name="see-also"></a>Vedere anche  
 [Migrazione a OLTP in memoria](../../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)  
  
  
