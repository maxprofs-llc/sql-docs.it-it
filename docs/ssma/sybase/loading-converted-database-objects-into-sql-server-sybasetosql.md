---
title: Caricamento di oggetti di database convertiti in SQL Server (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Loading Converted Database Objects
ms.assetid: 4c59256f-99a8-4351-9559-a455813dbd06
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 5185e8b1364fe2a5bae92c40c99e8f52bcd32ba7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028936"
---
# <a name="loading-converted-database-objects-into-sql-server-sybasetosql"></a>Caricamento di oggetti di database convertiti in SQL Server (SybaseToSQL)
Dopo aver convertito oggetti di database di Sybase Adaptive Server Enterprise (ASE) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure, è possibile caricare gli oggetti di database risultanti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure. È possibile fare in modo che SSMA crei gli oggetti oppure è possibile creare script per gli oggetti ed eseguire gli script manualmente. SSMA consente inoltre di aggiornare i metadati di destinazione con il contenuto effettivo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di o SQL Azure database.  
  
## <a name="choosing-between-synchronization-and-scripts"></a>Scelta tra sincronizzazione e script  
Se si desidera caricare gli oggetti di database convertiti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in o SQL Azure senza modifiche, è possibile fare in modo che SSMA crei o ricrei direttamente gli oggetti di database. Questo metodo è rapido e semplice, ma non consente la [!INCLUDE[tsql](../../includes/tsql-md.md)] personalizzazione del codice che definisce [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure oggetti, diversi dalle stored procedure.  
  
Se si desidera modificare [!INCLUDE[tsql](../../includes/tsql-md.md)] l'oggetto utilizzato per creare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure oppure se si desidera un maggiore controllo sul momento e sulla modalità di creazione degli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure, utilizzare SSMA per creare [!INCLUDE[tsql](../../includes/tsql-md.md)] gli script. È quindi possibile modificare tali script, creare singolarmente ogni oggetto e persino utilizzare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure Agent per pianificare la creazione di tali oggetti.  
  
## <a name="using-ssma-to-load-objects-into-sql-server-or-sql-azure"></a>Utilizzo di SSMA per caricare oggetti in SQL Server o SQL Azure  
Per utilizzare SSMA per creare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure oggetti di database, è necessario selezionare gli [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetti in o SQL Azure Esplora metadati, quindi sincronizzare gli oggetti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con o SQL Azure, come illustrato nella procedura seguente. Per impostazione predefinita, se gli oggetti sono già [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] presenti in o SQL Azure e se i metadati SSMA hanno alcune modifiche locali o aggiornamenti alla definizione di tali oggetti, SSMA modificherà le definizioni degli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure. È possibile modificare il comportamento predefinito modificando **le impostazioni del progetto**.  
  
> [!NOTE]  
> È possibile selezionare gli [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oggetti di database esistenti o SQL Azure che non sono stati convertiti dai database dell'ambiente del servizio app. Tuttavia, tali oggetti non verranno ricreati o modificati da SSMA.  
  
**Per sincronizzare oggetti con SQL Server o SQL Azure**  
  
1.  In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure Esplora Metadati espandere il nodo superiore [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure, quindi espandere **database**.  
  
2.  Selezionare gli oggetti da elaborare:  
  
    -   Per sincronizzare un database completo, selezionare la casella di controllo accanto al nome del database.  
  
    -   Per sincronizzare o omettere singoli oggetti o categorie di oggetti, selezionare o deselezionare la casella di controllo accanto all'oggetto o alla cartella.  
  
3.  Dopo aver selezionato gli oggetti da elaborare in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o SQL Azure Esplora metadati, fare clic con il pulsante destro del mouse su **database**, quindi scegliere **Sincronizza con database**.  
  
    È inoltre possibile sincronizzare singoli oggetti o categorie di oggetti facendo clic con il pulsante destro del mouse sull'oggetto o la relativa cartella padre, quindi scegliendo **Sincronizza con database**.  
  
    Successivamente, SSMA visualizzerà la finestra di dialogo **Sincronizza con database, in** cui è possibile visualizzare due gruppi di elementi. Sul lato sinistro, SSMA Mostra gli oggetti di database selezionati rappresentati in un albero. Sul lato destro è possibile visualizzare un albero che rappresenta gli stessi oggetti nei metadati SSMA. È possibile espandere l'albero facendo clic sul pulsante a destra o a sinistra. La direzione della sincronizzazione viene visualizzata nella colonna azione posizionata tra i due alberi.  
  
    Un segno di azione può trovarsi in tre stati:  
  
    -   Una freccia sinistra indica che il contenuto dei metadati verrà salvato nel database (impostazione predefinita).  
  
    -   Una freccia destra indica che il contenuto del database sovrascriverà i metadati SSMA.  
  
    -   Un segno incrociato indica che non verrà eseguita alcuna azione.  
  
Fare clic sul segno di azione per modificare lo stato. La sincronizzazione effettiva verrà eseguita quando si fa clic sul pulsante **OK** della finestra di dialogo **Sincronizza con database** .  
  
## <a name="scripting-objects"></a>Oggetti di scripting  
Se si desidera salvare [!INCLUDE[tsql](../../includes/tsql-md.md)] le definizioni degli oggetti di database convertiti o si desidera modificare le definizioni degli oggetti ed eseguire manualmente gli script, è possibile salvare le definizioni degli oggetti di [!INCLUDE[tsql](../../includes/tsql-md.md)] database convertiti in script.  
  
**Per salvare oggetti come script**  
  
1.  Dopo aver selezionato gli oggetti da salvare in uno script, fare clic con il pulsante destro del mouse su **database**e quindi scegliere **Salva come script**.  
  
    È anche possibile creare script per singoli oggetti o categorie di oggetti facendo clic con il pulsante destro del mouse sull'oggetto o sulla cartella che lo contiene, quindi selezionando **Salva script**.  
  
2.  Nella finestra di dialogo **Salva con** nome individuare la cartella in cui si desidera salvare lo script, immettere un nome di file nella casella **nome file** , quindi fare clic su **OK**.  
  
    SSMA aggiungerà l'estensione del nome di file SQL.  
  
### <a name="modifying-scripts"></a>Modifica di script  
Dopo aver salvato le definizioni [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] degli oggetti o SQL Azure come uno o più script, è possibile utilizzare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per visualizzare e modificare gli script.  
  
**Per modificare uno script**  
  
1.  Scegliere [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Apri** dal menu **File**e quindi fare clic su **File**.  
  
2.  Nella finestra di dialogo **Apri** passare a e selezionare il file di script, quindi fare clic su **OK**.  
  
3.  Modificare e il file di script utilizzando l'editor di query di.  
  
    Per ulteriori informazioni sull'editor di query, vedere "comandi pratici e funzionalità dell'editor" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nella documentazione online di.  
  
4.  Per salvare lo script, scegliere **Salva**dal menu file.  
  
### <a name="running-scripts"></a>Esecuzione di script  
È possibile eseguire uno script o singole istruzioni in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
**Per eseguire uno script**  
  
1.  Scegliere [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **Apri** dal menu **File**e quindi fare clic su **File**.  
  
2.  Nella finestra di dialogo **Apri** passare a e selezionare il file di script, quindi fare clic su **OK**.  
  
3.  Per eseguire lo script completo, premere il tasto **F5** .  
  
4.  Per eseguire un set di istruzioni, selezionare le istruzioni nella finestra dell'editor di query, quindi premere il tasto **F5** .  
  
Per ulteriori informazioni sull'utilizzo dell'editor di query per eseguire gli script, vedere l' [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] argomento "query [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] " nella documentazione in linea.  
  
È inoltre possibile eseguire script dalla riga di comando tramite l'utilità **SQLCMD** e da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Per ulteriori informazioni su **SQLCMD**, vedere l'argomento relativo all'utilità [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sqlcmd nella documentazione online di. Per ulteriori informazioni su [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, vedere "automazione delle attività amministrative ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent)" nella [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] documentazione online di.  
  
## <a name="securing-objects-in-sql-server"></a>Protezione di oggetti in SQL Server  
Dopo aver caricato gli oggetti di database convertiti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in, è possibile concedere e negare autorizzazioni per tali oggetti. È consigliabile eseguire questa operazione prima di eseguire la migrazione dei dati [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]a. Per informazioni su come proteggere gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vedere "Considerazioni sulla protezione per database e applicazioni di database" [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nella documentazione online di.  
  
## <a name="next-step"></a>passaggio successivo  
Il passaggio successivo del processo di migrazione consiste nell'eseguire la [migrazione di dati di Sybase ASE in SQL Server/SQL Azure (SybaseToSQL)](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione dei database Sybase ASE a SQL Server-database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
