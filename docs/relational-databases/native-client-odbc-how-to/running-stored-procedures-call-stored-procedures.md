---
title: Stored procedure call (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- stored procedures [ODBC], calling
ms.assetid: 31176be8-d40e-4f93-8d44-a46e804a3e2d
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2d9d3dd9955f8b7f5cf6b02934f34af0d420dae8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73780641"
---
# <a name="running-stored-procedures---call-stored-procedures"></a>Esecuzione delle stored procedure - Chiamare le stored procedure
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta l'esecuzione di stored procedure come stored procedure remote. L'esecuzione di una stored procedure come stored procedure remota consente al driver e al server di ottimizzare le prestazioni di esecuzione della procedura.  
  
  Quando un'istruzione SQL chiama una stored procedure utilizzando la clausola di escape ODBC CALL, tramite driver di Microsoft® SQL Server™ la stored procedure viene inviata a SQL Server utilizzando il meccanismo di chiamata RPC (Remote Procedure Call). Le richieste RPC ignorano la maggior parte dell'analisi delle istruzioni e dell'elaborazione dei parametri in SQL Server e sono più veloci rispetto a un'istruzione Transact-SQL EXECUTE.  
  
 Per un'applicazione di esempio in cui viene illustrata questa funzionalità, vedere [elaborare i codici restituiti e i parametri di Output &#40;&#41;ODBC ](../../relational-databases/native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).  
  
### <a name="to-run-a-procedure-as-an-rpc"></a>Per eseguire una procedura come RPC  
  
1.  Costruire un'istruzione SQL che utilizzi la sequenza di escape ODBC CALL. Nell'istruzione vengono utilizzati marcatori di parametro per ogni parametro di input, input/output e di output e per il valore restituito della procedura, se disponibile:  
  
    ```  
    {? = CALL procname (?,?)}  
    ```  
  
2.  Chiamare [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md) per ogni parametro di input, di input/output e di output e per il valore restituito della procedura, se disponibile.  
  
3.  Eseguire l'istruzione con [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).  
  
> [!NOTE]  
>  Se un'applicazione invia una procedura utilizzando la sintassi Transact-SQL EXECUTE, invece della sequenza di escape ODBC CALL, il driver ODBC di SQL Server passa la chiamata di procedura a SQL Server come istruzione SQL anziché come chiamata RPC. Se viene utilizzata l'istruzione Transact-SQL EXECUTE, inoltre, i parametri di output non vengono restituiti.  
  
## <a name="see-also"></a>Vedere anche  
  [Invio in batch di chiamate a stored procedure](../../relational-databases/native-client-odbc-stored-procedures/batching-stored-procedure-calls.md)   
 [Esecuzione di stored procedure](../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)   
 [Chiamata di una stored procedure](../../relational-databases/native-client-odbc-stored-procedures/calling-a-stored-procedure.md)   
 [Procedure](../../relational-databases/native-client-odbc-queries/executing-statements/procedures.md)  
  
  
