---
title: 'Lezione 3: scrivere un backup completo del database nel servizio di archiviazione BLOB di Azure | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 1d5a749c61a3bc97de841e1149dd1539cbc990f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "70153469"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-azure-blob-storage-service"></a>Lezione 3: Scrivere un backup completo del database nel servizio di archiviazione BLOB di Azure
  In questa lezione viene illustrato l'utilizzo dell'istruzione tsql per eseguire un backup completo del database nel servizio di archiviazione BLOB di Azure.  
  
## <a name="perform-a-full-database-backup-to-the-azure-blob-storage-service"></a>Eseguire un backup completo del database nel servizio di archiviazione BLOB di Azure  
 Per creare un backup completo del database, attenersi ai passaggi seguenti:  
  
1.  Connettersi a [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  In **Esplora oggetti**connettersi all'istanza di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
3.  Sulla barra del menu Standard fare clic su **Nuova query**.  
  
4.  Copiare e incollare l'esempio seguente nella finestra Query, modificare se necessario, quindi fare clic su **Esegui**.  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  In Esplora oggetti connettersi alla risorsa di archiviazione Azure. Sfogliare per individuare il contenitore e i file di backup appena creati.  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 4: eseguire un ripristino da un backup completo del database](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).  
  
  
