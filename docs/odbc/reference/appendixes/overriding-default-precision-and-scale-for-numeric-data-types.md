---
title: Override della precisione e della scala predefinite per i tipi di dati numerici | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 66fc728440808314dbdaa30065c68232f4a89fba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100609"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Override della precisione predefinita e della scala per i tipi di dati numerici
Quando il campo SQL_DESC_TYPE in un ARD è impostato su SQL_C_NUMERIC, chiamando **SQLBindCol** o **SQLSetDescField**, il campo SQL_DESC_SCALE in ARD è impostato su 0 e il campo SQL_DESC_PRECISION è impostato su una precisione predefinita definita dal driver. Ciò si verifica anche quando il campo SQL_DESC_TYPE in un oggetto APD è impostato su SQL_C_NUMERIC, chiamando **SQLBindParameter** o **SQLSetDescField**. Questo vale per i parametri di input, di input/output o di output.  
  
 Se una delle impostazioni predefinite descritte in precedenza non è accettabile per un'applicazione, l'applicazione deve impostare il campo SQL_DESC_SCALE o SQL_DESC_PRECISION chiamando **SQLSetDescField** o **SQLSetDescRec**.  
  
 Se l'applicazione chiama **SQLGetData** per restituire dati in una struttura di SQL_C_NUMERIC, vengono usati i campi SQL_DESC_SCALE e SQL_DESC_PRECISION predefiniti. Se le impostazioni predefinite non sono accettabili, l'applicazione deve chiamare **SQLSetDescRec** o **SQLSetDescField** per impostare i campi e quindi chiamare **SQLGetData** con un *targetType* di SQL_ARD_TYPE per usare i valori nei campi del descrittore.  
  
 Quando viene chiamato **SQLPutData** , la chiamata usa i campi SQL_DESC_SCALE e SQL_DESC_PRECISION del record del descrittore che corrisponde al parametro o alla colonna data-at-execution, ovvero i campi APD per le chiamate a **SQLExecute** o **SQLExecDirect**oppure i campi ARD per le chiamate a **SQLBulkOperations** o **SQLSetPos**.
