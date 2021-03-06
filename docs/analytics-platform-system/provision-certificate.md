---
title: Provisioning del certificato
description: Provisioning del certificato nel sistema della piattaforma Analytics.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 669e65a7d27b208d861a33618d889707134dfefa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400517"
---
# <a name="certificate-provisioning-in-analytics-platform-system"></a>Provisioning del certificato nel sistema della piattaforma Analytics
La pagina di **provisioning del certificato PDW** del sistema di piattaforma di analisi**Configuration Manager** importa o rimuove il certificato usato da PDW. 

Usando, un certificato per crittografare le connessioni può aiutare a proteggere le comunicazioni con il nodo di controllo tramite SQL Server client, strumenti che usano i driver SQL Server PDW, la [console di amministrazione](monitor-the-appliance-by-using-the-admin-console.md)e i carichi di Integration Services. 
  
## <a name="prerequisites"></a>Prerequisites  
Prima di installare il certificato, eseguire le operazioni seguenti:  
  
1.  Ottenere un certificato protetto. Per ulteriori informazioni su come ottenere un certificato protetto, contattare supporto tecnico Microsoft.  
  
2.  Salvare il certificato nel nodo di controllo in un file PFX protetto da password.  
  
## <a name="for-security-reasons-obtain-a-trusted-certificate"></a>Per motivi di sicurezza, ottenere un certificato attendibile  
SQL Server PDW supporta l'utilizzo di un certificato per crittografare le connessioni al nodo di controllo; incluse le connessioni alla **console di amministrazione**.  
  
Per impostazione predefinita, la **console di amministrazione** include un certificato autofirmato che fornisce privacy, ma non l'autenticazione server. Questo può lasciare le comunicazioni vulnerabili a un attacco man-in-the-Middle. Quando un utente si connette alla console di amministrazione usando il certificato autofirmato, Internet Explorer restituisce l'errore: "si è verificato un problema con il certificato di sicurezza del sito Web".  
  
Sebbene la connessione tramite il certificato autofirmato crittografa i dati in corso tra il client e il server, la connessione è ancora a rischio da utenti malintenzionati.  
  
> [!WARNING]  
> Gli amministratori del dispositivo devono acquisire immediatamente un certificato concatenato a un'autorità di certificazione attendibile riconosciuta dai client, in modo da disporre di una connessione protetta e rimuovere l'errore segnalato da Internet Explorer.  
  
Il percorso di certificazione deve contenere il nome di dominio completo che esegue il mapping all'indirizzo IP del cluster del nodo di controllo (scelta consigliata) o il nome digitato dagli utenti nelle barre degli indirizzi del browser per accedere alla **console di amministrazione**.  
  
Usare il sistema di piattaforma di analisi**Configuration Manager** per aggiungere o rimuovere il certificato attendibile. Lo strumento di configurazione dei certificati dei servizi HTTP di Microsoft Windows (**winHttpCertCfg. exe**) per gestire il certificato non è supportato.  
  
## <a name="import-or-remove-the-certificate"></a>Importare o rimuovere il certificato  
Le istruzioni seguenti illustrano come importare o rimuovere il certificato del dispositivo.  
  
### <a name="to-import-the-certificate"></a>Per importare il certificato  
  
1.  Avviare il **Configuration Manager**.  
Per ulteriori informazioni, vedere [la pagina relativa all'avvio del&#41;di sistema della piattaforma Configuration Manager &#40;Analytics ](launch-the-configuration-manager.md).  

2.  Nel riquadro sinistro del **Configuration Manager**espandere **topologia data warehouse parallela**, quindi fare clic su **certificati**.  
  
3.  Selezionare **Importa un certificato e configurare l'appliance per utilizzarlo**, quindi fare clic su **Sfoglia** per individuare e selezionare il file del certificato.  
  
4.  Immettere la password per il certificato nel campo **password** .  
  
5.  Fare clic su **applica** per configurare il certificato per l'appliance.  
  
SQL Server PDW non effettuerà la crittografia della connessione corrente utilizzando il certificato importato, ma utilizzerà il certificato per le nuove connessioni.  
  
### <a name="to-remove-the-previously-imported-certificate"></a>Per rimuovere il certificato importato in precedenza  
  
1.  Avviare il **Configuration Manager**. 

<!-- MISSING LINKS
For more information, see [Launch the Configuration Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager-analytics-platform-system.md).  
-->
  
2.  Nel riquadro sinistro del **Configuration Manager**espandere **topologia data warehouse parallela**, quindi fare clic su **certificati**.  
  
3.  Selezionare Rimuovi i certificati di cui è stato effettuato **il provisioning nell'appliance**.  
  
4.  Fare clic su **applica** per rimuovere il certificato importato in precedenza dal dispositivo.  
  
SQL Server PDW continuerà a crittografare le connessioni correnti, ma non utilizzerà il certificato rimosso per le nuove connessioni.  
  
![Certificato PDW strumento DWConfig](media/dwconfig-appl-pdw-cert.png "Certificato PDW Appliance DWConfig")  
  
## <a name="see-also"></a>Vedere anche  
[Avviare la piattaforma Configuration Manager &#40;Analytics System&#41;](launch-the-configuration-manager.md)  
