---
title: Dettagli errore SQL Server | Documenti Microsoft
description: Dettagli sull'errore di SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-errors
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], error details
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error details
- ISQLServerErrorInfo interface
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d606e6e33e71100c4be512b454138483dd74c6dc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="sql-server-error-detail"></a>Dettagli relativi agli errori SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il Driver OLE DB per SQL Server definisce l'interfaccia di errore specifico del provider [ISQLServerErrorInfo](http://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1). L'interfaccia restituisce maggiori dettagli relativi agli errori [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e risulta molto utile quando operazioni di esecuzione di comandi o del set di righe non riescono.  
  
 Esistono due modi per ottenere l'accesso a **ISQLServerErrorInfo** interfaccia.  
  
 Il consumer può chiamare **IErrorRecords:: Getcustomererrorobject** per ottenere un **ISQLServerErrorInfo** puntatore, come illustrato nell'esempio di codice seguente. (Non è necessario ottenere **ISQLErrorInfo.**) Entrambi **ISQLErrorInfo** e **ISQLServerErrorInfo** sono oggetti errore OLE DB personalizzati, con **ISQLServerErrorInfo** rappresenta l'interfaccia da utilizzare per ottenere informazioni errori del server, inclusi dettagli quali di numeri di riga e il nome di stored procedure.  
  
```  
// Get the SQL Server custom error object.  
if(FAILED(hr=pIErrorRecords->GetCustomErrorObject(  
   nRec, IID_ISQLServerErrorInfo,  
   (IUnknown**)&pISQLServerErrorErrorInfo)))  
```  
  
 Un altro modo per ottenere un **ISQLServerErrorInfo** puntatore consiste nel chiamare il **QueryInterface** metodo su un già ottenuto **ISQLErrorInfo** puntatore. Si noti che poiché **ISQLServerErrorInfo** contiene un superset delle informazioni disponibili da **ISQLErrorInfo**, è utile per passare direttamente alla **ISQLServerErrorInfo** tramite **GetCustomerErrorObject**.  
  
 Il **ISQLServerErrorInfo** interfaccia espone una funzione membro, [ISQLServerErrorInfo:: GetErrorInfo](../../oledb/ole-db-interfaces/isqlservererrorinfo-geterrorinfo-ole-db.md). La funzione restituisce un puntatore a una struttura SSERRORINFO e un puntatore a un buffer di stringhe. Entrambi i puntatori fanno riferimento a memoria, il consumer deve deallocare utilizzando il **IMalloc:: Free** metodo.  
  
 I membri di struttura SSERRORINFO vengono interpretati dal consumer come segue.  
  
|Membro|Descrizione|  
|------------|-----------------|  
|*pwszMessage*|Messaggio di errore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Identico con la stringa restituita **IErrorInfo:: GetDescription**.|  
|*pwszServer*|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per la sessione.|  
|*pwszProcedure*|Se appropriato, restituisce il nome della stored procedure in cui ha avuto origine l'errore. In caso contrario, una stringa vuota.|  
|*lNative*|Numero di errore nativo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Identico al valore restituito nel *plNativeError* parametro di **ISQLErrorInfo:: Getsqlinfo**.|  
|*bState*|Stato di un messaggio di errore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*bClass*|Gravità di un messaggio di errore di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|*wLineNumber*|Quando è applicabile, restituisce il numero di riga di una stored procedure in cui si è verificato l'errore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Errori](../../oledb/ole-db-errors/errors.md)   
 [RAISERROR & #40; Transact-SQL & #41;](../../../t-sql/language-elements/raiserror-transact-sql.md)  
  
  