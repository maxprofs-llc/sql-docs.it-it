---
title: CONTEXT_INFO (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CONTEXT_INFO_TSQL
- CONTEXT_INFO
dev_langs:
- TSQL
helpviewer_keywords:
- CONTEXT_INFO function
- Multiple Active Result Sets
- context information [SQL Server]
- MARS [SQL Server]
- session context information [SQL Server]
ms.assetid: 571320f5-7228-4b0e-9d01-ab732d2d1eab
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b6278faa80721ce500257650db70359dcc740ee8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68132068"
---
# <a name="context_info--transact-sql"></a>CONTEXT_INFO (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Questa funzione restituisce il valore di **context_info** impostato per la sessione o il batch corrente oppure derivato tramite l'uso dell'istruzione [SET CONTEXT_INFO](../../t-sql/statements/set-context-info-transact-sql.md).
  
![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Sintassi  
  
```sql
CONTEXT_INFO()  
```  
  
## <a name="return-value"></a>Valore restituito
Valore di **context_info**.
  
Se **context_info** non è stato impostato:
-   In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituisce NULL.  
-   In [!INCLUDE[ssSDS](../../includes/sssds-md.md)] restituisce un GUID univoco specifico della sessione.  
  
## <a name="remarks"></a>Osservazioni  
Grazie alla funzionalità MARS (Multiple Active Result Set) le applicazioni possono eseguire più batch o richieste contemporaneamente usando la stessa connessione. Se uno dei batch in una connessione MARS esegue SET CONTEXT_INFO, la funzione `CONTEXT_INFO` restituisce il nuovo valore del contesto, quando la funzione `CONTEXT_INFO` viene eseguita nello stesso batch dell'istruzione SET. Se la funzione `CONTEXT_INFO` viene eseguita in uno o più degli altri batch nella connessione, `CONTEXT_FUNCTION` restituisce il nuovo valore solo se tali batch sono stati avviati dopo il completamento del batch che ha eseguito l'istruzione SET.
  
## <a name="permissions"></a>Autorizzazioni  
Non sono richieste autorizzazioni particolari. Le viste di sistema seguenti archiviano le informazioni del contesto, ma per l'esecuzione di query dirette su tali viste sono necessarie le autorizzazioni SELECT e VIEW SERVER STATE:
- **sys.dm_exec_requests**
- **sys.dm_exec_sessions**
- **sys.sysprocesses**
  
## <a name="examples"></a>Esempi  
Questo semplice esempio imposta il valore di **context_info** su `0x1256698456` e quindi usa la funzione `CONTEXT_INFO` per recuperare il valore.
  
```sql
SET CONTEXT_INFO 0x1256698456;  
GO  
SELECT CONTEXT_INFO();  
GO  
```  
  
## <a name="see-also"></a>Vedere anche
[SET CONTEXT_INFO &#40;Transact-SQL&#41;](../../t-sql/statements/set-context-info-transact-sql.md)
  
  
