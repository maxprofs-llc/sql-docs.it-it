---
title: sys. Endpoints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- endpoints
- sys.endpoints
- endpoints_TSQL
- sys.endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.endpoints catalog view
ms.assetid: e6dafa4e-e47e-43ec-acfc-88c0af53c1a1
author: stevestein
ms.author: sstein
ms.openlocfilehash: b814f8cb0013a202f88aba76b99cf52c49dd1c1a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061408"
---
# <a name="sysendpoints-transact-sql"></a>sys.endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni endpoint creato nel sistema. Esiste sempre un solo endpoint SYSTEM.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**nome**|**sysname**|Nome dell'endpoint. Valore univoco all'interno del server. Non ammette i valori Null.|  
|**endpoint_id**|**int**|ID dell'endpoint. Valore univoco all'interno del server. Un endpoint con ID minore di 65536 è un endpoint di sistema. Non ammette i valori Null.|  
|**principal_id**|**int**|ID dell'entità server che ha creato l'endpoint e ne è proprietaria. Ammette i valori Null.|  
|**protocollo**|**tinyint**|Protocollo dell'endpoint.<br /><br /> 1 = HTTP<br /><br /> 2 = TCP<br /><br /> 3 = Named pipe<br /><br /> 4 = Memoria condivisa<br /><br /> 5 = VIA (Virtual Interface Adapter)<br /><br /> Non ammette i valori Null.|  
|**protocol_desc**|**nvarchar (60)**|Descrizione del protocollo dell'endpoint. Ammette valori Null. Uno dei valori seguenti:<br /><br /> **HTTP**<br /><br /> **TCP**<br /><br /> **NAMED_PIPES**<br /><br /> **SHARED_MEMORY**<br /><br /> **Via** Nota: il protocollo VIA è deprecato. [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]|  
|**tipo**|**tinyint**|Tipo di payload dell'endpoint.<br /><br /> 1 = SOAP<br /><br /> 2 = TSQL<br /><br /> 3 = SERVICE_BROKER<br /><br /> 4 = DATABASE_MIRRORING<br /><br /> Non ammette i valori Null.|  
|**type_desc**|**nvarchar (60)**|Descrizione del tipo di payload dell'endpoint. Ammette i valori Null. Uno dei valori seguenti:<br /><br /> **SOAP**<br /><br /> **TSQL**<br /><br /> **SERVICE_BROKER**<br /><br /> **DATABASE_MIRRORING**|  
|**state**|**tinyint**|Stato dell'endpoint.<br /><br /> 0 = STARTED: l'endpoint è in attesa ed elabora le richieste.<br /><br /> 1 = STOPPED: l'endpoint è in attesa, ma non elabora le richieste.<br /><br /> 2 = DISABLED: l'endpoint non è in attesa.<br /><br /> Il valore predefinito è 1. Ammette i valori Null.|  
|**state_desc**|**nvarchar (60)**|Descrizione dello stato dell'endpoint:<br /><br /> STARTED = L'endpoint è in attesa ed elabora le richieste.<br /><br /> STOPPED = L'endpoint è in attesa, ma non elabora le richieste.<br /><br /> DISABLED = L'endpoint non è in attesa.<br /><br /> Il valore predefinito è STOPPED.<br /><br /> Ammette i valori Null.|  
|**is_admin_endpoint**|**bit**|Specifica se l'endpoint è destinato a un utilizzo amministrativo.<br /><br /> 0 = Endpoint non amministrativo.<br /><br /> 1 = Endpoint amministrativo.<br /><br /> Non ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo degli endpoint &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
