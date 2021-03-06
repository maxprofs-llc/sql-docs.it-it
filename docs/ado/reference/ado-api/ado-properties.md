---
title: Proprietà ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- properties [ADO]
- ADO properties
ms.assetid: 0ac0d1a7-6c7a-4f4c-b115-428935e0f98b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d3ddf4e26d015067c0b5bf06f6e2adeecd39f041
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67920890"
---
# <a name="ado-properties"></a>Proprietà ADO

|||  
|-|-|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|Indica in quale pagina si trova il record corrente.|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|Indica la posizione ordinale del record corrente di un oggetto **Recordset** .|  
|[ActiveCommand](../../../ado/reference/ado-api/activecommand-property-ado.md)|Indica l'oggetto **comando** che ha creato l'oggetto **Recordset** associato.|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Indica a quale oggetto **connessione** appartiene attualmente il **comando**, il **Recordset**o l'oggetto **record** specificato.|  
|[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)|Indica la lunghezza effettiva del valore di un campo.|  
|[Attributes](../../../ado/reference/ado-api/attributes-property-ado.md)|Indica una o più caratteristiche di un oggetto.|  
|[BOF e EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|**BOF** indica che la posizione del record corrente precede il primo record in un oggetto recordset.<br /><br /> **EOF** indica che la posizione corrente del record è successiva all'ultimo record in un oggetto recordset.|  
|[Segnalibro](../../../ado/reference/ado-api/bookmark-property-ado.md)|Indica un segnalibro che identifica in modo univoco il record corrente in un oggetto **Recordset** o imposta il record corrente in un oggetto **Recordset** sul record identificato da un segnalibro valido.|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|Indica il numero di record di un oggetto **Recordset** memorizzati nella cache localmente in memoria.|  
|[Capitolo](../../../ado/reference/ado-api/chapter-property-ado.md)|Ottiene o imposta un oggetto OLE DB **capitolo** da/su un oggetto **ADORecordsetConstruction** .|  
|[CharSet](../../../ado/reference/ado-api/charset-property-ado.md)|Indica il set di caratteri in cui deve essere convertito il contenuto di un **flusso** di testo.|  
|[CommandStream](../../../ado/reference/ado-api/commandstream-property-ado.md)|Indica il flusso utilizzato come input per un oggetto **comando** .|  
|[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)|Indica il testo di un comando da emettere a fronte di un provider.|  
|[CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)|Indica il tempo di attesa durante l'esecuzione di un comando prima di terminare il tentativo e generare un errore.|  
|[CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)|Indica il tipo di un oggetto **comando** .|  
|[Proprietà ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)|Indica le informazioni utilizzate per stabilire una connessione a un'origine dati.|  
|[ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)|Indica il tempo di attesa durante il tentativo di stabilire una connessione prima di terminare il tentativo e generare un errore.|  
|[Conteggio](../../../ado/reference/ado-api/count-property-ado.md)|Indica il numero di oggetti in una raccolta.|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|Indica la posizione del servizio del cursore.|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Indica il tipo di cursore utilizzato in un oggetto **Recordset** .|  
|[DataMember](../../../ado/reference/ado-api/datamember-property.md)|Indica il nome del membro dati che verrà recuperato dall'oggetto a cui fa riferimento la proprietà **DataSource** .|  
|[DataSource](../../../ado/reference/ado-api/datasource-property-ado.md)|Indica un oggetto che contiene i dati che devono essere rappresentati come oggetto **Recordset** .|  
|[DefaultDatabase](../../../ado/reference/ado-api/defaultdatabase-property.md)|Indica il database predefinito per un oggetto **Connection** .|  
|[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)|Indica la capacità dei dati di un oggetto **campo** .|  
|[Descrizione](../../../ado/reference/ado-api/description-property.md)|Descrive un oggetto **Error** .|  
|[Sottolinguaggio](../../../ado/reference/ado-api/dialect-property.md)|Indica la sintassi e le regole generali che il provider utilizzerà per analizzare le proprietà **CommandText** o **CommandStream** .|  
|[Direzione](../../../ado/reference/ado-api/direction-property.md)|Indica se il **parametro** rappresenta un parametro di input, un parametro di output o entrambi o se il parametro è il valore restituito da un stored procedure.|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|Indica lo stato di modifica del record corrente.|  
|[EOS](../../../ado/reference/ado-api/eos-property.md)|Indica se la posizione corrente è alla fine del flusso.|  
|[Filter](../../../ado/reference/ado-api/filter-property.md)|Indica un filtro per i dati in un **Recordset**.|  
|[HelpContext e fileguida](../../../ado/reference/ado-api/helpcontext-helpfile-properties.md)|Indica il file della guida e l'argomento associato a un oggetto **Error** .<br /><br /> **HelpContextID** restituisce un ID di contesto, come valore **Long** , per un argomento in un file della guida.<br /><br /> FilePath restituisce un valore **stringa** **che restituisce un** percorso completamente risolto di un file della guida.|  
|[Indice](../../../ado/reference/ado-api/index-property.md)|Indica il nome dell'indice attualmente attivo per un oggetto **Recordset** .|  
|[IsolationLevel](../../../ado/reference/ado-api/isolationlevel-property.md)|Indica il livello di isolamento per un oggetto **Connection** .|  
|[Elemento](../../../ado/reference/ado-api/item-property-ado.md)|Indica un membro specifico di una raccolta, in base al nome o al numero ordinale.|  
|[LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)|Indica il carattere binario da utilizzare come separatore di riga negli oggetti del **flusso** di testo.|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Indica il tipo di blocchi inseriti nei record durante la modifica.|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|Indica i record di cui deve essere eseguito il marshalling sul server.|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|Indica il numero massimo di record da restituire a un **Recordset** da una query.|  
|[Mode](../../../ado/reference/ado-api/mode-property-ado.md)|Indica le autorizzazioni disponibili per la modifica dei dati in una **connessione**, un **record**o un oggetto **flusso** .|  
|[Nome](../../../ado/reference/ado-api/name-property-ado.md)|Indica il nome di un oggetto.|  
|[NativeError](../../../ado/reference/ado-api/nativeerror-property-ado.md)|Indica il codice di errore specifico del provider per un determinato oggetto **Error** .|  
|[Numero](../../../ado/reference/ado-api/number-property-ado.md)|Indica il numero che identifica in modo univoco un oggetto **Error** .|  
|[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)|Indica la scala dei valori numerici in un **parametro** o in un oggetto **campo** .|  
|[OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)|Indica il valore di un **campo** esistente nel record prima che siano state apportate modifiche.|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Indica il numero di pagine di dati contenute nell'oggetto **Recordset** .|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|Indica il numero di record che rappresentano una pagina nel **Recordset**.|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Imposta il contenitore di un oggetto OLE DB **riga** su un oggetto **ADORecordConstruction** , in modo che l'elemento padre della riga venga trasformato in un oggetto **record** ADO.|  
|[ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)|Indica una stringa URL assoluta che punta al **record** padre dell'oggetto **record** corrente.|  
|[Posizione](../../../ado/reference/ado-api/position-property-ado.md)|Indica la posizione corrente all'interno di un oggetto **flusso** .|  
|[Precision](../../../ado/reference/ado-api/precision-property-ado.md)|Indica il grado di precisione per i valori numerici in un oggetto **Parameter** o per gli oggetti **campo** numerico.|  
|[Prepared](../../../ado/reference/ado-api/prepared-property-ado.md)|Indica se salvare una versione compilata di un comando prima dell'esecuzione.|  
|[Provider](../../../ado/reference/ado-api/provider-property-ado.md)|Indica il nome del provider per un oggetto **Connection** .|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Indica il numero di record in un oggetto **Recordset** .|  
|[RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)|Indica il tipo di oggetto **record** .|  
|[Riga](../../../ado/reference/ado-api/row-property-ado.md)|Ottiene o imposta un oggetto OLE DB **riga** da/in un oggetto **ADORecordConstruction** .|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|Ottiene o imposta un OLE DB oggetto **RowPosition** da/in un oggetto **ADORecordsetConstruction** .|  
|[Set di righe](../../../ado/reference/ado-api/rowset-property-ado.md)|Ottiene o imposta un oggetto OLE DB **set di righe** da/in un oggetto **ADORecordsetConstruction** .|  
|[Origine (errore ADO)](../../../ado/reference/ado-api/source-property-ado-error.md)|Indica il nome dell'oggetto o dell'applicazione che ha generato originariamente un errore.|  
|[Origine (record ADO)](../../../ado/reference/ado-api/source-property-ado-record.md)|Indica l'entità rappresentata dall'oggetto **record** .|  
|[Origine (recordset ADO)](../../../ado/reference/ado-api/source-property-ado-recordset.md)|Indica l'origine dei dati in un oggetto **Recordset** .|  
|[SQLState](../../../ado/reference/ado-api/sqlstate-property.md)|Indica lo stato SQL per un oggetto **errore** specifico.|  
|[Stato](../../../ado/reference/ado-api/state-property-ado.md)|Indica per tutti gli oggetti applicabili se lo stato dell'oggetto è aperto o chiuso. Indica per tutti gli oggetti applicabili che eseguono un metodo asincrono, se lo stato corrente dell'oggetto è la connessione, l'esecuzione o il recupero.|  
|[Stato (campo ADO)](../../../ado/reference/ado-api/status-property-ado-field.md)|Indica lo stato di un oggetto **campo** .|  
|[Stato (recordset ADO)](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Indica lo stato del record corrente relativo agli aggiornamenti batch o ad altre operazioni bulk.|  
|[StayInSync](../../../ado/reference/ado-api/stayinsync-property.md)|Indica, in un oggetto **Recordset** gerarchico, se il riferimento ai record figlio sottostanti (ovvero il *capitolo*) cambia quando la posizione della riga padre cambia.|  
|[Proprietà Stream](../../../ado/reference/ado-api/stream-property.md)|Ottiene o imposta un oggetto OLE DB **flusso** da/in un oggetto **ADOStreamConstruction** .|  
|[Tipo](../../../ado/reference/ado-api/type-property-ado.md)|Indica il tipo operativo o il tipo di dati di un **parametro**, un **campo**o un oggetto **proprietà** .|  
|[Tipo (flusso ADO)](../../../ado/reference/ado-api/type-property-ado-stream.md)|Indica il tipo di dati contenuti nel **flusso** (binario o testo).|  
|[UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)|Indica il valore corrente nel database per un oggetto **campo** .|  
|[Valore](../../../ado/reference/ado-api/value-property-ado.md)|Indica il valore assegnato a un **campo**, un **parametro**o un oggetto **proprietà** .|  
|[Version](../../../ado/reference/ado-api/version-property-ado.md)|Indica il numero di versione ADO.|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento all'API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Raccolte ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Proprietà dinamiche ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Costanti enumerate ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Appendice B: errori ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Eventi ADO](../../../ado/reference/ado-api/ado-events.md)   
 [Metodi ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modello a oggetti ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Interfacce e oggetti ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)
