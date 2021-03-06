---
title: Rimozione di SSMA per i componenti Oracle (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 0434f88c46d14672c84f5f7939488a827b229e27
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266556"
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Rimozione di SSMA per i componenti Oracle (OracleToSQL)
Al termine della migrazione dei database da Oracle a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], potrebbe essere necessario disinstallare i componenti di SSMA. È possibile disinstallare i componenti client in qualsiasi momento. Tuttavia, non è consigliabile disinstallare il pacchetto di estensione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] da a meno che i database migrati non usino più funzioni nello schema **ssma_oracle** del database **sysdb** .  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>Disinstallazione di SSMA per il client Oracle  
È possibile disinstallare SSMA utilizzando **Installazione applicazioni**.  
  
**Per disinstallare SSMA**  
  
1.  Nel Pannello di controllo aprire **Installazione applicazioni**.  
  
2.  ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] Selezionare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant per Oracle**e quindi fare clic su **Rimuovi**.  
  
3.  Per confermare che si vuole disinstallare SSMA, fare clic su **Sì**.  
  
## <a name="uninstalling-the-extension-pack"></a>Disinstallazione del pacchetto di estensione  
Se si è certi che i database migrati non utilizzino oggetti nello schema **sysdb. ssma_oracle** , è possibile rimuovere il pacchetto di estensione utilizzando **Installazione applicazioni**.  
  
**Per disinstallare il pacchetto di estensione**  
  
1.  Nel Pannello di controllo aprire **Installazione applicazioni**.  
  
2.  Selezionare **Microsoft SQL Server Migration Assistant per Oracle Extension Pack**, quindi fare clic su **Rimuovi**.  
  
3.  Per confermare che si vuole disinstallare il pacchetto di estensione, fare clic su **Sì**.  
  
4.  Nella pagina istanze con script database utilità selezionare un'istanza e quindi fare clic su **Avanti**.  
  
5.  Nella pagina parametri connessione selezionare il metodo di autenticazione e quindi fare clic su **Avanti**.  
  
    L'autenticazione di Windows utilizzerà le credenziali di Windows per tentare di accedere all'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]di. Se si seleziona [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l'autenticazione di, è necessario [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] immettere un nome di account di accesso e una password.  
  
6.  Nella pagina operazione completata fare clic su **OK**.  
  
7.  Nella pagina fine fare clic su **Esci**.  
  
Dopo la disinstallazione, è possibile verificare che gli oggetti nello schema **sysdb. ssma_oracle** e possibilmente nell'intero database **sysdb** siano stati rimossi tramite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Tuttavia, se si usano altri prodotti SSMA, viene usato anche il database **sysdb** . Se il database esiste e si è certi che nessun altro database faccia riferimento a oggetti in questo database, è possibile scollegare il database.  
  
## <a name="see-also"></a>Vedere anche  
[Installazione di SSMA per il client Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Installazione dei componenti di SSMA in SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
