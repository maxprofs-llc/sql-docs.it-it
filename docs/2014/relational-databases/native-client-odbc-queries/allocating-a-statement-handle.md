---
title: Allocazione di un handle di istruzione | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- statements [ODBC], statement handles
- ODBC applications, executing queries
- SQLGetStmtAttr function
- SQL Server Native Client ODBC driver, statements
- allocating statement handles
- ODBC applications, statements
- statement handles [ODBC]
- SQLAllocHandle function
ms.assetid: 9ee207f3-2667-45f5-87ca-e6efa1fd7a5c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68e3d7a53f96216d158ddbdb1d1d0ca59db5f81f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63200259"
---
# <a name="allocating-a-statement-handle"></a>Allocazione di un handle di istruzione
  Prima che un'applicazione possa eseguire un'istruzione, deve allocare un handle di istruzione. Questa operazione viene eseguita chiamando **SQLAllocHandle** con il parametro *HandleType* impostato su SQL_HANDLE_STMT e *InputHandle puntare* che punta a un handle di connessione.  
  
 Gli attributi di istruzione sono caratteristiche dell'handle di istruzione. Attributi di istruzione di esempio possono includere l'utilizzo di segnalibri e il tipo di cursore da utilizzare con il set di risultati dell'istruzione. Gli attributi dell'istruzione sono impostati con [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)e le impostazioni correnti vengono recuperate tramite [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md). Non vi è alcun requisito che stabilisce che un'applicazione debba impostare tutti gli attributi di istruzione. Per tutti gli attributi di istruzione sono disponibili valori predefiniti, alcuni dei quali specifici del driver.  
  
 Prestare particolare attenzione nell'utilizzare molte delle opzioni di istruzione e connessione ODBC. La chiamata a [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) con *fOption* impostato su SQL_ATTR_LOGIN_TIMEOUT controlla il tempo di attesa di un'applicazione per il timeout di una connessione durante l'attesa del tentativo di stabilire una connessione (0 specifica un'attesa infinita). Per i siti con tempi di risposta prolungati è possibile impostare un valore elevato per garantire che le connessioni dispongano di tempo sufficiente per il completamento. L'intervallo, tuttavia, deve essere sempre sufficientemente ridotto per consentire all'utente di ricevere una risposta entro un periodo di tempo ragionevole se il driver non è in grado di connettersi.  
  
 La chiamata di **SQLSetStmtAttr** con *fOption* impostato su SQL_ATTR_QUERY_TIMEOUT imposta un intervallo di timeout della query per proteggere il server e l'utente da query con esecuzione prolungata.  
  
 La chiamata di **SQLSetStmtAttr** con *fOption* impostato su SQL_ATTR_MAX_LENGTH limita la quantità di dati di **testo** e di **immagine** che una singola istruzione può recuperare. La chiamata a **SQLSetStmtAttr** con *fOption* impostato su SQL_ATTR_MAX_ROWS limita anche un set di righe alle prime *n* righe, se è necessario per tutte le applicazioni. Si noti che impostando SQL_ATTR_MAX_ROWS, il driver esegue un'istruzione SET ROWCOUNT nel server. Questa operazione ha [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] effetto su tutte le istruzioni, inclusi i trigger e gli aggiornamenti.  
  
 Utilizzare particolare attenzione quando si impostano queste opzioni. È preferibile che tutti gli handle di istruzione in un handle di connessione specifichino le stesse impostazioni per SQL_ATTR_MAX_LENGTH e SQL_ATTR_MAX_ROWS. Se il driver passa da un handle di istruzione a un altro con valori diversi per queste opzioni, il driver deve generare le istruzioni SET TEXTSIZE e SET ROWCOUNT appropriate per modificare le impostazioni. Il driver non può inserire queste istruzioni nello stesso batch dell'istruzione SQL dell'utente perché l'istruzione SQL dell'utente può contenere un'istruzione che deve essere la prima in un batch. Il driver deve inviare le istruzioni SET TEXTSIZE e SET ROWCOUNT in un batch distinto, che genera automaticamente un round trip aggiuntivo al server.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di query &#40;ODBC&#41;](executing-queries-odbc.md)  
  
  
