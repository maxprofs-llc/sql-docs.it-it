---
title: Funzione SQLWriteDSNToIni | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWriteDSNToIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteDSNToIni
helpviewer_keywords:
- SQLWriteDSNToIni [ODBC]
ms.assetid: dc7018b2-18d4-4657-96d0-086479a47474
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8eece6a1347aa7fba41577f66493e35f92a69d6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68039515"
---
# <a name="sqlwritedsntoini-function"></a>Funzione SQLWriteDSNToIni
**Conformità**  
 Versione introdotta: ODBC 1,0  
  
 **Summary**  
 **SQLWriteDSNToIni** aggiunge un'origine dati alle informazioni sul sistema.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Argomenti  
 *lpszDSN*  
 Input Nome dell'origine dati da aggiungere.  
  
 *lpszDriver*  
 Input Descrizione del driver (in genere il nome del DBMS associato) presentata agli utenti anziché al nome del driver fisico.  
  
## <a name="returns"></a>Valori di codice restituiti  
 La funzione restituisce TRUE se ha esito positivo, FALSE in caso di esito negativo.  
  
## <a name="diagnostics"></a>Diagnostica  
 Quando **SQLWriteDSNToIni** restituisce false, è possibile ottenere un valore * \*pfErrorCode* associato chiamando **SQLInstallerError**. La tabella seguente elenca i * \*valori pfErrorCode* che possono essere restituiti da **SQLInstallerError** e ne illustra ognuno nel contesto di questa funzione.  
  
|*\*pfErrorCode*|Errore|Descrizione|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Errore generale del programma di installazione|Si è verificato un errore per il quale non è stato specificato alcun errore di programma di installazione.|  
|ODBC_ERROR_INVALID_DSN|DSN non valido|L'argomento *lpszDSN* contiene una stringa non valida per un DSN.|  
|ODBC_ERROR_INVALID_NAME|Nome del driver o del traduttore non valido|L'argomento *lpszDriver* non è valido.|  
|ODBC_ERROR_REQUEST_FAILED|Richiesta non riuscita|Il programma di installazione non è riuscito a creare un DSN nel registro di sistema.|  
|ODBC_ERROR_OUT_OF_MEM|Memoria insufficiente|Il programma di installazione non è riuscito a eseguire la funzione a causa di memoria insufficiente.|  
  
## <a name="comments"></a>Commenti  
 **SQLWriteDSNToIni** aggiunge l'origine dati alla sezione [origini dati ODBC] delle informazioni sul sistema. Viene quindi creata una sezione specifica per l'origine dati e viene aggiunta una singola parola chiave (**driver**) con il nome della dll del driver come valore. Se la sezione specifica dell'origine dati esiste già, **SQLWriteDSNToIni** rimuove la sezione precedente prima di crearne una nuova.  
  
 Il chiamante di questa funzione deve aggiungere eventuali parole chiave e valori specifici del driver alla sezione relativa alla specifica dell'origine dati delle informazioni sul sistema.  
  
 Se il nome dell'origine dati è predefinito, **SQLWriteDSNToIni** crea anche la sezione specifica driver predefinita nelle informazioni di sistema.  
  
 Questa funzione deve essere chiamata solo da una DLL di installazione.  
  
## <a name="related-functions"></a>Funzioni correlate  
  
|Per informazioni su|Vedere|  
|---------------------------|---------|  
|Aggiunta, modifica o rimozione di un'origine dati|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(nella DLL di installazione)|  
|Aggiunta, modifica o rimozione di un'origine dati|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Rimozione di un nome di origine dati dalle informazioni di sistema|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|
