---
title: Statistiche sulle query dinamiche | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- query statistics [SQL Server] live query stats
- live query statistics
- debugging [SQL Server], live query stats
- statistics [SQL Server], live query statistics
- query profiling
- lightweight query profiling
- lightweight profiling
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753e
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 03e19dd52f7ea996690eaf55bad9cdf9d5eccb6b
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "78256947"
---
# <a name="live-query-statistics"></a>Live Query Statistics
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] consente di visualizzare il piano di esecuzione dinamico di una query attiva. Il piano dinamico delle query offre informazioni approfondite in tempo reale sul processo di esecuzione della query, man mano che i controlli passano da un [operatore del piano di query](../../relational-databases/showplan-logical-and-physical-operators-reference.md) a un altro. Il piano dinamico delle query visualizza lo stato complessivo delle query e le statistiche di esecuzione a livello di operatore, ad esempio il numero di righe prodotte, il tempo trascorso, lo stato di avanzamento dell'operatore e così via. Poiché questi dati sono disponibili in tempo reale senza dover attendere il completamento della query, queste statistiche di esecuzione sono estremamente utili per il debug di problemi relativi alle prestazioni delle query. Questa funzionalità è disponibile a partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ma può funzionare con [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  

> [!NOTE]
> Internamente le statistiche sulle query dinamiche sfruttano la DMV [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md).
  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]) e [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
> [!WARNING]  
> Questa funzionalità viene usata principalmente per la risoluzione dei problemi. L'uso di questa funzionalità può rallentare in parte le prestazioni complessive delle query, in particolare in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]. Per altre informazioni, vedere [Infrastruttura di profilatura query](../../relational-databases/performance/query-profiling-infrastructure.md).  
> Questa funzionalità può essere usata con il [debugger Transact-SQL](../../relational-databases/scripting/configure-firewall-rules-before-running-the-tsql-debugger.md).  
  
## <a name="to-view-live-query-statistics-for-one-query"></a>Per visualizzare le statistiche sulle query dinamiche per una query 
  
1.  Per visualizzare il piano di esecuzione dinamico delle query, dal menu degli strumenti scegliere l'icona **Includi statistiche query dinamiche**.  
  
     ![Pulsante Statistiche query dinamiche sulla barra degli strumenti](../../relational-databases/performance/media/livequerystatstoolbar.png "Pulsante Statistiche query dinamiche sulla barra degli strumenti")  
  
     È anche possibile accedere al piano di esecuzione dinamico delle query facendo clic con il pulsante destro del mouse su una query selezionata in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] e quindi scegliendo **Includi statistiche query dinamiche**.  
  
     ![Pulsante Statistiche query dinamiche nel menu popup](../../relational-databases/performance/media/livequerystatsmenu.png "Pulsante Statistiche query dinamiche nel menu popup")  
  
2.  A questo punto, eseguire la query. Il piano di query dinamiche descrive lo stato di avanzamento complessivo delle query e le statistiche di esecuzione, ad esempio il tempo trascorso, lo stato di avanzamento e così via, degli operatori del piano di query. Le informazioni sullo stato di avanzamento e le statistiche di esecuzione delle query vengono aggiornate periodicamente durante l'esecuzione delle query. Usare queste informazioni per comprendere il processo generale di esecuzione delle query e per eseguire il debug di query a esecuzione prolungata, query eseguite per un periodo illimitato, query che causano l'overflow di tempdb e problemi di timeout.  
  
     ![Pulsante Statistiche query dinamiche in showplan](../../relational-databases/performance/media/livequerystatsplan.png "Pulsante Statistiche query dinamiche in showplan")  
  
## <a name="to-view-live-query-statistics-for-any-query"></a>Per visualizzare le statistiche sulle query dinamiche per qualsiasi query 

È anche possibile accedere al piano di esecuzione dinamico delle query da **[Monitoraggio attività](../../relational-databases/performance-monitor/activity-monitor.md)** facendo clic con il pulsante destro del mouse su qualsiasi query nella tabella **Processi** o **Query attive con costo elevato**.  
  
 ![Pulsante Statistiche query dinamiche in Monitoraggio attività](../../relational-databases/performance/media/livequerystatsactmon.png "Pulsante Statistiche query dinamiche in Monitoraggio attività")  
  
## <a name="remarks"></a>Osservazioni  
 Perché le statistiche delle query dinamiche possano acquisire informazioni sullo stato di avanzamento delle query, è necessario che l'infrastruttura del profilo delle statistiche sia stata abilitata. A seconda della versione, l'overhead può essere notevole. Per altre informazioni su questo overhead, vedere [Infrastruttura di profilatura query](../../relational-databases/performance/query-profiling-infrastructure.md).
  
## <a name="permissions"></a>Autorizzazioni  
Sono richieste l'autorizzazione a livello di database `SHOWPLAN` per popolare la pagina dei risultati **Statistiche query dinamiche** e le autorizzazioni necessarie per eseguire la query.
In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è richiesta l'autorizzazione a livello di server `VIEW SERVER STATE` per visualizzare le statistiche dinamiche.  
Nei livelli [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Premium è richiesta l'autorizzazione `VIEW DATABASE STATE` nel database per visualizzare le statistiche dinamiche. Nei livelli [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard e Basic è richiesto l'account **Amministratore server** o **Amministratore Azure Active** per visualizzare le statistiche dinamiche.
  
## <a name="see-also"></a>Vedere anche  
 [Piani di esecuzione](../../relational-databases/performance/execution-plans.md)    
 [Guida sull'architettura di elaborazione delle query](../../relational-databases/query-processing-architecture-guide.md)    
 [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Strumenti per il monitoraggio e l'ottimizzazione delle prestazioni](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Aprire Monitoraggio attività &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)     
 [Monitoraggio attività](../../relational-databases/performance-monitor/activity-monitor.md)     
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)     
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)     
 [Flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)    
 [Guida di riferimento a operatori Showplan logici e fisici](../../relational-databases/showplan-logical-and-physical-operators-reference.md)     
 [Infrastruttura di profilatura query](../../relational-databases/performance/query-profiling-infrastructure.md)   
