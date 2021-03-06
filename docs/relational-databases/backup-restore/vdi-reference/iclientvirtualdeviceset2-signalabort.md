---
title: IClientVirtualDeviceSet2::SignalAbort
titlesuffix: SQL Server VDI reference
description: Questo articolo include informazioni di riferimento sul comando IClientVirtualDeviceSet2::SignalAbort.
ms.date: 08/30/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.technology: backup-restore
ms.topic: reference
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0a0d53421f0928b1ebf0ba557afbd29dd8680993
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "70847542"
---
# <a name="iclientvirtualdeviceset2signalabort-vdi"></a>IClientVirtualDeviceSet2::SignalAbort (VDI)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

La funzione **SignalAbort** viene usata per segnalare che dovrebbe verificarsi una terminazione anomala.

## <a name="syntax"></a>Sintassi

```c
HRESULT IClientVirtualDeviceSet2::SignalAbort ();
```

## <a name="return-value"></a>Valore restituito

Restituisce un *HRESULT* che indica l'esito positivo o negativo della chiamata al metodo. Il valore NOERROR indica l'esito positivo della chiamata del metodo. Un valore diverso da zero indica che si è verificato un errore.

## <a name="remarks"></a>Osservazioni

In qualsiasi momento il client può scegliere di interrompere l'operazione di backup o ripristino. Questa routine segnala che tutte le operazioni devono essere interrotte. L'intero set di dispositivi virtuali entra nello stato di interruzione. Nessun altro comando viene restituito su nessun dispositivo. Tutti i comandi non completati vengono completati automaticamente, restituendo ERROR_OPERATION_ABORTED come codice di completamento. Il client deve chiamare IClientVirtualDeviceSet2::Close dopo aver terminato in modo sicuro qualsiasi uso in corso dei buffer forniti al client. Per altre informazioni, vedere Terminazione anomala.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni, vedere [Informazioni di riferimento sull'interfaccia dispositivo virtuale di SQL Server](reference-virtual-device-interface.md).