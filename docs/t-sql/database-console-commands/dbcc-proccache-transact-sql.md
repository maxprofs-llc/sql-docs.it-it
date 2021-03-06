---
title: DBCC PROCCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC PROCCACHE
- DBCC_PROCCACHE_TSQL
- PROCCACHE_TSQL
- PROCCACHE
dev_langs:
- TSQL
helpviewer_keywords:
- procedure cache [SQL Server]
- displaying procedure cache information
- DBCC PROCCACHE statement
ms.assetid: 7a4f9f8a-13ff-4bf2-ba29-c17012a23659
author: pmasl
ms.author: umajay
ms.openlocfilehash: 7720324915ea147cf5cac938c196957a6cb04c51
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68116464"
---
# <a name="dbcc-proccache-transact-sql"></a>DBCC PROCCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Visualizza in formato di tabella le informazioni sulla cache delle procedure.
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
DBCC PROCCACHE [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argomenti  
 WITH  
 Consente di specificare opzioni.  
  
 NO_INFOMSGS  
 Disattiva la visualizzazione di tutti i messaggi informativi con livello di gravità compreso tra 0 e 10.  
  
## <a name="remarks"></a>Osservazioni  
La cache delle procedure viene utilizzata per inserire nella cache i piani compilati e piani di esecuzione per velocizzare l'esecuzione di batch. Le voci in una cache delle procedure si trovano a livello di batch. La cache delle procedure include le voci seguenti:
-   Piani compilati  
-   Piani di esecuzione  
-   Albero di algebrizzazione  
-   Procedure estese  
  
## <a name="result-sets"></a>Set di risultati  
Nella tabella seguente vengono descritte le colonne del set di risultati.
  
|Nome colonna|Descrizione|  
|-----------------|-----------------|  
|**num proc buffs**|Numero totale di pagine utilizzate da tutte le voci nella cache delle procedure.|  
|**num proc buffs used**|Numero totale di pagine utilizzate da tutte le voci in uso.|  
|**num proc buffs active**|Disponibile solo per compatibilità con le versioni precedenti. Numero totale di pagine utilizzate da tutte le voci in uso.|  
|**proc cache size**|Numero totale di voci nella cache delle procedure.|  
|**proc cache used**|Numero totale di voci in uso.|  
|**proc cache active**|Disponibile solo per compatibilità con le versioni precedenti. Numero totale di voci in uso.|  
  
## <a name="permissions"></a>Autorizzazioni  
È richiesta l'appartenenza al ruolo predefinito del server **sysadmin** o al ruolo predefinito del database **db_owner** .
  
## <a name="see-also"></a>Vedere anche  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  
