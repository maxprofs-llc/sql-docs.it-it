---
title: Tipi di cursori scorrevoli | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: dbd32576-0453-4e90-ae45-1a81cee8259d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 210b66a800670f033508f903b18778f88ddd4c8b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061633"
---
# <a name="scrollable-cursor-types"></a>Tipi di cursore scorrevoli
I quattro tipi di cursori scorrevoli sono statici, dinamici, gestiti da keyset e misti. I cursori statici rilevano poche o nessuna modifica, ma sono relativamente convenienti da implementare. I cursori dinamici rilevano tutte le modifiche ma sono costose da implementare. I cursori gestiti da keyset e i cursori misti si trovano tra, rilevando la maggior parte delle modifiche ma a meno spese rispetto ai cursori dinamici.  
  
 I termini seguenti vengono usati per definire le caratteristiche di ogni tipo di cursore scorrevole:  
  
-   **Aggiornamenti, eliminazioni e inserimenti personalizzati.** Aggiornamenti, eliminazioni e inserimenti eseguiti tramite il cursore, con una chiamata a **SQLBulkOperations** o **SQLSetPos** o con un'istruzione Update o DELETE posizionata.  
  
-   **Altri aggiornamenti, eliminazioni e inserimenti.** Aggiornamenti, eliminazioni e inserimenti non eseguiti dal cursore, inclusi quelli creati da altre operazioni nella stessa transazione, quelli eseguiti attraverso altre transazioni e quelli creati da altre applicazioni.  
  
-   **Appartenenza.** Set di righe nel set di risultati.  
  
-   **Ordine.** Ordine in cui le righe vengono restituite dal cursore.  
  
-   **Valori.** Valori in ogni riga del set di risultati.  
  
 Per informazioni su come aggiornare, eliminare e inserire i dati, vedere [Cenni preliminari sull'aggiornamento dei dati](../../../odbc/reference/develop-app/updating-data-overview.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Cursori statici ODBC](../../../odbc/reference/develop-app/odbc-static-cursors.md)  
  
-   [Cursori dinamici ODBC](../../../odbc/reference/develop-app/odbc-dynamic-cursors.md)  
  
-   [Cursori gestiti da keyset](../../../odbc/reference/develop-app/keyset-driven-cursors.md)  
  
-   [Cursori misti](../../../odbc/reference/develop-app/mixed-cursors.md)
