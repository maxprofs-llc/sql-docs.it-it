---
title: Strumenti per la risoluzione dei problemi relativi allo sviluppo dei pacchetti | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 41dd248c-dab3-4318-b8ba-789a42d5c00c
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d4ee6252daa58a5e99b8fdd5be6099e8e9de936d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37320681"
---
# <a name="troubleshooting-tools-for-package-development"></a>Risoluzione dei problemi relativi agli strumenti per lo sviluppo dei pacchetti
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include funzionalità e strumenti per la risoluzione dei problemi che possono verificarsi durante lo sviluppo di pacchetti in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
## <a name="troubleshooting-design-time-validation-issues"></a>Risoluzione dei problemi relativi alla convalida in fase di progettazione  
 Nella versione corrente di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], all'apertura di un pacchetto il sistema convalida tutte le connessioni prima di convalidare tutti i componenti del flusso di dati e imposta tutte le connessioni che sono lente o non disponibili per il funzionamento offline. In questo modo è possibile ridurre il ritardo nella convalida del flusso di dati del pacchetto.  
  
 Dopo aver aperto un pacchetto, è possibile disattivare una connessione anche facendo clic con il pulsante destro del mouse sulla gestione connessione nell'area **Gestioni connessioni** e scegliendo quindi **Offline**. In questo modo è possibile velocizzare le operazioni in Progettazione SSIS.  
  
 Le connessioni impostate per funzionare offline, rimarranno tali fino a quando non viene effettuata una delle operazioni seguenti:  
  
-   Testare la connessione facendo clic con il pulsante destro del mouse sulla gestione connessione nell'area **Gestioni connessioni** di Progettazione SSIS e scegliendo quindi **Test connettività**.  
  
     Ad esempio, una connessione è impostata inizialmente per funzionare offline quando viene aperto il pacchetto. Modificare la stringa di connessione per risolvere il problema e fare clic su **Test connettività** per testare la connessione.  
  
-   Aprire di nuovo il pacchetto o il progetto contenente il pacchetto. La convalida viene eseguita nuovamente su tutte le connessioni nel pacchetto.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include le seguenti funzionalità aggiuntive per evitare errori di convalida:  
  
-   **Impostare tutto il pacchetto e tutte le connessioni per il funzionamento offline quando le origini dati non sono disponibili**. È possibile abilitare **Offline** dal menu **SSIS** . A differenza di `DelayValidation` proprietà, il **lavora Offline** opzione è disponibile anche prima di aprire un pacchetto. È anche possibile abilitare l'opzione **Offline** per rendere più veloci le operazioni di progettazione e disabilitarla solo quando si vuole convalidare il pacchetto.  
  
-   **Configurare la proprietà DelayValidation per gli elementi del pacchetto non validi fino alla fase di esecuzione**. È possibile impostare la proprietà `DelayValidation` su `True` per gli elementi del pacchetto la cui configurazione non è valida in fare di progettazione, per impedire gli errori di convalida. Potrebbe ad esempio essere presente un'attività Flusso di dati in cui viene utilizzata una tabella di destinazione che non esiste fino a quando non viene creata in fase di esecuzione da un'attività Esegui SQL. Il `DelayValidation` proprietà può essere abilitata a livello di pacchetto o a livello di singole attività e contenitori che include il pacchetto. In genere, è necessario lasciare impostata questa proprietà su `True` negli stessi elementi del pacchetto quando si distribuisce il pacchetto, per impedire gli stessi errori di convalida in fase di esecuzione.  
  
     Il `DelayValidation` proprietà può essere impostata su un'attività flusso di dati, ma non sui dati singoli componenti del flusso. È possibile ottenere un risultato simile impostando la proprietà <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> dei singoli componenti flusso di dati su `false`. Tuttavia, quando il valore di questa proprietà è `false`, il componente non riconosce le modifiche ai metadati delle origini dati esterne.  
  
 Se gli oggetti di database utilizzati dal pacchetto risultano bloccati durante la convalida, è possibile che il processo di convalida si arresti. In questi casi, si arresterà anche Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . È possibile riprendere la convalida usando [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] per chiudere le sessioni associate in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questo problema può essere evitato anche utilizzando le impostazioni descritte in questa sezione.  
  
