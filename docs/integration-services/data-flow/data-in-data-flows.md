---
title: Dati nei flussi di dati | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- converting data types [Integration Services]
- comparing data
- data types [Integration Services], data flow
- parsing [Integration Services]
- string comparisons
- data flow [Integration Services], data options
ms.assetid: 8a9d6186-eb52-48e3-997e-021f24d458a3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ac04c9b6a8838ba338407533834a7950dabe055d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "71293049"
---
# <a name="data-in-data-flows"></a>Dati nei flussi di dati

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] è disponibile un set di tipi di dati che è possibile usare nei flussi di dati.  
  
## <a name="data-type-conversion"></a>Conversione tipo di dati  
 L'origine aggiunta a un flusso di dati converte i dati di origine nei tipi di dati di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Le trasformazioni successive possono convertire i dati in tipi di dati di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] diversi e, a seconda del tipo di archivio dati in cui vengono caricati i dati, le destinazioni possono convertire il tipo di dati finale di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] nel tipo di dati richiesto dall'archivio dati di destinazione. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
 Per essere convertivi nei tipi di dati di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , i dati vengono analizzati da un componente del flusso di dati. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sono disponibili due tipi di analisi dei dati: analisi veloce e analisi standard. La maggior parte dei componenti dei flussi di dati è in grado di eseguire solo l'analisi standard. L'origine file flat e la trasformazione Conversione dati sono tuttavia in grado di utilizzare sia l'analisi veloce che l'analisi standard. Per altre informazioni, vedere [Analisi dei dati](../../integration-services/data-flow/parsing-data.md).  
  
## <a name="data-type-comparison"></a>Conversione dei tipi di dati  
 Molte trasformazioni confrontano i valori dei dati. La trasformazione Aggregazione, ad esempio, confronta i valori al fine di eseguirne l'aggregazione su un set di righe di dati, la trasformazione Ordinamento confronta i valori allo scopo di ordinarli e la trasformazione Ricerca confronta i valori con quelli contenuti in una tabella di riferimento separata. Per specificare la modalità di confronto delle stringhe, la trasformazione include un set di opzioni di confronto che consentono ad esempio di ignorare la distinzione tra maiuscole e minuscole, gestire i caratteri Katakana e Hiragana nel testo giapponese e ignorare i caratteri spazio nelle stringhe. Per altre informazioni, vedere [Comparing String Data](../../integration-services/data-flow/comparing-string-data.md).  
  
 Anche l'analizzatore di espressioni confronta i valori dei dati durante la valutazione delle espressioni utilizzate da variabili, vincoli di precedenza e trasformazioni.  
  
## <a name="data-flow-troubleshooting"></a>Risoluzione dei problemi del flusso di dati  
 Dopo avere distribuito un pacchetto nel catalogo [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , è possibile analizzare il flusso di dati nel pacchetto durante l'esecuzione per verificarne le prestazioni o per verificare la presenza di altri problemi. Sono disponibili alcuni report standard che consentono di visualizzare lo stato e la cronologia dei pacchetti ed è possibile eseguire una query sulle viste del database per ottenere informazioni dettagliate sull'esecuzione dei pacchetti. È inoltre possibile aggiungere e rimuovere dinamicamente i data tap durante l'esecuzione per individuare specifici componenti del pacchetto. Per altre informazioni, vedere [Debug di un flusso di dati](../../integration-services/troubleshooting/debugging-data-flow.md).  
  
  
