---
title: Reduce (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Reduce_TSQL
- Reduce
dev_langs:
- TSQL
helpviewer_keywords:
- Reduce method
ms.assetid: c5dfa8c1-6764-41d8-9150-f3cb30633d3e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 0713ba46d6d99a8ed325d37d11396b46618f92ab
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68101761"
---
# <a name="reduce-geography-data-type-"></a>Reduce (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un'approssimazione dell'istanza **geography** specificata prodotta eseguendo l'algoritmo Douglas-Peucker sull'istanza con la tolleranza specificata.  
  
 Questo metodo con tipo di dati **geography** supporta le istanze **FullGlobe** o le istanze spaziali con dimensioni maggiori di un emisfero.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.Reduce ( tolerance )  
```  
  
## <a name="arguments"></a>Argomenti  
  
|||  
|-|-|  
|Termine|Definizione|  
|*tolerance*|Valore di tipo **float**. *tolerance* è la tolleranza per l'input dell'algoritmo Douglas-Peucker. *tolerance* deve essere un numero positivo.|  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Osservazioni  
 Per i tipi relativi a una raccolta, questo algoritmo opera indipendentemente su ogni tipo **geography** contenuto nell'istanza. Questo algoritmo non modifica le istanze **Point**.  
  
 Questo metodo prova a mantenere gli endpoint delle istanze **LineString**, ma il tentativo può non riuscire se si vuole mantenere un risultato valido.  
  
 Se `Reduce()` viene chiamato con un valore negativo, il metodo genera l'eccezione **ArgumentException**. Le tolleranze utilizzate in `Reduce()` devono essere numeri positivi.  
  
 L'algoritmo Douglas-Peucker può essere usato su ogni curva o cerchio nell'istanza **geography** rimuovendo tutti i punti ad eccezione di quello iniziale e di quello finale. Ogni punto rimosso viene quindi aggiunto nuovamente, a partire da quello esterno più lontano, fino a quando nessun punto ha una distanza dal risultato superiore al valore *tolerance*. Poiché deve essere garantito un risultato valido, se necessario il risultato viene reso valido.  
  
 In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] questo metodo è stato esteso alle istanze **FullGlobe**.  
  
 Il metodo non è preciso.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `LineString` e viene utilizzato il metodo `Reduce()` per semplificarla.  
  
```  
DECLARE @g geography = 'LineString(120 45, 120.1 45.1, 199.9 45.2, 120 46)'  
SELECT @g.Reduce(10000).ToString()  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi estesi sulle istanze geografiche](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
