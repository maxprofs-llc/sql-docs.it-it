---
title: Metodo unwrap (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: eb8abe29-f3ec-4752-a590-1d5dc3e48f08
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f8cb254ba464b0e051c00c7ac6d410c5e6da1e36
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "67997283"
---
# <a name="unwrap-method-sqlserverdatasource"></a>Metodo unwrap (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Restituisce un oggetto che implementa l'interfaccia specificata per consentire l'accesso ai metodi specifici di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>Parametri  
 *iface*  
  
 Classe di tipo T che definisce un'interfaccia.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto che implementa l'interfaccia specificata.  
  
## <a name="exceptions"></a>Eccezioni  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Osservazioni  
 Il metodo [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md) è definito dall'interfaccia java.sql.Wrapper, introdotta nella specifica JDBC 4.0.  
  
 È possibile che le applicazioni debbano accedere alle estensioni dell'API JDBC specifiche di [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Il metodo unwrap supporta l'annullamento del wrapping nelle classi pubbliche estese dall'oggetto, se le classi espongono estensioni del fornitore.  
  
 Quando viene chiamato questo metodo, l'oggetto annulla il wrapping nella classe [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
 Per altre informazioni, vedere [Wrapper e interfacce](../../../connect/jdbc/wrappers-and-interfaces.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo isWrapperFor &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)   
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
