---
title: Impostazione delle opzioni di elaborazione | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ea766d26034b9ee0d1fcefbd215f41c19da1f9ef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075231"
---
# <a name="specifying-processing-options"></a>Impostazione delle opzioni di elaborazione
  La [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuzione guidata legge le opzioni di elaborazione dal \< *nome del progetto*> file con estensione deploymentoptions. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]crea questo file quando si compila il [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]utilizza le opzioni di elaborazione specificate nella pagina **distribuzione** della finestra di dialogo **pagine delle proprietà** del nome del * \<progetto>* per creare il *nome* del \<progetto> file con estensione deploymentoptions.  
  
## <a name="reviewing-the-processing-options-for-deployment"></a>Esame delle opzioni di elaborazione per la distribuzione  
 Di seguito sono riportate \<le impostazioni di configurazione archiviate nel *nome del progetto*> file con estensione deploymentoptions:  
  
-   **Metodo di elaborazione** Questa impostazione determina se gli oggetti distribuiti vengono elaborati dopo la distribuzione e il tipo di elaborazione che verrà eseguita. Sono previste tre opzioni di elaborazione:  
  
    -   Elaborazione predefinita (impostazione predefinita)  
  
    -   Elaborazione completa  
  
    -   nessuno  
  
-   **Opzioni tabella writeback** Se il writeback è abilitato nel [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto, questa impostazione definisce il modo in cui viene gestito il writeback. Sono previste tre opzioni per la tabella writeback:  
  
    -   Per impostazione predefinita, se esiste una tabella writeback essa verrà utilizzata. Se non esiste alcuna tabella writeback, ne verrà creata una nuova.  
  
    -   Se la tabella writeback esiste già, non potrà essere portata a termine la distribuzione. Se non esiste alcuna tabella writeback, ne verrà creata una nuova.  
  
    -   Anche se dovesse esistere già una tabella writeback, ne verrà creata una nuova. In questo caso, Distribuzione guidata [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] elimina ogni eventuale tabella esistente e la sostituisce con una nuova tabella writeback.  
  
-   **Distribuzione transazionale** Questa impostazione determina se la distribuzione delle modifiche dei metadati e dei comandi di elaborazione viene eseguita in una singola transazione o in transazioni separate.  
  
    -   Se questa opzione è impostata su `True` (impostazione predefinita), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuisce tutte le modifiche dei metadati e tutti i comandi di elaborazione attraverso una singola transazione.  
  
    -   Se invece questa opzione è impostata su `False`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] distribuisce le modifiche dei metadati attraverso una singola transazione e distribuisce ogni comando di elaborazione in transazioni separate.  
  
## <a name="modifying-the-processing-options-for-deployment"></a>Modifica delle opzioni di elaborazione per la distribuzione  
 Potrebbe tuttavia essere necessario distribuire il [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] progetto utilizzando diverse opzioni di elaborazione rispetto a quelle archiviate nel \< *nome del progetto*> file con estensione deploymentoptions. Potrebbe ad esempio essere preferibile elaborare tutti gli oggetti in modo completo o elaborarli utilizzando l'opzione di elaborazione predefinita o infine non elaborarli affatto. Se i cubi o le dimensioni sono abilitati per la scrittura, è possibile specificare se verrà utilizzata una tabella writeback nuova o preesistente.  
  
 Per modificare le opzioni di elaborazione da utilizzare durante la distribuzione, è possibile modificare o ricompilare il progetto, oppure è possibile modificare le opzioni di elaborazione nel file di input utilizzando uno dei metodi descritti nella procedura seguente.  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a>Per modificare le opzioni di elaborazione dopo la generazione dei file di input  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in modo interattivo. Nella pagina **Opzioni di elaborazione** specificare le opzioni di elaborazione per il progetto da distribuire.  
  
     -oppure-  
  
-   Eseguire Distribuzione guidata di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] attraverso il prompt dei comandi e impostarla in modo che venga eseguita in modalità file di risposte. Per altre informazioni sulla modalità file di risposte, vedere [Esecuzione della Distribuzione guidata Analysis Services](running-the-analysis-services-deployment-wizard.md).  
  
     -oppure-  
  
-   Modificare il \< *nome del progetto*> file deploymentoptions utilizzando un editor di testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazione della destinazione di installazione](deployment-script-files-specifying-the-installation-target.md)   
 [Impostazione delle opzioni di distribuzione di partizioni e ruoli](deployment-script-files-partition-and-role-deployment-options.md)   
 [Definizione delle impostazioni di configurazione per la distribuzione di soluzioni](deployment-script-files-solution-deployment-config-settings.md)  
  
  
