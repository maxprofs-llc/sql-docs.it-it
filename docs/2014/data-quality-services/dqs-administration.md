---
title: Amministrazione di DQS| Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
helpviewer_keywords:
- dqs administration
- administration
- dqs,adminstration
ms.assetid: 9940ef5d-f6f6-4dec-9414-1077a4d7f12b
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 7f4ddc16bdfcc7e0d3acdfabe83e81f3d06c0b93
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "70154444"
---
# <a name="dqs-administration"></a>amministrazione dqs
  
  [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) consente di amministrare e gestire varie attività DQS eseguite sul [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], configurare proprietà a livello di server correlate alle attività DQS, configurare le impostazioni del servizio dati di riferimento e le impostazioni di log DQS. Queste attività vengono eseguite tramite la funzionalità **Amministrazione** del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]. In base all'accesso di sicurezza (ruolo) di cui si dispone in DQS, l'accesso a determinate funzioni in quest'area può essere concesso o negato.  
  
 Oltre che per queste attività di amministrazione, in questo argomento vengono fornite informazioni anche per un'attività amministrativa, il backup e ripristino di database DQS, che non viene eseguita utilizzando il [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
 La funzionalità di amministrazione nel [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] offre i vantaggi seguenti:  
  
-   Consente agli amministratori dei dati di eseguire il monitoraggio di varie attività DQS su un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] da un [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
-   Consente agli amministratori DQS di eseguire il monitoraggio delle attività DQS su un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] da un [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]e, se necessario, *terminare* un'attività in esecuzione o *arrestare* un processo in esecuzione all'interno di un'attività.  
  
-   Configurare le impostazioni del servizio dati di riferimento, ad esempio la configurazione della connettività con Azure Marketplace e la gestione diretta di provider del servizio dati di riferimento di terze parti.  
  
-   Configurare valori soglia per le attività di pulizia e di corrispondenza.  
  
-   Abilitare/disabilitare notifiche nel [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
-   Configurare la registrazione in base al livello di gravità degli eventi.  
  
##  <a name="AdminUsingClent"></a>Attività amministrative tramite Data Quality Client  
 Queste attività vengono eseguite tramite la funzionalità **Amministrazione** nel [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].  
  
### <a name="activity-monitoring"></a>Monitoraggio attività  
 Nella schermata **Monitoraggio attività** del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] vengono visualizzate informazioni dettagliate su ogni attività eseguita su un [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]. Questa schermata viene utilizzata principalmente dall'amministratore dei dati per eseguire un monitoraggio di alto livello di tutte le attività eseguite sul [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] a cui è connessa l'applicazione [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] . Questa schermata non consente il monitoraggio a livello di sistema. Inoltre, questa schermata consente agli amministratori DQS di controllare un'attività o un processo all'interno di un'attività terminando un'attività in esecuzione o arrestando un processo in esecuzione all'interno di un'attività, se necessario. Vengono visualizzati i dati per l'individuazione delle informazioni, la gestione del dominio, i criteri di corrispondenza, la pulizia, la corrispondenza e la pulizia basata su SQL Server Integration Services (SSIS).  
  
### <a name="configuration"></a>Configurazione  
 La schermata **Configurazione** del [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] consente all'amministratore DQS di effettuare le attività seguenti:  
  
-   **Dati di riferimento**: configurare provider del servizio dati di riferimento: Azure Marketplace o provider del servizio dati di riferimento diretti. Dopo avere configurato i provider del servizio dati di riferimento, è possibile eseguire il mapping di un dominio singolo/composito ai dati di riferimento durante l'attività di gestione del dominio in una Knowledge Base, quindi utilizzare la stessa Knowledge Base per l'attività di pulizia in un progetto Data Quality. Consente inoltre di specificare le impostazioni proxy per la connessione a Internet per l'uso di Azure Marketplace.  
  
-   **Impostazioni generali**: specificare i valori soglia per la pulizia dei dati e la corrispondenza dei dati e se abilitare le notifiche per la [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)]profilatura in. Questi valori soglia vengono utilizzati da DQS durante le attività di pulizia assistita da computer e di corrispondenza in un progetto Data Quality.  
  
-   **Impostazioni log**: i file di log in DQS registrano le attività eseguite in DQS e sono utili per tenere traccia di problemi operativi durante la manutenzione e la risoluzione dei problemi. È possibile filtrare i messaggi che si desidera registrare per varie funzionalità DQS (gestione del dominio, individuazione delle informazioni, pulizia, corrispondenza e servizi dati di riferimento) e moduli DQS in base al livello di gravità degli eventi.  
  
> [!NOTE]  
>  La schermata **Configurazione** è disponibile solo per gli utenti che dispongono del ruolo dqs_administrator sul database DQS_MAIN.  
  
##  <a name="AdminOutsideClient"></a>Attività amministrative esterne a Data Quality Client  
 Vi sono attività che vengono eseguite esternamente al client Data Quality:  
  
-   **Backup e ripristino di database DQS**: la funzionalità di backup e ripristino dei database DQS è analoga al backup e al ripristino di qualsiasi database di SQL Server con alcune considerazioni specifiche di DQS.  
  
-   **Scollegamento e collegamento di database DQS**: i passaggi per scollegare e connettere i database DQS sono analoghi allo scollegamento e al collegamento di qualsiasi database di SQL Server con alcune considerazioni specifiche di DQS.  
  
 Per altre informazioni, vedere [Manage DQS Databases](../../2014/data-quality-services/manage-dqs-databases.md).  
  
## <a name="related-tasks"></a>Attività correlate  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene descritto come eseguire il monitoraggio delle attività in DQS.|[Monitorare le attività DQS](../../2014/data-quality-services/monitor-dqs-activities.md)|  
|Viene descritto come configurare le impostazioni dei dati di riferimento in DQS.|[Configurazione di DQS per l'utilizzo di dati di riferimento](../../2014/data-quality-services/configure-dqs-to-use-reference-data.md)|  
|Viene descritto come configurare valori soglia per le attività di pulizia e di corrispondenza.|[Configurazione dei valori soglia per le attività di pulizia e di individuazione delle corrispondenze](../../2014/data-quality-services/configure-threshold-values-for-cleansing-and-matching.md)|  
|Viene descritto come abilitare o disabilitare le notifiche in DQS.|[Abilitare o disabilitare le notifiche di profiling in DQS](../../2014/data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md)|  
|Viene descritto come configurare la registrazione DQS in base al livello di gravità degli eventi.|[Configurare livelli di gravità per i file di log DQS](../../2014/data-quality-services/configure-severity-levels-for-dqs-log-files.md)|  
|Viene descritto come configurare le impostazioni avanzate per la registrazione DQS.|[Configurare le impostazioni avanzate per i file di log DQS](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)|  
|Viene descritto come eseguire il backup e il ripristino di database DQS.|[Backup e ripristino di database DQS](../../2014/data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|Viene descritto come scollegare e collegare i database DQS.|[Scollegamento e collegamento di database DQS](../../2014/data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Servizi dati di riferimento in DQS](../../2014/data-quality-services/reference-data-services-in-dqs.md)   
 [Gestire i file di log DQS](../../2014/data-quality-services/manage-dqs-log-files.md)   
 [Manage DQS Databases](../../2014/data-quality-services/manage-dqs-databases.md)  
  
  
