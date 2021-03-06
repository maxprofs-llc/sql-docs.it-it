---
title: Preparazione all'implementazione di un'estensione per il recapito | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- interfaces [Reporting Services]
- delivery extensions [Reporting Services], implementing
ms.assetid: aee1608d-374f-4ad3-bc23-fe07fdaa52b7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: abc5b51acc9c6beef6d3a62b95370f5081d5364d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63181364"
---
# <a name="preparing-to-implement-a-delivery-extension"></a>Preparazione all'implementazione di un'estensione per il recapito
  Prima di implementare l'estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], è necessario definire le interfacce da implementare. È innanzitutto necessario stabilire in che modo verrà utilizzata l'estensione per il recapito, quali impostazioni sono necessarie per l'estensione per il recapito e le funzionalità specifiche da implementare per il recapito delle notifiche dei report.  
  
 Ogni estensione per il recapito di [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] deve fornire le funzionalità seguenti:  
  
-   Un'implementazione dell'interfaccia <xref:Microsoft.ReportingServices.Interfaces.IExtension> che rappresenta l'estensione e un nome di estensione localizzato.  
  
-   Un'implementazione di <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> che crea un'estensione per il recapito che può essere utilizzata per recapitare notifiche dei report agli utenti finali.  
  
-   La possibilità di elaborare dati utente specifici per una sottoscrizione.  
  
 Ogni estensione per il recapito può essere estesa per includere la funzionalità seguente:  
  
-   Un'implementazione del controllo utente [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] che consente agli utenti finali di utilizzare Gestione report per creare sottoscrizioni dei report che utilizzano l'estensione per il recapito.  
  
 Nella tabella seguente sono descritte le interfacce e le classi disponibili per le estensioni per il recapito.  
  
|Interfaccia o classe|Descrizione|  
|------------------------|-----------------|  
|<xref:Microsoft.ReportingServices.Interfaces.IExtension> Interfaccia|Rappresenta un'estensione in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> Interfaccia|Rappresenta un'estensione per il recapito in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|<xref:Microsoft.ReportingServices.Interfaces.IDeliveryReportServerInformation> Interfaccia|Contiene informazioni sul server di report richieste dalle estensioni per il recapito (ad esempio, un elenco delle estensioni per il rendering disponibili).|  
|Classe <xref:Microsoft.ReportingServices.Interfaces.Setting>|Rappresenta un'impostazione per un'estensione.|  
|Classe <xref:Microsoft.ReportingServices.Interfaces.Notification>|Contiene informazioni sulle sottoscrizioni utilizzate dalle estensioni per il recapito dei report.|  
|Classe <xref:Microsoft.ReportingServices.Interfaces.Report>|Rappresenta informazioni e metodi specifici del report che consentono alle estensioni per il recapito di recapitare i report agli utenti.|  
|Classe <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile>|Rappresenta l'output di un'estensione per il rendering. Un oggetto <xref:Microsoft.ReportingServices.Interfaces.RenderedOutputFile> contiene il nome file associato e le informazioni sul tipo richiesti dall'estensione per il recapito per elaborare il flusso restituito dall'estensione per il rendering.|  
|<xref:Microsoft.ReportingServices.Interfaces.ISubscriptionBaseUIUserControl> Interfaccia|Controllo utente che rappresenta il mezzo per il recupero delle informazioni sulla sottoscrizione specifiche dell'estensione dall'utente in Gestione report (ad esempio, un indirizzo di posta elettronica o il percorso di una condivisione file).|  
  
## <a name="see-also"></a>Vedere anche  
 [Estensioni di Reporting Services](../reporting-services-extensions.md)   
 [Implementazione di un'estensione per il recapito](implementing-a-delivery-extension.md)   
 [Libreria di estensioni di Reporting Services](../reporting-services-extension-library.md)  
  
  
