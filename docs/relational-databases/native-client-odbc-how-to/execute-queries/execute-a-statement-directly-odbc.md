---
title: Eseguire un'istruzione direttamente (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a5ece0a8b0e0844e8c33779796b0217ebf744050
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73781421"
---
# <a name="execute-a-statement-directly-odbc"></a>Eseguire un'istruzione direttamente (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a>Per eseguire un'istruzione direttamente e solo una volta  
  
1.  Se l'istruzione include marcatori di parametro, usare [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) per associare ogni parametro a una variabile di programma. Inserire nelle variabili di programma i valori dei dati e quindi configurare tutti i parametri data-at-execution.  
  
2.  Chiamare [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) per eseguire l'istruzione.  
  
3.  Se vengono utilizzati parametri di input data-at-execution, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) restituisce SQL_NEED_DATA. Inviare i dati in blocchi usando [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) e [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  

### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a>Per eseguire un'istruzione più volte utilizzando l'associazione di parametri per colonna  
  
1.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare gli attributi seguenti:  
  
     Impostare SQL_ATTR_PARAMSET_SIZE sul numero di set (S) di parametri.  
  
     Impostare SQL_ATTR_PARAM_BIND_TYPE su SQL_PARAMETER_BIND_BY_COLUMN.  
  
     Impostare l'attributo SQL_ATTR_PARAMS_PROCESSED_PTR in modo che punti a una variabile SQLUINTEGER che contenga il numero di parametri elaborati.  
  
     Impostare SQL_ATTR_PARAMS_STATUS_PTR in modo che punti a una matrice [S] di variabili SQLUSSMALLINT contenente gli indicatori di stato dei parametri.  
  
2.  Per ogni marcatore di parametro:  
  
     Allocare una matrice di buffer di S parametri per archiviare i valori dei dati.  
  
     Allocare una matrice di buffer di S parametri per archiviare le lunghezze dei dati.  
  
     Chiamare [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) per associare il valore dei dati del parametro e le matrici di lunghezza dei dati al parametro dell'istruzione.  
  
     Configurare tutti i parametri data-at-execution di tipo text o image.  
  
     Inserire S valori dei dati e S lunghezze dei dati nella matrice di parametri associati.  
  
3.  Chiamare [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) per eseguire l'istruzione. Il driver esegue in modo efficace l'istruzione S volte, una volta per ogni set di parametri.  
  
4.  Se vengono utilizzati parametri di input data-at-execution, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) restituisce SQL_NEED_DATA. Inviare i dati in blocchi usando [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) e [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a>Per eseguire un'istruzione più volte utilizzando l'associazione di parametri per riga  
  
1.  Allocare una matrice [S] di strutture, dove S è il numero di set di parametri. Nella struttura è presente un elemento per ogni parametro e ogni elemento è costituito da due parti:  
  
     La prima parte è una variabile del tipo di dati appropriato che contiene i dati dei parametri.  
  
     La seconda parte è una variabile SQLINTEGER che deve contenere l'indicatore di stato.  
  
2.  Chiamare [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) per impostare gli attributi seguenti:  
  
     Impostare SQL_ATTR_PARAMSET_SIZE sul numero di set (S) di parametri.  
  
     Impostare SQL_ATTR_PARAM_BIND_TYPE sulla dimensione della struttura allocata nel Passaggio 1.  
  
     Impostare l'attributo SQL_ATTR_PARAMS_PROCESSED_PTR in modo che punti a una variabile SQLUINTEGER che contenga il numero di parametri elaborati.  
  
     Impostare SQL_ATTR_PARAMS_STATUS_PTR in modo che punti a una matrice [S] di variabili SQLUSSMALLINT contenente gli indicatori di stato dei parametri.  
  
3.  Per ogni marcatore di parametro, chiamare [SQLBindParameter](../../../relational-databases/native-client-odbc-api/sqlbindparameter.md) per puntare il valore dei dati del parametro e il puntatore alla lunghezza dei dati alle variabili nel primo elemento della matrice di strutture allocate nel passaggio 1. Se il parametro è di tipo data-at-execution, configurarlo.  
  
4.  Inserire i valori dei dati nella matrice di buffer dei parametri associati.  
  
5.  Chiamare [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) per eseguire l'istruzione. Il driver esegue in modo efficace l'istruzione S volte, una volta per ogni set di parametri.  
  
6.  Se vengono utilizzati parametri di input data-at-execution, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) restituisce SQL_NEED_DATA. Inviare i dati in blocchi usando [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) e [SQLPutData](../../../relational-databases/native-client-odbc-api/sqlputdata.md).  
  
 **Nota** Le associazioni a livello di colonna e di riga vengono in genere utilizzate in combinazione con la [funzione SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360) e [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) anziché con [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure relative all'esecuzione di query &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