## <a name="troubleshooting-control-flow"></a>Risoluzione dei problemi del flusso di controllo  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include gli strumenti e le funzionalità seguenti per la risoluzione dei problemi relativi al flusso di controllo nei pacchetti che possono verificarsi durante lo sviluppo di pacchetti:  
  
-   **Impostare punti di interruzione in attività, contenitori e pacchetti**. È possibile impostare punti di interruzione tramite gli strumenti grafici disponibili in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] . I punti di interruzione possono essere abilitati a livello di pacchetto oppure delle singole attività e dei singoli contenitori del pacchetto. Alcune attività e contenitori includono condizioni di interruzione aggiuntive per l'impostazione dei punti di interruzione. Per il contenitore Ciclo For è ad esempio possibile abilitare una condizione di interruzione che sospende l'esecuzione all'inizio di ogni iterazione del ciclo.  
  
-   **Usare le finestre di debug**. Quando si esegue un pacchetto che include punti di interruzione, tramite le finestre di debug di [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] è possibile accedere ai valori di variabili e ai messaggi di stato.  
  
-   **Esaminare le informazioni nella scheda Stato**. [!INCLUDE[ssIS](../../includes/ssis-md.md)] Progettazione visualizza informazioni aggiuntive sul flusso di controllo quando si esegue un pacchetto in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Nella scheda Stato sono elencati i contenitori e le attività in ordine di esecuzione, nonché l'ora di inizio e di fine, gli avvisi e i messaggi di errore per ogni contenitore e attività, inclusi quelli relativi al pacchetto stesso.  
  
 Per altre informazioni su queste funzionalità, vedere [Debug del flusso di controllo](debugging-control-flow.md).  
  
## <a name="troubleshooting-data-flow"></a>Risoluzione dei problemi del flusso di dati  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] include gli strumenti e le funzionalità seguenti per la risoluzione dei problemi relativi ai flussi di dati nei pacchetti che possono verificarsi durante lo sviluppo di pacchetti:  
  
-   **Eseguire test con solo un subset di dati**. Se si desidera risolvere i problemi del flusso di dati di un pacchetto utilizzando solo un campionamento del set di dati, è possibile includere una trasformazione Campionamento percentuale o Campionamento righe in modo da creare un campionamento dei dati inline in fase di esecuzione. Per altre informazioni, vedere [Trasformazione Campionamento percentuale](../data-flow/transformations/percentage-sampling-transformation.md) e [Trasformazione Campionamento righe](../data-flow/transformations/row-sampling-transformation.md).  
  
-   **Usare visualizzatori dati per il monitoraggio dei dati durante il passaggio nel flusso di dati**. Nei visualizzatori dati vengono visualizzati i valori dei dati durante il trasferimento tra origini, trasformazioni e destinazioni. Un visualizzatore consente di visualizzare i dati in una griglia. È possibile copiare dati dal visualizzatore agli Appunti e incollare quindi i dati copiati in un file o foglio di calcolo di Excel. Per altre informazioni, vedere [Aggiungere un visualizzatore dati a un flusso di dati](../add-a-data-viewer-to-a-data-flow.md).  
  
