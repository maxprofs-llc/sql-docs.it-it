---
title: DROP SYNONYM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP SYNONYM
- DROP_SYNONYM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting synonyms
- synonyms [SQL Server], removing
- removing synonyms
- DROP SYNONYM statement
- dropping synonyms
ms.assetid: 23578932-e4de-4c39-a5a0-ce45139c4269
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 59c26a7e490edb120d8819d8e2b16158b5b41e76
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68072134"
---
# <a name="drop-synonym-transact-sql"></a>DROP SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Rimuove un sinonimo da uno schema specificato.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DROP SYNONYM [ IF EXISTS ] [ schema. ] synonym_name  
```  
  
## <a name="arguments"></a>Argomenti  
 *IF EXISTS*  
**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] alla [versione corrente](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 Rimuove in modo condizionale il sinonimo solo se esiste già.  
  
 *schema*  
 Specifica lo schema in cui è contenuto il sinonimo. Se lo schema viene omesso, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilizza lo schema predefinito dell'utente corrente.  
  
 *synonym_name*  
 Nome del sinonimo da eliminare.  
  
## <a name="remarks"></a>Osservazioni  
 I riferimenti ai sinonimi non sono associati a uno schema. È pertanto possibile eliminare un sinonimo in qualsiasi momento. I riferimenti ai sinonimi eliminati verranno trovati solo in fase di esecuzione.  
  
 È possibile creare, eliminare e fare riferimento ai sinonimi in SQL dinamico.  
  
## <a name="permissions"></a>Autorizzazioni  
 Per eliminare un sinonimo, un utente deve soddisfare almeno una delle condizioni seguenti: L'utente deve essere:  
  
-   Il proprietario corrente di un sinonimo.  
  
-   Un utente autorizzato che dispone dell'autorizzazione CONTROL su un sinonimo.  
  
-   Un utente autorizzato che dispone dell'autorizzazione ALTER SCHEMA sullo schema contenitore.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene prima creato e quindi eliminato il sinonimo `MyProduct`.  
  
```  
USE tempdb;  
GO  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
-- Drop synonym MyProduct.  
USE tempdb;  
GO  
DROP SYNONYM MyProduct;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
