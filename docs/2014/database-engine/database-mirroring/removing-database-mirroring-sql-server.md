---
title: Rimozione di mirroring del database (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], removing
- stopping database mirroring [SQL Server]
- removing database mirroring [SQL Server]
ms.assetid: 40c72091-8f03-4037-8b55-5e95309fe145
caps.latest.revision: 31
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6a1d3bcb83efcd6488ca1e85302aafdc7f7a8b55
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37171352"
---
# <a name="removing-database-mirroring-sql-server"></a>Rimozione di mirroring del database (SQL Server)
  Il proprietario del database può arrestare manualmente una sessione di mirroring del database in qualsiasi momento in uno dei partner.  
  
## <a name="impact-of-removing-mirroring"></a>Impatto della rimozione del mirroring  
 Quando il mirroring viene rimosso, si verificano le situazioni seguenti:  
  
-   La relazione, se presente, tra i partner e tra ogni partner e il server di controllo del mirroring viene interrotta in modo permanente.  
  
     Se al momento dell'interruzione della sessione è in corso la comunicazione tra i partner, la relazione viene immediatamente arrestata in entrambi i computer. Se i partner non stanno comunicando, ovvero il database è in stato DISCONNECTED al momento dell'arresto, la relazione viene immediatamente interrotta nel partner in cui è stato arrestato il mirroring. Quando l'altro partner tenta di riconnettersi, individua che la sessione di mirroring del database è stata terminata.  
  
-   Le informazioni sulla sessione di mirroring vengono eliminate, diversamente da ciò che si verifica nel caso di sospensione di una sessione. Il mirroring viene rimosso sia nel database principale, sia nel database mirror. In **sys.databases** la colonna **mirroring_state** e tutte le altre colonne di mirroring vengono impostate su NULL. Per altre informazioni, vedere [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).  
  
-   Viene mantenuta ogni istanza del server partner con una copia distinta del database.  
  
-   Il database mirror viene lasciato nello stato RESTORING (vedere la colonna **state** di **sys.databases**), poiché è stato creato tramite RESTORE WITH NORECOVERY. A questo punto, è possibile eliminare il database mirror precedente o recuperarlo tramite WITH RECOVERY. Il database recuperato presenterà alcune divergenze rispetto al database principale precedente, in quanto tramite il recupero viene avviato un nuovo fork di recupero.  
  
> [!NOTE]  
>  Per proseguire il mirroring dopo avere arrestato una sessione, è necessario stabilire una nuova sessione di mirroring del database. Se dopo l'arresto del mirroring è stato creato un backup del log, è necessario applicarlo al database mirror prima di riavviare il mirroring.  
  
##  <a name="RelatedTasks"></a> Attività correlate  
 **Per rimuovere il mirroring del database**  
  
-   [Rimuovere il mirroring del database &#40;SQL Server&#41;](database-mirroring-sql-server.md)  
  
 **Per avviare il mirroring del database**  
  
-   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Stabilire una sessione di mirroring del database tramite autenticazione di Windows &#40;Transact-SQL&#41;](database-mirroring-establish-session-windows-authentication.md)  
  

  
## <a name="see-also"></a>Vedere anche  
 [Mirroring del database di ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [Mirroring del database &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Sospensione e ripresa del mirroring del database &#40;SQL Server&#41;](pausing-and-resuming-database-mirroring-sql-server.md)   
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  