-   **Configurare gli output degli errori nei componenti del flusso di dati che li supportano**. Molte origini, trasformazioni e destinazioni del flusso di dati supportano gli output degli errori. Tramite la configurazione dell'output degli errori di un componente flusso di dati, è possibile dirigere i dati contenenti errori a una destinazione specifica. È ad esempio possibile acquisire in un file di testo distinto i dati che hanno generato un errore o che sono stati troncati. È inoltre possibile associare visualizzatori dati agli output degli errori ed esaminare solo i dati errati. In fase di progettazione negli output degli errori vengono acquisiti valori di dati errati per consentire lo sviluppo di pacchetti che gestiscano in modo efficiente dati reali. A differenza, tuttavia, di altri strumenti e caratteristiche per la risoluzione di problemi utili solo in fase di progettazione, gli output degli errori sono utili nell'ambiente di produzione. Per altre informazioni, vedere [Gestione degli errori nei dati](../data-flow/error-handling-in-data.md).  
  
-   **Acquisire il conteggio delle righe elaborate**. Quando si esegue un pacchetto in Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] , nella finestra di progettazione del flusso di dati viene visualizzato il numero di righe che sono state spostate lungo un determinato percorso. Tale numero viene aggiornato periodicamente quando i dati vengono spostati lungo tale percorso. Nel flusso di dati è inoltre possibile aggiungere una trasformazione Conteggio righe per l'acquisizione del conteggio di righe finale in una variabile. Per altre informazioni, vedere [Trasformazione Conteggio righe](../data-flow/transformations/row-count-transformation.md).  
  
-   **Esaminare le informazioni nella scheda Stato**. [!INCLUDE[ssIS](../../includes/ssis-md.md)] Progettazione visualizza informazioni aggiuntive sui flussi di dati quando si esegue un pacchetto in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Nella scheda Stato sono elencati i componenti flusso di dati in ordine di esecuzione, nonché lo stato di ogni fase del pacchetto, visualizzato in forma di percentuale di completamento, e il numero di righe scritte nella destinazione.  
  
 Per altre informazioni su queste funzionalità, vedere [Debug del flusso di dati](debugging-data-flow.md).  
  
## <a name="troubleshooting-scripts"></a>Risoluzione dei problemi relativi agli script  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] L'attività Script e il componente Script usano Microsoft Visual Studio Tools for Applications (VSTA) come ambiente di sviluppo in cui scrivere gli script e come motore in cui eseguirli. In VSTA sono disponibili gli strumenti e le caratteristiche seguenti per la risoluzione dei problemi relativi agli script durante lo sviluppo dei pacchetti:  
  
-   **Impostazione dei punti di interruzione negli script delle attività Script.** In VSTA è disponibile il supporto per il debug di script solo per l'attività Script. I punti di interruzione impostati nell'attività Script vengono integrati con i punti di interruzione impostati sia nei pacchetti che nelle attività e nei contenitori dei pacchetti in modo da consentire il debug di tutti gli elementi del pacchetto.  
  
    > [!NOTE]  
    >  Quando si esegue il debug di un pacchetto che contiene più attività Script, il debugger rileva i punti di interruzione in una sola attività Script, ignorando i punti di interruzione nelle altre attività Script. Se un'attività Script fa parte di un contenitore Ciclo Foreach o Ciclo For, il debugger ignorerà i punti di interruzione nell'attività Script dopo la prima iterazione del ciclo.  
  
 Per altre informazioni, vedere [Debug degli script](debugging-script.md). Per suggerimenti su come eseguire il debug del componente Script, vedere [codifica e debug del componente Script] (.. / extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md.  
  
## <a name="troubleshooting-errors-without-a-description"></a>Risoluzione dei problemi relativi agli errori senza descrizione  
 Se durante lo sviluppo di un pacchetto viene visualizzato un numero di errore di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] senza una descrizione, è possibile ottenere la descrizione in [Guida di riferimento ai messaggi e agli errori di Integration Services](../integration-services-error-and-message-reference.md). Al momento, nell'elenco non sono incluse informazioni per la risoluzione dei problemi.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi degli strumenti per l'esecuzione del pacchetto](troubleshooting-tools-for-package-execution.md)   
 [Funzionalità delle prestazioni del flusso di dati](../data-flow/data-flow-performance-features.md)  
  
  