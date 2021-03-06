---
title: Oggetto record (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Record
helpviewer_keywords:
- Record object [ADO]
ms.assetid: db83ed2c-a8e3-460c-8682-64667e4d5d01
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5ffc515350bfff4307da382c05aae50ed1930802
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917365"
---
# <a name="record-object-ado"></a>Oggetto Record (ADO)
Rappresenta una riga di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) o del provider di dati oppure un oggetto restituito da un provider di dati semistrutturato, ad esempio un file o una directory.  
  
## <a name="remarks"></a>Osservazioni  
 Un oggetto **record** rappresenta una riga di dati e presenta alcune somiglianze concettuali con un **Recordset**a una riga. A seconda delle funzionalità del provider, gli oggetti **record** possono essere restituiti direttamente dal provider anziché da un **Recordset**di una riga, ad esempio quando viene eseguita una query SQL che seleziona solo una riga. In alternativa, è possibile ottenere un oggetto **record** direttamente da un oggetto **Recordset** . In alternativa, è possibile restituire un **record** direttamente da un provider ai dati semistrutturati, ad esempio il provider di OLE DB di Microsoft Exchange.  
  
 È possibile visualizzare i campi associati all'oggetto **record** per mezzo della raccolta [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) nell'oggetto **record** . ADO consente colonne con valori di oggetto, inclusi **Recordset**, **SAFEARRAY**e valori scalari nella raccolta **Fields** di oggetti **record** .  
  
 Se l'oggetto **record** rappresenta una riga in un **Recordset**, è possibile tornare al **Recordset** originale con la proprietà [source](../../../ado/reference/ado-api/source-property-ado-record.md) .  
  
 L'oggetto **record** può essere usato anche da provider di dati semistrutturati, ad esempio il [provider Microsoft OLE DB per Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md), per modellare gli spazi dei nomi strutturati ad albero. Ogni nodo dell'albero è un oggetto **record** con colonne associate. Le colonne possono rappresentare gli attributi di tale nodo e altre informazioni rilevanti. L'oggetto **record** può rappresentare sia un nodo foglia che un nodo non foglia nella struttura ad albero. I nodi non foglia hanno altri nodi come contenuto, ma i nodi foglia non hanno tale contenuto. I nodi foglia in genere contengono flussi binari di dati e nodi non foglia possono avere anche un flusso binario predefinito associato. Le proprietà dell'oggetto **record** identificano il tipo di nodo.  
  
 L'oggetto **record** rappresenta anche un modo alternativo per spostarsi tra i dati organizzati gerarchicamente. È possibile creare un oggetto **record** per rappresentare la radice di un sottoalbero specifico in una struttura ad albero di grandi dimensioni e i nuovi oggetti **record** possono essere aperti per rappresentare i nodi figlio.  
  
 Una risorsa, ad esempio un file o una directory, può essere identificata in modo univoco da un URL assoluto. Un oggetto [connessione](../../../ado/reference/ado-api/connection-object-ado.md) viene creato in modo implicito e impostato sull'oggetto **record** quando il **record** viene aperto utilizzando un URL assoluto. Un oggetto **connessione** può essere impostato in modo esplicito sull'oggetto **record** tramite la proprietà [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) . I file e le directory a cui è possibile accedere tramite l'oggetto **Connection** definiscono il *contesto* in cui possono essere eseguite le operazioni di **registrazione** .  
  
 I metodi di navigazione e modifica dei dati nell'oggetto **record** accettano anche un URL relativo, che individua una risorsa usando un URL assoluto o il contesto dell'oggetto di **connessione** come punto di partenza.  
  
> [!NOTE]
>  Gli URL che usano lo schema http richiameranno automaticamente il [provider di Microsoft OLE DB per la pubblicazione Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Per ulteriori informazioni, vedere [URL assoluto e relativo](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Un oggetto **Connection** è associato a ogni oggetto **record** . Di conseguenza, le operazioni di **registrazione** di oggetti possono far parte di una transazione richiamando i metodi di transazione dell'oggetto **Connection** .  
  
 L'oggetto **record** non supporta gli eventi ADO e pertanto non risponderà alle notifiche.  
  
 Con i metodi e le proprietà di un oggetto **record** , è possibile eseguire le operazioni seguenti:  
  
-   Impostare o restituire l'oggetto **connessione** associato con la proprietà [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) .  
  
-   Indica le autorizzazioni di accesso con la proprietà [mode](../../../ado/reference/ado-api/mode-property-ado.md) .  
  
-   Restituisce l'URL della directory, se presente, che contiene la risorsa rappresentata dal **record** con la proprietà [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md) .  
  
-   Indica l'URL assoluto, l'URL relativo o il **Recordset** da cui il **record** viene derivato con la proprietà [source](../../../ado/reference/ado-api/source-property-ado-record.md) .  
  
-   Indica lo stato corrente del **record** con la proprietà [state](../../../ado/reference/ado-api/state-property-ado.md) .  
  
-   Indica il tipo di **record** - *semplice*, di *raccolta*o di *documento strutturato* con la proprietà [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md).  
  
-   Arrestare l'esecuzione di un'operazione asincrona con il metodo [Cancel](../../../ado/reference/ado-api/cancel-method-ado.md) .  
  
-   Annullare l'associazione del **record** da un'origine dati con il metodo [Close](../../../ado/reference/ado-api/close-method-ado.md) .  
  
-   Copiare il file o la directory rappresentata da un **record** in un altro percorso con il metodo [CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md) .  
  
-   Eliminare il file, la directory e le sottodirectory, rappresentati da un **record** con il metodo [DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md) .  
  
-   Aprire un **Recordset** contenente le righe che rappresentano le sottodirectory e i file dell'entità rappresentata dal **record** con il metodo [GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md) .  
  
-   Spostare (rinominare) il file, la directory e le sottodirectory, rappresentati da un **record** in un altro percorso con il metodo [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) .  
  
-   Associare il **record** a un'origine dati esistente o creare un nuovo file o una nuova directory con il metodo [Open](../../../ado/reference/ado-api/open-method-ado-record.md) .  
  
 L'oggetto **record** è sicuro per lo scripting.  
  
 Questa sezione contiene l'argomento seguente.  
  
-   [Proprietà, metodi ed eventi dell'oggetto Record](../../../ado/reference/ado-api/record-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Raccolta Fields (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Raccolta Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Record e flussi](../../../ado/guide/data/records-and-streams.md)   
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
