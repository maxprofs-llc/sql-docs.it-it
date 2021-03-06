---
title: sysmail_add_principalprofile_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_add_principalprofile_sp_TSQL
- sysmail_add_principalprofile_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_add_principalprofile_sp
ms.assetid: b2a0b313-abb9-4c23-8511-db77ca8172b3
author: stevestein
ms.author: sstein
ms.openlocfilehash: fedc7e0dd7fe71feb0b0da1f00f2a7f996c6129c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72305055"
---
# <a name="sysmail_add_principalprofile_sp-transact-sql"></a>sysmail_add_principalprofile_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Concede l'autorizzazione a un'entità di database msdb per l'utilizzo di un profilo di Posta elettronica database. È necessario eseguire il mapping dell'entità di database a un utente di SQL Server Authentication, a un utente di Windows o a un gruppo di Windows.
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_add_principalprofile_sp  { [ @principal_id = ] principal_id | [ @principal_name = ] 'principal_name' } ,  
    { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
    [ , [ @is_default ] = 'is_default' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @principal_id = ] principal_id`ID dell'utente del database o del ruolo nel database **msdb** per l'associazione. *principal_id* è di **tipo int**e il valore predefinito è null. È necessario specificare *principal_id* o *principal_name* . Un *principal_id* di **0** rende questo profilo un profilo pubblico, concedendo l'accesso a tutte le entità nel database.  
  
`[ @principal_name = ] 'principal_name'`Nome dell'utente del database o del ruolo nel database **msdb** per l'associazione. *principal_name* è di **tipo sysname**e il valore predefinito è null. È necessario specificare *principal_id* o *principal_name* . Un *principal_name* di **' Public '** rende questo profilo un profilo pubblico, concedendo l'accesso a tutte le entità nel database.  
  
`[ @profile_id = ] profile_id`ID del profilo per l'associazione. *profile_id* è di **tipo int**e il valore predefinito è null. È necessario specificare *profile_id* o *profile_name* .  
  
`[ @profile_name = ] 'profile_name'`Nome del profilo per l'associazione. *profile_name* è di **tipo sysname**e non prevede alcun valore predefinito. È necessario specificare *profile_id* o *profile_name* .  
  
`[ @is_default = ] is_default`Specifica se il profilo è il profilo predefinito per l'entità. A un'entità può essere associato un solo profilo predefinito. *is_default* è di **bit**e non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 Per rendere pubblico un profilo, specificare un ** \@principal_id** **0** o un ** \@principal_name** di **public**. Un profilo pubblico è disponibile per tutti gli utenti nel database **msdb** , anche se gli utenti devono essere anche membri di **DatabaseMailUserRole** per eseguire **sp_send_dbmail**.  
  
 A un utente del database può essere associato un solo profilo predefinito. Quando ** \@is_default** è'**1**' e l'utente è già associato a uno o più profili, il profilo specificato diventa il profilo predefinito per l'utente. Il profilo che in precedenza era il profilo predefinito è tuttora associato all'utente, ma non è più il profilo predefinito.  
  
 Quando ** \@is_default** è'**0**' e non esiste nessun'altra associazione, il stored procedure restituisce un errore.  
  
 Il stored procedure **sysmail_add_principalprofile_sp** si trova nel database **msdb** ed è di proprietà dello schema **dbo** . La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione per questa procedura vengono assegnate per impostazione predefinita ai membri del ruolo predefinito del server **sysadmin** .  
  
## <a name="examples"></a>Esempi  
 **A. Creazione di un'associazione e impostazione del profilo predefinito**  
  
 Nell'esempio seguente viene creata un'associazione tra il profilo `AdventureWorks Administrator Profile` denominato e l'utente `ApplicationUser`del database **msdb** . Il profilo è il profilo predefinito per l'utente.  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'ApplicationUser',  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @is_default = 1 ;  
```  
  
 **B. Impostazione di un profilo come profilo pubblico predefinito**  
  
 Nell'esempio seguente il `AdventureWorks Public Profile` profilo viene reso il profilo pubblico predefinito per gli utenti nel database **msdb** .  
  
```  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @principal_name = 'public',  
    @profile_name = 'AdventureWorks Public Profile',  
    @is_default = 1 ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Oggetti di configurazione Posta elettronica database](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [Stored procedure di Posta elettronica database &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
