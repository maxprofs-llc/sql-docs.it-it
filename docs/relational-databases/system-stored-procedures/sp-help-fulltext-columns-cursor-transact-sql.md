---
title: sp_help_fulltext_columns_cursor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_columns_cursor
- sp_help_fulltext_columns_cursor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_columns_cursor
ms.assetid: 26054e76-53b7-4004-8d48-92ba3435e9d7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a9bbd9039e20fad5cf4c22b71e9a85662bf5912
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68055102"
---
# <a name="sp_help_fulltext_columns_cursor-transact-sql"></a>sp_help_fulltext_columns_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilizza un cursore per restituire le colonne impostate per l'indicizzazione full-text.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Utilizzare invece la vista del catalogo [sys. fulltext_index_columns](../../relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql.md) .  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_fulltext_columns_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @column_name = ] 'column_name' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @cursor_return = ] @cursor_variable OUTPUT`Variabile di output di tipo **Cursor**. Il cursore restituito è di tipo scorrevole, dinamico e di sola lettura.  
  
`[ @table_name = ] 'table_name'`Nome di tabella costituito da una o due parti per cui sono richieste informazioni sugli indici full-text. *table_name* è di **tipo nvarchar (517)** e il valore predefinito è null. Se *table_name* viene omesso, vengono recuperate le informazioni sulla colonna dell'indice full-text per ogni tabella con indicizzazione full-text.  
  
`[ @column_name = ] 'column_name'`Nome della colonna per cui si desiderano i metadati dell'indice full-text. *column_name* è di **tipo sysname** e il valore predefinito è null. Se *column_name* viene omesso o è null, vengono restituite informazioni sulla colonna full-text per ogni colonna con indicizzazione full-text per *table_name*. Se *table_name* viene omesso o è null, vengono restituite informazioni sulla colonna dell'indice full-text per ogni colonna indicizzata full-text per tutte le tabelle del database.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (esito positivo) o 1 (esito negativo)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Proprietario della tabella. Corrisponde al nome dell'utente del database che ha creato la tabella.|  
|**TABLE_ID**|**int**|ID della tabella.|  
|**TABLE_NAME**|**sysname**|Nome della tabella.|  
|**FULLTEXT_COLUMN_NAME**|**sysname**|Colonna impostata per l'indicizzazione in una tabella indicizzata full-text.|  
|**FULLTEXT_COLID**|**int**|ID della colonna indicizzata full-text.|  
|**FULLTEXT_BLOBTP_COLNAME**|**sysname**|Colonna di una tabella indicizzata full-text che specifica il tipo di documento della colonna indicizzata full-text. Questo valore è applicabile solo quando la colonna con indicizzazione full-text è una colonna **varbinary (max)** o **Image** .|  
|**FULLTEXT_BLOBTP_COLID**|**int**|ID della colonna per il tipo di documento. Questo valore è applicabile solo quando la colonna con indicizzazione full-text è una colonna **varbinary (max)** o **Image** .|  
|**FULLTEXT_LANGUAGE**|**sysname**|Lingua utilizzata per la ricerca full-text nella colonna.|  
  
## <a name="permissions"></a>Autorizzazioni  
 Le autorizzazioni di esecuzione vengono assegnate per impostazione predefinita ai membri del ruolo **public** .  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sulle colonne impostate per l'indicizzazione full-text in tutte le tabelle del database.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_columns_cursor @mycursor OUTPUT  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>Vedere anche  
 [COLUMNPROPERTY &#40;&#41;Transact-SQL](../../t-sql/functions/columnproperty-transact-sql.md)   
 [sp_fulltext_column &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-fulltext-column-transact-sql.md)   
 [sp_help_fulltext_columns &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-help-fulltext-columns-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
