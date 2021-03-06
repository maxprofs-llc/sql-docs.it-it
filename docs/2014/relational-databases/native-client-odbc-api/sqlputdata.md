---
title: SQLPutData | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e15353cd9f4c4a837fe5978d00259ad5460d50d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046626"
---
# <a name="sqlputdata"></a>SQLPutData
  Quando si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] USA SQLPutData per inviare più di 65.535 byte di dati (per la versione 4.21 a) o 400 KB di dati (per SQL Server versione 6,0 e successive) per una colonna SQL_LONGVARCHAR (`text`), SQL_WLONGVARCHAR (`ntext`) o SQL_LONGVARBINARY (`image`), si applicano le restrizioni seguenti:  
  
-   Il parametro a cui si fa riferimento può essere il *insert_Value* in un'istruzione INSERT.  
  
-   Il parametro a cui si fa riferimento può essere un' *espressione* nella clausola set di un'istruzione Update.  
  
 L'annullamento di una sequenza di chiamate SQLPutData che forniscono dati in blocchi a un server [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che esegue comporta un aggiornamento parziale del valore della colonna quando si usa la versione 6,5 o precedente. La `text`colonna `ntext`, o `image` a cui è stato fatto riferimento quando è stato chiamato SQLCancel è impostata su un valore di segnaposto intermedio.  
  
> [!NOTE]  
>  Il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client non supporta la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 e versioni precedenti.  
  
## <a name="diagnostics"></a>Diagnostica  
 Per SQLPutData è [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disponibile un SQLSTATE specifico di Native Client:  
  
|SQLSTATE|Errore|Descrizione|  
|--------------|-----------|-----------------|  
|22026|Lunghezza dei dati non corrispondente.|Se la lunghezza dei dati in byte da inviare è stata specificata da un'applicazione, ad esempio con SQL_LEN_DATA_AT_EXEC (*n*), dove *n* è maggiore di 0, il numero totale di byte fornito dall'applicazione tramite SQLPutData deve corrispondere alla lunghezza specificata.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>SQLPutData e parametri con valori di tabella  
 SQLPutData viene utilizzato da un'applicazione quando si utilizza l'associazione di righe variabili con parametri con valori di tabella. Il parametro *StrLen_Or_Ind* indica che è possibile che il driver raccolga i dati per la riga o le righe successive dei dati dei parametri con valori di tabella oppure che non siano disponibili altre righe:  
  
-   Un valore maggiore di 0 indica che è disponibile il set di valori di riga successivo.  
  
-   Il valore 0 indica che non sono disponibili altre righe da inviare.  
  
-   Qualsiasi valore minore di 0 rappresenta un errore e restituisce un record di diagnostica registrato con SQLState HY090 e il messaggio "Lunghezza di stringa o di buffer non valida".  
  
 Il parametro *DataPtr* viene ignorato, ma deve essere impostato su un valore non null. Per ulteriori informazioni, vedere la sezione relativa all'associazione di righe di variabile TVP nell' [associazione e trasferimento dati di parametri con valori di tabella e valori di colonna](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Se *StrLen_Or_Ind* ha un valore diverso da SQL_DEFAULT_PARAM o un numero compreso tra 0 e il SQL_PARAMSET_SIZE (ovvero il parametro *ColumnSize* di SQLBindParameter), si tratta di un errore. A causa di questo errore, SQLPutData restituisce SQL_ERROR: SQLSTATE=HY090, "Lunghezza di stringa o di buffer non valida".  
  
 Per ulteriori informazioni sui parametri con valori di tabella, vedere [parametri con valori di tabella &#40;&#41;ODBC ](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>Supporto di SQLPutData per le caratteristiche avanzate di data e ora  
 I valori dei parametri di tipo data/ora vengono convertiti come descritto in [conversioni da C a SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Per ulteriori informazioni, vedere [miglioramenti di data e ora &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>Supporto di SQLPutData per i tipi CLR definiti dall'utente di grandi dimensioni  
 
  `SQLPutData` supporta i tipi CLR definiti dall'utente di grandi dimensioni. Per ulteriori informazioni, vedere [tipi CLR definiti dall'utente di grandi dimensioni &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SQLPutData (funzione)](https://go.microsoft.com/fwlink/?LinkId=59365)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
