---
title: Riduzione dell'utilizzo dello spazio per i file di log | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- log file space in RDS [ADO]
ms.assetid: 669662a0-e20f-483e-ab28-53f66c524c98
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c8dc0799fbeba24ad4725d25647ef471edad8fb7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922551"
---
# <a name="minimizing-log-file-space-usage"></a>Riduzione al minimo dell'utilizzo dello spazio per il file di log
Un file di log può essere riempito rapidamente (arrestando così il server) se è presente un volume elevato di attività in un database SQL Server. È possibile impostare il file di log in modo da **troncare il Checkpoint** per estendere significativamente la durata del file di log per un database.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-65"></a>Per abilitare il troncamento in checkpoint in Microsoft SQL Server 6,5  
  
1.  Avviare Microsoft SQL Server Enterprise Manager, aprire l'albero per il server, quindi aprire l'albero dispositivi di database.  
  
2.  Fare doppio clic sul nome del database in cui verrà abilitata la funzionalità.  
  
3.  Nella scheda **database** selezionare **Tronca**.  
  
4.  Nella scheda **Opzioni** selezionare **Tronca log in Checkpoint**, quindi fare clic su **OK**.  
  
### <a name="to-enable-truncate-on-checkpoint-in-microsoft-sql-server-70"></a>Per abilitare il troncamento in checkpoint in Microsoft SQL Server 7,0  
  
1.  Avviare Microsoft SQL Server Enterprise Manager, aprire l'albero per il server, quindi aprire l'albero database.  
  
2.  Fare clic con il pulsante destro del mouse sul nome del database in cui verrà abilitata questa funzionalità e scegliere **Proprietà**.  
  
3.  Nella scheda **Opzioni** selezionare **Tronca log in Checkpoint**, quindi fare clic su **OK**.  
  
 Per ulteriori informazioni sulla funzionalità **troncamento in Checkpoint** , vedere la documentazione di Microsoft SQL Server.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali su RDS](../../../ado/guide/remote-data-service/rds-fundamentals.md)


