---
title: sys.fn_cdc_get_column_ordinal (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/25/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_get_column_ordinal
- fn_cdc_get_column_ordinal_TSQL
- fn_cdc_get_column_ordinal
- sys.fn_cdc_get_column_ordinal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_get_column_ordinal
- sys.fn_cdc_get_column_ordinal
ms.assetid: 4bb21a57-2b94-4208-8bdf-6a3e2681d881
author: rothja
ms.author: jroth
ms.openlocfilehash: 893c7b0a4c7c88c0fdc7bf89b01b61bfaae6f2f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046504"
---
# <a name="sysfn_cdc_get_column_ordinal-transact-sql"></a>sys.fn_cdc_get_column_ordinal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il numero ordinale di colonna della colonna specificata così come viene visualizzato nella [tabella delle modifiche](../../relational-databases/system-tables/cdc-capture-instance-ct-transact-sql.md) associata all'istanza di acquisizione specificata.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_cdc_get_column_ordinal ( 'capture_instance','column_name')  
```  
  
## <a name="arguments"></a>Argomenti  
 **'** *capture_instance* **'**  
 Nome dell'istanza di acquisizione in cui la colonna specificata viene identificata come una colonna acquisita. *capture_instance* è di **tipo sysname**.  
  
 **'** *column_name* **'**  
 Colonna per la quale eseguire un report. *column_name* è di **tipo sysname**.  
  
## <a name="return-type"></a>Tipo restituito  
 **int**  
  
## <a name="remarks"></a>Osservazioni  
 Questa funzione viene utilizzata per identificare la posizione ordinale di una colonna acquisita all'interno della maschera di aggiornamento dell'acquisizione dei dati delle modifiche. Viene utilizzata principalmente insieme alla funzione [sys. fn_cdc_is_bit_set](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md) per estrarre informazioni dalla maschera di aggiornamento quando si eseguono query sui dati delle modifiche.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione SELECT in tutte le colonne acquisite della tabella di origine. Se per l'istanza di acquisizione viene specificato un ruolo del database per il componente di acquisizione dei dati delle modifiche, viene anche richiesta l'appartenenza a tale ruolo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente si ottiene la posizione ordinale della colonna `VacationHours` nella maschera di aggiornamento per l'istanza di acquisizione `HumanResources_Employee`. Questo valore viene poi utilizzato nella chiamata a `sys.fn_cdc_is_bit_set` per estrarre informazioni dalla maschera di aggiornamento restituita.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @from_lsn binary(10), @to_lsn binary(10),  @VacationHoursOrdinal int;  
SET @from_lsn = sys.fn_cdc_get_min_lsn('HumanResources_Employee');  
SET @to_lsn = sys.fn_cdc_get_max_lsn();  
SET @VacationHoursOrdinal = sys.fn_cdc_get_column_ordinal   
    ( 'HumanResources_Employee','VacationHours');  
SELECT *, sys.fn_cdc_is_bit_set(@VacationHoursOrdinal,  
    __$update_mask) as 'VacationHours'  
FROM cdc.fn_cdc_get_net_changes_HumanResources_Employee  
    ( @from_lsn, @to_lsn, 'all with mask');  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni Change Data Capture &#40;Transact-SQL&#41;](../../relational-databases/system-functions/change-data-capture-functions-transact-sql.md)   
 [Informazioni su Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)   
 [sys. sp_cdc_help_change_data_capture &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)   
 [sys. sp_cdc_get_captured_columns &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-captured-columns-transact-sql.md)   
 [sys. fn_cdc_is_bit_set &#40;&#41;Transact-SQL](../../relational-databases/system-functions/sys-fn-cdc-is-bit-set-transact-sql.md)  
  
  
