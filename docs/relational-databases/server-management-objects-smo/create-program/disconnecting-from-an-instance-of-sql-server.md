---
title: Disconnessione da un'istanza di SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, disconnecting
- SMO [SQL Server], disconnecting
- instances of SQL Server, disconnecting
- disconnecting [SMO]
ms.assetid: 4ca7f7eb-6b3f-4c73-ac63-88afa8570b61
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: de53acd4ef3d9feb6ed1a5026d8890f83e88d557
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "70148729"
---
# <a name="disconnecting-from-an-instance-of-sql-server"></a>Disconnessione da un'istanza di SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Non è richiesta la chiusura e la disconnessione manuale degli oggetti SMO ( [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects). Le connessioni vengono aperte e chiuse in base alle necessità.  
  
## <a name="connection-pooling"></a>Pool di connessioni  
 Quando viene chiamato il metodo [Connect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.connect) , la connessione non viene rilasciata automaticamente. Il metodo [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) deve essere chiamato in modo esplicito per rilasciare la connessione al pool di connessioni. È inoltre possibile richiedere una connessione non in pool. A tale scopo, impostare la proprietà [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) della <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà che fa riferimento all'oggetto [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) .  
  
## <a name="disconnecting-from-an-instance-of-sql-server-for-rmo"></a>Disconnessione da un'istanza di SQL Server per RMO  
 La chiusura delle connessioni al server quando si programma con RMO funziona in modo leggermente diverso da SMO.  
  
 Poiché la connessione al server per un oggetto RMO viene gestita dall'oggetto [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) , questo oggetto viene utilizzato anche per la disconnessione da un'istanza di [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] quando si programma utilizzando RMO. Per chiudere una connessione utilizzando l'oggetto [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx) , chiamare il metodo [Disconnect](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionmanager.disconnect) dell'oggetto RMO. Dopo che è stata chiusa la connessione, gli oggetti RMO non possono essere utilizzati.  
  
## <a name="example"></a>Esempio  
Per utilizzare qualsiasi esempio di codice fornito, è necessario scegliere l'ambiente di programmazione, il modello di programmazione e il linguaggio di programmazione per la creazione dell'applicazione. Per altre informazioni, vedere [creare un progetto Visual C&#35; SMO in Visual Studio .NET](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
 
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-basic"></a>Chiusura e disconnessione di un oggetto SMO in Visual Basic  
 In questo esempio di codice viene illustrato come richiedere una connessione non in pool impostando la proprietà [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) della <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà dell'oggetto.  
  
```VBNET
Dim srv As Server
srv = New Server
'Disable automatic disconnection.
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect
'Connect to the local, default instance of SQL Server.
srv.ConnectionContext.Connect()
'The actual connection is made when a property is retrieved.
Console.WriteLine(srv.Information.Version)
'Disconnect explicitly.
srv.ConnectionContext.Disconnect()
```
  
## <a name="closing-and-disconnecting-an-smo-object-in-visual-c"></a>Chiusura e disconnessione di un oggetto SMO in Visual C#  
 In questo esempio di codice viene illustrato come richiedere una connessione non in pool impostando la proprietà [NonPooledConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.connectionsettings.nonpooledconnection) della <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> proprietà dell'oggetto.  
  
```csharp  
{   
Server srv;   
srv = new Server();   
//Disable automatic disconnection.   
srv.ConnectionContext.AutoDisconnectMode = AutoDisconnectMode.NoAutoDisconnect;   
//Connect to the local, default instance of SQL Server.   
srv.ConnectionContext.Connect();   
//The actual connection is made when a property is retrieved.   
Console.WriteLine(srv.Information.Version);   
//Disconnect explicitly.   
srv.ConnectionContext.Disconnect();  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.SqlServer.Management.Smo.Server>   
 [ServerConnection](https://msdn.microsoft.com/library/microsoft.sqlserver.management.common.serverconnection.aspx)  
  
  
