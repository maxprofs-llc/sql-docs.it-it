---
title: Connessione al database SQL di Azure (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 9e77e4b0-40c0-455c-8431-ca5d43849aa7
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 10be1dc3652c944b9de08a01b0f4cdff5ae5849a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "70176235"
---
# <a name="connecting-to-azure-sql-db-sybasetosql"></a>Connessione al database SQL di Azure (SybaseToSQL)
Per eseguire la migrazione dei database Sybase al database SQL di Azure, è necessario connettersi all'istanza di destinazione del database SQL di Azure. Quando si esegue la connessione, SSMA ottiene i metadati relativi a tutti i database nell'istanza del database SQL di Azure e Visualizza i metadati del database in Esplora metadati del database SQL di Azure. SSMA archivia le informazioni dell'istanza del database SQL di Azure a cui si è connessi, ma non archivia le password.  
  
La connessione al database SQL di Azure rimane attiva fino a quando non si chiude il progetto. Quando si riapre il progetto, è necessario riconnettersi al database SQL di Azure se si vuole una connessione attiva al server. È possibile lavorare offline fino a quando non si caricano oggetti di database nel database SQL di Azure e si migrano i dati.  
  
I metadati relativi all'istanza del database SQL di Azure non vengono sincronizzati automaticamente. Per aggiornare i metadati in Esplora metadati del database SQL di Azure, è invece necessario aggiornare manualmente i metadati del database SQL di Azure. Per ulteriori informazioni, vedere la sezione relativa alla sincronizzazione dei metadati del database SQL di Azure più avanti in questo argomento.  
  
## <a name="required-azure-sql-db-permissions"></a>Autorizzazioni del database SQL di Azure necessarie  
L'account usato per connettersi al database SQL di Azure richiede autorizzazioni diverse a seconda delle azioni eseguite dall'account:  
  
1.  Per convertire gli oggetti Sybase [!INCLUDE[tsql](../../includes/tsql-md.md)] in sintassi, per aggiornare i metadati dal database SQL di Azure o per salvare la sintassi convertita in script, l'account deve disporre dell'autorizzazione per accedere all'istanza del database SQL di Azure.  
  
2.  Per caricare oggetti di database nel database SQL di Azure, il requisito di autorizzazione minimo è l'appartenenza al ruolo del database **db_owner** nel database di destinazione.  
  
## <a name="establishing-an-azure-sql-db-connection"></a>Creazione di una connessione del database SQL di Azure  
Prima di convertire gli oggetti di database Sybase nella sintassi del database SQL di Azure, è necessario stabilire una connessione all'istanza del database SQL di Azure in cui si vuole eseguire la migrazione del database o dei database Sybase.  
  
Quando si definiscono le proprietà di connessione, è inoltre necessario specificare il database in cui verrà eseguita la migrazione degli oggetti e dei dati. È possibile personalizzare questo mapping a livello di schema Sybase dopo la connessione al database SQL di Azure. Per altre informazioni, vedere mapping degli schemi dell'ambiente del servizio app [Sybase a schemi SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
> [!WARNING]  
> Prima di provare a connettersi al database SQL di Azure, assicurarsi che l'istanza del database SQL di Azure sia in esecuzione e che sia in grado di accettare le connessioni.  
  
**Per connettersi al database SQL di Azure**  
  
1.  Scegliere **Connetti al database SQL di Azure**dal menu **file** . questa opzione è abilitata dopo la creazione di un progetto.  
  
    Se si è già connessi al database SQL di Azure, il nome del comando verrà **riconnesso al database SQL di Azure**  
  
2.  Nella finestra di dialogo connessione immettere o selezionare il nome del server del database SQL di Azure.  
  
3.  Immettere, selezionare o **esplorare** il nome del database.  
  
4.  Immettere o selezionare **username**.  
  
5.  Immettere la **password**.  
  
6.  SSMA consiglia la connessione crittografata al database SQL di Azure.  
  
7.  Fare clic su **Connetti**.  
  
> [!IMPORTANT]  
> SSMA per Sybase non supporta la connessione al database **Master** nel database SQL di Azure.  
  
## <a name="synchronizing-azure-sql-db-metadata"></a>Sincronizzazione dei metadati del database SQL di Azure  
I metadati relativi ai database SQL di Azure non vengono aggiornati automaticamente. I metadati in Esplora metadati del database SQL di Azure sono uno snapshot dei metadati alla prima connessione al database SQL di Azure o all'ultima volta che sono stati aggiornati manualmente i metadati. È possibile aggiornare manualmente i metadati per tutti i database o per qualsiasi singolo database o oggetto di database.  
  
**Per sincronizzare i metadati**  
  
1.  Assicurarsi di essere connessi al database SQL di Azure.  
  
2.  In Esplora metadati del database SQL di Azure selezionare la casella di controllo accanto allo schema del database o del database che si desidera aggiornare.  
  
    Ad esempio, per aggiornare i metadati per tutti i database, selezionare la casella accanto a database.  
  
3.  Fare clic con il pulsante destro del mouse su database o sul database singolo o sullo schema del database, quindi scegliere **Sincronizza con database**.  
  
## <a name="next-step"></a>passaggio successivo  
Il passaggio successivo della migrazione dipende dalle esigenze del progetto:  
  
-   Per personalizzare il mapping tra gli schemi di Sybase e i database e gli schemi del database SQL di Azure, vedere mapping degli schemi dell'ambiente del servizio app [Sybase a schemi SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql.md)  
  
-   Per personalizzare le opzioni di configurazione per i progetti, vedere [impostazione delle opzioni del progetto &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)  
  
-   Per personalizzare il mapping dei tipi di dati di origine e di destinazione, vedere Mapping dei tipi di [dati di Sybase ASE e SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)  
  
-   Se non è necessario eseguire nessuna di queste attività, è possibile convertire le definizioni degli oggetti di database Sybase nelle definizioni degli oggetti del database SQL di Azure. Per altre informazioni, vedere [conversione di oggetti di database di Sybase ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/converting-sybase-ase-database-objects-sybasetosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione dei database Sybase ASE a SQL Server-database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
