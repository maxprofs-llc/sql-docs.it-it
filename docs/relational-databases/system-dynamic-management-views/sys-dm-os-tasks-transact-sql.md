---
title: sys. dm_os_tasks (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_tasks
- sys.dm_os_tasks_TSQL
- dm_os_tasks_TSQL
- dm_os_tasks
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_tasks dynamic management view
ms.assetid: 180a3c41-e71b-4670-819d-85ea7ef98bac
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 086065aa79ca6fba7ad84e5b7e7f99f6f462f7dd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "74164903"
---
# <a name="sysdm_os_tasks-transact-sql"></a>sys.dm_os_tasks (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per ogni attività in corso nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Un'attività è l'unità di base di esecuzione in SQL Server. Esempi di attività includono una query, un account di accesso, una disconnessione e attività di sistema come attività di pulizia fantasma, attività Checkpoint, writer di log, attività di rollforward parallela. Per ulteriori informazioni sulle attività, vedere la [Guida all'architettura dei thread e delle attività](../../relational-databases/thread-and-task-architecture-guide.md).
  
> [!NOTE]  
> Per chiamare questo oggetto [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]o, usare il nome **sys. dm_pdw_nodes_os_tasks**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**task_address**|**varbinary (8)**|Indirizzo di memoria dell'oggetto.|  
|**task_state**|**nvarchar (60)**|Stato dell'attività. Può essere uno dei valori seguenti:<br /><br /> PENDING: in attesa di un thread di lavoro.<br /><br /> RUNNABLE: eseguibile, ma in attesa di ricevere un quantum.<br /><br /> RUNNING: esecuzione in corso nell'utilità di pianificazione.<br /><br /> SUSPENDED: è disponibile un thread di lavoro, ma è in attesa di un evento.<br /><br /> DONE: completato.<br /><br /> SPINLOOP: bloccato in uno spinlock.|  
|**context_switches_count**|**int**|Numero di cambi di contesto dell'utilità di pianificazione completati dall'attività.|  
|**pending_io_count**|**int**|Numero di I/O fisici eseguiti dall'attività.|  
|**pending_io_byte_count**|**bigint**|Numero totale di byte degli I/O eseguiti dall'attività.|  
|**pending_io_byte_average**|**int**|Numero medio di byte degli I/O eseguiti dall'attività.|  
|**scheduler_id**|**int**|ID dell'utilità di pianificazione padre. Si tratta di un handle per le informazioni dell'utilità di pianificazione per l'attività. Per ulteriori informazioni, vedere [sys. dm_os_schedulers &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md).|  
|**session_id**|**smallint**|ID della sessione associata all'attività.|  
|**exec_context_id**|**int**|ID del contesto di esecuzione associato all'attività.|  
|**request_id**|**int**|ID della richiesta dell'attività. Per ulteriori informazioni, vedere [sys. dm_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md).|  
|**worker_address**|**varbinary (8)**|Indirizzo di memoria del thread di lavoro che sta eseguendo l'attività.<br /><br /> NULL = Per poter essere eseguita, l'attività è in attesa di un thread di lavoro oppure l'esecuzione dell'attività è stata completata.<br /><br /> Per ulteriori informazioni, vedere [sys. dm_os_workers &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md).|  
|**host_address**|**varbinary (8)**|Indirizzo di memoria dell'host.<br /><br /> 0 = Per creare l'attività non è stato utilizzato alcun host. Ciò semplifica l'identificazione dell'host utilizzato per creare l'attività.<br /><br /> Per ulteriori informazioni, vedere [sys. dm_os_hosts &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-os-hosts-transact-sql.md).|  
|**parent_task_address**|**varbinary (8)**|Indirizzo di memoria dell'attività padre dell'oggetto.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificatore del nodo su cui si trova questa distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni
In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]è richiesta `VIEW SERVER STATE` l'autorizzazione.   
Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, richiede l' `VIEW DATABASE STATE` autorizzazione nel database. Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli standard e Basic, richiede l' **amministratore del server** o un account **amministratore Azure Active Directory** .   

## <a name="examples"></a>Esempi  
  
### <a name="a-monitoring-parallel-requests"></a>R. Monitoraggio di richieste in parallelo  
 Per le richieste eseguite in parallelo, vengono visualizzate più righe per la stessa combinazione di (\<**session_id**>, \< **request_id**>). Usare la query seguente per trovare l' [opzione di configurazione del server max degree of parallelism](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md) per tutte le richieste attive.  
  
> [!NOTE]  
>  Una **request_id** è univoca all'interno di una sessione.  
  
```  
SELECT  
    task_address,  
    task_state,  
    context_switches_count,  
    pending_io_count,  
    pending_io_byte_count,  
    pending_io_byte_average,  
    scheduler_id,  
    session_id,  
    exec_context_id,  
    request_id,  
    worker_address,  
    host_address  
  FROM sys.dm_os_tasks  
  ORDER BY session_id, request_id;  
```  
  
### <a name="b-associating-session-ids-with-windows-threads"></a>B. Associazione di ID di sessione con thread di Windows  
 È possibile utilizzare la query seguente per associare un valore di ID di sessione a un ID di thread di Windows. È possibile monitorare le prestazioni del thread utilizzando Performance Monitor di Windows. La query seguente non restituisce informazioni per le sessioni sospese.  
  
```  
SELECT STasks.session_id, SThreads.os_thread_id  
  FROM sys.dm_os_tasks AS STasks  
  INNER JOIN sys.dm_os_threads AS SThreads  
    ON STasks.worker_address = SThreads.worker_address  
  WHERE STasks.session_id IS NOT NULL  
  ORDER BY STasks.session_id;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
[SQL Server viste a gestione dinamica relative al sistema operativo &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
[Guida sull'architettura dei thread e delle attività](../../relational-databases/thread-and-task-architecture-guide.md)     
  


