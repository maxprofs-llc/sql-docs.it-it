---
title: Eliminazione di righe nel set di righe con SQLSetPos | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e39b70f92f7b239b011cdd4fdd6abd36c27561c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076797"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Eliminazione di righe nel set di righe con SQLSetPos
L'operazione di eliminazione di **SQLSetPos** consente all'origine dati di eliminare una o più righe selezionate di una tabella. Per eliminare righe con **SQLSetPos**, l'applicazione chiama **SQLSetPos** con *Operation* set su SQL_DELETE e *RowNumber* impostato sul numero della riga da eliminare. Se *RowNumber* è 0, vengono eliminate tutte le righe del set di righe.  
  
 Quando **SQLSetPos** restituisce, la riga eliminata è la riga corrente e il relativo stato è SQL_ROW_DELETED. La riga non può essere usata in altre operazioni posizionate, ad esempio le chiamate a **SQLGetData** o **SQLSetPos**.  
  
 Quando si eliminano tutte le righe del set di righe (*RowNumber* è uguale a 0), l'applicazione può impedire al driver di eliminare determinate righe usando la matrice dell'operazione di riga, come per l'operazione di aggiornamento di **SQLSetPos**. Vedere [aggiornamento delle righe nel set di righe con SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
 Ogni riga eliminata deve essere una riga che esiste nel set di risultati. Se i buffer dell'applicazione sono stati riempiti tramite il recupero e se è stata mantenuta una matrice di stato della riga, i relativi valori in ognuna di queste posizioni delle righe non devono essere SQL_ROW_DELETED, SQL_ROW_ERROR o SQL_ROW_NOROW.
