---
title: Metodo NextRecordset (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- NextRecordset
- Recordset15::NextRecordset
- Recordset15::raw_NextRecordset
helpviewer_keywords:
- NextRecordset method [ADO]
ms.assetid: ab1fa449-a695-4987-b1ee-bc68f89418dd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3c7af4f5d217670ab23e71a3c53ccd5cf7944b0c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932030"
---
# <a name="nextrecordset-method-ado"></a>Metodo NextRecordset (ADO)
Cancella l'oggetto [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) corrente e restituisce il **Recordset** successivo avanzando attraverso una serie di comandi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Set recordset2 = recordset1.NextRecordset(RecordsAffected )  
```  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un oggetto **Recordset** . Nel modello di sintassi, *Recordset1* e *Recordset2* possono essere lo stesso oggetto **Recordset** oppure è possibile utilizzare oggetti distinti. Quando si utilizzano oggetti **Recordset** distinti, la reimpostazione della proprietà **ActiveConnection** sul **Recordset** originale (*Recordset1*) dopo la chiamata di **NextRecordset** genera un errore.  
  
#### <a name="parameters"></a>Parametri  
 *RecordsAffected*  
 Facoltativa. Variabile **Long** a cui il provider restituisce il numero di record interessati dall'operazione corrente.  
  
> [!NOTE]
>  Questo parametro restituisce solo il numero di record interessati da un'operazione. non restituisce un conteggio dei record da un'istruzione SELECT utilizzata per generare il **Recordset**.  
  
## <a name="remarks"></a>Osservazioni  
 Usare il metodo **NextRecordset** per restituire i risultati del comando successivo in un'istruzione di comando composta o in un stored procedure che restituisce più risultati. Se si apre un oggetto **Recordset** basato su un'istruzione di comando composta, ad esempio "Select \* FROM tabella1; SELECT \* from Table2 ") con il metodo [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) su un [comando](../../../ado/reference/ado-api/command-object-ado.md) o il metodo [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) su un **Recordset**, ADO esegue solo il primo comando e restituisce i risultati al *Recordset*. Per accedere ai risultati dei comandi successivi nell'istruzione, chiamare il metodo **NextRecordset** .  
  
 Finché sono presenti risultati aggiuntivi e il **Recordset** contenente le istruzioni composte non viene disconnesso o sottoposto a marshalling attraverso i limiti del processo, il metodo **NextRecordset** continuerà a restituire oggetti **Recordset** . Se un comando di restituzione della riga viene eseguito correttamente, ma non restituisce alcun record, l'oggetto **Recordset** restituito sarà aperto, ma vuoto. Eseguire un test per questo caso verificando che le proprietà [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) e [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) siano entrambe **true**. Se un comando non restituito dalla riga viene eseguito correttamente, l'oggetto **Recordset** restituito verrà chiuso, che è possibile verificare testando la proprietà [state](../../../ado/reference/ado-api/state-property-ado.md) nel **Recordset**. Quando non sono presenti altri risultati, *Recordset* verrà impostato su *Nothing*.  
  
 Il metodo **NextRecordset** non è disponibile in un oggetto **Recordset** disconnesso, dove [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) è stato impostato su **Nothing** (in Microsoft Visual Basic) o null (in altre lingue).  
  
 Se è in corso una modifica in modalità di aggiornamento immediato, la chiamata del metodo **NextRecordset** genera un errore. chiamare prima il metodo [Update](../../../ado/reference/ado-api/update-method.md) o [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) .  
  
 Per passare i parametri per più di un comando nell'istruzione composta compilando la raccolta [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md) oppure passando una matrice con la chiamata **Open** o **Execute** originale, i parametri devono essere nello stesso ordine della raccolta o della matrice come rispettivi comandi nella serie di comandi. Prima di leggere i valori dei parametri di output, è necessario completare la lettura di tutti i risultati.  
  
 Il provider di OLE DB determina quando viene eseguito ogni comando in un'istruzione composta. Il [provider di OLE DB Microsoft per SQL Server](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md), ad esempio, esegue tutti i comandi in un batch alla ricezione dell'istruzione composta. I **Recordset** risultanti vengono restituiti semplicemente quando si chiama **NextRecordset**.  
  
 Tuttavia, altri provider possono eseguire il comando successivo in un'istruzione solo dopo la chiamata a NextRecordset. Per questi provider, se si chiude in modo esplicito l'oggetto **Recordset** prima di eseguire l'intera istruzione Command, ADO non esegue mai i comandi rimanenti.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di metodo NextRecordset (VB)](../../../ado/reference/ado-api/nextrecordset-method-example-vb.md)   
 [Esempio del metodo NextRecordset (VC++)](../../../ado/reference/ado-api/nextrecordset-method-example-vc.md)   
