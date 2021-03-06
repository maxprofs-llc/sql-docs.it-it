---
title: "Passaggio 1: connettersi all'origine dati | Microsoft Docs"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], connecting to data source
- data sources [ODBC], connections
- connecting to data source [ODBC], steps
ms.assetid: 84298664-4523-4149-b821-7b2e42c85281
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 80f2dfc05d9d27f60aca414ee0abd13e13b3ea65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114266"
---
# <a name="step-1-connect-to-the-data-source"></a>Passaggio 1: Connettersi all'origine dati
Il primo passaggio in qualsiasi applicazione è la connessione all'origine dati. Questa fase, incluse le funzioni richieste, è illustrata nella figura seguente.  
  
 ![Connessione all'origine dati in un'applicazione ODBC](../../../odbc/reference/develop-app/media/pr11.gif "pr11")  
  
 Il primo passaggio per la connessione all'origine dati consiste nel caricare Gestione driver e allocare l'handle di ambiente con **SQLAllocHandle**. Per altre informazioni, vedere [allocazione dell'handle di ambiente](../../../odbc/reference/develop-app/allocating-the-environment-handle.md).  
  
 L'applicazione registra quindi la versione di ODBC a cui è conforme chiamando **SQLSetEnvAttr** con l'attributo di ambiente SQL_ATTR_APP_ODBC_VER. Per ulteriori informazioni, vedere [dichiarazione della versione ODBC dell'applicazione](../../../odbc/reference/develop-app/declaring-the-application-s-odbc-version.md) e [compatibilità con le versioni precedenti e conformità agli standard](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Successivamente, l'applicazione alloca un handle di connessione con **SQLAllocHandle** e si connette all'origine dati con **SQLConnect**, **SQLDriverConnect**o **SQLBrowseConnect**. Per ulteriori informazioni, vedere [allocazione di un handle di connessione](../../../odbc/reference/develop-app/allocating-a-connection-handle-odbc.md) e [stabilire una connessione](../../../odbc/reference/develop-app/establishing-a-connection.md).  
  
 L'applicazione imposta quindi tutti gli attributi di connessione, ad esempio se eseguire manualmente il commit delle transazioni. Per ulteriori informazioni, vedere [attributi di connessione](../../../odbc/reference/develop-app/connection-attributes.md).
