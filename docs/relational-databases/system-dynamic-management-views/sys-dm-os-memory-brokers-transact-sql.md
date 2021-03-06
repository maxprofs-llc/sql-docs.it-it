---
title: sys. dm_os_memory_brokers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_brokers
- dm_os_memory_brokers_TSQL
- sys.dm_os_memory_brokers_TSQL
- dm_os_memory_brokers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_brokers dynamic management view
ms.assetid: 48dd6ad9-0d36-4370-8a12-4921d0df4b86
author: stevestein
ms.author: sstein
ms.openlocfilehash: a8e131e2550ffa5078df5e284898ffe936128b7e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265870"
---
# <a name="sysdm_os_memory_brokers-transact-sql"></a>sys.dm_os_memory_brokers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Le allocazioni interne a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizzano il gestore della memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Il rilevamento delle differenze tra i contatori della memoria del processo da **sys. dm_os_process_memory** e i contatori interni può indicare l'utilizzo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] della memoria da parte dei componenti esterni nello spazio di memoria.  
  
 I broker della memoria distribuiscono equamente le allocazioni di memoria tra i vari componenti all'interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], in base all'utilizzo corrente e previsto. I broker di memoria non eseguono allocazioni. Le registrano solo per calcolare la distribuzione.  
  
 Nella tabella seguente sono disponibili informazioni sui broker di memoria.  
  
> [!NOTE]  
>  Per chiamare questo oggetto [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]o, usare il nome **sys. dm_pdw_nodes_os_memory_brokers**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**pool_id**|**int**|ID del pool di risorse se associato a un pool di Resource Governor.|  
|**memory_broker_type**|**nvarchar (60)**|Tipo di broker di memoria. Esistono attualmente tre tipi di broker di memoria in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], elencati di seguito con le relative descrizioni.<br /><br /> **MEMORYBROKER_FOR_CACHE** : memoria allocata per l'utilizzo da oggetti memorizzati nella cache (non cache del pool di buffer).<br /><br /> **MEMORYBROKER_FOR_STEAL** : memoria rubata dal pool di buffer. Tale memoria non è disponibile per il riutilizzo da parte di altri componenti fino a che non viene liberata dal proprietario corrente.<br /><br /> **MEMORYBROKER_FOR_RESERVE** : memoria riservata per l'uso futuro da richieste attualmente in esecuzione.|  
|**allocations_kb**|**bigint**|Quantità di memoria, in kilobyte (KB), allocata a questo tipo di broker.|  
|**allocations_kb_per_sec**|**bigint**|Velocità delle allocazioni di memoria in kilobyte (KB) al secondo. Il valore può essere negativo per le deallocazioni di memoria.|  
|**predicted_allocations_kb**|**bigint**|Quantità stimata di memoria allocata dal broker. Si basa sul modello di utilizzo della memoria.|  
|**target_allocations_kb**|**bigint**|Quantità consigliata di memoria allocata, in kilobyte (KB) basata sulle impostazioni correnti e sul modello di utilizzo della memoria. Il broker deve crescere o diminuire fino a questo numero.|  
|**future_allocations_kb**|**bigint**|Numero previsto di allocazioni, in kilobyte (KB), che verranno effettuate nei prossimi secondi.|  
|**overall_limit_kb**|**bigint**|Quantità massima di memoria, espressa in kilobyte (KB), che può essere allocata dal broker.|  
|**last_notification**|**nvarchar (60)**|Indicazione sull'utilizzo della memoria basato sulle impostazioni correnti e sul modello di utilizzo. I valori validi sono i seguenti:<br /><br /> grow<br /><br /> shrink<br /><br /> stable|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificatore del nodo su cui si trova questa distribuzione.|  
  
## <a name="permissions"></a>Autorizzazioni  

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]è richiesta `VIEW SERVER STATE` l'autorizzazione.   
Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, richiede l' `VIEW DATABASE STATE` autorizzazione nel database. Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli standard e Basic, richiede l' **amministratore del server** o un account **amministratore Azure Active Directory** .   
  
## <a name="see-also"></a>Vedere anche  

  [SQL Server viste a gestione dinamica relative al sistema operativo &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


