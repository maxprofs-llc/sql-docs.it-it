---
title: Creare un avviso usando un numero di errore | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server], creating
- SQL Server Agent, alerts
- alerts [SQL Server], error numbers
ms.assetid: 03dd7fac-5073-4f86-babd-37e45a86023c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9f0884a37c443f863cf0c1001bae1242852db3ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63135361"
---
# <a name="create-an-alert-using-an-error-number"></a>Creazione di un avviso utilizzando un numero di errore
  In questo argomento viene descritto come creare [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un avviso di Agent [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] in che verrà generato quando si verifica un errore di un numero specifico tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] o [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Contenuto dell'articolo**  
  
-   **Prima di iniziare:**  
  
     [Limitazioni e restrizioni](#Restrictions)  
  
     [Sicurezza](#Security)  
  
-   **Per creare un avviso utilizzando un numero di errore utilizzando:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Prima di iniziare  
  
###  <a name="Restrictions"></a> Limitazioni e restrizioni  
  
-   
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] include un semplice strumento grafico per la gestione del sistema di avvisi ed è lo strumento consigliato per la configurazione di un'infrastruttura di avvisi.  
  
-   Gli eventi generati con la stored procedure **xp_logevent** si verificano nel database master. Pertanto, **xp_logevent** genera un avviso solo se **@database_name** per l'avviso è **'master'** o NULL.  
  
###  <a name="Security"></a> Sicurezza  
  
####  <a name="Permissions"></a> Autorizzazioni  
 Per impostazione predefinita, solo i membri del ruolo predefinito del server **sysadmin** possono eseguire **sp_add_alert**.  
  
##  <a name="SSMSProcedure"></a> Con SQL Server Management Studio  
  
#### <a name="to-create-an-alert-using-an-error-number"></a>Per creare un avviso utilizzando un numero di errore  
  
1.  In **Esplora oggetti** fare clic sul segno più per espandere il server in cui si desidera creare un avviso tramite un numero di errore.  
  
2.  Fare clic sul segno più per espandere **SQL Server Agent**.  
  
3.  Fare clic con il pulsante destro del mouse su **Avvisi** e selezionare **Nuovo avviso**.  
  
4.  Nella casella **Nome** della finestra di dialogo **Nuovo avviso** immettere un nome per l'avviso.  
  
5.  Selezionare la casella di controllo **Abilita** per abilitare l'esecuzione dell'avviso. Per impostazione predefinita, l'opzione **Abilita** è selezionata.  
  
6.  Nell'elenco **Tipo** selezionare **Avviso per evento di SQL Server**.  
  
7.  Nell'elenco **Nome database**sotto **Definizione di avviso di evento** selezionare un database per limitare l'avviso a un database specifico.  
  
8.  In **Genera avvisi in base a**fare clic su **Numero errore**, quindi digitare un numero errore valido per l'avviso. Alternativamente, fare clic su **Gravità** , quindi selezionare la gravità specifica che genererà l'avviso.  
  
9. Per limitare l'avviso a una particolare sequenza di caratteri, selezionare la casella di controllo corrispondente a **Genera avviso quando il messaggio contiene** e immettere una parola chiave o una stringa di caratteri nella casella **Testo del messaggio**. Il numero massimo di caratteri consentito è 100.  
  
10. Fare clic su **OK**.  
  
##  <a name="TsqlProcedure"></a> Con Transact-SQL  
  
#### <a name="to-create-an-alert-using-an-error-number"></a>Per creare un avviso utilizzando un numero di errore  
  
1.  In **Esplora oggetti**connettersi a un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Sulla barra Standard fare clic su **Nuova query**.  
  
3.  Copiare e incollare l'esempio seguente nella finestra Query, quindi fare clic su **Esegui**.  
  
    ```  
    -- adds an alert (Test Alert) that runs the Back up the AdventureWorks2012 Database job when fired   
    -- assumes that the message 55001 and the Back up the AdventureWorks2012 Database job already exist.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_alert  
        @name = N'Test Alert',  
        @message_id = 55001,   
       @severity = 0,   
       @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
       @job_name = N'Back up the AdventureWorks2012 Database' ;  
    GO  
    ```  
  
 Per ulteriori informazioni, vedere [sp_add_alert &#40;&#41;Transact-SQL ](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql).  
  
  
