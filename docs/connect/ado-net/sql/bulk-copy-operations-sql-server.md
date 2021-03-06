---
title: Operazioni di copia bulk in SQL Server
description: Viene descritta la funzionalità di copia bulk per il provider di dati .NET per SQL Server.
ms.date: 09/30/2019
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: c827ae70d9aa344f52de1d76c482beaef90c09aa
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "78897028"
---
# <a name="bulk-copy-operations-in-sql-server"></a>Operazioni di copia bulk in SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Microsoft SQL Server include una popolare utilità della riga di comando denominata **bcp** per eseguire rapidamente la copia bulk di file di grandi dimensioni in tabelle o viste nei database di SQL Server. La classe <xref:Microsoft.Data.SqlClient.SqlBulkCopy> consente di scrivere soluzioni di codice gestito che offrono funzionalità simili. Esistono altri modi per caricare dati in una tabella di SQL Server (ad esempio, istruzioni INSERT) ma <xref:Microsoft.Data.SqlClient.SqlBulkCopy> offre un significativo vantaggio in termini di prestazioni.  
  
Con la classe <xref:Microsoft.Data.SqlClient.SqlBulkCopy> è possibile eseguire:  
  
- Una singola operazione di copia bulk  
  
- Più operazioni di copia bulk  
  
- Un'operazione di copia bulk all'interno di una transazione  
  
> [!NOTE]
>  Con .NET Framework versione 1.1 o precedenti (in cui non è supportata la classe <xref:Microsoft.Data.SqlClient.SqlBulkCopy>), è possibile eseguire l'istruzione **BULK INSERT** di SQL Server Transact-SQL usando l'oggetto <xref:Microsoft.Data.SqlClient.SqlCommand>.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
[Installazione di esempio della copia bulk](bulk-copy-example-setup.md)  
Descrive le tabelle usate negli esempi di copia bulk e fornisce script SQL per la creazione delle tabelle nel database AdventureWorks.  
  
[Singole operazioni di copia bulk](single-bulk-copy-operations.md)  
Viene descritto come eseguire una singola copia bulk dei dati in un'istanza di SQL Server usando la classe <xref:Microsoft.Data.SqlClient.SqlBulkCopy> e come eseguire l'operazione di copia bulk usando istruzioni Transact-SQL e la classe <xref:Microsoft.Data.SqlClient.SqlCommand>.  
  
[Più operazioni di copia bulk](multiple-bulk-copy-operations.md)  
Viene descritto come eseguire più operazioni di copia bulk dei dati in un'istanza di SQL Server usando la classe <xref:Microsoft.Data.SqlClient.SqlBulkCopy>.  
  
[Transazioni e operazioni di copia bulk](transaction-bulk-copy-operations.md)  
Viene descritto come eseguire un'operazione di copia bulk all'interno di una transazione e come eseguire il commit o il ripristino dello stato precedente della transazione.  
  
## <a name="next-steps"></a>Passaggi successivi
- [SQL Server e ADO.NET](index.md)
