---
title: RecordStatusEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordStatusEnum
helpviewer_keywords:
- RecordStatusEnum enumeration [ADO]
ms.assetid: 506fdd70-4452-4e83-95d5-c94311988dfa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 233b2f84b6a60c7b5162edce6c1b76b63946ae81
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931282"
---
# <a name="recordstatusenum"></a>RecordStatusEnum
Specifica lo [stato](../../../ado/reference/ado-api/status-property-ado-recordset.md) di un record per quanto riguarda gli aggiornamenti in batch e altre operazioni bulk.  
  
|Costante|valore|Descrizione|  
|--------------|-----------|-----------------|  
|**adRecCanceled**|0x100|Indica che il record non è stato salvato perché l'operazione è stata annullata.|  
|**adRecCantRelease**|0x400|Indica che il nuovo record non è stato salvato perché il record esistente è stato bloccato.|  
|**adRecConcurrencyViolation**|0x800|Indica che il record non è stato salvato perché è in uso la concorrenza ottimistica.|  
|**adRecDBDeleted**|0x40000|Indica che il record è già stato eliminato dall'origine dati.|  
|**adRecDeleted**|0x4|Indica che il record è stato eliminato.|  
|**adRecIntegrityViolation**|0x1000|Indica che il record non è stato salvato perché l'utente ha violato i vincoli di integrità.|  
|**adRecInvalid**|0x10|Indica che il record non è stato salvato perché il relativo segnalibro non è valido.|  
|**adRecMaxChangesExceeded**|0x2000|Indica che il record non è stato salvato a causa di un numero eccessivo di modifiche in sospeso.|  
|**adRecModified**|0x2|Indica che il record è stato modificato.|  
|**adRecMultipleChanges**|0x40|Indica che il record non è stato salvato perché avrebbe interessato più record.|  
|**adRecNew**|0x1|Indica che il record è nuovo.|  
|**adRecObjectOpen**|0x4000|Indica che il record non è stato salvato a causa di un conflitto con un oggetto di archiviazione aperto.|  
|**adRecOK**|0|Indica che il record è stato aggiornato correttamente.|  
|**adRecOutOfMemory**|0x8000|Indica che il record non è stato salvato perché la memoria del computer è esaurita.|  
|**adRecPendingChanges**|0x80|Indica che il record non è stato salvato perché fa riferimento a un inserimento in sospeso.|  
|**adRecPermissionDenied**|0x10000|Indica che il record non è stato salvato perché l'utente non dispone di autorizzazioni sufficienti.|  
|**adRecSchemaViolation**|0x20000|Indica che il record non è stato salvato poiché viola la struttura del database sottostante.|  
|**adRecUnmodified**|0x8|Indica che il record non è stato modificato.|  
  
## <a name="adowfc-equivalent"></a>Equivalente ADO/WFC  
 AdoEnums. RecordStatus.  
  
 Pacchetto: **com. ms. wfc. Data**  
  
|Costante|  
|--------------|  
|AdoEnums. RecordStatus. annullato|  
|AdoEnums. RecordStatus. CANTRELEASE|  
|AdoEnums. RecordStatus. CONCURRENCYVIOLATION|  
|AdoEnums. RecordStatus. DBDELETED|  
|AdoEnums. RecordStatus. DELETED|  
|AdoEnums. RecordStatus. INTEGRITYVIOLATION|  
|AdoEnums. RecordStatus. non valido|  
|AdoEnums. RecordStatus. MAXCHANGESEXCEEDED|  
|AdoEnums. RecordStatus. MODIFIED|  
|AdoEnums. RecordStatus. MULTIPLECHANGES|  
|AdoEnums. RecordStatus. NEW|  
|AdoEnums. RecordStatus. OBJECTOPEN|  
|AdoEnums. RecordStatus. OK|  
|AdoEnums. RecordStatus. OUTOFMEMORY|  
|AdoEnums. RecordStatus. PENDINGCHANGES|  
|AdoEnums. RecordStatus. PERMISSIONDENIED|  
|AdoEnums. RecordStatus. SCHEMAVIOLATION|  
|AdoEnums. RecordStatus. unmodified|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà Status (Recordset - ADO)](../../../ado/reference/ado-api/status-property-ado-recordset.md)
