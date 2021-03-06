---
title: dbo. sysjobservers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/26/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobservers
- sysjobservers_TSQL
- dbo.sysjobservers
- dbo.sysjobservers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobservers system table
ms.assetid: 9abcc20f-a421-4591-affb-62674d04575e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 03a4457cb5dd087639a439e9e9bb883eaf924366
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "70026200"
---
# <a name="dbosysjobservers-transact-sql"></a>dbo.sysjobservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Archivia l'associazione o la relazione di un determinato processo con uno o più server di destinazione. Questa tabella è archiviata nel database msdb.
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|job_id|**uniqueidentifier**|Numero di identificazione del processo.|  
|server_id|**int**|Numero di identificazione del server.|  
|last_run_outcome|**tinyint**|Risultato dell'ultima esecuzione del processo:<br /><br /> **0** = esito negativo<br /><br /> **1** = esito positivo<br /><br /> **2** = nuovo tentativo<br /><br /> **3** = Annulla<br /><br /> **4** = in corso<br /><br /> **5** = sconosciuto (vedere la sezione Osservazioni seguente) |  
|last_outcome_ message|**nvarchar(1024)**|Eventuale messaggio associato alla colonna last_run_outcome.|  
|last_run_date|**int**|Data dell'ultima esecuzione del processo.|  
|last_run_time|**int**|Ora dell'ultima esecuzione del processo.|  
|last_run_duration|**int**|Durata di esecuzione del processo, in ore, minuti e secondi. Calcolato mediante la formula: (*ore*\*10000) + (*minuti*\*100) + *secondi*.|  


## <a name="remarks"></a>Osservazioni

Un valore superiore a *4* indica che l'agente SQL non conosce lo stato del processo. Il *last_run_outcome* viene inizialmente impostato su *5* quando viene creato un processo.


## <a name="see-also"></a>Vedere anche

[SQL Server Agent tabelle &#40;&#41;Transact-SQL](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
