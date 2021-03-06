---
title: sys. sysobjects (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysobjects_TSQL
- sysobjects
- sysobjects_TSQL
- sys.sysobjects
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysobjects compatibility view
- sysobjects system table
ms.assetid: 44fdc387-67b0-4139-8bf5-ed26cf640cd1
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 26d4860c7ea434aecb0255134178b73fb7c01be4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67995603"
---
# <a name="syssysobjects-transact-sql"></a>sys.sysobjects (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Contiene una riga per ogni oggetto creato all'interno di un database, ad esempio un vincolo, un valore predefinito, un log, una regola o una stored procedure.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|name|**sysname**|Nome dell'oggetto|  
|id|**int**|Numero di identificazione dell'oggetto|  
|xtype|**carattere (2)**|Tipo di oggetto. Può trattarsi di uno dei tipi di oggetti seguenti:<br /><br /> AF = funzione di aggregazione (CLR)<br /><br /> C = vincolo CHECK<br /><br /> D = vincolo predefinito o DEFAULT<br /><br /> F = vincolo FOREIGN KEY<br /><br /> L = Log<br /><br /> FN = funzione scalare<br /><br /> FS = funzione scalare di assembly (CLR)<br /><br /> FT = funzione valutata a livello di tabella assembly (CLR)<br /><br /> IF = funzione della tabella inline<br /><br /> IT = tabella interna<br /><br /> P = stored procedure<br /><br /> PC = stored procedure di assembly (CLR)<br /><br /> PK = vincolo PRIMARY KEY (il tipo è K)<br /><br /> RF = stored procedure del filtro di replica<br /><br /> S = tabella di sistema<br /><br /> SN = sinonimo<br /><br /> SQ = coda di servizio<br /><br /> TA = trigger DML assembly (CLR)<br /><br /> TF = funzione tabella<br /><br /> TR = trigger DML SQL<br /><br /> TT = tipo tabella<br /><br /> U = tabella utente<br /><br /> UQ = vincolo UNIQUE (il tipo è K)<br /><br /> V = vista<br /><br /> X = stored procedure estesa|  
|uid|**smallint**|ID dello schema del proprietario dell'oggetto. Per i database aggiornati da una versione precedente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'ID dello schema corrisponde all'ID utente del proprietario. Causa un errore di overflow o restituisce NULL se il numero di utenti e ruoli è maggiore di 32.767.<br /><br /> ** \* Importante \* \* ** Se si utilizza una delle istruzioni DDL [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] seguenti, è necessario utilizzare la vista del catalogo [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) anziché sys. sysobjects.<br /><br /> CREARE &#124; ALTER &#124; DROP USER<br /><br /> CREARE &#124; ALTER &#124; DROP ROLE<br /><br /> CREAZIONE DEL RUOLO APPLICAZIONE &#124; ALTER &#124; DROP<br /><br /> CREATE SCHEMA<br /><br /> ALTER AUTHORIZATION ON OBJECT|  
|info|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|base_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|replinfo|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|parent_obj|**int**|Numero di identificazione dell'oggetto padre. Ad esempio, l'ID della tabella se si tratta di un trigger o di un vincolo.|  
|crdate|**datetime**|Data di creazione dell'oggetto.|  
|ftcatid|**smallint**|Identificatore del catalogo full-text per tutte le tabelle utente registrate per l'indicizzazione full-text. È 0 per le tabelle utente non registrate.|  
|schema_ver|**int**|Numero di versione incrementato in corrispondenza della modifica dello schema di una tabella. Restituisce sempre 0.|  
|stats_schema_ver|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|type|**carattere (2)**|Tipo di oggetto. Può avere uno dei valori seguenti:<br /><br /> AF = funzione di aggregazione (CLR)<br /><br /> C = vincolo CHECK<br /><br /> D = vincolo predefinito o DEFAULT<br /><br /> F = vincolo FOREIGN KEY<br /><br /> FN = funzione scalare<br /><br /> FS = funzione scalare di assembly (CLR)<br /><br /> FT = funzione valutata a livello di tabella assembly (CLR)IF = funzione della tabella inline<br /><br /> IT = tabella interna<br /><br /> K = vincolo PRIMARY KEY o UNIQUE<br /><br /> L = Log<br /><br /> P = stored procedure<br /><br /> PC = stored procedure di assembly (CLR)<br /><br /> R = regola<br /><br /> RF = stored procedure del filtro di replica<br /><br /> S = tabella di sistema<br /><br /> SN = sinonimo<br /><br /> SQ = coda di servizio<br /><br /> TA = trigger DML assembly (CLR)<br /><br /> TF = funzione tabella<br /><br /> TR = trigger DML SQL<br /><br /> TT = tipo tabella<br /><br /> U = tabella utente<br /><br /> V = vista<br /><br /> X = stored procedure estesa|  
|userstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|sysstat|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|indexdel|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|refdate|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|version|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|deltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|instrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|updtrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|seltrig|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|category|**int**|Utilizzato per pubblicazioni, vincoli e colonne Identity.|  
|cache|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste di compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
