---
title: Configurare i parametri per la raccolta dati (T-SQL)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b7d8d45273fc9ac79a5dd65cfb168868e76f55cd
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "74056465"
---
# <a name="configure-data-collection-parameters-transact-sql"></a>Configurazione dei parametri per la raccolta dati (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Prima di creare un set di raccolta personalizzato è necessario configurare i parametri della raccolta dati. A tale scopo, utilizzare le stored procedure fornite con l'agente di raccolta dati. Il completamento di questa attività comporta l'utilizzo dell'editor di query in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per effettuare la procedura descritta di seguito.  
  
> [!NOTE]  
>  I parametri per la raccolta dati possono essere configurati una volta sola. Dopo la configurazione, tali parametri vengono utilizzati per qualsiasi set di raccolta aggiuntivo creato.  
  
### <a name="configure-data-collection-parameters"></a>Configurazione dei parametri per la raccolta dati  
  
1.  In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]connettersi al database in cui si desidera creare un set di raccolta personalizzato.  
  
2.  Nell'editor di query eseguire le istruzioni indicate di seguito.  

    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)   
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
