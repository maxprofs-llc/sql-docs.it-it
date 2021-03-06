---
title: Applicazioni generiche | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6b1544f5562468db03a649c263993039a722a3c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139301"
---
# <a name="generic-applications"></a>Applicazioni generiche
Le applicazioni generiche a volte eseguono un'attività hardcoded, ad esempio un foglio di calcolo che recupera i dati da un database. Potrebbero inoltre eseguire un'ampia gamma di attività definite dall'utente, ad esempio un'applicazione di query generica che consente all'utente di immettere ed eseguire un'istruzione SQL. Per quanto riguarda le applicazioni generiche, è necessario che funzionino con un'ampia gamma di sistemi DBMS diversi e che lo sviluppatore non conosca in anticipo quali saranno i DBMS.  
  
 Pertanto, le applicazioni generiche devono essere altamente interoperative. Lo sviluppatore deve effettuare molte scelte, effettuare il trading di interoperabilità per le funzionalità e deve scrivere codice che prevede che i driver supportino una vasta gamma di funzionalità. Sebbene sia possibile ottimizzare le applicazioni generiche in modo che funzionino con DBMS diffusi, raramente contengono codice specifico del driver o DBMS.
