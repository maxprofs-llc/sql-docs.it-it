---
title: sys. system_sql_modules (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- system_sql_modules_TSQL
- sys.system_sql_modules
- sys.system_sql_modules_TSQL
- system_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.system_sql_modules catalog view
ms.assetid: ad3548bc-4780-4821-b962-b421d52daed9
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: fe249cd389e71fa5565e2877fba46b47cf0a4f38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108778"
---
# <a name="syssystem_sql_modules-transact-sql"></a>sys.system_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Restituisce una riga per oggetto di sistema contenente un modulo definito tramite il linguaggio SQL. Gli oggetti di sistema di tipo FN, IF, P, PC, TF, V sono associati a un modulo SQL. Per identificare l'oggetto contenitore, è possibile unire in join questa visualizzazione a [sys. system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md).  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Numero di identificazione dell'oggetto contenitore, univoco all'interno di un database.|  
|**definizione**|**nvarchar(max)**|Testo SQL che definisce il modulo.|  
|**uses_ansi_nulls**|**bit**|1 = Il modulo è stato creato con l'opzione di database SET ANSI_NULLS impostata su ON.<br /><br /> Restituisce sempre 1.|  
|**uses_quoted_identifier**|**bit**|1= Il modulo è stato creato con SET QUOTED_IDENTIFIER ON.<br /><br /> Restituisce sempre 1.|  
|**is_schema_bound**|**bit**|0 = Il modulo non è stato creato con l'opzione SCHEMABINDING.<br /><br /> Restituisce sempre 0.|  
|**uses_database_collation**|**bit**|0 = Il modulo non dipende dalle regole di confronto predefinite del database.<br /><br /> Restituisce sempre 0.|  
|**is_recompiled**|**bit**|0 = La procedura non è stata creata tramite l'opzione WITH RECOMPILE.<br /><br /> Restituisce sempre 0.|  
|**null_on_null_input**|**bit**|0 = Il modulo è stato creato in modo da produrre un output NULL per ogni input NULL.<br /><br /> Restituisce sempre 0.|  
|**execute_as_principal_id**|**int**|Restituisce sempre NULL.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys. all_sql_modules &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-all-sql-modules-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Viste del catalogo oggetti &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
