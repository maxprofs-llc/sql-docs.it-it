---
title: sp_droprole (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprole
- sp_droprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprole
ms.assetid: 889ee074-00f8-40a9-bddb-d7d3ef0cbc19
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2573019948a326c9171fc83d62428e7e2f888eb5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933816"
---
# <a name="sp_droprole-transact-sql"></a>sp_droprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Rimuove un ruolo del database dal database corrente.  
  
> [!IMPORTANT]  
>  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **sp_droprole** stato sostituito dall'istruzione DROP ROLE. **sp_droprole** è incluso solo per la compatibilità con le versioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] precedenti di e potrebbe non essere supportato in una versione futura.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_droprole [ @rolename= ] 'role'  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @rolename = ] 'role'`Nome del ruolo del database da rimuovere dal database corrente. *Role* è di **tipo sysname**e non prevede alcun valore predefinito. il *ruolo* deve essere già presente nel database corrente.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="remarks"></a>Osservazioni  
 È possibile rimuovere solo i ruoli del database utilizzando **sp_droprole**.  
  
 Non è possibile rimuovere un ruolo del database a cui sono associati membri esistenti. È necessario rimuovere tutti i membri di un ruolo del database prima di poter rimuovere il ruolo del database stesso. Per rimuovere gli utenti da un ruolo, utilizzare **sp_droprolemember**. Se gli utenti sono ancora membri del ruolo, **sp_droprole** Visualizza tali membri.  
  
 Non è possibile rimuovere i ruoli predefiniti e il ruolo **public** .  
  
 Non è possibile rimuovere un ruolo proprietario di un'entità a sicurezza diretta. Prima di rimuovere un ruolo applicazione proprietario di entità a protezione diretta, è necessario innanzitutto trasferire la proprietà delle entità a protezione diretta oppure rimuoverle. Utilizzare ALTER AUTHORIZATION per modificare il proprietario degli oggetti che non devono essere rimossi.  
  
 Impossibile eseguire **sp_droprole** in una transazione definita dall'utente.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione CONTROL per il ruolo.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene rimosso il ruolo applicazione `Sales`.  
  
```  
EXEC sp_droprole 'Sales';  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sicurezza &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrole &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [DROP ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_dropapprole &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
