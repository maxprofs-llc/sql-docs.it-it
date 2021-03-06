---
title: sys. partition_parameters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- partition_parameters_TSQL
- partition_parameters
- sys.partition_parameters_TSQL
- sys.partition_parameters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.partition_parameters catalog view
ms.assetid: 2012ed9d-3ea3-4c29-9b78-dfa54a392dce
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 32fe257f14c1e085a43b4150ee933888a83d5d14
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125337"
---
# <a name="syspartition_parameters-transact-sql"></a>sys.partition_parameters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Contiene una riga per ogni parametro di una funzione di partizione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**function_id**|**int**|ID della funzione di partizione a cui appartiene il parametro.|  
|**parameter_id**|**int**|ID del parametro. Valore univoco all'interno della funzione di partizione, a partire da 1.|  
|**system_type_id**|**tinyint**|ID del tipo di sistema del parametro. Corrisponde alla colonna **system_type_id** della vista del catalogo **sys. Types** .|  
|**max_length**|**smallint**|Lunghezza massima del parametro in byte.|  
|**precisione**|**tinyint**|Precisione del parametro se numerica. In caso contrario 0.|  
|**scala**|**tinyint**|Scala del parametro se numerica. In caso contrario 0.|  
|**collation_name**|**sysname**|Nome delle regole di confronto del parametro, se di tipo carattere. In caso contrario, NULL.|  
|**user_type_id**|**int**|ID del tipo. Valore univoco all'interno del database. Per i tipi di dati di sistema, **user_type_id** = **system_type_id**.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo delle funzioni di partizione &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [sys. partition_functions &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys. partition_range_values &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)  
  
  
