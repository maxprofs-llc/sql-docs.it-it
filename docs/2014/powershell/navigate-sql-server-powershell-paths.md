---
title: Spostarsi all'interno dei percorsi di SQL Server PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: d68aca48-d161-45ed-9f4f-14122ed30218
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce1e3a2088214c222cd2c2e84fc333f4993b7a6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72797807"
---
# <a name="navigate-sql-server-powershell-paths"></a>Spostarsi all'interno dei percorsi di SQL Server PowerShell
  Il provider [!INCLUDE[ssDE](../includes/ssde-md.md)] PowerShell espone il set di oggetti in un'istanza di SQL Server in una struttura analoga a un percorso di file. È possibile utilizzare cmdlet di Windows PowerShell per spostarsi all'interno del percorso del provider e creare unità personalizzate per rendere più breve il percorso da digitare.  
  
## <a name="before-you-begin"></a>Prima di iniziare  
 Windows PowerShell implementa cmdlet per spostarsi all'interno della struttura del percorso che rappresenta la gerarchia di oggetti supportati da un provider PowerShell. Quando si passa a un nodo nel percorso, è possibile utilizzare altri cmdlet per eseguire operazioni di base sull'oggetto corrente. Poiché vengono utilizzati frequentemente, i cmdlet dispongono di alias brevi e canonici. È inoltre presente un set di alias che esegue il mapping dei cmdlet a comandi simili del prompt dei comandi e un altro set per i comandi della shell di UNIX.  
  
 Il provider [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] implementa un subset di cmdlet del provider, illustrato nella tabella seguente.  
  
|Cmdlet|Alias canonico|Alias cmd|Alias di shell di UNIX|Descrizione|  
|------------|---------------------|---------------|----------------------|-----------------|  
|**Get-Location**|**gl**|**pwd**|**pwd**|Consente di ottenere il nodo corrente.|  
|`Set-Location`|**SL**|**CD, ChDir**|**CD, ChDir**|Consente di modificare il nodo corrente.|  
|**Get-ChildItem**|**GCI**|**dir**|**LS**|Consente di visualizzare un elenco degli oggetti archiviati nel nodo corrente.|  
|**Get-Item**|**gi**|||Restituisce le proprietà dell'elemento corrente.|  
|**Rinomina-elemento**|**RNI**|**RN**|**Ren**|Consente di rinominare un oggetto.|  
|**Remove-Item**|**istanza riservata**|**CANC, Rd**|**RM, rmdir**|Consente di rimuovere un oggetto.|  
  
> [!IMPORTANT]  
>  Alcuni identificatori (nomi di oggetto) di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contengono caratteri non supportati da Windows PowerShell nei nomi dei percorsi. Per altre informazioni sull'uso dei nomi che contengono questi caratteri, vedere [Identificatori di SQL Server in PowerShell](sql-server-identifiers-in-powershell.md).  
  
### <a name="sql-server-information-returned-by-get-childitem"></a>Informazioni su SQL Server restituite da Get-ChildItem  
 Le informazioni restituite da **Get-ChildItem** (o dai relativi alias **dir** e **ls** ) dipendono dalla posizione in un percorso SQLSERVER.  
  
|Posizione nel percorso|Risultati di Get-ChildItem|  
|-------------------|----------------------------|  
|SQLSERVER:\SQL|Restituisce il nome del computer locale. Se è stato utilizzato SMO o WMI per connettersi a istanze del [!INCLUDE[ssDE](../includes/ssde-md.md)] in altri computer, vengono elencati anche tali computer.|  
|SQLSERVER:\SQL\\*NomeComputer*|Elenco delle istanze di [!INCLUDE[ssDE](../includes/ssde-md.md)] nel computer.|  
|SqlServer: \ SQL\\*nomecomputer*\\*NomeIstanza*|Elenco dei tipi di oggetto di primo livello nell'istanza, ad esempio Endpoint, Certificati e Database.|  
|Nodo della classe di oggetto, ad esempio Database|Elenco di oggetti del tipo, ad esempio l'elenco di database: master, model, AdventureWorks2008R2.|  
|Nodo del nome dell'oggetto, ad esempio AdventureWorks2012|Elenco dei tipi di oggetto contenuti all'interno dell'oggetto. Per un database, ad esempio, vengono elencati tipi di oggetto come tabelle e viste.|  
  
 Per impostazione predefinita, **Get-ChildItem** non elenca oggetti di sistema. Usare il parametro *Force* per visualizzare gli oggetti di sistema, ad esempio gli oggetti nello schema **sys** .  
  
