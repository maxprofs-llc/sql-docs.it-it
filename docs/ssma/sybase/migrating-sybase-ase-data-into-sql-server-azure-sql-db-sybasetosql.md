---
title: Eseguire la migrazione di dati di Sybase ASE in SQL Server-database SQL di Azure | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Migrating data,Client Side Data Migration
- Migrating data,Server Side Data Migration
ms.assetid: 54a39f5e-9250-4387-a3ae-eae47c799811
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 28a07c08fd801a9d5fdcdde4206f7aa6fe7b926f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028841"
---
# <a name="migrating-sybase-ase-data-into-sql-server---azure-sql-db--sybasetosql"></a>Migrazione di dati di Sybase ASE in SQL Server-database SQL di Azure (SybaseToSQL)
Dopo aver caricato correttamente gli oggetti di database di Sybase Adaptive Server Enterprise (ASE) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o nel database SQL di Azure, è possibile eseguire la migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dei dati dall'ambiente del servizio app al database SQL di Azure o.  
  
> [!IMPORTANT]  
> Se il motore usato è il motore di migrazione dei dati lato server, prima di eseguire la migrazione dei dati, è necessario installare il pacchetto di estensione SSMA per Sybase ASE e i provider dell'ambiente del servizio app Sybase nel computer che esegue SSMA. È inoltre necessario che il servizio SQL Server Agent sia in esecuzione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti di SSMA su SQL Server (SybaseToSQL)](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d) .  
  
## <a name="setting-migration-options"></a>Impostazione delle opzioni di migrazione  
Prima di eseguire la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] migrazione dei dati in o nel database SQL di Azure, esaminare le opzioni di migrazione del progetto nella finestra di dialogo **Impostazioni progetto** .  
  
