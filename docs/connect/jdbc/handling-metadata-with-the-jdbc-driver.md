---
title: Gestione dei metadati con il driver JDBC | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0176e1da9a64e4ed32ba6989496178f5f9741193
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028022"
---
# <a name="handling-metadata-with-the-jdbc-driver"></a>Gestione dei metadati con il driver JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  È possibile usare [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] per gestire metadati in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in molti modi diversi. Il driver JDBC può essere utilizzato per estrarre i metadati del database, un set di risultati o parametri.  
  
 Il driver JDBC offre anche tre classi per il recupero dei metadati da un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), usata per restituire le informazioni sul database attualmente connesso.  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), usata per restituire le informazioni sul set di risultati.  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md), usata per restituire le informazioni sui parametri di istruzioni preparate e disponibili per la chiamata.  
  
 Negli argomenti di questa sezione viene illustrato come usare le tre classi per operare con i metadati in un database di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  I metodi per metadati illustrati in questa sezione sono in genere dispendiosi in termini di prestazioni dell'applicazione e si consiglia pertanto di utilizzarli con molta attenzione.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Uso dei metadati del database](../../connect/jdbc/using-database-metadata.md)|Viene descritto come recuperare i metadati relativi al database con connessione attiva.|  
|[Uso dei metadati del set di risultati](../../connect/jdbc/using-result-set-metadata.md)|Viene descritto come recuperare i metadati relativi al set di risultati corrente.|  
|[Uso dei metadati dei parametri](../../connect/jdbc/using-parameter-metadata.md)|Viene descritto come recuperare i metadati sui parametri di istruzioni CallableStatement.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del driver JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
