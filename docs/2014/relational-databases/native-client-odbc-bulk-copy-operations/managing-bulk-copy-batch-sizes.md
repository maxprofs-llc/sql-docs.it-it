---
title: Gestione delle dimensioni dei batch per la copia bulk | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07f87bf0f231419e4f1345369211ba6ceebf1d12
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63199179"
---
# <a name="managing-bulk-copy-batch-sizes"></a>Gestione delle dimensioni dei batch di copia bulk
  Lo scopo principale di un batch nelle operazioni di copia bulk è definire l'ambito di una transazione. Se non si impostano le dimensioni del batch, le funzioni di copia bulk considerano un'intera copia bulk come una transazione. Se le dimensioni del batch vengono impostate, ogni batch rappresenterà una transazione di cui verrà eseguito il commit alla fine dell'esecuzione.  
  
 Se una copia bulk viene eseguita senza specificare le dimensioni del batch e si verifica un errore, viene eseguito il rollback dell'intera copia bulk. Il recupero di una copia bulk con esecuzione prolungata può richiedere molto tempo. Quando vengono impostate le dimensioni di un batch, la copia bulk considera ogni batch come una singola transazione e ne esegue il commit. Se si verifica un errore, è necessario eseguire il rollback solo dell'ultimo batch in attesa.  
  
 Le dimensioni del batch possono influire anche sull'overhead dei blocchi. Quando si esegue una copia bulk [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in, è possibile specificare l'hint TABLOCK usando [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) per acquisire un blocco di tabella anziché i blocchi di riga. Il singolo blocco di tabella può essere gestito con un overhead minimo per un'operazione di copia bulk intera. Se TABLOCK non viene specificato, i blocchi vengono gestiti su righe singole e l'overhead della gestione di tutti i blocchi per la durata della copia bulk può rallentare le prestazioni. Poiché i blocchi vengono gestiti solo per la durata di una transazione, la specifica delle dimensioni del batch risolve il problema grazie alla generazione periodica di un commit che libera i blocchi attualmente gestiti.  
  
 Il numero di righe che costituiscono un batch può avere effetti significativi sulle prestazioni quando si esegue la copia bulk di un gran numero di righe. I requisiti per le dimensioni del batch dipendono dal tipo di copia bulk eseguita.  
  
-   Quando si esegue la copia bulk in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], specificare l'hint di copia bulk TABLOCK e impostare le dimensioni del batch su un valore grande.  
  
-   Quando TABLOCK non viene specificato, impostare le dimensioni del batch su un valore che non superi 1.000 righe.  
  
 Quando si esegue la copia bulk da un file di dati, le dimensioni del batch vengono specificate chiamando **bcp_control** con l'opzione BCPBATCH prima di chiamare [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md). Quando si esegue la copia bulk da variabili di programma usando [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) e [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md), le dimensioni del batch vengono controllate chiamando [bcp_batch](../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) dopo aver chiamato [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x* volte, dove *x* è il numero di righe in un batch.  
  
 Oltre a specificare le dimensioni di una transazione, i batch influiscono anche sull'invio in rete delle righe al server. Le funzioni di copia bulk normalmente memorizzano nella cache le righe da **bcp_sendrow** fino a quando non viene compilato un pacchetto di rete e quindi inviano il pacchetto completo al server. Quando un'applicazione chiama **bcp_batch**, tuttavia, il pacchetto corrente viene inviato al server, indipendentemente dal fatto che sia stato compilato. L'utilizzo di dimensioni del batch molto ridotte può rallentare le prestazioni se determina l'invio al server di più pacchetti riempiti parzialmente. Ad esempio, la chiamata di **bcp_batch** dopo ogni **bcp_sendrow** causa l'invio di ogni riga in un pacchetto separato e, a meno che le righe non siano di dimensioni molto elevate, spreca spazio in ogni pacchetto. Le dimensioni predefinite dei pacchetti di rete per SQL Server sono pari a 4 KB, sebbene un'applicazione possa modificare le dimensioni chiamando [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) specificando l'attributo SQL_ATTR_PACKET_SIZE.  
  
 Un altro effetto collaterale dei batch è che ogni batch viene considerato un set di risultati in attesa finché non viene completato con **bcp_batch**. Se si tenta di eseguire altre operazioni su un handle di connessione mentre un batch è in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] attesa, il driver ODBC di Native Client genera un errore con SQLSTATE = "HY000" e una stringa del messaggio di errore:  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di operazioni di copia bulk &#40;ODBC&#41;](performing-bulk-copy-operations-odbc.md)   
 [Informazioni sull'importazione ed esportazione bulk di dati &#40;SQL Server&#41;](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
