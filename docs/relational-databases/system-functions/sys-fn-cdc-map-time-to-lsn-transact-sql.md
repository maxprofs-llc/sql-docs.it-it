---
title: sys.fn_cdc_map_time_to_lsn (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_cdc_map_time_to_lsn
- fn_cdc_map_time_to_lsn_TSQL
- sys.fn_cdc_map_time_to_lsn_TSQL
- fn_cdc_map_time_to_lsn
dev_langs:
- TSQL
helpviewer_keywords:
- fn_cdc_map_time_to_lsn
- sys.fn_cdc_map_time_to_lsn
ms.assetid: 6feb051d-77ae-4c93-818a-849fe518d1d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 7f4f6820aeeca8b600631810ed35933d2519b495
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046335"
---
# <a name="sysfn_cdc_map_time_to_lsn-transact-sql"></a>sys.fn_cdc_map_time_to_lsn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce il valore del numero di sequenza del file di log (LSN) dalla colonna **start_lsn** nella tabella di sistema [CDC. lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) per l'ora specificata. È possibile utilizzare questa funzione per eseguire sistematicamente il mapping di intervalli DateTime nell'intervallo basato su LSN richiesto dalle funzioni di enumerazione Change Data Capture [CDC. fn_cdc_get_all_changes_<capture_instance>](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md) e [CDC. fn_cdc_get_net_changes_](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)<capture_instance>per restituire le modifiche dei dati all'interno di tale intervallo.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sys.fn_cdc_map_time_to_lsn ( '<relational_operator>', tracking_time )  
  
<relational_operator> ::=  
{  largest less than  
 | largest less than or equal  
 | smallest greater than  
 | smallest greater than or equal  
}  
```  
  
## <a name="arguments"></a>Argomenti  
 **'**<relational_operator>**'** {maggiore di | maggiore di | maggiore o uguale a | più piccolo maggiore di | maggiore o uguale a}  
 Viene utilizzato per identificare un valore LSN distinto all'interno della tabella **CDC. lsn_time_mapping** con un **tran_end_time** associato che soddisfa la relazione rispetto al valore di *tracking_time* .  
  
 *relational_operator* è di **tipo nvarchar (30)**.  
  
 *tracking_time*  
 Valore datetime da confrontare. *tracking_time* è **DateTime**.  
  
## <a name="return-type"></a>Tipo restituito  
 **binario (10)**  
  
## <a name="remarks"></a>Osservazioni  
 Per comprendere il modo in cui è possibile utilizzare **sys. fn_cdc_map_time_lsn** per eseguire il mapping di intervalli DateTime a intervalli LSN, considerare lo scenario seguente. Si supponga che un utente desideri estrarre su base giornaliera i dati delle modifiche. Ovvero, l'utente desidera solo le modifiche relative a un giorno specifico fino alla mezzanotte (inclusa). Il limite inferiore dell'intervallo di tempo raggiunge, ma non include, la mezzanotte del giorno precedente. Il limite superiore raggiunge e include la mezzanotte del giorno specificato. Nell'esempio seguente viene illustrato come è possibile utilizzare la funzione **sys. fn_cdc_map_time_to_lsn** per eseguire sistematicamente il mapping di questo intervallo basato sul tempo nell'intervallo basato su LSN richiesto dalle funzioni di enumerazione Change Data Capture per restituire tutte le modifiche all'interno di tale intervallo.  
  
 `DECLARE @begin_time datetime, @end_time datetime, @begin_lsn binary(10), @end_lsn binary(10);`  
  
 `SET @begin_time = '2007-01-01 12:00:00.000';`  
  
 `SET @end_time = '2007-01-02 12:00:00.000';`  
  
 `SELECT @begin_lsn = sys.fn_cdc_map_time_to_lsn('smallest greater than', @begin_time);`  
  
 `SELECT @end_lsn = sys.fn_cdc_map_time_to_lsn('largest less than or equal', @end_time);`  
  
 `SELECT * FROM cdc.fn_cdc_get_net_changes_HR_Department(@begin_lsn, @end_lsn, 'all` `');`  
  
 L'operatore relazionale '`smallest greater than`' è utilizzato per limitare le modifiche a quelle che si sono verificate dopo la mezzanotte del giorno precedente. Se più voci con valori LSN diversi condividono il valore **tran_end_time** identificato come limite inferiore nella tabella [CDC. lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) , la funzione restituirà il valore LSN più piccolo, assicurando che tutte le voci siano incluse. Per il limite superiore, viene usato l'operatore relazionale '`largest less than or equal to`' per garantire che l'intervallo includa tutte le voci per il giorno, incluse quelle che hanno mezzanotte come valore **tran_end_time** . Se più voci con valori LSN diversi condividono il valore **tran_end_time** identificato come limite superiore, la funzione restituirà il valore LSN più grande che garantisce che tutte le voci siano incluse.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzata `sys.fn_cdc_map_time_lsn` la funzione per determinare se sono presenti righe nella tabella [CDC. lsn_time_mapping](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md) con un valore **tran_end_time** maggiore o uguale a mezzanotte. Questa query può essere utilizzata per determinare, ad esempio, se il processo di acquisizione ha già elaborato le modifiche di cui è stato eseguito il commit fino alla mezzanotte del giorno precedente, in modo tale che possa procedere l'estrazione di dati delle modifiche per il giorno specifico.  
  
```  
DECLARE @extraction_time datetime, @lsn binary(10);  
SET @extraction_time = '2007-01-01 12:00:00.000';  
SELECT @lsn = sys.fn_cdc_map_time_to_lsn ('smallest greater than or equal', @extraction_time);  
IF @lsn IS NOT NULL  
BEGIN  
<some action>  
END  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CDC. lsn_time_mapping &#40;&#41;Transact-SQL](../../relational-databases/system-tables/cdc-lsn-time-mapping-transact-sql.md)   
 [sys. fn_cdc_map_lsn_to_time &#40;&#41;Transact-SQL](../../relational-databases/system-functions/sys-fn-cdc-map-lsn-to-time-transact-sql.md)   
 [CDC. fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)   
 [CDC. fn_cdc_get_all_changes_&#60;capture_instance&#62;  &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)  
  
  
