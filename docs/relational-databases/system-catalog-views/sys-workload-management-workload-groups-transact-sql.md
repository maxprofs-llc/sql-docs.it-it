---
title: sys. workload_management_workload_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/05/2019
ms.prod: sql
ms.technology: system-objects
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.topic: language-reference
dev_langs:
- TSQL
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: =azure-sqldw-latest||=sqlallproducts-allversions
ms.openlocfilehash: 76b5b09a07189db127c970e75dac2894fdbea1ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73633445"
---
# <a name="sysworkload_management_workload_groups-transact-sql"></a>sys. workload_management_workload_groups (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

 Restituisce i dettagli per i gruppi del carico di lavoro.  
  
|Nome colonna|Tipo di dati|Descrizione|Range|  
|-----------------|---------------|-----------------|-----------|
|group_id|**int**|ID univoco del gruppo del carico di lavoro. Non ammette i valori Null.||
|name|**sysname**|Nome del gruppo del carico di lavoro. Deve essere univoco per l'istanza.  Non ammette i valori Null.||
|importance|**nvarchar(128)**|È l'importanza relativa di una richiesta nel gruppo del carico di lavoro e nei gruppi di carico di lavoro per le risorse condivise. Non ammette i valori Null.|Low, below_normal, Normal (impostazione predefinita), above_normal, High||
|min_percentage_resource|**tinyint**|Quantità di risorse garantita per le richieste nel gruppo del carico di lavoro. Le risorse non sono condivise con altri gruppi del carico di lavoro. Non ammette i valori Null.||
|cap_percentage_resource|**tinyint**|Limite rigido sulla percentuale di allocazione delle risorse per le richieste nel gruppo del carico di lavoro. Limita il numero massimo di risorse allocate al livello specificato. L'intervallo consentito per il valore è compreso tra 1 e 100.||
|request_min_resource_grant_percent|**Decimal (5, 2)**|Specifica la quantità minima di risorse allocate a una richiesta. L'intervallo consentito per value è compreso tra 0,75 e 100.||
|request_max_resource_grant_percent |**Decimal (5, 2)**|Specifica la quantità massima di risorse allocate a una richiesta.||
|query_execution_timeout_sec|**int**|Quantità di tempo di esecuzione, in secondi, consentita prima che la query venga annullata.  Le query non possono essere annullate dopo che è stata raggiunta la fase di esecuzione restituita.  in query_execution_timeout_sec non è incluso il tempo impiegato per la coda.|
|query_wait_timeout_sec|**int**|INTERNAL||
|create_time|**datetime**|Ora di creazione del gruppo di carico di lavoro. Non ammette i valori Null.||
modify_time|**datetime**|Ora dell'Ultima modifica del gruppo di carico di lavoro. Non ammette i valori Null.||
|&nbsp;||||
  
## <a name="permissions"></a>Autorizzazioni

È richiesta l'autorizzazione VIEW SERVER STATE.

## <a name="next-steps"></a>Passaggi successivi

 Per un elenco di tutte le viste del catalogo per SQL Data Warehouse e data warehouse parallele, vedere [SQL data warehouse e le viste del catalogo data warehouse parallele](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md). Per creare un gruppo di carico di lavoro, vedere [creare un gruppo di carico di lavoro](../../t-sql/statements/create-workload-group-transact-sql.md). Per ulteriori informazioni sulla classificazione del carico di lavoro, vedere [isolamento dei carichi di lavoro](/azure/sql-data-warehouse/sql-data-warehouse-workload-isolation)
