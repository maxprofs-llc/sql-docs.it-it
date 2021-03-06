---
title: MSpeer_conflictdetectionconfigresponse (T-SQL)
description: Descrive le MSPeer_conflictdetectionconfigureresponse stored procedure utilizzate nella replica peer-to-peer per archiviare la risposta di ogni nodo a una configurazione a livello di topologia.
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_conflictdetectionconfigresponse
- MSpeer_conflictdetectionconfigresponse_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_conflictdetectionconfigureresponse
ms.assetid: 2685fb66-731d-40f7-af4b-596b9222c5d4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6ed3a127d2527b35c301ab7f3d05305c4f8d2ced
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "75322131"
---
# <a name="mspeer_conflictdetectionconfigresponse-transact-sql"></a>MSpeer_conflictdetectionconfigresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilizzata nella replica peer-to-peer per archiviare la risposta di ogni nodo a una richiesta di configurazione a livello di topologia. Questa tabella è archiviata nel database di pubblicazione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|request_id|**int**|Identifica una voce della richiesta di configurazione dei conflitti nella tabella [MSpeer_conflictdetectionconfigrequest](../../relational-databases/system-tables/mspeer-conflictdetectionconfigrequest-transact-sql.md) .|  
|peer_node|**sysname**|Nome dell'istanza del server che ha generato la risposta.|  
|peer_db|**sysname**|Database di sottoscrizione del peer che ha generato la risposta.|  
|peer_version|**sysname**|Identifica il numero di versione del server di pubblicazione.|  
|peer_db_version|**sysname**|Identifica il numero di versione del database peer.|  
|is_peer|**bit**|Indica se un nodo è un Sottoscrittore di sola lettura. Il valore **0** indica un Sottoscrittore di sola lettura.|  
|conflict_detection_enabled|**bit**|Indica se il rilevamento dei conflitti è abilitato per la topologia.|  
|originator_id|**varbinary (16)**|Identifica ogni nodo nella topologia per consentire il rilevamento dei conflitti. Per altre informazioni, vedere [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
|peer_conflict_retention|**int**|Periodo di tempo, espresso in giorni, in cui i metadati vengono archiviati nelle tabelle dei conflitti.|  
|peer_subscriptions|**XML**|Informazioni sul nodo che ha risposto alla richiesta.|  
|progress_phase|**nvarchar (32)**|Identifica la fase di elaborazione corrente utilizzando uno dei valori seguenti:<br /><br /> Started<br /><br /> Versione peer raccolta<br /><br /> Stato raccolto|  
|modified_date|**datetime**|Data e ora del completamento di una fase.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
