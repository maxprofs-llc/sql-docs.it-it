---
title: Attività di eliminazione cluster di Azure HDInsight | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpdelcltask.f1
- sql14.dts.designer.afpdelcltask.f1
ms.assetid: e298776e-d18a-4393-a8e6-65ee3d555749
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a82b5abf846bb9904d6ea8db879ff73e98f43a8c
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "71298413"
---
# <a name="azure-hdinsight-delete-cluster-task"></a>Attività di eliminazione cluster di Azure HDInsight

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


L'**attività di eliminazione cluster di Azure HDInsight** consente a un pacchetto di SSIS di eliminare un cluster Azure HDInsight nel gruppo di risorse e nella sottoscrizione di Azure specificati.
  
L'**attività di eliminazione cluster di Azure HDInsight** è un componente del[ Feature Pack di SQL Server Integration Services (SSIS) per Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).
  
> [!NOTE]
> L'eliminazione di un cluster HDInsight può richiedere da 10 a 20 minuti circa.  
  
Per aggiungere un' **attività di eliminazione cluster di Azure HDInsight**, trascinare l'attività in Progettazione SSIS e farvi doppio clic oppure clic con il pulsante destro del mouse, quindi scegliere **Modifica** per visualizzare la finestra di dialogo seguente relativa all' **editor dell'attività di eliminazione cluster di Azure HDInsight** .  
  
La tabella seguente fornisce una descrizione dei campi della finestra di dialogo.  
  
|||  
|-|-|  
|**Campo**|**Descrizione**|  
|AzureResourceManagerConnection|Selezionare un'istanza di Gestione connessioni esistente per Azure Resource Manager oppure creare una nuova istanza che verrà usata per eliminare il cluster HDInsight.|
|SubscriptionId|Specificare l'ID della sottoscrizione del cluster HDInsight.|
|ResourceGroup|Specificare il gruppo di risorse di Azure in cui si trova il cluster HDInsight.|
|ClusterName|Consente di specificare il nome del cluster da eliminare.|  
|FailIfNotExists|Consente di indicare se l'attività deve avere esito negativo se il cluster non esiste.|
