---
title: Supporto di FOR XML per i tipi di dati definiti dall'utente (UDT) | Microsoft Docs
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
ms.openlocfilehash: 34764dcdc6b8f0fa91ce4a79ef6dde8cb8eaacc1
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "75244775"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>Supporto di FOR XML per i tipi di dati definiti dall'utente (UDT)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  FOR XML non supporta tipi di dati definiti dall'utente Common Language Runtime (CLR).  
  
 Per utilizzare FOR XML con tipi di dati definiti dall'utente CLR, assicurarsi che il tipo di dati abbia una serializzazione XML e utilizzare un cast esplicito per XML nella clausola scelta FOR XML.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto di FOR XML per vari tipi di dati di SQL Server](../../relational-databases/xml/for-xml-support-for-various-sql-server-data-types.md)  
  
  
