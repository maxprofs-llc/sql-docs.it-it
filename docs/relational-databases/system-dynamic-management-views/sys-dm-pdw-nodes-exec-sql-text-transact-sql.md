---
title: sys. dm_pdw_nodes_exec_sql_text (Transact-SQL) | Microsoft Docs
description: Vista a gestione dinamica che restituisce il testo del batch SQL identificato dal sql_handle specificato.
ms.custom: ''
ms.date: 10/14/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: fd886217b2fb2caf0fe3f32e88b7bf0215ece1a9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73145676"
---
# <a name="syspdw_nodes_dm_exec_sql_text-transact-sql"></a>sys. pdw_nodes_dm_exec_sql_text (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Restituisce il testo del batch SQL identificato dal *sql_handle*specificato. Questa funzione con valori di tabella sostituisce la funzione di sistema **fn_get_sql**.  
   
## <a name="table-returned"></a>Tabella restituita  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**pdw_node_id**|**int**|ID numerico univoco associato al nodo.|
|**dbid**|**smallint**|ID del database.<br /><br /> Per le istruzioni SQL non pianificate e preparate, l'ID del database in cui sono state compilate le istruzioni.|  
|**ObjectId**|**int**|ID dell'oggetto.<br /><br /> Per istruzioni SQL ad hoc e preparate viene restituito NULL.|  
|**number**|**smallint**|Per una stored procedure numerata, questa colonna restituisce il numero della stored procedure. Per ulteriori informazioni, vedere [sys. numbered_procedures &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md).<br /><br /> Per istruzioni SQL ad hoc e preparate viene restituito NULL.|  
|**crittografati**|**bit**|1: il testo SQL è crittografato.<br /><br /> 0: il testo SQL non è crittografato.|  
|**text**|**nvarchar(max)**|Testo della query SQL.<br /><br /> Per gli oggetti crittografati viene restituito NULL.|  

## <a name="remarks"></a>Osservazioni  
Si applicano le stesse osservazioni in [sys. dm_exec_sql_text](https://docs.microsoft.com/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql?view=sql-server-ver15) .  
  
## <a name="permissions"></a>Autorizzazioni  
 Richiedere **** il ruolo del server `VIEW SERVER STATE` sysadmin o l'autorizzazione per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Data Warehouse e Parallel data warehouse viste a gestione dinamica &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  

  ## <a name="next-steps"></a>Passaggi successivi
 Per altri suggerimenti sullo sviluppo, vedere [Panoramica sullo sviluppo per SQL Data Warehouse](https://docs.microsoft.com/azure/sql-data-warehouse/sql-data-warehouse-overview-develop).