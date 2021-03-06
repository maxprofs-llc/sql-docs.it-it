---
title: Creazione di una stringa di connessione | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/20/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
- connection strings [ADO]
ms.assetid: 14eae122-2d1e-40c8-b88e-b7cb8dfbc93b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c9d81ef7be98f3c65167de24b3ff59ac6f05df5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925769"
---
# <a name="creating-a-connection-string"></a>Creazione di una stringa di connessione
Una stringa di connessione è costituita da un elenco di coppie argomento/valore (ovvero parametri), separate da punti e virgola. Ad esempio:  
  
```syntax
"arg1=val1; arg2=val2; ... argN=valN;"  
```  
  
 Tutti i parametri devono essere riconosciuti da ADO o dal provider specificato.  
  
 ADO riconosce i cinque argomenti seguenti in una stringa di connessione.  
  
|Argomento|Descrizione|  
|--------------|-----------------|  
|*Provider*|Specifica il nome di un provider da utilizzare per la connessione.|  
|*Nome file*|Specifica il nome di un file specifico del provider (ad esempio, un oggetto origine dati permanente) contenente le informazioni di connessione predefinite.|  
|*URL*|Specifica la stringa di connessione come URL assoluto che identifica una risorsa, ad esempio un file o una directory.|  
|*Provider remoto*|Specifica il nome di un provider da utilizzare per l'apertura di una connessione sul lato client. (Solo Remote Data Service).|  
|*Server remoto*|Specifica il nome del percorso del server da utilizzare per l'apertura di una connessione sul lato client. (Solo Remote Data Service).|  
  
 Gli altri argomenti vengono passati al provider denominato nell'argomento del *provider* , senza alcuna elaborazione da parte di ADO.  
  
 Applicazione HelloData in [HelloData: una semplice applicazione ADO](../../../ado/guide/data/hellodata-a-simple-ado-application.md) usava la stringa di connessione seguente:  
  
```vb
m_sConnStr = "Provider=SQLOLEDB;Data Source=MySqlServer;" & _  
             "Initial Catalog=Northwind;Integrated Security='SSPI';"  
```  
  
 In questa stringa di connessione, ADO riconosce solo `"Provider=SQLOLEDB"` il parametro, che specifica il provider di Microsoft OLE DB per SQL Server come origine dati ADO. Il resto delle coppie argomento/valore, `"Data Source=MySqlServer; Initial Catalog=Northwind;Integrated Security='SSPI';"`, viene passato Verbatim a questo provider. Il tipo e la validità di tali parametri sono specifici del provider. Per informazioni sui parametri validi che possono essere passati nella stringa di connessione, consultare la documentazione del singolo provider.  
  
 In base al provider OLE DB per SQL Server documentazione, è possibile sostituire "Server" per il parametro dell' *origine dati* e "database" per il parametro del *catalogo iniziale* . Quindi, la stringa di connessione seguente produrrebbe risultati identici a quelli precedenti:  
  
```vb
m_sConnStr = "Provider=SQLOLEDB;Server=MySqlServer;" & _  
             "Database=Northwind;Integrated Security='SSPI';"  
```
