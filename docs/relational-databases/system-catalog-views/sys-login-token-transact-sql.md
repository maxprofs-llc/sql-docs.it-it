---
title: sys. login_token (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- login_token_TSQL
- sys.login_token_TSQL
- sys.login_token
- login_token
dev_langs:
- TSQL
helpviewer_keywords:
- sys.login_token catalog view
- logins [SQL Server], security tokens
- tokens [SQL Server]
ms.assetid: 86e06938-9d0a-44e5-99e2-55c8ef5f2f84
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: fb396d47da69724d16c0d72e1373527f9c5e700f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68102432"
---
# <a name="syslogin_token-transact-sql"></a>sys.login_token (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni entità server appartenente al token dell'account di accesso.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**principal_id**|**int**|ID dell'entità. Questo valore è univoco all'interno del server.|  
|**SID**|**varbinary(85)**|ID di sicurezza dell'entità. Se si tratta di un'entità di Windows, **SID** = SID di Windows. Se viene eseguito il mapping dell'account di accesso a un certificato, **SID** = GUID del certificato.|  
|**nome**|**nvarchar(128)**|Nome dell'entità. Questo valore è univoco all'interno del server.|  
|**tipo**|**nvarchar(128)**|Descrizione del tipo dell'entità. Viene eseguito il mapping di tutti i tipi a **SID**. Il valore può essere uno dei seguenti:<br /><br /> SQL LOGIN<br /><br /> WINDOWS LOGIN<br /><br /> WINDOWS GROUP<br /><br /> SERVER ROLE<br /><br /> LOGIN MAPPED TO CERTIFICATE<br /><br /> LOGIN MAPPED TO ASYMMETRIC KEY<br /><br /> CERTIFICATE<br /><br /> ASYMMETRIC KEY|  
|**utilizzo**|**nvarchar(128)**|Specifica che l'entità partecipa alla valutazione di autorizzazioni GRANT or DENY o funge da autenticatore.<br /><br /> I valori validi sono i seguenti:<br /><br /> GRANT OR DENY<br /><br /> DENY ONLY<br /><br /> AUTHENTICATOR|  
  
## <a name="see-also"></a>Vedere anche  
 [sys. user_token &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-user-token-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sys. database_principals &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [Entità &#40;motore di database&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
