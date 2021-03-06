---
title: ExecuteOptionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ExecuteOptionEnum
helpviewer_keywords:
- ExecuteOptionEnum enumeration [ADO]
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bef70bd72425e749865e31ecf162e719737dd272
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932840"
---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
Specifica la modalità di esecuzione di un comando da un provider.  
  
|Costante|valore|Descrizione|  
|--------------|-----------|-----------------|  
|**adAsyncExecute**|0x10|Indica che il comando deve essere eseguito in modo asincrono.<br /><br /> Questo valore non può essere combinato con il valore di [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) **adCmdTableDirect**.|  
|**adAsyncFetch**|0x20|Indica che le righe rimanenti dopo la quantità iniziale specificata nella proprietà [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) devono essere recuperate in modo asincrono.|  
|**adAsyncFetchNonBlocking**|0x40|Indica che il thread principale non si blocca mai durante il recupero. Se la riga richiesta non è stata recuperata, la riga corrente viene spostata automaticamente alla fine del file.<br /><br /> Se si apre un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) da un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) contenente un **Recordset**archiviato in modo permanente, **adAsyncFetchNonBlocking** non avrà alcun effetto. l'operazione sarà sincrona e bloccante.<br /><br /> **adAsynchFetchNonBlocking** non ha alcun effetto quando viene usata l'opzione [adCmdTableDirect](../../../ado/reference/ado-api/commandtypeenum.md) per aprire il **Recordset**.|  
|**adExecuteNoRecords**|0x80|Indica che il testo del comando è un comando o stored procedure che non restituisce righe, ad esempio un comando che inserisce solo i dati. Se vengono recuperate righe, queste vengono ignorate e non vengono restituite.<br /><br /> **adExecuteNoRecords** può essere passato solo come parametro facoltativo al **comando** o al metodo **Execute della connessione** .|  
|**adExecuteStream**|0x400|Indica che i risultati dell'esecuzione di un comando devono essere restituiti come flusso.<br /><br /> **adExecuteStream** può essere passato solo come parametro facoltativo al metodo **Execute del comando** .|  
|**adExecuteRecord**||Indica che **CommandText** è un comando o stored procedure che restituisce una singola riga che deve essere restituita come oggetto **record** .|  
|**adOptionUnspecified**|-1|Indica che il comando non è specificato.|  
  
## <a name="adowfc-equivalent"></a>Equivalente ADO/WFC  
 Pacchetto: **com. ms. wfc. Data**  
  
|Costante|  
|--------------|  
|AdoEnums. ExecuteOption. ASYNCEXECUTE|  
|AdoEnums. ExecuteOption. ASYNCFETCH|  
|AdoEnums. ExecuteOption. ASYNCFETCHNONBLOCKING|  
|AdoEnums. ExecuteOption. NORECORDS|  
|AdoEnums. ExecuteOption. Unspecified|  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Metodo Execute (Command - ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|[Metodo Execute (Connection - ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|  
|[Metodo Open (Recordset - ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Metodo Requery](../../../ado/reference/ado-api/requery-method.md)|