### <a name="custom-drives"></a>Unità personalizzate  
 Windows PowerShell consente agli utenti di definire unità virtuali, definite come unità di PowerShell. Per tali unità viene eseguito il mapping ai nodi iniziali di un'istruzione di percorso. Tali unità vengono in genere utilizzate per abbreviare percorsi digitati con frequenza. I percorsi SQLSERVER: possono diventare lunghi, occupando spazio nella finestra di Windows PowerShell e richiedendo molta digitazione. Se si prevede di lavorare molto in un particolare nodo del percorso, è possibile definire un'unità di Windows PowerShell personalizzata di cui è stato eseguito il mapping a tale nodo.  
  
## <a name="use-powershell-cmdlet-aliases"></a>Utilizzare alias di cmdlet di PowerShell  
 **Usare un alias di cmdlet**  
  
-   Anziché digitare il nome completo di un cmdlet, digitare un alias più breve o uno con mapping a un comando comune del prompt dei comandi.  
  
### <a name="alias-example-powershell"></a>Esempio di alias (PowerShell)  
 È ad esempio possibile utilizzare uno dei set di cmdlet o alias seguenti per recuperare un elenco delle istanze di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] disponibili passando alla cartella SQLSERVER:\SQL e richiedendo l'elenco di elementi figlio per la cartella:  
  
```powershell
## Shows using the full cmdet name.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## Shows using canonical aliases.  
sl SQLSERVER:\SQL  
gci  
  
## Shows using command prompt aliases.  
cd SQLSERVER:\SQL  
dir  
  
## Shows using Unix shell aliases.  
cd SQLSERVER:\SQL  
ls  
```  
  
## <a name="use-get-childitem"></a>Utilizzare Get-ChildItem  

### <a name="return-information-by-using-get-childitem"></a>Restituire informazioni utilizzando Get-ChildItem
  
1.  Passare al nodo per il quale si desidera un elenco di childrem  
  
2.  Eseguire Get-ChildItem per ottenere l'elenco.  
  
### <a name="get-childitem-example-powershell"></a>Esempio di Get-ChildItem (PowerShell)  
 In questi esempi sono illustrate le informazioni restituite da Get-ChildItem per i nodi diversi in un percorso del provider SQL Server.  
  
```powershell
## Return the current computer and any computer  
## to which you have made a SQL or WMI connection.  
Set-Location SQLSERVER:\SQL  
Get-ChildItem  
  
## List the instances of the Database Engine on the local computer.  
Set-Location SQLSERVER:\SQL\localhost  
Get-ChildItem  
  
## Lists the categories of objects available in the  
## default instance on the local computer.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT  
Get-ChildItem  
  
## Lists the databases from the local default instance.  
## The force parameter is used to include the system databases.  
Set-Location SQLSERVER:\SQL\localhost\DEFAULT\Databases  
Get-ChildItem -force  
```  
  
## <a name="create-a-custom-drive"></a>Creare un'unità personalizzata  

### <a name="create-and-use-a-custom-drive"></a>Creare e utilizzare un'unità personalizzata
  
1.  Utilizzare `New-PSDrive` per definire un'unità personalizzata. Utilizzare il parametro `Root` per specificare il percorso rappresentato dal nome di unità personalizzato.  
  
2.  Fare riferimento al nome di unità personalizzata nei cmdlet di navigazione come `Set-Location`.  
  
### <a name="custom-drive-example-powershell"></a>Esempio di unità personalizzata (PowerShell)  
 Questo esempio crea un'unità virtuale denominata AWDB con mapping al nodo di una copia distribuita del database di esempio di AdventureWorks2012. L'unità virtuale è utilizzata quindi per passare a una tabella nel database.  
  
```powershell
## Create a new virtual drive.  
New-PSDrive -Name AWDB -Root SQLSERVER:\SQL\localhost\DEFAULT\Databases\AdventureWorks2012  
  
## Use AWDB: to navigate to a specific table.  
Set-Location AWDB:\Tables\Purchasing.Vendor  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Provider di SQL Server PowerShell](sql-server-powershell-provider.md)   
 [Usare i percorsi di SQL Server PowerShell](work-with-sql-server-powershell-paths.md)   
 [Converti URN in percorsi di provider SQL Server](../database-engine/convert-urns-to-sql-server-provider-paths.md)   
 [SQL Server PowerShell](sql-server-powershell.md)  
