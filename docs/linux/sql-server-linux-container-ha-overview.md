---
title: Disponibilità elevata per i contenitori di SQL Server
description: Questo articolo illustra la disponibilità elevata per i contenitori di SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-2017||>=sql-server-linux-2017||=sqlallproducts-allversions'
ms.openlocfilehash: 688db496825af348183e195bfd4003cfcfb53d81
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "69653382"
---
# <a name="high-availability-for-sql-server-containers"></a>Disponibilità elevata per i contenitori di SQL Server

Creare e gestire le istanze di SQL Server in modo nativo in Kubernetes.

Distribuire SQL Server in contenitori Docker gestiti da [Kubernetes](https://kubernetes.io/). In Kubernetes un contenitore con un'istanza di SQL Server può essere ripristinato automaticamente in caso di errore di un nodo del cluster.

SQL Server 2017 introduce un'immagine Docker che può essere distribuita in Kubernetes. È possibile configurare l'immagine con una richiesta di volume persistente Kubernetes. Kubernetes monitora il processo di SQL Server nel contenitore. In caso di problemi di un processo, un pod, un contenitore o un nodo, Kubernetes esegue automaticamente il bootstrap di un'altra istanza ed esegue la riconnessione alla risorsa di archiviazione.

## <a name="container-with-sql-server-instance-on-kubernetes"></a>Contenitore con un'istanza di SQL Server in Kubernetes

Kubernetes 1.6 e versioni successive supportano le [*classi di archiviazione*](https://kubernetes.io/docs/concepts/storage/storage-classes/), le [*richieste di volumi persistenti*](https://kubernetes.io/docs/concepts/storage/storage-classes/#persistentvolumeclaims) e il [*tipo di volume del disco di Azure*](https://github.com/kubernetes/examples/tree/master/staging/volumes/azure_disk). 

In questa configurazione Kubernetes svolge il ruolo di agente di orchestrazione del contenitore. 

![Diagramma del cluster SQL Server in Kubernetes](media/tutorial-sql-server-containers-kubernetes/kubernetes-sql.png)

Nel diagramma precedente `mssql-server` è un'istanza di SQL Server (contenitore) in un [*pod*](https://kubernetes.io/docs/concepts/workloads/pods/pod/). Un [set di repliche](https://kubernetes.io/docs/concepts/workloads/controllers/replicaset/) garantisce che il pod venga automaticamente ripristinato dopo un errore del nodo. Le applicazioni si connettono al servizio. In questo caso, il servizio rappresenta un servizio di bilanciamento del carico che ospita un indirizzo IP che rimane invariato dopo l'errore di `mssql-server`.

Kubernetes orchestra le risorse nel cluster. Quando si verifica un errore in un nodo che ospita un contenitore con un'istanza di SQL Server, viene eseguito il bootstrap di un nuovo contenitore con un'istanza di SQL Server e viene collegato alla stessa risorsa di archiviazione permanente.

SQL Server 2017 e versioni successive supportano i contenitori in Kubernetes.

Per creare un contenitore in Kubernetes, vedere [Distribuire un contenitore SQL Server in Kubernetes](tutorial-sql-server-containers-kubernetes.md)

## <a name="next-steps"></a>Passaggi successivi

Per distribuire contenitori di SQL Server nel servizio Azure Kubernetes, vedere gli esempi seguenti:
* [Distribuire SQL Server in un contenitore Docker](sql-server-linux-configure-docker.md)
* [Distribuire un contenitore di SQL Server in Kubernetes](tutorial-sql-server-containers-kubernetes.md)
