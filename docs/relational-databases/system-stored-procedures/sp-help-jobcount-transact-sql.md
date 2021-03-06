---
title: sp_help_jobcount (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_jobcount
- sp_help_jobcount_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_jobcount
ms.assetid: ae8ef851-646c-4889-bc11-c8ec78762572
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f874aa26001b7d595f319a59d5c116907aa096e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68054958"
---
# <a name="sp_help_jobcount-transact-sql"></a>sp_help_jobcount (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fornisce il numero di processi a cui è associata una pianificazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_jobcount   
     [ @schedule_name = ] 'schedule_name' ,  
     [ @schedule_id = ] schedule_id   
```  
  
## <a name="arguments"></a>Argomenti  
`[ @schedule_id = ] schedule_id`Identificatore della pianificazione da elencare. *schedule_id* è di **tipo int**e non prevede alcun valore predefinito. È possibile specificare *schedule_id* o *schedule_name* .  
  
`[ @schedule_name = ] 'schedule_name'`Nome della pianificazione da elencare. *schedule_name* è di **tipo sysname**e non prevede alcun valore predefinito. È possibile specificare *schedule_id* o *schedule_name* .  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 Restituisce il set di risultati seguente:  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**JobCount**|**int**|Numero di processi per la pianificazione specificata.|  
  
## <a name="remarks"></a>Osservazioni  
 Questa procedura visualizza un elenco del numero di processi associati alla pianificazione specificata.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per impostazione predefinita, i membri del ruolo predefinito del server **sysadmin** possono eseguire questo stored procedure. Gli altri utenti devono essere membri di uno dei ruoli predefiniti del database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent seguenti nel database **msdb** :  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Per informazioni dettagliate sulle autorizzazioni di questi ruoli, vedere [Ruoli di database predefiniti di SQL Server Agent](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Solo i membri di **sysadmin** possono visualizzare i conteggi dei processi di proprietà di altri utenti.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene visualizzato un elenco del numero di processi associati alla pianificazione `NightlyJobs`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_jobcount  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di SQL Server Agent &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_schedule &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)   
 [sp_attach_schedule &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql.md)   
 [sp_delete_schedule &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-delete-schedule-transact-sql.md)   
 [sp_detach_schedule &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-detach-schedule-transact-sql.md)  
  
  
