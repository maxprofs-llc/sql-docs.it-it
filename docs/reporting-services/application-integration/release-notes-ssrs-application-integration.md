---
title: Note sulla versione per i controlli Visualizzatore report
description: Note sulla versione per i controlli Visualizzatore report di WebForms e WinForms, correlati a Reporting Services.
ms.date: 01/16/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.custom: seo-lt-2019
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
ms.reviewer: maggies
author: RhysSchmidtke
ms.author: rhys
ms.openlocfilehash: 5ee9bd80519e9dc9d75bb78a98b548b2a60ef247
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "76259379"
---
# <a name="release-notes-for-report-viewer-controls-for-webforms-and-winforms-of-ssrs"></a>Note sulla versione per i controlli Visualizzatore report per WebForms e WinForms di SSRS

Questo articolo presenta le note sulla versione per i controlli Visualizzatore report di WebForms e WinForms, correlati a [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (SSRS).

Per le note sulla versione per SSRS, vedere [Note sulla versione per SQL Server Reporting Services (SSRS) 2017 e versioni successive](../release-notes-reporting-services.md).

## <a name="15014000"></a>150.1400.0
| Descrizione modifica: | Dettagli |
| :----------------- | :------ |
| Correzioni di bug | È stato risolto un problema per cui il controllo del visualizzatore non veniva caricato in modalità progettazione. |
| &nbsp; | &nbsp; |

## <a name="15013580"></a>150.1358.0
| Descrizione modifica: | Dettagli |
| :----------------- | :------ |
| Correzioni di bug | È stata annullata una modifica che aveva rimosso gli assembly Microsoft.ReportViewer.Design dai riferimenti del progetto. |
|           | Nell'ambito di altre modifiche, due assembly erano stati modificati dalla versione 15.0 alla versione 15.3. Questa modifica è stata annullata |
| &nbsp; | &nbsp; |

## <a name="15013570"></a>150.1357.0
| Descrizione modifica: | Dettagli |
| :----------------- | :------ |
| Correzioni di bug  | Anteprima di stampa corretta per i monitor con valori DPI alti |
|            | La finestra di dialogo stampa veniva visualizzata al di fuori dello spazio visibile |
|            | Con un numero elevato di parametri, le barre di scorrimento e gli elenchi a discesa dei parametri non funzionavano correttamente |
|            | È stato risolto il problema relativo ai parametri Null e datetime |
|            | Aggiornamento di JQuery alla versione 3.3.1 |
|            | È stata risolta la sovrapposizione con le celle delle Tablix nel rendering HTML |
|            | Sono stati rimossi i riferimenti al progetto in fase di progettazione per evitare l'aggiunta di assembly di Visual Studio non corretti ai progetti |
|            | Correzione dell'accessibilità per la barra degli strumenti in modo che visualizzi una descrizione solo per gli elementi attivi |
| &nbsp; | &nbsp; |

## <a name="150900148"></a>150.900.148

| Descrizione modifica: | Dettagli |
| :----------------- | :------ |
| Correzione di un bug che impedisce il caricamento dei report senza parametri mediante **Server.LoadReportDefinition**. | &nbsp; |
| Controllo Visualizzatore report WebForms. | Supporta l'incorporamento nelle pagine da destra a sinistra (pagine che cambiano il flusso del testo usando la proprietà CSS *direction: rtl;* ).<br/><br/>Supporta la personalizzazione del testo della finestra di dialogo Stampa tramite l'interfaccia di localizzazione *IReportViewerMessages5*.<br/><br/>Migliorato il supporto dell'accessibilità.<br/><br/>&bull; &nbsp; &nbsp; [Pacchetto NuGet per il controllo di WebForms da parte del Visualizzatore report](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Webforms/150.900.148) |
| Controllo Visualizzatore report WinForms. | Correzione della stampa quando un'app è in esecuzione in una modalità con valori DPI alti.<br/><br/>&bull; &nbsp; &nbsp; [Pacchetto NuGet per il controllo di WinForms da parte del Visualizzatore report](https://www.nuget.org/packages/Microsoft.ReportingServices.ReportViewerControl.Winforms/150.900.148) |
| &nbsp; | &nbsp; |

## <a name="next-steps"></a>Passaggi successivi

[Guida introduttiva](integrating-reporting-services-using-reportviewer-controls-get-started.md) ai controlli Visualizzatore report.

Altre domande? [Visitare il forum su Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
