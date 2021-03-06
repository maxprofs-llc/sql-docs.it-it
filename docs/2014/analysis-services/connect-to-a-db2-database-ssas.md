---
title: Connettersi a un database DB2 (SSAS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.conndb2db.f1
ms.assetid: eeef3697-a4fd-4263-ba7e-f86afa1f46cc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 50818393a81cf3c6db1b54a0752e6fa098277709
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "66087380"
---
# <a name="connect-to-a-db2-database-ssas"></a>Connettersi a un database di DB2 (SSAS)
  Questa pagina dell' **Importazione guidata tabella** consente di specificare le impostazioni per connettersi a un database di DB2. Per accedere alla procedura guidata da [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dal menu **Modello** selezionare **Importa da origine dati**.  
  
 Per connettersi a un'origine dati, è necessario che nel computer sia installato il provider appropriato.  
  
> [!NOTE]  
>  In caso di selezione di un database in questa pagina, vengono utilizzate le credenziali dell'utente specificate. Tuttavia, l'importazione non verrà completata se l'utente specificato nella pagina Impostazioni di rappresentazione non dispone di privilegi sufficienti per leggere dal database selezionato.  
  
## <a name="uielement-list"></a>Elenco degli elementi di interfaccia  
 **Nome descrittivo connessione**  
 Digitare un nome univoco per questa connessione all'origine dati. Questo campo è obbligatorio.  
  
 **Nome server**  
 Digitare o selezionare l'istanza del server a cui connettersi.  
  
 **Nome utente**  
 Specificare un nome utente per la connessione al database.  
  
 Questo nome utente viene utilizzato quando si crea la stringa di connessione per l'origine dati. Queste credenziali vengono utilizzate anche in caso di visualizzazione in anteprima e filtro dei dati nella finestra Proprietà tabella e nell'Importazione guidata. Non vengono utilizzate per importare o aggiornare dati; in tal caso vengono infatti utilizzate le credenziali di Windows specificate nella pagina Impostazioni di rappresentazione.  
  
 **Password**  
 Specificare una password per la connessione al database.  
  
 **Salva password**  
 Specificare se archiviare la password immessa nella casella **Password** .  
  
 **Nome database**  
 Selezionare un database dall'elenco di database.  
  
 **Raccolta pacchetti**  
 Specificare il nome della raccolta per i pacchetti di DB2. Un provider utilizza i pacchetti per creare istruzioni SQL e chiamare stored procedure.  
  
 **Schema predefinito**  
 Specificare il nome dello schema predefinito per il database selezionato.  
  
 **Funzionalità avanzate**  
 Impostare altre proprietà relative alla connessione tramite la finestra di dialogo **Impostazione delle proprietà avanzate** .  
  
 **Test connessione**  
 Provare a stabilire una connessione all'origine dati utilizzando le impostazioni correnti. Viene visualizzato un messaggio che indica se la connessione è stata stabilita.  
  
  
