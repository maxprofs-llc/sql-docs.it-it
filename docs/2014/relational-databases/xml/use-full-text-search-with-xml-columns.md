---
title: Usare la ricerca full-text con colonne XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xml columns [full-text search]
- indexes [full-text search]
ms.assetid: 8096cfc6-1836-4ed5-a769-a5d63b137171
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 897002d437dcee8a6c64750f964c957c18a077f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "63193257"
---
# <a name="use-full-text-search-with-xml-columns"></a>Utilizzo della ricerca full-text con colonne XML
  Sulle colonne XML è possibile creare un indice full-text che indicizza il contenuto dei valori XML, ma ignora i markup XML. I tag degli elementi vengono utilizzati come limiti dei token. Gli elementi riportati di seguito sono indicizzati:  
  
-   Contenuto degli elementi XML.  
  
-   Solo il contenuto degli attributi XML dell'elemento di livello principale, a meno che non si tratti di valori numerici.  
  
 In alcuni casi è possibile combinare la ricerca full-text con l'indicizzazione XML, procedendo nel modo descritto di seguito.  
  
1.  Filtrare innanzitutto i valori XML desiderati utilizzando la ricerca full-text SQL.  
  
2.  Eseguire quindi una query sui valori XML che utilizzano l'indice XML sulla colonna XML.  
  
## <a name="example-combining-full-text-search-with-xml-querying"></a>Esempio: combinazione di ricerca full-text e query XML  
 Dopo la creazione dell'indice full-text sulla colonna XML è possibile utilizzare la query seguente per verificare se un valore XML contiene la parola "custom" nel titolo di un libro:  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'custom')   
AND    xCol.exist('/book/title/text()[contains(.,"custom")]') =1  
```  
  
 Il metodo **contains()** usa l'indice full-text per creare un subset dei valori XML contenenti la parola "custom", in qualunque punto del documento. La clausola **exist()** garantisce che la parola "custom" compaia nel titolo di un libro.  
  
 Una ricerca full-text che usa **contains()** a la query XQuery **contains()** hanno semantiche diverse. Nel secondo caso si tratta di una corrispondenza tra sottostringhe, mentre nel primo si tratta di una corrispondenza tra token basata sullo stemming. Quindi, se si esegua la ricerca della stringa che include la parola "run" nel titolo, le corrispondenze includeranno le parole "run", "runs" e "running", perché sono soddisfatti sia i criteri della ricerca full-text **contains()** che quelli della query XQuery **contains()** . La query, tuttavia, non individua la parola "customizable" nel titolo, perché la ricerca full-text **contains()** non riesce, ma la query XQuery **contains()** è soddisfatta. In genere, per le semplici corrispondenze di sottostringhe è consigliabile rimuovere la clausola **contains()** della ricerca full-text.  
  
 Inoltre, la ricerca full-text usa lo stemming delle parole, mentre la query XQuery **contains()** richiede una corrispondenza letterale. Tale differenza è illustrata nell'esempio successivo.  
  
## <a name="example-full-text-search-on-xml-values-using-stemming"></a>Esempio: ricerca full-text su valori XML tramite stemming  
 Il controllo eseguito dalla query XQuery **contains()** nell'esempio precedente non può essere in genere eliminato. Considerare la query seguente:  
  
```  
SELECT *   
FROM   T   
WHERE  CONTAINS(xCol,'run')   
```  
  
 La parola "ran" nel documento soddisfa la condizione di ricerca a causa dello stemming. Se si utilizza una query XQuery, inoltre, il contesto della ricerca non viene verificato.  
  
 Quando i valori XML vengono scomposti tramite AXSD in colonne relazionali con indicizzazione full-text, le query XPath sulla visualizzazione XML non eseguono una ricerca full-text sulle tabelle sottostanti.  
  
## <a name="see-also"></a>Vedere anche  
 [Indici XML &#40;SQL Server&#41;](xml-indexes-sql-server.md)  
  
  
