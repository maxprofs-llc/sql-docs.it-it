---
title: MSSQLSERVER_611 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 611 (Database Engine error)
ms.assetid: ac6a213f-5c38-44ad-bc85-a62863786614
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0c61febeb9eba4be69978e1966cbf754f8f1a3ff
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424840"
---
# <a name="mssqlserver611"></a>MSSQLSERVER_611
    
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|SQL Server|  
|ID evento|611|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|VAR_SIZE_TOO_BIG|  
|Testo del messaggio|Impossibile inserire o aggiornare una riga perché le dimensioni di colonna variabili totali, incluso l'overhead, superano il limite di %d byte.|  
  
## <a name="explanation"></a>Spiegazione  
 Le dimensioni di colonna variabili totali sono maggiori del limite consentito dallo schema. L'errore 611 viene restituito quando la colonna variabili supera il limite nel case fisso, se il formato di archiviazione vardecimal è abilitato, o quando le dimensioni della colonna variabili superano il limite consentito in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per un record di dati compresso.  
  
## <a name="user-action"></a>Azione dell'utente  
 Ridurre le dimensioni del record.  
  
  