---
title: sys. dm_clr_loaded_assemblies (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_clr_loaded_assemblies
- sys.dm_clr_loaded_assemblies_TSQL
- dm_clr_loaded_assemblies_TSQL
- sys.dm_clr_loaded_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_loaded_assemblies dynamic management view
ms.assetid: 8523d8db-d8a0-4b1f-ae19-6705d633e0a6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1cd677e516048aa52badec7fc9875e5a5b13f25a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138661"
---
# <a name="sysdm_clr_loaded_assemblies-transact-sql"></a>sys.dm_clr_loaded_assemblies (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni assembly gestito dall'utente nello spazio degli indirizzi del server. Utilizzare questa visualizzazione per comprendere e risolvere i problemi relativi agli oggetti di database gestiti dell'integrazione [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]CLR in esecuzione in.  
  
 Gli assembly sono costituiti da file DLL di codice gestito utilizzati per definire e distribuire gli oggetti di database gestito in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ogni volta che un utente esegue uno di questi oggetti di database gestito, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il CLR caricano l'assembly in cui l'oggetto di database gestito viene definito e i relativi riferimenti. L'assembly rimane caricato in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per migliorare le prestazioni. In seguito sarà infatti possibile chiamare gli oggetti di database gestito contenuti nell'assembly senza che sia necessario ricaricare l'assembly. L'assembly non viene scaricato finché la quantità di memoria in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] non risulta insufficiente. Per ulteriori informazioni sugli assembly e sull'integrazione con CLR, vedere [CLR hosted Environment](../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md). Per ulteriori informazioni sugli oggetti di database gestiti, vedere [compilazione di oggetti di database con Common Language Runtime &#40;l'integrazione con&#41; CLR](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md).  

  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**assembly_id**|**int**|ID dell'assembly caricato. Il **assembly_id** può essere utilizzato per cercare ulteriori informazioni sull'assembly nella vista del catalogo [sys. Assemblies &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) . Si noti che [!INCLUDE[tsql](../../includes/tsql-md.md)] il catalogo [sys. Assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md) Mostra gli assembly solo nel database corrente. La vista **SQS. dm_clr_loaded_assemblies** Mostra tutti gli assembly caricati nel server.|  
|**appdomain_address**|**int**|Indirizzo del dominio applicazione (**AppDomain**) in cui viene caricato l'assembly. Tutti gli assembly di proprietà di un singolo utente vengono sempre caricati nello stesso **AppDomain**. Il **appdomain_address** può essere utilizzato per cercare ulteriori informazioni sull' **AppDomain** nella vista [sys. dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md) .|  
|**load_time**|**datetime**|Ora di caricamento dell'assembly. Si noti che l'assembly rimane caricato [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fino a quando non viene sottoposto a richieste di memoria e Scarica **AppDomain**. È possibile monitorare **load_time** per comprendere la frequenza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con cui si verifica un utilizzo elevato di memoria e Scarica l' **AppDomain**.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="remarks"></a>Osservazioni  
 La vista **dm_clr_loaded_assemblies. appdomain_address** ha una relazione molti-a-uno con **dm_clr_appdomains. appdomain_address**. La vista **dm_clr_loaded_assemblies. assembly_id** dispone di una relazione uno-a-molti con **sys. Assemblies. assembly_id**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrato come visualizzare dettagli relativi a tutti gli assembly del database corrente che sono attualmente caricati.  
  
```  
 SELECT a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
FROM sys.dm_clr_loaded_assemblies AS l   
INNER JOIN sys.assemblies AS a  
ON l.assembly_id = a.assembly_id;  
```  
  
 Nell'esempio seguente viene illustrato come visualizzare i dettagli di **AppDomain** in cui viene caricato un determinato assembly.  
  
```  
SELECT appdomain_id, creation_time, db_id, user_id, state  
FROM sys.dm_clr_appdomains AS a  
WHERE appdomain_address =   
(SELECT appdomain_address   
 FROM sys.dm_clr_loaded_assemblies  
 WHERE assembly_id = 555);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Viste a gestione dinamica relative a Common Language Runtime &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
