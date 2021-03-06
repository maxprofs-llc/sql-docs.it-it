---
title: 'Passaggio 2: inizializzare la casella di riepilogo principale | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8ad89d806f8a6774cb0fe2de056e30fd274a517c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924082"
---
# <a name="step-2-initialize-the-main-list-box"></a>Passaggio 2: Inizializzare la casella di riepilogo Main
Per dichiarare oggetti record e recordset globali, inserire il codice seguente in (General) (dichiarazioni) per Form1:  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 Questo codice dichiara i riferimenti a oggetti globali per gli oggetti record e recordset che verranno usati più avanti in questo scenario.  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>Per connettersi a un URL e popolare lstMain  
 Inserire il codice seguente nel gestore dell'evento di caricamento del form per Form1:  
  
```  
Private Sub Form_Load()  
    Set grec = New Record  
    Set grs = New Recordset  
    grec.Open "", "URL=https://servername/foldername/", , _  
        adOpenIfExists Or adCreateCollection  
    Set grs = grec.GetChildren  
    While Not grs.EOF  
        lstMain.AddItem grs(0)  
        grs.MoveNext  
    Wend  
End Sub  
```  
  
 Questo codice crea un'istanza degli oggetti record e recordset globali. L'oggetto record, `grec`, viene aperto con un URL specificato come ActiveConnection. Se l'URL esiste, viene aperto; Se non esiste già, viene creato. Si noti che è necessario sostituire<https://servername/foldername/>"" con un URL valido dall'ambiente.  
  
 L'oggetto recordset, `grs`, viene aperto negli elementi figlio del record `grec`. Viene `lstMain` quindi popolato con i nomi di file delle risorse pubblicate nell'URL.  
  
## <a name="see-also"></a>Vedere anche  
 [Scenario di pubblicazione Internet](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Passaggio 1: configurare il progetto di Visual Basic](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Passaggio 3: Popolare la casella di riepilogo Fields](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
