---
title: sp_lookupcustomresolver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_lookupcustomresolver_TSQL
- sp_lookupcustomresolver
helpviewer_keywords:
- sp_lookupcustomresolver
ms.assetid: 356a7b8a-ae53-4fb5-86ee-fcfddbf23ddd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 274276a55a7b3e91ff85330a0810f01786a5a080
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937908"
---
# <a name="sp_lookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce le informazioni su un gestore della logica di business o il valore dell'identificatore di classe (CLSID) di un componente di un sistema di risoluzione personalizzato basato su COM che è registrato nel server di distribuzione. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_lookupcustomresolver [ @article_resolver = ] 'article_resolver'   
    [, [ @resolver_clsid = ] 'resolver_clsid' OUTPUT ]  
    [ , [ @is_dotnet_assembly = ] is_dotnet_assembly OUTPUT ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @article_resolver = ] 'article_resolver'`Specifica il nome della logica di business personalizzata di cui è in corso l'annullamento della registrazione. *article_resolver* è di **tipo nvarchar (255)** e non prevede alcun valore predefinito. Se la logica di business in fase di rimozione è un componente COM, questo parametro è il nome descrittivo del componente. Se la logica di business è un assembly [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework, questo parametro è il nome dell'assembly.  
  
`[ @resolver_clsid = ] 'resolver_clsid' OUTPUT`È il valore CLSID dell'oggetto COM associato al nome della logica di business personalizzata specificata nel parametro *article_resolver* . *resolver_clsid* è di **tipo nvarchar (50)** e il valore predefinito è null.  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly' OUTPUT`Specifica il tipo di logica di business personalizzata in fase di registrazione. *is_dotnet_assembly* è di **bit**e il valore predefinito è 0. **1** indica che la logica di business personalizzata in fase di registrazione è un assembly del gestore della logica di business. **0** indica che si tratta di un componente com.  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT`Nome dell'assembly che implementa il gestore della logica di business. *dotnet_assembly_name* è di **tipo nvarchar (255)** e il valore predefinito è null.  
  
`[ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT`Nome della classe che esegue l'override <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> di per implementare il gestore della logica di business. *dotnet_class_name* è di **tipo nvarchar (255)** e il valore predefinito è null.  
  
`[ @publisher = ] 'publisher'`Nome del server di pubblicazione. *Publisher* è di **tipo sysname**e il valore predefinito è null. Utilizzare questo parametro quando la stored procedure non viene chiamata dal server di pubblicazione. Se omesso, si presuppone che il server locale è il server di pubblicazione.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 **0** (esito positivo) o **1** (esito negativo)  
  
## <a name="remarks"></a>Osservazioni  
 **sp_lookupcustomresolver** viene utilizzata nella replica di tipo merge.  
  
 **sp_lookupcustomresolver** restituisce un valore NULL per *resolver_clsid* quando il componente non è registrato alla distribuzione e il valore "00000000-0000-0000-0000-000000000000" quando la registrazione appartiene a un assembly di .NET Framework registrato come gestore della logica di business.  
  
 **sp_lookupcustomresolver** viene chiamato da [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) e [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) per convalidare il *article_resolver*specificato.  
  
## <a name="permissions"></a>Autorizzazioni  
 Solo i membri del ruolo predefinito del database **db_owner** nel database di pubblicazione possono eseguire **sp_lookupcustomresolver**.  
  
## <a name="see-also"></a>Vedere anche  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Eseguire la logica di business durante la sincronizzazione di tipo merge](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [Implementare un gestore della logica di business per un articolo di merge](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Specificare un sistema di risoluzione dell'articolo di merge](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
