---
title: Creare query di eliminazione
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- row removal [SQL Server], Delete query
- Delete query
- queries [SQL Server], types
- removing rows
- removing data
- data deletions [SQL Server]
- deleting rows
- deleting data
ms.assetid: 0db3af43-1ec4-48c8-b769-2bb9c76d3434
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: cb40fee1f7176c9d1fe64e22cda220513f88d58e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254366"
---
# <a name="create-delete-queries-visual-database-tools"></a>Creazione di query (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Per eliminare tutte le righe di una tabella, è possibile utilizzare una query di eliminazione.  
  
> [!NOTE]  
> Se si eliminano tutte le righe di una tabella, non verrà eliminata la tabella, ma solo i dati in essa contenuti. Per eliminare una tabella da un database, fare clic su di essa con il pulsante destro del mouse in Esplora oggetti, quindi scegliere **Elimina**.  
  
Quando si crea una query di eliminazione, nel riquadro Criteri vengono visualizzate le opzioni disponibili per l'eliminazione delle righe. Poiché la query di eliminazione non consente la visualizzazione di dati, vengono eliminate le colonne Output, Ordina per e Ordinamento. Vengono inoltre rimosse le caselle di controllo accanto ai nomi di colonna nel rettangolo che rappresenta la tabella o l'oggetto con valori di tabella, in quanto non è possibile specificare singole colonne da eliminare.  
  
Se in Progettazione query e Progettazione viste non è possibile eliminare una o più righe, non ne verrà eliminata alcuna e un messaggio indicherà in quali righe sono contenute informazioni che non possono essere eliminate dal database.  
  
> [!CAUTION]  
> Una volta eseguita, la query di eliminazione non potrà essere annullata. È dunque opportuno eseguire una copia di backup dei dati prima di eseguire la query di eliminazione.  
  
### <a name="to-create-a-delete-query"></a>Per creare una query di eliminazione  
  
1.  Aggiungere al riquadro Diagramma la tabella da cui eliminare le righe.  
  
2.  Scegliere **Modifica tipo** dal menu **Progettazione query**, quindi **Elimina**. **Nota** Se nel riquadro Diagramma sono visualizzate più tabelle quando si inizia a creare la query di eliminazione, in Progettazione query e Progettazione viste verrà visualizzata la finestra di dialogo [Elimina tabella](../../ssms/visual-db-tools/delete-table-dialog-box-visual-database-tools.md) , in cui è necessario specificare il nome della tabella contenente le righe da eliminare.  
  
Quando si esegue una query di eliminazione, non viene restituito alcun risultato nel [riquadro Risultati](../../ssms/visual-db-tools/results-pane-visual-database-tools.md). Viene invece visualizzato un messaggio che indica il numero di righe eliminate.  
  
## <a name="see-also"></a>Vedere anche  
[Tipi di query supportati &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Procedure per la progettazione di query e viste &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
