---
title: Limitazioni di parole riservate | Microsoft Docs
ms.custom: ''
ms.date: 05/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ed42f083-c9e8-4ee4-9d64-d879bf955c78
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c884d8594c3c4511bed0e24f9b3dd43092176b4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67988023"
---
# <a name="reserved-keyword-limitations"></a>Limitazioni delle parole chiave riservate

Evitare di utilizzare parole chiave riservate ODBC come identificatori nelle tabelle SQL o negli oggetti correlati. Se si verifica un caso dispari in cui è necessario utilizzare una parola chiave riservata come identificatore, è necessario racchiudere l'identificatore con una coppia di *apice* inverso ('). Un altro nome *per l'* *apice inverso è indietro*.

La limitazione della parola chiave riservata si applica anche a qualsiasi forma abbreviata delle parole chiave riservate.

Un elenco di parole chiave riservate ODBC è disponibile all'indirizzo:

- [Parole chiave riservate di ODBC](https://docs.microsoft.com/sql/odbc/reference/appendixes/reserved-keywords).

- Nella *Guida di riferimento per programmatori ODBC*vedere [Appendice C: grammatica SQL](https://docs.microsoft.com/sql/odbc/reference/appendixes/appendix-c-sql-grammar).

