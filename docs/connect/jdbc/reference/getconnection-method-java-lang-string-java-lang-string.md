---
title: Metodo getConnection (java.lang.String, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 78db89d6-a8a0-4116-8885-548e627220ed
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87d3dfc2183bdc00261417a024507b41ea5fde28
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "67952747"
---
# <a name="getconnection-method-javalangstring-javalangstring"></a>Metodo getConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Tenta di stabilire una connessione all'origine dati rappresentata da questo oggetto [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) usando il nome utente e la password specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
public java.sql.Connection getConnection(java.lang.String username,  
                                         java.lang.String password)  
```  
  
#### <a name="parameters"></a>Parametri  
 *username*  
  
 Valore **String** contenente il nome utente.  
  
 *password*  
  
 Valore **String** che contiene la password.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="exceptions"></a>Eccezioni  
 java.sql.SQLException  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo getConnection viene specificato dal metodo getConnection nell'interfaccia javax.sql.DataSource.  
  
 La chiamata del metodo getConnection con una password o nome utente non Null sostituirà le proprietà del nome utente e della password che vengono impostate per la classe SQLServerDataSource quando si inizializza l'oggetto SQLServerConnection. Ad esempio, se il chiamante ha chiamato [setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md) e [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) nell'origine dati e quindi chiama getConnection e specifica un nome utente non Null o una password non Null, il nome utente e la password impostati da setUser e setPassword verranno sostituiti dal nome utente e dalla password passati in getConnection.  
  
> [!NOTE]  
>  Il nome utente e la password impostati nell'URL tramite una chiamata al metodo [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md) non verranno modificati in questo caso.  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo getConnection &#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)   
 [Membri di SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Classe SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
