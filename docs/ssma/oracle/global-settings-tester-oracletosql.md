---
title: Impostazioni globali (tester) (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4acc0f2a-85ba-4c99-856a-89030f5c418e
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: f7e421774d3a09622835b181d5c053c994e905ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264407"
---
# <a name="global-settings-tester-oracletosql"></a>Impostazioni globali (tester) (OracleToSQL)
Utilizzare la pagina tester della finestra di dialogo **Impostazioni globali** per specificare le impostazioni per SSMA tester.  
  
Per accedere alle impostazioni del tester, scegliere **Impostazioni globali**dal menu **strumenti** e fare clic su **tester** nella parte inferiore del riquadro sinistro.  
  
## <a name="options"></a>Opzioni  
**Analisi oggetto testabile**  
Questa impostazione specifica se eseguire l'analisi degli oggetti testabili. Selezionare **Sì** se si vuole che SSMA tester analizzi e controlli automaticamente gli oggetti dipendenti. Il set di opzioni predefinito è **Sì**.  
  
Per questa impostazione sono disponibili le opzioni seguenti:  
  
1.  Sì  
  
2.  No  
  
**Modalità di salvataggio delle tabelle ausiliarie**  
Questa impostazione specifica come salvare le tabelle ausiliarie interne create durante l'esecuzione del test case. Per questa particolare impostazione è possibile impostare le opzioni seguenti:  
  
1.  Elimina sempre  
  
2.  Salva sempre  
  
3.  Salva se il confronto tabella non è riuscito  
  
4.  Richiedi all'utente se il confronto tra tabelle non è riuscito  
  
Il set di opzioni predefinito è: **Always Delete**.  
  
**Eseguire il rollback dei dati**  
Questa impostazione specifica se eseguire un'operazione di rollback dopo l'esecuzione di ogni test case. Il set di opzioni predefinito è **No**.  
  
Per questa impostazione sono disponibili le opzioni seguenti:  
  
1.  Sì  
  
2.  No  
  
**Interrompi esecuzione del test dopo il primo errore**  
Questa impostazione specifica se arrestare la test case corrente in esecuzione, se si è verificato un errore durante l'esecuzione. Il set di opzioni predefinito è **Sì**.  
  
Per questa impostazione sono disponibili le opzioni seguenti:  
  
1.  Sì  
  
2.  No  
  
## <a name="see-also"></a>Vedere anche  
[Completamento della preparazione del test case &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
