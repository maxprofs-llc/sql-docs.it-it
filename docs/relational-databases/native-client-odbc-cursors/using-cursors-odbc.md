---
title: Utilizzo di cursori (ODBC) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 59a7e18c69ffa8d928dc38eaefcaf89249c18b38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73784074"
---
# <a name="using-cursors-odbc"></a>Uso dei cursori (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC supporta un modello di cursore che consente:  
  
-   Diversi tipi di cursori.  
  
-   Scorrimento e posizionamento all'interno di un cursore.  
  
-   Diverse opzioni di concorrenza.  
  
-   Aggiornamenti posizionati.  
  
 Le applicazioni ODBC raramente dichiarano e aprono cursori o utilizzano istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] correlate ai cursori. ODBC apre automaticamente un cursore per ogni set di risultati restituito da un'istruzione SQL. Le caratteristiche dei cursori vengono controllate dagli attributi di istruzione impostati con [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) prima dell'esecuzione dell'istruzione SQL. Le funzioni delle API ODBC per l'elaborazione di set di risultati supportano l'intervallo completo delle funzionalità del cursore, inclusi il recupero, lo scorrimento e gli aggiornamenti posizionati.  
  
 Di seguito viene presentato un confronto tra il funzionamento dei cursori nelle applicazioni ODBC e negli script [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
|Azione|[!INCLUDE[tsql](../../includes/tsql-md.md)]|ODBC|  
|------------|------------------------|----------|  
|Definire il comportamento del cursore|Specificare tramite parametri DECLARE CURSOR|Impostare gli attributi del cursore utilizzando [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)|  
|Aprire un cursore|DICHIARARE il cursore aperto *cursor_name*|**SQLExecDirect** o **SQLExecute**|  
|Recuperare righe|FETCH|**SQLFetch** o [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)|  
|Aggiornamento posizionato|Clausola WHERE CURRENT OF su UPDATE o DELETE|**SQLSetPos**|  
|Chiudere un cursore|Chiudi *cursor_name* deallocare|[SQLCloseCursor](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)|  
  
 I cursori server implementati in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supportano la funzionalità del modello del cursore ODBC. Il driver ODBC di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client utilizza cursori server per supportare la funzionalità del cursore dell'API ODBC.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
-   [Modalità di implementazione dei cursori](../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
-   [Tipi di cursore](../../relational-databases/native-client-odbc-cursors/cursor-types.md)  
  
-   [Comportamenti dei cursori](../../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)  
  
-   [Proprietà del cursore](../../relational-databases/native-client-odbc-cursors/properties/cursor-properties.md)  
  
-   [Dettagli sulla programmazione dei cursori &#40;&#41;ODBC](../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
-   [Scorrimento e recupero di righe](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows.md)  
  
-   [Aggiornamenti posizionati &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/positioned-updates-odbc.md)  
  
## <a name="see-also"></a>Vedere anche  
 [SQL Server Native Client &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [CLOSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [Cursori](../../relational-databases/cursors.md)   
 [DEALLOCATE &#40;Transact-SQL&#41;](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [DECLARE CURSOR &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-cursor-transact-sql.md)   
 [FETCH &#40;Transact-SQL&#41;](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN &#40;Transact-SQL&#41;](../../t-sql/language-elements/open-transact-sql.md)  
  
  
