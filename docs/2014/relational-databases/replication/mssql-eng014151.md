---
title: MSSQL_ENG014151 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014151 error
ms.assetid: 54b45e70-46b3-4c7a-a5bf-06f6dd028ceb
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1f292841c227db26f1c518b2eaef896f7ce3570c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63191464"
---
# <a name="mssql_eng014151"></a>MSSQL_ENG014151
    
## <a name="message-details"></a>Dettagli messaggio  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|14151|  
|Origine evento|MSSQLSERVER|  
|Componente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nome simbolico||  
|Testo del messaggio|Replica-%s: l'esecuzione dell'agente %s non è riuscita. %s|  
  
## <a name="explanation"></a>Spiegazione  
 Questo errore viene generato per qualunque errore dell'agente di replica. Il testo alla fine del messaggio dipende dal contesto dell'errore.  
  
## <a name="user-action"></a>Azione dell'utente  
 Questo errore può verificarsi in numerose situazioni. Utilizzare gli approcci seguenti in base alla necessità:  
  
-   Riavviare l'agente che ha presentato l'errore per vedere se viene eseguito senza errori. Per altre informazioni, vedere [Avviare e arrestare un agente di replica &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) e [Concetti di base relativi ai file eseguibili dell'agente di replica](concepts/replication-agent-executables-concepts.md).  
  
-   Verificare nella cronologia dell'agente e nella cronologia processo la presenza di eventuali altri errori verificatisi nello stesso momento. Per informazioni sui dettagli di stato e di errore dell'agente di visualizzazione in Monitoraggio replica, vedere [Visualizzare le informazioni ed eseguire attività usando Monitoraggio replica](monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
-   Verificare il funzionamento della connettività di base tra i computer a cui l'agente accede, quindi connettersi a ogni computer con un'utilità come [sqlcmd Utility](../../tools/sqlcmd-utility.md). Quando ci si connette, utilizzare lo stesso account con cui l'agente effettua le connessioni. Per ulteriori informazioni sulle autorizzazioni richieste da ogni account di agente, vedere [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
-   Se l'errore si verifica durante la creazione o l'applicazione di uno snapshot, verificare l'eventuale presenza di errori nei file della directory snapshot.  
  
-   Se l'errore continua a verificarsi, aumentare il livello di dettaglio per la registrazione delle operazioni dell'agente e specificare un file di output per il log. A seconda del contesto dell'errore, in questo modo si potrebbero ottenere ulteriori informazioni sui passaggi che conducono all'errore e/o messaggi di errore aggiuntivi.  
  
## <a name="see-also"></a>Vedere anche  
 [Amministrazione dell'agente di replica](agents/replication-agent-administration.md)   
 [Guida di riferimento a errori ed eventi &#40;replica&#41;](errors-and-events-reference-replication.md)   
 [Replication Distribution Agent](agents/replication-distribution-agent.md)   
 [Replication Log Reader Agent](agents/replication-log-reader-agent.md)   
 [Replication Merge Agent](agents/replication-merge-agent.md)   
 [Agente di lettura coda repliche](agents/replication-queue-reader-agent.md)   
 [Replication Snapshot Agent](agents/replication-snapshot-agent.md)  
  
  
