---
title: SELECT FROM &lt;Model&gt; (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5611ce3da4f12bca5cb271cabe8af3e149dcbf35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67928335"
---
# <a name="select-from-ltmodelgt-dmx"></a>SELECT FROM &lt;Model&gt; (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue un prediction join vuoto e restituisce il valore o i valori più probabili per le colonne specificate. Per creare la stima viene utilizzato solo il contenuto del modello di data mining.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
SELECT <expression list> [TOP <n>] FROM <model>   
[WHERE <condition list>]   
[ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Argomenti  
 *elenco di espressioni*  
 Elenco delimitato da virgole contenente espressioni o colonne di tipo PREDICT o PREDICT ONLY.  
  
 *n*  
 Facoltativa. Valore intero mediante il quale viene specificato il numero di righe da restituire.  
  
 *model*  
 Identificatore del modello.  
  
 *Elenco condizioni*  
 Facoltativa. Condizioni per limitare i valori restituiti dall'elenco di colonne.  
  
 *espressione*  
 Facoltativa. Espressione che restituisce un valore scalare.  
  
## <a name="remarks"></a>Osservazioni  
 Le colonne nell' *elenco di espressioni* devono essere definite come Predict o Predict Only oppure in relazione a una colonna stimabile.  
  
## <a name="naive-bayes-example"></a>Esempio sull'algoritmo Naive Bayes  
 Nell'esempio seguente viene eseguito un prediction join vuoto sulla colonna Bike Buyer e viene restituito lo stato più probabile nel modello di data mining TM_Naive_Bayes.  
  
```  
SELECT ([Bike Buyer]) FROM [TM_Naive_Bayes]  
```  
  
## <a name="time-series-example"></a>Esempio sull'algoritmo Time Series  
 Nell'esempio seguente viene eseguita una stima sulla colonna Amount nel modello Forecasting e vengono restituiti i quattro intervalli temporali successivi. La colonna Model Region combina modelli di biciclette e regioni in un singolo identificatore. La query utilizza la funzione [PredictTimeSeries &#40;DMX&#41;](../dmx/predicttimeseries-dmx.md) per eseguire la stima.  
  
```  
SELECT [Model Region], PredictTimeSeries(Amount, 4)   
FROM Forecasting  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SELEZIONARE &#40;DMX&#41;](../dmx/select-dmx.md)   
 [Le estensioni di data mining &#40;DMX&#41; le istruzioni di definizione dei dati](../dmx/dmx-statements-data-definition.md)   
 [Le estensioni di data mining &#40;DMX&#41; le istruzioni di manipolazione dei dati](../dmx/dmx-statements-data-manipulation.md)   
 [Guida di riferimento alle istruzioni DMX&#41; &#40;di Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
