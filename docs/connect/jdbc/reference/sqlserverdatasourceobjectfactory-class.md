---
title: Classe SQLServerDataSourceObjectFactory | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
author: MightyPen
ms.author: genemi
ms.openlocfilehash: cf4c90644282ff420e064e7a7b5b99a93c257194
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "67971384"
---
# <a name="sqlserverdatasourceobjectfactory-class"></a>Classe SQLServerDataSourceObjectFactory
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Rappresenta una object factory per la materializzazione delle origini dati dall'interfaccia JNDI (Java Naming and Directory Interface).  
  
 **Pacchetto:** com.microsoft.sqlserver.jdbc  
  
 **Estende:** java.lang.Object  
  
 **Implementa:** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo viene ereditato da tutte le classi dell'origine dati. Come parte del supporto per l'interfaccia Referenceable, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] espone questa classe che implementa un elemento ObjectFactory. I server applicazioni Java chiameranno getReference in una classe dell'origine dati creando in questo modo un oggetto Reference che userà il nome della classe internamente come relativa class factory.  
  
 Quando il server applicazioni Java deve dereferenziare l'oggetto Reference, crea un'istanza dell'oggetto SQLServerDataSourceObjectFactory e chiama il metodo [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md) passando l'oggetto Reference per recuperare l'istanza dell'origine dati.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri di SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Informazioni di riferimento sull'API del driver JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
