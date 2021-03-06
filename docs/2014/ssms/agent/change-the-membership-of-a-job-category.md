---
title: Modificare l'appartenenza a una categoria di processi | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f5ed0e086f5743f6759ed8b317750eefcb377180
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72782792"
---
# <a name="change-the-membership-of-a-job-category"></a>Modificare l'appartenenza a una categoria di processi
  In questo argomento viene descritto come modificare l'appartenenza della categoria di processi in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]o SQL Server Management Objects.  
  
 Le categorie consentono di organizzare i processi per semplificare le operazioni di raggruppamento e filtro. È possibile creare categorie di processi personalizzate. È inoltre possibile modificare l'appartenenza dei processi di Microsoft SQL Server Agent alle categorie del processo.  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Sicurezza](#Security)  
  
-   **Per modificare l'appartenenza di una categoria di processi utilizzando:**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Security"></a> Sicurezza  
 Per informazioni dettagliate, vedere [Implementazione della sicurezza di SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Con SQL Server Management Studio  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Per modificare l'appartenenza a una categoria di processi  
  
1.  In **Esplora oggetti**fare clic sul segno più per espandere il server in cui si desidera modificare una categoria di processi.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse sulla cartella **Processi** e selezionare **Gestione categorie processi**.  
  
4.  Nella finestra di dialogo **Gestisci categorie di processi**_server_name_ Selezionare la categoria di processi che si desidera modificare, quindi fare clic su **Visualizza processi**.  
  
5.  Selezionare la casella di controllo **Mostra tutti i processi** .  
  
6.  Per aggiungere un processo alla categoria, selezionare nella griglia principale la casella di controllo della colonna **Seleziona** corrispondente al processo. Per rimuovere un processo dalla categoria, deselezionare la casella. Al termine, fare clic su **OK**.  
  
7.  Chiudere la finestra di dialogo **Gestisci categorie di processi**_server_name_ .  
  
##  <a name="TSQL"></a> Con Transact-SQL  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Per modificare l'appartenenza a una categoria di processi  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```sql
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
 Per ulteriori informazioni, vedere [sp_update_job &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).  
  
##  <a name="SMO"></a>Utilizzo di SQL Server Management Objects  
 **Per modificare l'appartenenza di una categoria di processi**  
  
 Usare la classe `JobCategory` tramite un linguaggio di programmazione scelto come Visual Basic, Visual C# o PowerShell.  
