---
title: sys. stats_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- stats_columns_TSQL
- stats_columns
- sys.stats_columns
- sys.stats_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.stats_columns catalog view
ms.assetid: 93414d07-97e9-4501-8577-f35b8d68fbe9
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6abf636a371047f344861f09affaa1dd9f7d82de
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108967"
---
# <a name="sysstats_columns-transact-sql"></a>sys.stats_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una riga per ogni colonna che fa parte delle statistiche **sys. stats** .  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|ID dell'oggetto a cui la colonna appartiene.|  
|**stats_id**|**int**|ID delle statistiche a cui la colonna appartiene.<br /><br />Se le statistiche corrispondono a un indice, il valore *stats_id* corrisponde al valore *index_id* nella vista del catalogo [sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) .|  
|**stats_column_id**|**int**|Ordinale in base 1 nel set di colonne di statistiche.|  
|**column_id**|**int**|ID della colonna da **sys. Columns**.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo oggetti &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Domande frequenti sull'esecuzione di query sul catalogo di sistema di SQL Server](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
 [Statistiche](../../relational-databases/statistics/statistics.md)    
 [sys.dm_db_stats_properties &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)   
 [sys. dm_db_stats_histogram &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)  
  
  
