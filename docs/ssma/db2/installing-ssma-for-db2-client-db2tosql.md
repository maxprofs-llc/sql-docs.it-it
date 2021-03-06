---
title: Installazione di SSMA per il client DB2 (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 09/07/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 3ae2a470-6afd-4512-b6d1-fcbe6afe88ad
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 1623430eed752db7fa387caf33124082eb318490
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "70774190"
---
# <a name="installing-ssma-for-db2-client-db2tosql"></a>Installazione di SSMA per il client DB2 (DB2ToSQL)

Il client SSMA è costituito dai file di programma che eseguono le attività seguenti:  
  
- Connettersi a un database di DB2.  
  
- Connettersi a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
- Convertire gli oggetti di database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2 in sintassi.  
  
- Caricare gli oggetti in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
- Eseguire la migrazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dei dati a.  
  
In questo argomento vengono forniti i prerequisiti e le istruzioni per l'installazione di SSMA.  
  
## <a name="prerequisites"></a>Prerequisites

SSMA è progettato per funzionare con DB2 in z/OS versione 9,0 e 10,0 o DB2 in LUW versione 9,8 e 10,1 o versioni successive e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 o versioni successive.  
  
Prima di installare SSMA, verificare che il computer soddisfi i requisiti seguenti:  
  
- Windows 7 o versioni successive o Windows Server 2008 o versioni successive.  
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)]Windows Installer 3,1 o versioni successive.  
  
- [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] successiva. La [!INCLUDE[dnprdnshort](../../includes/dnprdnshort_md.md)] versione 4,0 è disponibile sul supporto [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] del prodotto. È anche possibile ottenerlo dal [.NET Framework Developer Center](https://go.microsoft.com/fwlink/?LinkId=48882).  
  
- Provider Microsoft OLEDB per DB2 versione 5 o successiva e connettività ai database DB2 di cui si vuole eseguire la migrazione.  
  
- Accesso a e autorizzazioni sufficienti per il computer che ospita l'istanza di destinazione [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] di o database SQL di Azure in cui si eseguirà la migrazione di dati e oggetti di database. Per ulteriori informazioni, vedere [connessione a SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md).  
  
- 4 GB di RAM consigliata.  
  
## <a name="microsoft-oledb-provider-for-db2"></a>Provider Microsoft OLE DB per DB2  

Per scaricare il provider OLEDB per DB2 versione 6,0, passare a [Microsoft® SQL Server® 2017 Feature Pack](https://www.microsoft.com/download/details.aspx?id=55992).

SSMA è un download Web. Per scaricare la versione più recente, vedere la [pagina di download SQL Server Migration Assistant](https://aka.ms/ssmafordb2).  
  
Dopo aver scaricato la versione più recente, estrarre i file di installazione in modo che sia possibile installare SSMA.  
  
Per installare il client di SSMA:
  
1. Fare doppio clic su SSMA per DB2 *n*. Installare. exe, dove *n* è il numero di Build.  
  
2. Nella pagina di **benvenuto** selezionare **Avanti**.  
  
   Se i prerequisiti non sono installati, verrà visualizzato un messaggio che indica che è necessario prima installare i componenti necessari. Assicurarsi di aver installato tutti i prerequisiti, quindi eseguire di nuovo il programma di installazione.  
  
3. Leggere il contratto di licenza con l'utente finale. Se si accettano le condizioni, selezionare Accetto **i termini del contratto di licenza**e quindi fare clic su **Avanti**.  
  
4. Nella pagina Selezione **tipo di installazione** selezionare **tipico**.  
  
5. Selezionare **Installa**.  
  
> [!IMPORTANT]  
> Disinstallare tutte le versioni precedenti di SSMA per DB2 prima di installare la nuova versione.
  
Il percorso di installazione predefinito è C:\Programmi\Microsoft SQL Server Migration Assistant per DB2.  
  
## <a name="see-also"></a>Vedere anche

[Installazione dei componenti di SSMA in SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
[Migrazione di database DB2 a SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
