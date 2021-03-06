---
title: sys. availability_group_listeners (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_group_listeners_TSQL
- sys.availability_group_listeners
- sys.availability_group_listeners_TSQL
- availability_group_listeners
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_group_listeners catalog view
- Availability Groups [SQL Server], listeners
ms.assetid: b5e7d1fb-3ffb-4767-8135-604c575016b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b363e410f35eb7880933520dd1dbf47f258b651e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041066"
---
# <a name="sysavailability_group_listeners-transact-sql"></a>sys.availability_group_listeners (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Per ogni gruppo di disponibilità Always On, restituisce zero righe, che indica che nessun nome di rete è associato al gruppo di disponibilità, o restituisce una riga per ogni configurazione del listener del gruppo di disponibilità nel cluster WSFC (Windows Server Failover Clustering). In questa vista viene visualizzata la configurazione in tempo reale raccolta dal cluster.  
  
> [!NOTE]  
>  Questa vista del catalogo non descrive i dettagli di una configurazione IP, definita nel cluster WSFC.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|ID del gruppo di disponibilità (**group_id**) da [sys. availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md).|  
|**listener_id**|**nvarchar (36)**|GUID dall'ID della risorsa del cluster.|  
|**dns_name**|**nvarchar (63)**|Nome di rete configurato (nome host) del listener del gruppo di disponibilità.|  
|**porta**|**int**|Numero di porta TCP configurato per il listener del gruppo di disponibilità.<br /><br /> Null = Il listener è stato configurato all'esterno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e il numero di porta non è stato aggiunto al gruppo di disponibilità. Per aggiungere la porta, Modify l'opzione modifica listener dell'istruzione [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|**is_conformant**|**bit**|Se questa configurazione IP è conforme, uno di:<br /><br /> 1 = Il listener è conforme. Tra gli indirizzi IP (Internet Protocol) esistono solo relazioni "OR". La *conformità* comprende ogni configurazione IP creata dall'istruzione [create Availability Group](../../t-sql/statements/create-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] . Inoltre, se una configurazione IP creata all'esterno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio tramite Gestione cluster di failover WSFC, ma modificabile tramite l'istruzione Tsql ALTER AVAILABILITY GROUP, la configurazione IP viene qualificata come conforme.<br /><br /> 0 = Il listener non è conforme. In genere, indica un indirizzo IP che non può essere configurato tramite i comandi [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] e che è stato definito direttamente nel cluster WSFC.|  
|**ip_configuration_string_from_cluster**|**nvarchar(max)**|Eventuali stringhe di configurazione IP del cluster per questo listener. Null = Il listener non dispone di indirizzi IP virtuali. Ad esempio:<br /><br /> Indirizzo IPv4: `65.55.39.10`.<br /><br /> Indirizzo IPv6: `2001::4898:23:1002:20f:1fff:feff:b3a3`.|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>Autorizzazioni  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Per altre informazioni, vedere [configurazione della visibilità dei metadati](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e DMV di Gruppi di disponibilità AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Viste del catalogo dei gruppi di disponibilità AlwaysOn &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Monitorare Gruppi di disponibilità &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Gruppi di disponibilità AlwaysOn di &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
