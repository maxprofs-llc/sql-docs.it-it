---
title: Configurazione Analysis Services-Directory dati | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ef732855-b7af-4f40-a619-5573c1c354bb
author: heidisteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: 4ff1cd03eb260d892c22c36285fa07d912994510
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66096805"
---
# <a name="analysis-services-configuration---data-directories"></a>Configurazione di Analysis Services - Directory dati
  Le directory predefinite della tabella seguente sono configurabili dall'utente durante l'installazione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'autorizzazione per accedere a questi file viene concessa agli amministratori locali e ai membri del gruppo di sicurezza SQLServerMSASUser$\<istanza> creato e di cui viene effettuato il provisioning durante l'installazione.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
  
|Descrizione|Directory predefinita|Consigli|  
|-----------------|-----------------------|---------------------|  
|Directory radice dati|C:\Programmi\Microsoft SQL Server\MSAS12. \<InstanceId> \OLAP\Data\|assicurarsi che la cartella \Programmi\Microsoft SQL Server \ sia protetta con autorizzazioni limitate. Le prestazioni di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dipendono, in molte configurazioni, dalle prestazioni del sottosistema di archiviazione in cui si trova la directory dei dati. Posizionare tale directory nel sottosistema di archiviazione collegato al sistema in grado di garantire le prestazioni più elevate. Per le installazioni del cluster di failover, assicurarsi che le directory dei dati vengano posizionate nel disco condiviso.|  
|Directory file di log|C:\Programmi\Microsoft SQL Server\MSAS12. \<InstanceId> \OLAP\Log\|è la directory per i [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] file di log e include il log FlightRecorder. Se si aumenta la durata dell'Utilità Traccia eventi, assicurarsi che la directory dei log disponga di spazio sufficiente.|  
|Directory Temp|C:\Programmi\Microsoft SQL Server\MSAS12. \<InstanceId> \OLAP\Temp\|posizionare la directory temporanea nel sottosistema di archiviazione ad alte prestazioni.|  
|Directory di backup|C:\Programmi\Microsoft SQL Server\MSAS12. \<InstanceId> \OLAP\Backup\|è la directory per i [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] file di backup predefiniti. Per le installazioni di PowerPivot per SharePoint, si tratta inoltre della posizione in cui i servizi di sistema PowerPivot memorizzano nella cache i file di dati PowerPivot.<br /><br /> Verificare che vengano impostate le autorizzazioni appropriate in modo da impedire la perdita di dati e che il gruppo di utenti per il servizio [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] disponga delle autorizzazioni adeguate per la scrittura nella directory di backup. Non è supportato l'utilizzo di un'unità di cui è stato eseguito il mapping per le directory di backup.|  
  
## <a name="notes"></a>Note  
  
-   Le istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuite in una farm di SharePoint archiviano i file dell'applicazione, i file di dati e le proprietà nei database del contenuto e delle applicazioni di servizio.  
  
-   Quando si aggiungono funzionalità a un'installazione esistente, non è possibile modificare il percorso di una caratteristica installata in precedenza, né specificare il percorso di una nuova caratteristica.  
  
-   Se si specificano directory di installazione non predefinite, verificare che le cartelle di installazione siano univoche per l'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nessuna delle directory presenti in questa finestra di dialogo deve essere condivisa con le directory di altre istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Anche i componenti [!INCLUDE[ssDE](../../includes/ssde-md.md)] e [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] all'interno di un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] devono essere installati in directory separate.  
  
-   Non è possibile installare file di programma e file di dati nelle situazioni seguenti:  
  
    -   In un'unità disco rimovibile  
  
    -   In un file system che utilizza la compressione  
  
    -   In una directory in cui si trovano i file di sistema  
  
## <a name="see-also"></a>Vedere anche  
 [Percorsi dei file per le istanze predefinite e denominate di SQL Server](../../../2014/sql-server/install/file-locations-for-default-and-named-instances-of-sql-server.md)  
  
  
