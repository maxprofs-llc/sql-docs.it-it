---
title: sys. dm_os_performance_counters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_performance_counters
- sys.dm_os_performance_counters_TSQL
- dm_os_performance_counters_TSQL
- sys.dm_os_performance_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_performance_counters dynamic management view
ms.assetid: a1c3e892-cd48-40d4-b6be-2a9246e8fbff
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5c7b4d78f73af003e93bc662f10f1f95acda2b6a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265707"
---
# <a name="sysdm_os_performance_counters-transact-sql"></a>sys.dm_os_performance_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per contatore delle prestazioni gestito dal server. Per informazioni su ogni contatore delle prestazioni, vedere [usare oggetti SQL Server](../../relational-databases/performance-monitor/use-sql-server-objects.md).  
  
> [!NOTE]  
>  Per chiamare questo oggetto [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] da [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]o, usare il nome **sys. dm_pdw_nodes_os_performance_counters**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**object_name**|**nchar (128)**|Categoria di appartenenza del contatore.|  
|**counter_name**|**nchar (128)**|Nome del contatore. Per ottenere ulteriori informazioni su un contatore, questo è il nome dell'argomento da selezionare dall'elenco di contatori in [utilizzare SQL Server oggetti](../../relational-databases/performance-monitor/use-sql-server-objects.md). |  
|**instance_name**|**nchar (128)**|Nome dell'istanza specifica del contatore. Spesso include il nome del database.|  
|**cntr_value**|**bigint**|Valore corrente del contatore.<br /><br /> **Nota:** Per i contatori per secondo, questo valore è cumulativo. Il valore relativo alla frequenza deve essere calcolato tramite il campionamento del valore a intervalli di tempo discreti. La differenza tra due valori di campionamento successivi è uguale alla frequenza dell'intervallo di tempo utilizzato.|  
|**cntr_type**|**int**|Tipo di contatore definito dall'architettura di controllo delle prestazioni di Windows. Per ulteriori informazioni sui tipi di contatori delle prestazioni, vedere [tipi di contatori delle prestazioni WMI](https://docs.microsoft.com/windows/desktop/WmiSdk/wmi-performance-counter-types) in docs o nella documentazione di Windows Server.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Identificatore del nodo su cui si trova questa distribuzione.|  
  
## <a name="remarks"></a>Osservazioni  
 Se l'istanza dell'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non è in grado di visualizzare i contatori delle prestazioni del sistema operativo Windows, utilizzare la query [!INCLUDE[tsql](../../includes/tsql-md.md)] seguente per verificare se i contatori delle prestazioni sono stati disabilitati.  
  
```  
SELECT COUNT(*) FROM sys.dm_os_performance_counters;  
```  
  
 Se il valore restituito è di 0 righe, i contatori delle prestazioni sono stati disabilitati. È necessario quindi analizzare il log del programma di installazione e ricercare l'errore 3409 "Reinstallare sqlctr.ini e verificare che l'account di accesso dell'istanza disponga delle autorizzazioni di Registro di sistema appropriate".  Questo errore indica che i contatori delle prestazioni non sono stati abilitati. Gli errori immediatamente precedenti all'errore 3409 dovrebbero indicare la causa principale per l'errore relativo all'abilitazione dei contatori delle prestazioni. Per ulteriori informazioni sui file di log del programma di installazione, vedere [visualizzare e leggere SQL Server file di log del programma di installazione](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
## <a name="permission"></a>Autorizzazione

In [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]è richiesta `VIEW SERVER STATE` l'autorizzazione.   
Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli Premium, richiede l' `VIEW DATABASE STATE` autorizzazione nel database. Nei [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] livelli standard e Basic, richiede l' **amministratore del server** o un account **amministratore Azure Active Directory** .   
 
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituiti i valori dei contatori di prestazioni.  
  
```  
SELECT object_name, counter_name, instance_name, cntr_value, cntr_type  
FROM sys.dm_os_performance_counters;  
  
```  
  
## <a name="see-also"></a>Vedere anche  
  [SQL Server viste a gestione dinamica relative al sistema operativo &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  


