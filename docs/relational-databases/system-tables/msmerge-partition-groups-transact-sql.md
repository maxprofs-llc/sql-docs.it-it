---
title: MSmerge_partition_groups (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_partition_groups_TSQL
- MSmerge_partition_groups
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_partition_groups system table
ms.assetid: 5d56d780-ee40-4afc-9c2a-d1723d86e430
author: stevestein
ms.author: sstein
ms.openlocfilehash: 362735d33f835c7b66e4f0994fd5c4ff6f084f15
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68102190"
---
# <a name="msmerge_partition_groups-transact-sql"></a>MSmerge_partition_groups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  La tabella **MSmerge_partition_groups** archivia una riga per ogni partizione pre-calcolata in un database specifico. Oltre alle colonne elencate, a questa tabella viene aggiunta una colonna per ogni funzione utilizzata in un filtro di riga con parametri. Se, ad esempio, un filtro utilizza la funzione [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) , viene aggiunta una colonna denominata **HOST_NAME_FN** alla tabella. Viene archiviata una riga per ogni set univoco di valori di funzione sincronizzati con il server di pubblicazione corrente. Due o più Sottoscrittori che eseguono la sincronizzazione in base allo stesso valore per tutte le funzioni dovranno condividere la stessa riga della tabella e pertanto lo stesso ID di partizione. La tabella è archiviata nel database di pubblicazione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|Colonna Identity che offre un numero di ID univoco per la partizione pre-calcolata.|  
|**publication_number**|**smallint**|Numero di pubblicazione archiviato in **sysmergepublications**.|  
|**maxgen_whenadded**|**bigint**|Generazione con valore maggiore nota nel server di pubblicazione al momento dell'inserimento della riga nella tabella.|  
|**using_partition_groups**|**bit**|Indica se la partizione appartiene a una pubblicazione che utilizza partizioni pre-compilate. I possibili valori sono i seguenti.<br /><br /> **0** = la pubblicazione non utilizza partizioni pre-calcolate.<br /><br /> **1** = la pubblicazione utilizza partizioni pre-calcolate<br /><br /> Per altre informazioni, vedere [Ottimizzare le prestazioni dei filtri con parametri con le partizioni pre-calcolate](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).|  
|**HOST_NAME_FN**|**nvarchar(128)**|Valore specificato in caso di utilizzo di filtri di riga con parametri per generare partizioni. Per altre informazioni sui filtri di riga con parametri, vedere [Filtri di riga con parametri](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
