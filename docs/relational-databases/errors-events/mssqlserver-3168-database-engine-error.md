---
title: MSSQLSERVER_3168 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3168 (Database Engine error)
ms.assetid: 991111d9-1eb3-43e9-9333-a75a775c3200
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 00538607fca244177541b20b96324c421a3746f9
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68039301"
---
# <a name="mssqlserver_3168"></a>MSSQLSERVER_3168
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Dettagli  
  
|||  
|-|-|  
|Nome prodotto|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID evento|3168|  
|Origine evento|MSSQLSERVER|  
|Componente|SQLEngine|  
|Nome simbolico|LDDB_SYSTEMWRONGVER|  
|Testo del messaggio|Impossibile ripristinare il backup del database di sistema nel dispositivo %ls perché è stato creato da una versione del server (%ls) diversa da quella del server in uso (%ls).|  
  
## <a name="explanation"></a>Spiegazione  
Non è possibile ripristinare un backup di un database di sistema (**master**, **model** o **msdb**) in una build del server diversa rispetto alla build in cui il backup è stato originariamente eseguito.  
  
> [!NOTE]  
> L'installazione di un Service Pack o una build di hotfix modifica il numero di build del server. Le build del server sono sempre incrementali.  
  
### <a name="possible-causes"></a>Possibili cause  
Lo schema di database per i database di sistema potrebbe essere stato modificato nelle diverse build del server. Per verificare che una modifica dello schema non causi inconsistenze, l'istruzione RESTORE confronta il numero di build del server nel file di backup con il numero di build del server in cui si tenta di ripristinare il backup. In caso di build diverse, l'istruzione visualizza il messaggio di errore 3168 e l'operazione di ripristino viene terminata in modo anomalo.  
  
Questo problema potrebbe verificarsi ad esempio negli scenari seguenti:  
  
-   Un utente tenta di ripristinare un database di sistema sul server A da un backup eseguito sul server B. I server A e B sono basati su build diverse. Il server A potrebbe ad esempio utilizzare la build della versione originale e il server B potrebbe utilizzare una build del Service Pack 1 (SP1).  
  
-   Un utente tenta di ripristinare un database di sistema da un backup eseguito sullo stesso server. Al momento del backup, tuttavia, sul server era in esecuzione una build diversa. Dall'esecuzione del backup, il server è stato aggiornato.  
  
## <a name="user-action"></a>Azione dell'utente  
Questa situazione influisce sul processo di ripristino, che verrà utilizzato solo come ultima risorsa. Per altre informazioni, vedere "[Non è possibile ripristinare i backup di database di sistema a una build diversa di SQL Server](https://support.microsoft.com/kb/264474)".  
  
## <a name="see-also"></a>Vedere anche  
[Backup e ripristino di database di sistema &#40;SQL Server&#41;](~/relational-databases/backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
