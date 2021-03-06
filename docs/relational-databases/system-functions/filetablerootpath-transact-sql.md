---
title: FileTableRootPath (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- FileTableRootPath_TSQL
- FileTableRootPath
dev_langs:
- TSQL
helpviewer_keywords:
- FileTableRootPath function
ms.assetid: 0cba908a-c85c-4b09-b16a-df1cb333c629
author: rothja
ms.author: jroth
ms.openlocfilehash: 10b4aa19b86530213f852ea90f959a1d7ef6c74f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "72251236"
---
# <a name="filetablerootpath-transact-sql"></a>FileTableRootPath (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il percorso UNC di livello radice per una tabella FileTable specifica o per il database corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
FileTableRootPath ( [ '[schema_name.]FileTable_name' ], @option )  
```  
  
## <a name="arguments"></a>Argomenti  
 *FileTable_name*  
 Nome dell'oggetto FileTable. *FileTable_name* è di tipo **nvarchar**. Questo parametro è facoltativo. Il valore predefinito corrisponde al database corrente. È inoltre facoltativo specificare *schema_name* . È possibile passare NULL per *FileTable_name* per usare il valore del parametro predefinito  
  
 *\@opzione*  
 Espressione Integer che definisce la formattazione del componente server del percorso. l'opzione può avere uno dei valori seguenti: * \@*  
  
|valore|Descrizione|  
|-----------|-----------------|  
|**0**|Restituisce il nome del server convertito in formato NetBIOS, ad esempio:<br /><br /> `\\SERVERNAME\MSSQLSERVER\MyDocumentDatabase`<br /><br /> Si tratta del valore predefinito.|  
|**1**|Restituisce il nome del server senza conversione, ad esempio:<br /><br /> `\\ServerName\MSSQLSERVER\MyDocumentDatabase`|  
|**2**|Restituisce il percorso completo del server, ad esempio:<br /><br /> `\\ServerName.MyDomain.com\MSSQLSERVER\MyDocumentDatabase`|  
  
## <a name="return-type"></a>Tipo restituito  
 **nvarchar(4000)**  
  
 Quando il database appartiene a un gruppo di disponibilità Always On, la funzione **FileTableRootPath** restituisce il nome della rete virtuale (VNN) anziché il nome del computer.  
  
## <a name="general-remarks"></a>Osservazioni generali  
 La funzione **FileTableRootPath** restituisce null quando si verifica una delle condizioni seguenti:  
  
-   Il valore di *FileTable_name* non è valido.  
  
-   Il chiamante non dispone delle autorizzazioni sufficienti per fare riferimento alla tabella specificata o al database corrente.  
  
-   L'opzione FILESTREAM di *Database_Directory* non è impostata per il database corrente.  
  
 Per altre informazioni, vedere [Work with Directories and Paths in FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md).  
  
## <a name="best-practices"></a>Procedure consigliate  
 Per mantenere il codice e le applicazioni indipendenti dal database e dal computer correnti, evitare di scrivere codice basato su percorsi di file assoluti. Ottenere invece il percorso completo di un file in fase di esecuzione usando le funzioni **FileTableRootPath** e **GetFileNamespacePath** insieme, come illustrato nell'esempio seguente. Per impostazione predefinita, la funzione **GetFileNamespacePath** restituisce il percorso relativo del file all'interno del percorso radice per il database.  
  
```sql  
USE MyDocumentDatabase;  
  
@root varchar(100)  
SELECT @root = FileTableRootPath();  
@fullPath = varchar(1000);  
  
SELECT @fullPath = @root + file_stream.GetFileNamespacePath()  
FROM DocumentStore  
WHERE Name = N'document.docx';  
```  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 La funzione **FileTableRootPath** richiede:  
  
-   Autorizzazione SELECT per la tabella FileTable per ottenere il percorso radice di una tabella FileTable specifica.  
  
-   **db_datareader** o versione successiva per ottenere il percorso radice per il database corrente.  
  
## <a name="examples"></a>Esempi  
 Negli esempi seguenti viene illustrato come chiamare la funzione **FileTableRootPath** .  
  
```  
USE MyDocumentDatabase;  
-- returns "\\MYSERVER\MSSQLSERVER\MyDocumentDatabase"  
SELECT FileTableRootPath();  
  
-- returns "\\MYSERVER\MSSQLSERVER\MyDocumentDatabase\MyFileTable"  
SELECT FileTableRootPath(N'dbo.MyFileTable');  
  
-- returns "\\MYSERVER\MSSQLSERVER\MyDocumentDatabase\MyFileTable"  
SELECT FileTableRootPath(N'MyFileTable');  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Usare directory e percorsi in FileTable](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)  
  
  
