---
title: Creazione di un driver OLE DB per applicazione SQL Server | Microsoft Docs
description: Creazione di un driver OLE DB per applicazione SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, application creation
- applications [OLE DB Driver for SQL Server]
- OLE DB, creating applications
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 4f7861e02b1ed203911f4e3f86575a9688c861fb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015659"
---
# <a name="creating-an-ole-db-driver-for-sql-server-application"></a>Creazione di un'applicazione del driver OLE DB per SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  La creazione di un'applicazione OLE DB Driver per SQL Server prevede questi passaggi:  
  
1.  Avvio di una connessione a un'origine dati.  
  
2.  Esecuzione di un comando.  
  
3.  Elaborazione dei risultati.  
  
> [!NOTE]  
>  Se possibile, usare l'autenticazione di Windows. Se non è disponibile, agli utenti verrà richiesto di immettere le credenziali in fase di esecuzione. Evitare di archiviare le credenziali in un file. Se è necessario rendere persistenti le credenziali, è consigliabile crittografarle usando [CryptoAPI Win32](https://go.microsoft.com/fwlink/?LinkId=9504).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Avvio di una connessione a un'origine dati](../../oledb/ole-db-driver/establishing-a-connection-to-a-data-source.md)  
  
-   [Esecuzione di un comando](../../oledb/ole-db-driver/executing-a-command.md)  
  
-   [Elaborazione dei risultati](../../oledb/ole-db-driver/processing-results.md)  
  
-   [Informazioni sulle proprietà OLE DB](../../oledb/ole-db-driver/about-ole-db-properties.md)  
  
-   [Uso della clausola OUTPUT con OLE DB nel driver OLE DB per SQL Server](../../oledb/ole-db-driver/using-the-output-clause-with-ole-db-in-oledb-driver-for-sql-server.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Driver OLE DB per programmazione con SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
