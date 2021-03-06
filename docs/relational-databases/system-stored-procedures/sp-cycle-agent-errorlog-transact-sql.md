---
title: sp_cycle_agent_errorlog (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cycle_agent_errorlog
- sp_cycle_agent_errorlog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cycle_agent_errorlog
ms.assetid: 8aa96182-60b7-4d7b-b2a7-ccce70378c6e
author: stevestein
ms.author: sstein
ms.openlocfilehash: c95cc2db84bdf059437a45e2719bbc63d6eb6829
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108349"
---
# <a name="sp_cycle_agent_errorlog-transact-sql"></a>sp_cycle_agent_errorlog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Chiude il log degli errori corrente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent e rinumera le estensioni del log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, esattamente come quando si riavvia il server. Il nuovo log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent contiene una riga in cui è registrata l'operazione di creazione di un nuovo log.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_cycle_agent_errorlog  
```  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
 nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Ogni volta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che viene avviato Agent, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log degli errori corrente di Agent viene rinominato in **SQLAgent. 1**; **SQLAgent. 1** diventa **SQLAgent. 2**, **SQLAgent. 2** diventa **SQLAgent. 3**e così via. **sp_cycle_agent_errorlog** consente di scorrere i file di log degli errori senza arrestare e avviare il server.  
  
 Questo stored procedure deve essere eseguito dal database **msdb** .  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione per **sp_cycle_agent_errorlog** sono limitate ai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rinumerato il log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_cycle_agent_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_cycle_errorlog &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md)  
  
  
