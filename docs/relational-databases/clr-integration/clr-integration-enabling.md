---
title: Abilitazione dell'integrazione con CLR | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: 07066dc7ffbd48273ace55e0c9867661b2cbfe59
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "71680856"
---
# <a name="clr-integration---enabling"></a>Integrazione CLR - Abilitazione
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Per impostazione predefinita, la funzionalità di integrazione con Common Language Runtime (CLR) è disabilitata e deve essere abilitata per poter utilizzare gli oggetti implementati mediante l'integrazione con CLR. Per abilitare l'integrazione con CLR, utilizzare l'opzione **clr enabled** del stored procedure **sp_configure** in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
```sql  
EXEC sp_configure 'clr enabled', 1;  
RECONFIGURE;  
GO  
```  
  
 È possibile disabilitare l'integrazione CLR impostando l'opzione **clr enabled** su 0. Quando si disabilita l'integrazione con [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CLR, interrompe l'esecuzione di tutte le routine CLR definite dall'utente e Scarica tutti i domini applicazione. Le funzionalità che si basano su CLR, ad **** esempio il tipo di dati `FORMAT` hierarchyid, la funzione, la replica e la gestione basata su criteri, non sono interessate da questa impostazione e continueranno a funzionare.
  
> [!NOTE]  
>  Per abilitare l'integrazione con CLR, è necessario disporre dell'autorizzazione ALTER SETTINGS a livello di server, che viene utilizzata in modo implicito dai membri dei ruoli predefiniti del server **sysadmin** e **serveradmin** .  
  
> [!NOTE]  
>  I computer configurati con grandi quantità di memoria e con un gran numero di processori potrebbero non riuscire a caricare la funzionalità di integrazione con CLR di SQL Server all'avvio del server. Per risolvere questo problema, avviare il server utilizzando l'opzione di avvio del servizio **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e specificare un valore di memoria sufficientemente grande. Per altre informazioni, vedere [Opzioni di avvio del servizio del motore di database](../../database-engine/configure-windows/database-engine-service-startup-options.md).  
  
> [!NOTE]  
>  L'esecuzione di CLR (Common Language Runtime) non è supportata nell'ambito dell'opzione lightweight pooling. Prima di abilitare l'integrazione con CLR, è necessario disabilitare il lightweight pooling. Per altre informazioni, vedere [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).  
  
## <a name="see-also"></a>Vedere anche  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Opzione di configurazione del server clr enabled](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [CONCEDERE &#40;&#41;Transact-SQL](../../t-sql/statements/grant-transact-sql.md)   
 [Ruoli a livello di server](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
