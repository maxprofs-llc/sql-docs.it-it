---
title: Altri Sottoscrittori non SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- non-SQL Server Subscribers, other types
ms.assetid: 96b8beb9-38e8-4ce4-97ca-c0f8656b73b4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 135d317d74a720d51c966ed92f1c305f8c04b838
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63021943"
---
# <a name="other-non-sql-server-subscribers"></a>Altri Sottoscrittori non SQL Server
  Per un elenco di[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Sottoscrittori non supportati da [!INCLUDE[msCoName](../../../includes/msconame-md.md)], vedere [Sottoscrittori non SQL Server](non-sql-server-subscribers.md). In questo argomento vengono fornite informazioni sui requisiti per i driver ODBC e i provider OLE DB.  
  
## <a name="odbc-driver-requirements"></a>Requisiti per i driver ODBC  
 Il driver ODBC deve soddisfare i requisiti seguenti:  
  
-   Deve essere conforme a ODBC di livello 1.  
  
-   Deve essere affidabile e compatibile con l'architettura del processore, Intel o Alpha, e con la piattaforma, a 32 o a 64 bit, in cui è in esecuzione il server di distribuzione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Deve essere in grado di eseguire transazioni.  
  
-   Deve supportare il linguaggio DDL (Data Definition Language).  
  
-   Non può essere di sola lettura.  
  
-   Deve supportare nomi di tabella lunghi, ad esempio **MSreplication_subscriptions**.  
  
## <a name="replicating-using-ole-db-interfaces"></a>Esecuzione della replica tramite interfacce OLE DB  
 Per la replica transazionale i provider OLE DB devono supportare gli oggetti seguenti:  
  
-   **DataSource** (oggetto)  
  
-   Oggetto **Session**  
  
-   Oggetto **Command**  
  
-   Oggetto **rowset**  
  
-   **Error** (oggetto)  
  
### <a name="datasource-object-interfaces"></a>Interfacce per oggetti DataSource  
 Per la connessione a un'origine dei dati sono necessarie le interfacce seguenti:  
  
-   `IDBInitialize`  
  
-   `IDBCreateSession`  
  
-   `IDBProperties`  
  
 Se il provider supporta l'interfaccia **IDBInfo** , tale interfaccia viene utilizzata in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per il recupero di informazioni quali l'identificatore tra virgolette, la lunghezza massima delle istruzioni SQL e il numero massimo di caratteri nei nomi delle colonne e delle tabelle.  
  
### <a name="session-object-interfaces"></a>Interfacce per oggetti Session  
 Sono necessarie le interfacce seguenti:  
  
-   **IDBCreateCommand**  
  
-   **ITransaction**  
  
-   **ITransactionLocal**  
  
-   **IDBSchemaRowset**  
  
### <a name="command-object-interfaces"></a>Interfacce per oggetti Command  
 Sono necessarie le interfacce seguenti:  
  
-   **ICommand**  
  
-   **ICommandProperties**  
  
-   **ICommandText**  
  
-   **ICommandPrepare**  
  
-   **IColumnsInfo**  
  
-   **IAccessor**  
  
-   **ICommandWithParameters**  
  
 **IAccessor** è necessario per creare funzioni di accesso ai parametri. Se il provider supporta **interfaccia IColumnRowset**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizza tale interfaccia per determinare se una colonna è una colonna Identity.  
  
### <a name="rowset-object-interfaces"></a>Interfacce per oggetti Rowset  
 Sono necessarie le interfacce seguenti:  
  
-   **IRowset**  
  
-   **IAccessor**  
  
-   **IColumnsInfo**  
  
 In un'applicazione può essere necessario aprire un set di righe di una tabella replicata creata nel database di sottoscrizione. **IColumnsInfo** e **IAccessor** sono necessari per accedere ai dati nel set di righe.  
  
### <a name="error-object-interfaces"></a>Interfacce per oggetti Error  
 Per la gestione degli errori, utilizzare le interfacce seguenti:  
  
-   **IErrorRecords**  
  
-   **IErrorInfo**  
  
 Utilizzare l'interfaccia **ISQLErrorInfo** se è supportata dal provider OLE DB.  
  
 Per ulteriori informazioni sul provider OLE DB, vedere la relativa documentazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Non-SQL Server Subscribers](non-sql-server-subscribers.md)  
  
  
