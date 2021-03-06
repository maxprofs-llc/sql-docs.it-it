---
title: Test di oggetti di database migrati (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: f03ef5e1-66e6-4c84-ada2-252dd5ada82f
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 858c564c965fe7105c86a3087923887097e4ddac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266485"
---
# <a name="testing-migrated-database-objects-oracletosql"></a>Test di oggetti di database migrati (OracleToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant per Oracle tester (SSMA tester) verifica automaticamente la conversione degli oggetti di database e la migrazione dei dati eseguita da SSMA. Al termine di tutti i passaggi della migrazione di SSMA, utilizzare SSMA tester per verificare che gli oggetti convertiti funzionino allo stesso modo e che tutti i dati siano stati trasferiti correttamente.  
  
Con SSMA tester è possibile testare i tipi di oggetti seguenti:  
  
-   Tabelle  
  
-   Stored procedure, incluse le procedure in pacchetto.  
  
-   Funzioni definite dall'utente, incluse le funzioni in pacchetto.  
  
-   Visualizzazioni.  
  
-   Istruzioni autonome.  
  
SSMA tester esegue gli oggetti selezionati per il testing in Oracle e le relative controparti [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]in. In seguito, i risultati vengono confrontati in base ai criteri seguenti:  
  
-   Le modifiche ai dati della tabella sono identiche?  
  
-   I valori dei parametri di output per le procedure e le funzioni sono identici?  
  
-   Le funzioni restituiscono gli stessi risultati?  
  
-   I set di risultati sono identici?  
  
> [!NOTE]  
> Attenzione! Non usare mai SSMA tester nei sistemi di produzione. Durante l'esecuzione del tester, lo schema di origine e i dati vengono modificati. Nel frattempo, il ripristino completo dello stato originale potrebbe non essere possibile per alcuni tipi di codice testato.  
  
## <a name="prerequisites"></a>Prerequisites  
Se si vuole usare SSMA tester, installare SSMA Oracle Extension Pack con l'opzione di **database install tester** attivata.  
  
Per consentire il confronto dei dati della tabella risultante, impostare l'opzione **genera colonna ROWID** su **Sì** prima che venga avviata la conversione dello schema. SSMA consente di aggiungere una colonna ROWID a tutte le tabelle durante l'esecuzione del comando **Convert schema** .  
  
Verificare inoltre quanto segue:  
  
-   Gli strumenti client Oracle sono installati nel computer in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cui viene eseguito.  
  
-   Nell'motore di database è stata abilitata l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integrazione con CLR (Common Language Runtime).  
  
Si noti che la versione corrente di SSMA tester non supporta l'esecuzione parallela da parte di utenti diversi nello stesso server di origine o di destinazione.  
  
## <a name="getting-started"></a>Introduzione  
[Creazione di test case &#40;OracleToSQL&#41;](../../ssma/oracle/creating-test-cases-oracletosql.md)  
  
## <a name="see-also"></a>Vedere anche  
[Installazione dei componenti di SSMA in SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
[Impostazioni progetto &#40;conversione&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)  
  
