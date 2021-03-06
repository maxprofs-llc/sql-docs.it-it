---
title: sp_helplogins (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helplogins_TSQL
- sp_helplogins
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helplogins
ms.assetid: f9ad3767-5b9f-420d-8922-b637811404f7
author: stevestein
ms.author: sstein
ms.openlocfilehash: b4c3d6ded5d85e5d38556792aaa7ea71dd9f42fa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68122446"
---
# <a name="sp_helplogins-transact-sql"></a>sp_helplogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sugli account di accesso e sugli utenti corrispondenti in ogni database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento") [Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_helplogins [ [ @LoginNamePattern = ] 'login' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @LoginNamePattern = ] 'login'`Nome dell'account di accesso. *login* è di **tipo sysname**e il valore predefinito è null. Se specificato, deve esistere un *account di accesso* . Se *login* viene omesso, vengono restituite informazioni su tutti gli account di accesso.  
  
## <a name="return-code-values"></a>Valori del codice restituito  
 0 (operazione completata) o 1 (operazione non riuscita)  
  
## <a name="result-sets"></a>Set di risultati  
 Il primo report contiene le informazioni su ogni account di accesso specificato, come illustrato nella tabella seguente.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Nome dell'account di accesso.|  
|**SID**|**varbinary(85)**|ID di sicurezza (SID) dell'account di accesso.|  
|**DefDBName**|**sysname**|Database predefinito utilizzato da **LoginName** per la connessione a un'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]di.|  
|**DefLangName**|**sysname**|Lingua predefinita utilizzata da **LoginName**.|  
|**Auser**|**char (5)**|Yes = **LoginName** è associato a un nome utente in un database.<br /><br /> No = **LoginName** non è associato a un nome utente.|  
|**ARemote**|**carattere (7)**|Yes = **LoginName** è associato a un account di accesso remoto.<br /><br /> No = **LoginName** non dispone di un account di accesso associato.|  
  
 Il secondo report contiene informazioni sugli utenti sui quali viene eseguito il mapping a ogni account di accesso e le appartenenze al ruolo dell'account di acceso, come illustrato nella tabella seguente.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**LoginName**|**sysname**|Nome dell'account di accesso.|  
|**DBName**|**sysname**|Database predefinito utilizzato da **LoginName** per la connessione a un'istanza [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]di.|  
|**Nome utente**|**sysname**|Account utente a cui è stato eseguito il mapping di **LoginName** in **dbname**e i ruoli di cui è membro **LoginName** in **dbname**.|  
|**UserOrAlias**|**carattere (8)**|Membro = **username** è un ruolo.<br /><br /> User = **username** è un account utente.|  
  
## <a name="remarks"></a>Osservazioni  
 Prima di rimuovere un account di accesso, utilizzare **sp_helplogins** per identificare gli account utente di cui è stato eseguito il mapping all'account di accesso.  
  
## <a name="permissions"></a>Autorizzazioni  
 È richiesta l'appartenenza al ruolo predefinito del server **securityadmin** .  
  
 Per identificare tutti gli account utente mappati a un account di accesso specifico, **sp_helplogins** necessario controllare tutti i database all'interno del server. Pertanto, per ogni database nel server, è necessario che sia soddisfatta almeno una delle seguenti condizioni:  
  
-   L'utente che esegue **sp_helplogins** dispone dell'autorizzazione per accedere al database.  
  
-   L'account utente **Guest** è abilitato nel database.  
  
 Se **sp_helplogins** non è in grado di accedere a un database, **sp_helplogins** restituirà quante più informazioni possibile e visualizzerà il messaggio di errore 15622.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente vengono restituite informazioni sull'account di accesso `John`.  
  
```  
EXEC sp_helplogins 'John';  
GO  
  
LoginName SID                        DefDBName DefLangName AUser ARemote   
--------- -------------------------- --------- ----------- ----- -------   
John      0x23B348613497D11190C100C  master    us_english  yes   no  
  
(1 row(s) affected)  
  
LoginName   DBName   UserName   UserOrAlias   
---------   ------   --------   -----------   
John        pubs     John       User          
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sicurezza &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_helpdb &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpuser &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
