---
title: 'Classe di evento TM: Rollback Tran Completed| Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- 'TM: Rollback Tran Completed event class'
ms.assetid: af4043db-bc9f-4cd8-8d07-ef3efae85148
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 105c5da23d5d827271c5c94c70b293acf051d1aa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63061333"
---
# <a name="tm-rollback-tran-completed-event-class"></a>TM: Rollback Tran Completed - classe di evento
  La classe di evento TM: Rollback Tran Completed indica il completamento di una richiesta ROLLBACK TRANSACTION. La richiesta è stata inviata dal client tramite l'interfaccia di gestione delle transazioni. La colonna EventSubClass indica se una nuova transazione verrà avviata dopo il rollback della transazione corrente.  
  
## <a name="tm-rollback-tran-completed-event-class-data-columns"></a>Colonne di dati della classe di evento TM: Rollback Tran Completed  
  
|Nome colonna di dati|Tipo di dati|Descrizione|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|ClientProcessID|`int`|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se tramite il client viene indicato l'ID del processo client.|9|Sì|  
|DatabaseID|`int`|ID del database specificato nell'istruzione USE *database* oppure il database predefinito se non è stata eseguita alcuna istruzione USE *database* per una determinata istanza. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]consente di visualizzare il nome del database se la colonna di dati ServerName viene acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|DatabaseName|`nvarchar`|Nome del database nel quale viene eseguita l'istruzione dell'utente.|35|Sì|  
|Errore|`int`|Numero di errore di un evento specifico. Corrisponde spesso al numero di errore archiviato nella tabella sys.messages.|31|Sì|  
|EventClass|`int`|Tipo di evento = 188.|27|No|  
|EventSequence|`int`|Sequenza di un determinato evento all'interno della richiesta.|51|No|  
|EventSubClass|`int`|Tipo di sottoclasse di evento.<br /><br /> 1=Rollback<br /><br /> 2=Rollback e inizio|21|Sì|  
|GroupID|`int`|ID del gruppo del carico di lavoro in cui viene generato l'evento di Traccia SQL.|66|Sì|  
|HostName|`nvarchar`|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il client fornisce il nome host. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|IsSystem|`int`|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Sì|  
|LoginName|`nvarchar`|Nome dell'account di accesso dell'utente (account di accesso di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows nel formato DOMINIO\nomeutente).|11|Sì|  
|LoginSid|`image`|ID di sicurezza (SID) dell'utente connesso. Queste informazioni sono disponibili nella vista del catalogo sys.server_principals. Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|NTDomainName|`nvarchar`|Dominio Windows di appartenenza dell'utente.|7|Sì|  
|NTUserName|`nvarchar`|Nome utente di Windows.|6|Sì|  
|RequestID|`int`|ID della richiesta contenente l'istruzione.|49|Sì|  
|ServerName|`nvarchar`|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|SessionLoginName|`nvarchar`|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, SessionLoginName indica Login1 e LoginName indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Sì|  
|SPID|`int`|ID della sessione in cui si è verificato l'evento.|12|Sì|  
|StartTime|`datetime`|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|Operazione completata|`int`|1 = esito positivo. 0 = esito negativo (ad esempio, 1 indica che un controllo delle autorizzazioni ha avuto esito positivo, 0 che l'esito è stato negativo).|23|Sì|  
|TextData|`ntext`|Valore di testo che dipende dalla classe di evento acquisita nella traccia.|1|Sì|  
|TransactionID|`bigint`|ID della transazione assegnato dal sistema.|4|Sì|  
|XactSequence|`bigint`|Token utilizzato per descrivere la transazione corrente.|50|Sì|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)   
 [ROLLBACK TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/rollback-transaction-transact-sql)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