-   Utilizzando questa finestra di dialogo è possibile impostare opzioni quali le dimensioni del batch di migrazione, il blocco della tabella, il controllo dei vincoli, la gestione dei valori null e la gestione dei valori Identity. Per ulteriori informazioni sulle impostazioni di migrazione del progetto, vedere [Impostazioni progetto (migrazione) (Sybase)](https://msdn.microsoft.com/82f8857f-7ab1-4738-ab6e-b1e95ea94924).  
  
    Per altre informazioni sulle **impostazioni di migrazione dei dati estese**, vedere [impostazioni di migrazione dei dati](data-migration-settings-sybasetosql.md)  
  
-   Il **motore di migrazione** nella finestra di dialogo **Impostazioni progetto** consente all'utente di eseguire il processo di migrazione utilizzando due tipi di motori di migrazione dei dati, vale a dire:  
  
    1.  Motore di migrazione dati lato client  
  
    2.  Motore di migrazione dei dati lato server  
  
**Migrazione dei dati sul lato client:**  
  
-   Per avviare la migrazione dei dati sul lato client, selezionare l'opzione **motore di migrazione dei dati lato client** nella finestra di dialogo **Impostazioni progetto** .  
  
-   In **Impostazioni progetto**, l'opzione **motore di migrazione dati lato client** è impostata per impostazione predefinita.  
  
    > [!NOTE]  
    > Il motore di migrazione dei dati lato client si trova all'interno dell'applicazione SSMA e, di conseguenza, non dipende dalla disponibilità del pacchetto di estensione.  
  
**Migrazione dei dati lato server:**  
  
-   Durante la migrazione dei dati sul lato server, il motore risiede nel database di destinazione. Viene installato tramite il pacchetto di estensione. Per ulteriori informazioni su come installare il pacchetto di estensione, vedere [installazione dei componenti di SSMA su SQL Server (SybaseToSQL)](https://msdn.microsoft.com/5ad9e12c-2cdb-4dd2-8703-05a23242d19d) .  
  
-   Per avviare la migrazione sul lato server, selezionare l'opzione **motore di migrazione dei dati sul lato server** nella finestra di dialogo **Impostazioni progetto** .  
  
> [!NOTE]  
> Quando si usa il database SQL di Azure come database di destinazione, è consentita solo la **migrazione dei dati lato client** e la migrazione dei dati sul lato server non è supportata.  
  
## <a name="migrating-data-to-sql-server-or-azure-sql-db"></a>Migrazione dei dati a SQL Server o al database SQL di Azure  
La migrazione dei dati è un'operazione di caricamento bulk che sposta le righe di dati dalle tabelle dell'ambiente del servizio app alle tabelle SQL Server nelle transazioni. Il numero di righe caricate in SQL Server o nel database SQL di Azure in ogni transazione viene configurato nelle impostazioni del progetto.  
  
Per visualizzare i messaggi di migrazione, assicurarsi che il riquadro di output sia visibile. In caso contrario, scegliere **output** dal menu **Visualizza** .  
  
**Per eseguire la migrazione dei dati**  
  
1.  Verificare quanto segue:  
  
    -   I provider dell'ambiente del servizio app sono installati nel computer che esegue SSMA.  
  
    -   Gli oggetti convertiti sono stati sincronizzati con il database di destinazione (SQL Server o database SQL di Azure).  
  
2.  In Sybase Metadata Explorer selezionare gli oggetti che contengono i dati di cui si vuole eseguire la migrazione:  
  
    -   Per eseguire la migrazione dei dati per tutti gli schemi, selezionare la casella di controllo accanto agli **schemi**.  
  
    -   Per eseguire la migrazione dei dati o omettere singole tabelle, espandere innanzitutto lo schema, espandere **tabelle**, quindi selezionare o deselezionare la casella di controllo accanto alla tabella.  
  
3.  Per eseguire la migrazione dei dati, si verificano due casi:  
  
    **Migrazione dei dati sul lato client:**  
  
    Per eseguire la **migrazione dei dati lato client**, selezionare l'opzione **motore di migrazione dati lato client** nella finestra di dialogo **Impostazioni progetto** .  
  
    **Migrazione dei dati lato server:**  
  
    -   Prima di eseguire la migrazione dei dati sul lato server, verificare quanto segue:  
  
        1.  SSMA per Sybase Extension Pack è installato nell'istanza di SQL Server.  
  
        2.  Il servizio SQL Server Agent è in esecuzione nell'istanza di SQL Server  
  
    -   Per eseguire la **migrazione dei dati sul lato server**, selezionare l'opzione **motore di migrazione dei dati sul lato server** nella finestra di dialogo **Impostazioni progetto** .  
  
4.  Fare clic con il pulsante destro del mouse su **schemi** in Sybase Metadata Explorer, quindi scegliere **Migrate data**. È inoltre possibile eseguire la migrazione dei dati per singoli oggetti o categorie di oggetti: fare clic con il pulsante destro del mouse sull'oggetto o la relativa cartella padre, quindi selezionare l'opzione **Migrate data** .  
  
    > [!NOTE]  
    > Se SSMA per Sybase Extension Pack non è installato nell'istanza di SQL Server e se è selezionato **motore di migrazione dei dati lato server** , durante la migrazione dei dati nel database di destinazione si verifica l'errore seguente:' SSMA i componenti di migrazione dei dati non sono stati trovati nel SQL Server, non sarà possibile eseguire la migrazione dei dati sul lato server. Verificare se il pacchetto di estensione è installato correttamente. Fare clic su **Annulla** per terminare la migrazione dei dati.  
  
5.  Nella finestra di dialogo **Connetti a Sybase ASE** immettere le credenziali di connessione, quindi fare clic su **Connetti**. Per altre informazioni sulla connessione a Sybase ASE, vedere [connettersi a sybase &#40;SybaseToSQL&#41;](../../ssma/sybase/connect-to-sybase-sybasetosql.md)  
  
    Se il database di destinazione è SQL Server, immettere le credenziali di connessione nella finestra di dialogo **Connetti a SQL Server** , quindi fare clic su **Connetti**. Per ulteriori informazioni sulla connessione a SQL Server, vedere la pagina relativa [alla connessione a SQL Server (SybaseToSQL)](https://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)  
  
    Se il database di destinazione è database SQL di Azure, immettere le credenziali di connessione nella finestra di dialogo **Connetti a database SQL di Azure** e fare clic su **Connetti**. Per altre informazioni sulla connessione al database SQL di Azure, vedere [connessione al database SQL di azure &#40;SybaseToSQL&#41;](../../ssma/sybase/connecting-to-azure-sql-db-sybasetosql.md)  
  
    I messaggi verranno visualizzati nel riquadro di **output** . Al termine della migrazione, viene visualizzato il **report migrazione dei dati** . Se non è stata eseguita la migrazione di dati, fare clic sulla riga che contiene gli errori, quindi fare clic su **Dettagli**. Al termine del report, fare clic su **Chiudi**. Per ulteriori informazioni sul report di migrazione dei dati, vedere [report sulla migrazione dei dati (SSMA Common)](https://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Quando si usa SQL Express Edition come database di destinazione, è consentita solo la migrazione dei dati lato client e la migrazione dei dati sul lato server non è supportata.  
  
## <a name="see-also"></a>Vedere anche  
[Migrazione dei database Sybase ASE a SQL Server-database SQL di Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
