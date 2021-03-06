---
title: Installare versioni in lingua non inglese
description: Installare versioni in lingua non inglese di SQL Server Management Studio (SSMS)
ms.prod: sql
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 04/25/2019
ms.openlocfilehash: cc4d98322f0422053402bdf097674c90807e11a1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "75246879"
---
# <a name="install-non-english-language-versions-of-sql-server-management-studio-ssms"></a>Installare versioni in lingua non inglese di SQL Server Management Studio (SSMS)

SSMS è disponibile in varie lingue, ma il programma di installazione di SSMS blocca l'installazione nei computer in cui le impostazioni locali del sistema non corrispondono alla lingua di SSMS.

> [!NOTE]
> Questo articolo si applica a SSMS 17.x. Per SSMS 18.x il blocco dell'installazione per lingue diverse è stato rimosso ed è ora possibile, ad esempio, installare la versione in lingua tedesca o francese di SSMS per Windows. Se la lingua del sistema operativo non corrisponde a quella di SSMS, impostare la lingua desiderata in **Strumenti** > **Opzioni** > **Impostazioni internazionali**, altrimenti SSM visualizzerà l'interfaccia utente in inglese.

Le indicazioni seguenti variano a seconda della versione di Windows disponibile. Le istruzioni seguenti sono riferite a Windows 10.

## <a name="install-non-english-ssms-on-a-computer-running-an-english-operating-system-os"></a>Installare una versione di SSMS in una lingua diversa dall'inglese in un computer che esegue un sistema operativo inglese

1. Installare il Language Pack di Windows per la lingua da usare per SSMS:
   - **Impostazioni** > **Data/ora e lingua** > **Area geografica e lingua** > **Aggiungi una lingua**
2. Specificare ora le impostazioni locali del sistema per usare il Language Pack installato nel passaggio precedente facendo clic sulla lingua appena installata, quindi selezionare**Imposta come predefinito**. (Dopo aver installato SSMS, è possibile reimpostare le impostazioni locali del sistema sull'inglese.)
3. Quando il sistema operativo è in esecuzione nella lingua desiderata, installare la versione di SSMS nella lingua desiderata. Per la prima installazione di una lingua nuova di SSMS, usare il pacchetto completo. È possibile usare il pacchetto di aggiornamento per le installazioni successive.
4. Eseguire SSMS. Dovrebbe essere visualizzato nella lingua installata nel passaggio precedente.
5. Reimpostare l'inglese per le impostazioni locali di sistema del computer.

## <a name="install-ssms-in-a-language-other-than-the-language-of-the-installed-os"></a>Installare SSMS in una lingua diversa da quella del sistema operativo installato

1. Installare il Language Pack di Windows per la lingua da usare per SSMS:
   - **Impostazioni** > **Data/ora e lingua** > **Area geografica e lingua** > **Aggiungi una lingua**
2. Specificare ora le impostazioni locali del sistema per usare il Language Pack installato nel passaggio precedente facendo clic sulla lingua appena installata, quindi selezionare**Imposta come predefinito**.
3. Quando il sistema operativo è in esecuzione nella lingua desiderata, installare la versione di SSMS nella lingua desiderata. Per la prima installazione di una lingua nuova di SSMS, usare il pacchetto completo. È possibile usare il pacchetto di aggiornamento per le installazioni successive.
4. Per ogni lingua da installare che non corrisponde alla lingua della prima versione di SSMS installata, installare la versione corrispondente di Visual Studio 2015 Shell (Isolated) Language Pack:
   - Passare a [https://connect.microsoft.com/VisualStudio/ExtendVS](https://connect.microsoft.com/VisualStudio/ExtendVS) (potrebbe essere necessario eseguire l'accesso e completare il processo di *registrazione a Connect*).
   - Scaricare il Visual Studio 2015 Shell (Isolated) Language Pack desiderato e installarlo.

   > [!IMPORTANT]
   > Usare la procedura precedente per installare Visual Studio 2015 Shell (Isolated) Language Pack e non usare il collegamento **Lingue aggiuntive** in **Strumenti** | **Opzioni** | **Impostazioni internazionali**.

5. Eseguire SSMS e selezionare la lingua che si vuole usare in:
   - **Strumenti** | **Opzioni** | **Impostazioni internazionali**
6. Chiudere e riavviare SSMS.

## <a name="next-steps"></a>Passaggi successivi

- [Esercitazione su SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/tutorials/tutorial-sql-server-management-studio)
