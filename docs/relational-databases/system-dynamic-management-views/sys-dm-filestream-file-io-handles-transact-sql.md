---
title: sys. dm_filestream_file_io_handles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_filestream_file_io_handles
- sys.dm_filestream_file_io_handles
- dm_filestream_file_io_handles_TSQL
- sys.dm_filestream_file_io_handles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_handle catalog view
ms.assetid: e59632f4-3292-419f-9217-ca375749f1a5
author: stevestein
ms.author: sstein
ms.openlocfilehash: a96bcedaa3922ebb0691ac949f9eb15ed28336b3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103304"
---
# <a name="sysdm_filestream_file_io_handles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vengono visualizzati gli handle di file conosciuti dal proprietario dello spazio dei nomi (NSO, Namespace Owner). Gli handle FileStream che un client ha ottenuto utilizzando **OpenSqlFilestream** vengono visualizzati da questa visualizzazione.  
  
|Colonna|Type|Descrizione|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary (8)**|Mostra l'indirizzo della struttura NSO interna associata all'handle del client. Ammette i valori Null.|  
|**creation_request_id**|**int**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Non ammette i valori Null.|  
|**creation_irp_id**|**int**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Non ammette i valori Null|  
|**handle_id**|**int**|Viene mostrato l'ID univoco di questo handle assegnato dal driver. Non ammette i valori Null.|  
|**creation_client_thread_id**|**varbinary (8)**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Ammette i valori Null.|  
|**creation_client_process_id**|**varbinary (8)**|Viene mostrato un campo della richiesta di I/O REQ_PRE_CREATE utilizzata per creare questo handle. Ammette i valori Null.|  
|**filestream_transaction_id**|**varbinary (128)**|Viene mostrato l'ID della transazione associata all'handle specificato. Si tratta del valore restituito dalla funzione **GET_FILESTREAM_TRANSACTION_CONTEXT** . Utilizzare questo campo per aggiungere la vista **sys. dm_filestream_file_io_requests** . Ammette i valori Null.|  
|**access_type**|**nvarchar (60)**|Non ammette i valori Null.|  
|**logical_path**|**nvarchar(256)**|Viene mostrato il nome del percorso logico del file aperto da questo handle. Si tratta dello stesso percorso restituito da **. Metodo PathName** di **varbinary**(**Max**) FileStream. Ammette i valori Null.|  
|**physical_path**|**nvarchar(256)**|Viene mostrato il nome del percorso NTFS effettivo del file. Si tratta dello stesso percorso restituito da **. Metodo PhysicalPathName** del FileStream **varbinary**(**Max**). Viene abilitato dal flag di traccia 5556. Ammette i valori Null.|  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Viste a gestione dinamica FILESTREAM e FileTable &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  
