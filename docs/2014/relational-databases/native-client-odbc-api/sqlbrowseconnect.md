---
title: SQLBrowseConnect | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBrowseConnect function
ms.assetid: 57faf388-c7ca-4696-9845-34e0a10cc5f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d9cb9439dd76c636df46b8ac3d737d79415b5ea5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067665"
---
# <a name="sqlbrowseconnect"></a>SQLBrowseConnect
  **SQLBrowseConnect** utilizza parole chiave che possono essere categorizzate in tre livelli di informazioni di connessione. Per ogni parola chiave nella tabella seguente è indicato se viene restituito un elenco di valori validi e se la parola chiave è facoltativa.  
  
## <a name="level-1"></a>Livello 1  
  
|Parola chiave|Elenco restituito?|Facoltativa?|Descrizione|  
|-------------|--------------------|---------------|-----------------|  
|DSN|N/D|No|Nome dell'origine dati restituita da **SQLDataSources**. Se viene utilizzata la parola chiave DRIVER, non è possibile utilizzare la parola chiave DSN.|  
|DRIVER|N/D|No|Microsoft? [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Il nome del driver ODBC di Native[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client è {Native Client 11}. Se viene utilizzata la parola chiave DSN, non è possibile utilizzare la parola chiave DRIVER.|  
  
## <a name="level-2"></a>Level 2  
  
|Parola chiave|Elenco restituito?|Facoltativa?|Descrizione|  
|-------------|--------------------|---------------|-----------------|  
|SERVER|Sì|No|Nome del server in rete nel quale risiede l'origine dati. È consentita la specifica del termine "(local)" per indicare il server. In questo caso, è possibile utilizzare una copia locale di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], anche quando si tratta di una versione non in rete.|  
|UID|No|Sì|ID di accesso dell'utente.|  
|PWD|No|Sì (dipende dall'utente)|Password specificata dall'utente.|  
|APP|No|Sì|Nome dell'applicazione che chiama **SQLBrowseConnect**.|  
|WSID|No|Sì|ID della workstation. In genere, si tratta del nome di rete del computer sul quale viene eseguita l'applicazione.|  
  
## <a name="level-3"></a>Level 3  
  
|Parola chiave|Elenco restituito?|Facoltativa?|Descrizione|  
|-------------|--------------------|---------------|-----------------|  
|DATABASE|Sì|Sì|Nome del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|LANGUAGE|Sì|Sì|Lingua nazionale utilizzata in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
  
 **SQLBrowseConnect** ignora i valori delle parole chiave del database e della lingua archiviate nelle definizioni dell'origine dati ODBC. Se il database o la lingua specificata nella stringa di connessione passata a **SQLBrowseConnect** non è valida, **SQLBrowseConnect** restituisce SQL_NEED_DATA e gli attributi di connessione di livello 3.  
  
 Gli attributi seguenti, impostati chiamando [SQLSetConnectAttr](sqlsetconnectattr.md), determinano il set di risultati restituito da **SQLBrowseConnect**.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|SQL_COPT_SS_BROWSE_CONNECT|Se è impostato su SQL_MORE_INFO_YES, **SQLBrowseConnect** restituisce una stringa estesa di proprietà del server.<br /><br /> Di seguito è riportato un esempio di una stringa estesa restituita da **SQLBrowseConnect**: nomeserver\nomeistanza; In cluster: No; Versione: 8.00.131<br /><br /> In questa stringa i punti e virgola separano le diverse informazioni sul server. Le virgole separano le diverse istanze del server.|  
|SQL_COPT_SS_BROWSE_SERVER|Se viene specificato un nome di server, **SQLBrowseConnect** restituirà informazioni per il server specificato. Se SQL_COPT_SS_BROWSE_SERVER è impostato su NULL, **SQLBrowseConnect** restituisce informazioni per tutti i server nel dominio.<br /><br /> A causa di problemi di rete, **SQLBrowseConnect** potrebbe non ricevere una risposta tempestiva da tutti i server. L'elenco di server restituito può pertanto variare per ogni richiesta.|  
|SQL_COPT_SS_BROWSE_CACHE_DATA|Quando l'attributo SQL_COPT_SS_BROWSE_CACHE_DATA è impostato su SQL_CACHE_DATA_YES, è possibile recuperare i dati in blocchi quando la lunghezza del buffer non è sufficiente per contenere il risultato. Questa lunghezza viene specificata nell'argomento BufferLength per SQLBrowseConnect.<br /><br /> Quando sono disponibili più dati, viene restituito SQL_NEED_DATA. Quando non vi sono più dati da recuperare, viene restituito SQL_SUCCESS.<br /><br /> Il valore predefinito è SQL_CACHE_DATA_NO.|  
  
## <a name="sqlbrowseconnect-support-for-high-availability-disaster-recovery"></a>Supporto di SQLBrowseConnect per il ripristino di emergenza a disponibilità elevata  
 Per altre informazioni sull'uso di **SQLBrowseConnect** per la connessione [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] a un cluster, vedere [SQL Server Native client supporto per la disponibilità elevata e il ripristino di emergenza](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).  
  
## <a name="sqlbrowseconnect-support-for-service-principal-names-spns"></a>Supporto di SQLBrowseConnect per i nomi SPN (Service Principal Name)  
 Quando si apre una connessione, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client imposta SQL_COPT_SS_MUTUALLY_AUTHENTICATED e SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD sul metodo di autenticazione utilizzato per aprire la connessione.  
  
 Per ulteriori informazioni sui nomi SPN, vedere [nomi dell'entità servizio &#40;spn&#41; nelle connessioni Client &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).  
  
## <a name="change-history"></a>Cronologia modifiche  
  
|Contenuto aggiornato|  
|---------------------|  
|Informazioni su SQL_COPT_SS_BROWSE_CACHE_DATA.|  
  
## <a name="see-also"></a>Vedere anche  
 [SQLBrowseConnect (funzione)](https://go.microsoft.com/fwlink/?LinkId=59329)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
