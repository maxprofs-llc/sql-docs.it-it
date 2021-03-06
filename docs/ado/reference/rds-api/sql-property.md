---
title: Proprietà SQL | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- SQL property [RDS]
ms.assetid: e0dabf23-a159-4fe5-a962-3df544a21f5c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f70eba6b5f53be7068708fdd8b139f0add10be90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963345"
---
# <a name="sql-property"></a>Proprietà SQL
Indica la stringa di query utilizzata per recuperare il [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 È possibile impostare la proprietà **SQL** in fase di progettazione in Servizi Desktop remoto [. ](../../../ado/reference/rds-api/datacontrol-object-rds.md)Tag Object dell'oggetto DataControl o in fase di esecuzione nel codice di scripting.  
  
> [!IMPORTANT]
>  A partire da Windows 8 e Windows Server 2012, i componenti server Servizi Desktop remoto non sono più inclusi nel sistema operativo Windows. per altri dettagli, vedere le informazioni di riferimento sulla compatibilità di Windows 8 e [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) . I componenti client Servizi Desktop remoto verranno rimossi in una versione futura di Windows. Evitare di usare questa funzionalità in un nuovo progetto di sviluppo e prevedere interventi di modifica nelle applicazioni in cui è attualmente implementata. Le applicazioni che utilizzano Servizi Desktop remoto devono eseguire la migrazione a [WCF Data Services](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Design time: <PARAM NAME="SQL" VALUE="QueryString">  
Run time: DataControl.SQL = "QueryString"  
```  
  
#### <a name="parameters"></a>Parametri  
 *QueryString*  
 Valore **stringa** che contiene una richiesta di dati SQL valida.  
  
 *DataControl*  
 Variabile oggetto che rappresenta un Servizi Desktop remoto **. Oggetto DataControl** .  
  
## <a name="remarks"></a>Osservazioni  
 In generale, si tratta di un'istruzione SQL (che `"Select * from NewTitles"`usa il dialetto del server di database), ad esempio. Per garantire che i record vengano abbinati e aggiornati accuratamente, una query aggiornabile deve contenere un campo diverso da un campo binario lungo o un campo calcolato.  
  
 La proprietà **SQL** è facoltativa se un oggetto business sul lato server personalizzato recupera i dati per il client.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto DataControl (Servizi Desktop remoto)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà SQL (VBScript)](../../../ado/reference/rds-api/sql-property-example-vbscript.md)   
 [Proprietà Connect (RDS)](../../../ado/reference/rds-api/connect-property-rds.md)   
 [Metodo query (RDS)](../../../ado/reference/rds-api/query-method-rds.md)   
 [Metodo Refresh (RDS)](../../../ado/reference/rds-api/refresh-method-rds.md)   
 [Metodo SubmitChanges (Servizi Desktop remoto)](../../../ado/reference/rds-api/submitchanges-method-rds.md)


