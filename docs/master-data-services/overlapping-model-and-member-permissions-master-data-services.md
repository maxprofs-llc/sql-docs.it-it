---
title: Autorizzazioni per modelli e membri sovrapposte
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e12489cc490c5b8ee9f363e329da9a057fac8f3f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73728977"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a>Autorizzazioni per modelli e membri sovrapposte (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Le autorizzazioni assegnate a un membro possono sovrapporsi alle autorizzazioni assegnate a un oggetto modello. Quando si verificano sovrapposizioni, viene applicata l'autorizzazione più restrittiva.  
  
 Se un membro dispone di autorizzazione diversa da quella del relativo oggetto modello corrispondente, si applicano le regole seguenti:  
  
-   **Nega** esegue l'override di tutte le altre autorizzazioni.  
  
-   L'autorizzazione di **amministratore** per il livello del modello esegue l'override di tutte le altre autorizzazioni e viene modificata in tutte le autorizzazioni di accesso (CRUD) sui livelli secondari.  
  
-   Un'autorizzazione di accesso valida interseca le autorizzazioni per membri e attributi.  
  
     Ad esempio, se le autorizzazioni per i membri includono **Create** e **Update**, l'autorizzazione per gli attributi è **Update**. L'autorizzazione valida è **Update**.  
  
 Nell'immagine seguente viene indicato quali autorizzazioni vengono applicate a ogni singolo valore di attributo quando le autorizzazioni per gli attributi sono diverse dalle autorizzazioni per i membri.  
  
 ![mds_conc_security_member_overlap_table](../master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")  
  
## <a name="example-1"></a>Esempio 1  
 ![mds_conc_overlap_model_1](../master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")  
  
 Nella scheda **Modelli** all'entità Product è stata assegnata l'autorizzazione **Aggiorna** . Tutti gli attributi nell'entità ereditano questa autorizzazione.  
  
 Nella scheda **Membri gerarchia** il nodo della sottocategoria Mountain Bikes in una gerarchia derivata dispone dell'autorizzazione **Aggiorna** .  
  
 Risultato: in **Esplora**l'utente dispone dell'autorizzazione **Aggiorna** per tutti i valori di attributo per tutti i membri nel nodo Mountain Bike. Tutti gli altri membri e attributi sono nascosti.  
  
 ![mds_conc_overlap_model_example_1](../master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")  
  
## <a name="example-2"></a>Esempio 2  
 ![mds_conc_overlap_model_2](../master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")  
  
 Nella scheda **Modelli** all'attributo Subcategory è assegnata l'autorizzazione **Aggiorna** .  
  
 Nella scheda **Membri gerarchia** al nodo della sottocategoria Mountain Bikes in una gerarchia derivata è stata assegnata in modo esplicito l'autorizzazione **Lettura** .  
  
 Risultato: in **Esplora**l'utente ha l'autorizzazione **Lettura** per i valori dell'attributo Subcategory per i membri del nodo Mountain Bikes. Tutti gli altri membri e attributi sono nascosti.  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="example-3"></a>Esempio 3  
 ![mds_conc_overlap_model_3](../master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")  
  
 Nella scheda **Modelli** all'attributo Subcategory è stata assegnata l'autorizzazione **Lettura** .  
  
 Nella scheda **Membri gerarchia** alla sottocategoria Mountain Bikes in una gerarchia derivata è stata assegnata in modo esplicito l'autorizzazione **Aggiorna** .  
  
 Risultato: in **Esplora**l'utente ha l'autorizzazione **Lettura** per i valori di attributo. Tutti gli altri membri e attributi sono nascosti.  
  
 ![mds_conc_overlap_model_example_2](../master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità di determinazione delle autorizzazioni &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Autorizzazioni utenti e gruppi sovrapposte &#40;Master Data Services&#41;](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  
