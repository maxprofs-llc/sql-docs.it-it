---
title: '&lt;= (Minore o uguale a) (DMX) | Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8d88c4b986ab05ab3bd9e90308257dd94b9e6abf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68008338"
---
# <a name="lt-less-than-or-equal-to-dmx"></a>&lt;= (Minore o uguale a) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un'operazione di confronto che determina se il valore di un'espressione DMX (Data Mining Extensions) è minore o uguale a quello di un'altra espressione DMX.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DMX_Expression <= DMX_Expression  
```  
  
#### <a name="parameters"></a>Parametri  
 *DMX_Expression*  
 Espressione DMX valida.  
  
## <a name="return-value"></a>Valore restituito  
 Valore booleano che contiene TRUE se entrambi i parametri sono non Null e il valore del primo parametro è minore o uguale a quello del secondo. Tale valore booleano contiene FALSE se entrambi i parametri sono non Null e il valore del primo parametro è maggiore di quello del secondo. Il valore booleano contiene un valore Null se un parametro o entrambi restituiscono un valore Null.  
  
## <a name="see-also"></a>Vedere anche  
 [Operatori di confronto &#40;DMX&#41;](../dmx/operators-comparison.md)   
 [Guida di riferimento agli operatori DMX&#41; &#40;di Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Operatori &#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
