---
title: 'Lezione 3: installazione dei pacchetti | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 87bc4d82-39d8-424f-886f-98cf1e4bb07a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b15b19bfc7f04c96bb955207c6631706380063fd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057865"
---
# <a name="lesson-3-installing-packages"></a>Lezione 3: Installazione dei pacchetti
  Nella [lezione 2: creazione del pacchetto di distribuzione](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)è stata compilata un'utilità di distribuzione e è stato creato il pacchetto di distribuzione che contiene gli elementi necessari per installare i pacchetti in un altro computer. È stato inoltre verificato l'elenco dei file inclusi nel pacchetto di distribuzione ed è stato esaminato il contenuto del file manifesto creato contestualmente all'utilità di distribuzione.  
  
 In questa lezione si procederà alla copia del pacchetto di distribuzione nel computer di destinazione e quindi all'esecuzione dell'Installazione guidata pacchetti per installare i pacchetti, le rispettive dipendenze e i file ausiliari nel computer. I pacchetti verranno installati nel database **msdb** di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e gli altri elementi nel file system. Dopo aver completato l'installazione dei pacchetti, questi ultimi verranno eseguiti in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] mediante l'Utilità di esecuzione pacchetti allo scopo di testare la distribuzione.  
  
 **Tempo stimato per il completamento della lezione:** 30 minuti  
  
## <a name="lesson-tasks"></a>Argomenti della lezione  
 In questa lezione sono incluse le attività seguenti:  
  
-   [Passaggio 1: Copia del pacchetto di distribuzione](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
-   [Passaggio 2: Esecuzione dell'Installazione guidata pacchetti](../integration-services/lesson-3-2-running-the-package-installation-wizard.md)  
  
-   [Passaggio 3: Test dei pacchetti distribuiti](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
## <a name="start-the-lesson"></a>Inizio della lezione  
 [Passaggio 1: Copia del pacchetto di distribuzione](../integration-services/lesson-3-1-copying-the-deployment-bundle.md)  
  
![Integration Services icona (piccola)](media/dts-16.gif "Icona di Integration Services (piccola)")  **rimane aggiornata con Integration Services**<br /> Per i download, gli articoli, gli esempi e i video Microsoft più recenti, oltre alle soluzioni selezionate dalla community, visitare la pagina [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sul sito MSDN:<br /><br /> [Visita la pagina Integration Services su MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Per ricevere una notifica automatica su questi aggiornamenti, sottoscrivere i feed RSS disponibili nella pagina.  
  
  
