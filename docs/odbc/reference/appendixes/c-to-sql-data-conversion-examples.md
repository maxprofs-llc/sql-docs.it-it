---
title: Esempi di conversione di dati da C a SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from c to SQL types [ODBC], examples
- data conversions from C to SQL types [ODBC], examples
ms.assetid: 9f390afc-d8b8-4286-b559-98b3b8781f3d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e475abb699c7fa7240ca6eb39b1b32f1730d33c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125744"
---
# <a name="c-to-sql-data-conversion-examples"></a>Esempi di conversione di dati da C a SQL
Negli esempi seguenti viene illustrato il modo in cui il driver converte i dati C in dati SQL:  
  
|Identificatore di tipo C|Valore dati C|Tipo SQL<br /><br /> identificatore|Colonna<br /><br /> length|Dati SQL<br /><br /> Valore|SQLSTATE|  
|-----------------------|------------------|-----------------------------|-----------------------|------------------------|--------------|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|6|abcdef|n/d|  
|SQL_C_CHAR|abcdef\0 [a]|SQL_CHAR|5|abcde|22001|  
|SQL_C_CHAR|1234.56 \ 0 [a]|SQL_DECIMAL|8 [b]|1234,56|n/d|  
|SQL_C_CHAR|1234.56 \ 0 [a]|SQL_DECIMAL|7 [b]|1234,5|22001|  
|SQL_C_CHAR|1234.56 \ 0 [a]|SQL_DECIMAL|4|----|22003|  
|SQL_C_FLOAT|1234,56|SQL_FLOAT|n/d|1234,56|n/d|  
|SQL_C_FLOAT|1234,56|SQL_INTEGER|n/d|1234|22001|  
|SQL_C_FLOAT|1234,56|SQL_TINYINT|n/d|----|22003|  
|SQL_C_TYPE_DATE|1992, 12, 31 [c]|SQL_CHAR|10|1992-12-31|n/d|  
|SQL_C_TYPE_DATE|1992, 12, 31 [c]|SQL_CHAR|9|----|22003|  
|SQL_C_TYPE_DATE|1992, 12, 31 [c]|SQL_TIMESTAMP|n/d|1992-12-31 00:00:00.0|n/d|  
|SQL_C_TYPE_TIMESTAMP|1992, 12, 31, 23, 45, 55, 120000000 [d]|SQL_CHAR|22|1992-12-31 23:45:55.12|n/d|  
|SQL_C_TYPE_TIMESTAMP|1992, 12, 31, 23, 45, 55, 120000000 [d]|SQL_CHAR|21|1992-12-31 23:45:55.1|22001|  
|SQL_C_TYPE_TIMESTAMP|1992, 12, 31, 23, 45, 55, 120000000 [d]|SQL_CHAR|18|----|22003|  
  
 [a] "\ 0" rappresenta un byte di terminazione null. Il byte di terminazione null è necessario solo se la lunghezza dei dati viene SQL_NTS.  
  
 [b] oltre ai byte per i numeri, è necessario un byte per un segno e un altro byte per il separatore decimale.  
  
 [c] i numeri in questo elenco sono i numeri archiviati nei campi della struttura SQL_DATE_STRUCT.  
  
 [d] i numeri in questo elenco sono i numeri archiviati nei campi della struttura SQL_TIMESTAMP_STRUCT.
