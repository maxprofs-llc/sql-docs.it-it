---
title: STMLineFromWKB (tipo di dati geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STMLineFromWKB (geometry Data Type)
- STMLineFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMLineFromWKB (geometry Data Type)
ms.assetid: 00a8a8e7-11d6-47a0-b971-00e60f7877ce
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 47fd42c05e5d370172ab648b54689f732a7ade34
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "67894726"
---
# <a name="stmlinefromwkb-geometry-data-type"></a>STMLineFromWKB (tipo di dati geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce un'istanza **geometryMultiLineString** di una rappresentazione WKB (Well-Known Binary) OGC (Open Geospatial Consortium).
  
## <a name="syntax"></a>Sintassi  
  
```  
  
STMLineFromWKB ( 'WKB_multilinestring' , SRID )  
```  
  
## <a name="arguments"></a>Argomenti  
 *WKB_multilinestring*  
 Rappresentazione WKB dell'istanza **geometryMultiLineString** da restituire. *WKB_multilinestring* è un'espressione **varbinary(max)** .  
  
 *SRID*  
 Espressione **int** che rappresenta l'identificatore SRID dell'istanza **geometryMultiLineString** da restituire.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geometry**  
  
 Tipo CLR restituito: **SqlGeometry**  
  
 Tipo OGC: **MultiLineString**  
  
## <a name="remarks"></a>Osservazioni  
 Questo metodo genererà un'eccezione **FormatException** se l'input non è formattato in modo corretto.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene utilizzato il metodo `STMLineFromWKB()` per creare un'istanza `geometry`.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::STMLineFromWKB(0x0105000000020000000102000000020000000000000000005940000000000000594000000000000069400000000000006940010200000003000000000000000000084000000000000010400000000000001C40000000000000204000000000000024400000000000002440, 0);  
SELECT @g.STAsText();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi di geometria statici OGC](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

