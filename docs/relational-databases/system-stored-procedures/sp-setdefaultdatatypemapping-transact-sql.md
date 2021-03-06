---
title: sp_setdefaultdatatypemapping (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_setdefaultdatatypemapping
- sp_setdefaultdatatypemapping_TSQL
helpviewer_keywords:
- sp_setdefaultdatatypemapping
ms.assetid: 7394e8ca-4ce1-4e99-a784-205007c2c248
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9f0dfadc3b2b990d999df1d66069c4b68df9e6cf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68104408"
---
# <a name="sp_setdefaultdatatypemapping-transact-sql"></a>sp_setdefaultdatatypemapping (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contrassegna come predefinito un mapping del tipo [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di dati esistente tra [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e un sistema di gestione di database (DBMS) non. Questa stored procedure viene eseguita in qualsiasi database del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_setdefaultdatatypemapping [ [ @mapping_id = ] mapping_id ]  
    [ , [ @source_dbms = ] 'source_dbms' ]  
    [ , [ @source_version = ] 'source_version' ]  
    [ , [ @source_type = ] 'source_type' ]   
    [ , [ @source_length_min = ] source_length_min ]  
    [ , [ @source_length_max = ] source_length_max ]  
    [ , [ @source_precision_min = ] source_precision_min ]  
    [ , [ @source_precision_max = ] source_precision_max ]  
    [ , [ @source_scale_min = ] source_scale_min ]  
    [ , [ @source_scale_max = ] source_scale_max ]  
    [ , [ @source_nullable = ] source_nullable ]  
    [ , [ @destination_dbms = ] 'destination_dbms' ]  
    [ , [ @destination_version = ] 'destination_version' ]  
    [ , [ @destination_type = ] 'destination_type' ]  
    [ , [ @destination_length = ] destination_length ]  
    [ , [ @destination_precision = ] destination_precision ]  
    [ , [ @destination_scale = ] destination_scale ]  
    [ , [ @destination_nullable = ] source_nullable ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @mapping_id = ] mapping_id`Identifica un mapping del tipo di dati esistente.  *mapping_id* è di **tipo int**e il valore predefinito è null. Se si specifica *mapping_id*, i parametri rimanenti non sono obbligatori.  
  
`[ @source_dbms = ] 'source_dbms'`Nome del sistema DBMS da cui viene eseguito il mapping dei tipi di dati. *source_dbms* è di **tipo sysname**. i possibili valori sono i seguenti.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**MSSQLSERVER**|L'origine è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|L'origine è un database Oracle.|  
|NULL (predefinito)||  
  
 Se *mapping_id* è null, è necessario specificare questo parametro.  
  
`[ @source_version = ] 'source_version'`È il numero di versione del sistema DBMS di origine. *source_version* è di tipo **varchar (10)** e il valore predefinito è null.  
  
`[ @source_type = ] 'source_type'`Tipo di dati nel sistema DBMS di origine. *source_type* è di **tipo sysname**. Se *mapping_id* è null, è necessario specificare questo parametro.  
  
`[ @source_length_min = ] source_length_min`Lunghezza minima del tipo di dati nel sistema DBMS di origine. *source_length_min* è di tipo **bigint**e il valore predefinito è null.  
  
`[ @source_length_max = ] source_length_max`Lunghezza massima del tipo di dati nel sistema DBMS di origine. *source_length_max* è di tipo **bigint**e il valore predefinito è null.  
  
`[ @source_precision_min = ] source_precision_min`Precisione minima del tipo di dati nel sistema DBMS di origine. *source_precision_min* è di tipo **bigint**e il valore predefinito è null.  
  
`[ @source_precision_max = ] source_precision_max`Precisione massima del tipo di dati nel sistema DBMS di origine. *source_precision_max* è di tipo **bigint**e il valore predefinito è null.  
  
`[ @source_scale_min = ] source_scale_min`È la scala minima del tipo di dati nel sistema DBMS di origine. *source_scale_min* è di **tipo int**e il valore predefinito è null.  
  
`[ @source_scale_max = ] source_scale_max`Scala massima del tipo di dati nel sistema DBMS di origine. *source_scale_max* è di **tipo int**e il valore predefinito è null.  
  
`[ @source_nullable = ] source_nullable`Indica se il tipo di dati nel sistema DBMS di origine supporta un valore NULL. *source_nullable* è di **bit**e il valore predefinito è null. **1** indica che i valori null sono supportati.  
  
`[ @destination_dbms = ] 'destination_dbms'`Nome del sistema DBMS di destinazione. *destination_dbms* è di **tipo sysname**. i possibili valori sono i seguenti.  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**MSSQLSERVER**|La destinazione è un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|La destinazione è un database Oracle.|  
|**DB2**|La destinazione è un database IBM DB2.|  
|**SYBASE**|La destinazione è un database Sybase.|  
|NULL (predefinito)||  
  
`[ @destination_version = ] 'destination_version'`È la versione del prodotto del sistema DBMS di destinazione. *destination_version* è di tipo **varchar (10)** e il valore predefinito è null.  
  
`[ @destination_type = ] 'destination_type'`Tipo di dati elencato nel sistema DBMS di destinazione. *destination_type* è di **tipo sysname**e il valore predefinito è null.  
  
`[ @destination_length = ] destination_length`Lunghezza del tipo di dati nel sistema DBMS di destinazione. *destination_length* è di tipo **bigint**e il valore predefinito è null.  
  
`[ @destination_precision = ] destination_precision`Precisione del tipo di dati nel sistema DBMS di destinazione. *destination_precision* è di tipo **bigint**e il valore predefinito è null.  
  
`[ @destination_scale = ] destination_scale`Scala del tipo di dati nel sistema DBMS di destinazione. *destination_scale* è di **tipo int**e il valore predefinito è null.  
  
`[ @destination_nullable = ] destination_nullable`Indica se il tipo di dati nel sistema DBMS di destinazione supporta il valore NULL. *destination_nullable* è di **bit**e il valore predefinito è null. **1** indica che i valori null sono supportati.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_setdefaultdatatypemapping** viene utilizzato in tutti i tipi di replica [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tra e un non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBMS.  
  
 I mapping dei tipi di dati predefiniti vengono applicati a tutte le topologie di replica che includono il sistema DBMS specificato.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_setdefaultdatatypemapping**.  
  
## <a name="see-also"></a>Vedere anche  
 [Specificare i mapping dei tipi di dati per un server di pubblicazione Oracle](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [sp_getdefaultdatatypemapping &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-getdefaultdatatypemapping-transact-sql.md)   
 [sp_helpdatatypemap &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpdatatypemap-transact-sql.md)  
  
  
