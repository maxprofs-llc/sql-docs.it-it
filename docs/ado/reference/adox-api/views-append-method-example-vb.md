---
title: Esempio di metodo Append views (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Append method [ADOX]
ms.assetid: b5b4c082-ac29-4f49-a8b8-e21b554c9b0d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 50b24a21c54fcf23dba0748dfba31a99b5bbb1ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67964797"
---
# <a name="views-append-method-example-vb"></a>Esempio del metodo Append di Views (VB)
Nel codice seguente viene illustrato come utilizzare un oggetto [Command](../../../ado/reference/ado-api/command-object-ado.md) e il metodo [Append](../../../ado/reference/adox-api/append-method-adox-views.md) della raccolta [views](../../../ado/reference/adox-api/views-collection-adox.md) per creare una nuova visualizzazione nell'origine dati sottostante.  
  
```  
' BeginCreateViewVB  
Sub Main()  
    On Error GoTo CreateViewError  
  
    Dim cmd As New ADODB.Command  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Catalog  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Create the command representing the view.  
    cmd.CommandText = "Select * From Customers"  
  
    ' Create the new View  
    cat.Views.Append "AllCustomers", cmd  
  
    'Clean up  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Set cmd = Nothing  
    Exit Sub  
  
CreateViewError:  
  
    Set cat = Nothing  
    Set cmd = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCreateViewVB  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Metodo Append (viste ADOX)](../../../ado/reference/adox-api/append-method-adox-views.md)   
 [Oggetto Catalog (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Oggetto View (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)   
 [Raccolta Views (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
