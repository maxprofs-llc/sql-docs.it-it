---
title: Informazioni di riferimento sugli oggetti di sistema per il mirroring del database | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e61f8d9df3cb6dcaf545819d630c70bc18709d15
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "68041781"
---
# <a name="database-mirroring-system-object-reference"></a>Informazioni di riferimento sugli oggetti di sistema per il mirroring del database
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="system-catalog-views"></a>Viste del catalogo di sistema

| Vista del catalogo di sistema | Descrizione|
| :------ | :----------------------------- |
| [sys.database_mirroring_witnesses](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   | Contiene una riga per ogni ruolo del server di controllo del mirroring che un server riveste in una relazione di mirroring del database. |
| &nbsp; | &nbsp; |

## <a name="system-dynamic-management-views"></a>Viste a gestione dinamica (DMV) di sistema

| Vista a gestione dinamica (DMV) di sistema | Descrizione|
| :------ | :----------------------------- |
| [sys.dm_db_mirroring_auto_page_repair](../../relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-auto-page-repair.md)   | Viene restituita una riga per ogni tentativo di correzione automatica della pagina in qualsiasi database con mirroring nell'istanza del server.  |
| [sys.dm_db_mirroring_connections](../../relational-databases/system-dynamic-management-views/database-mirroring-sys-dm-db-mirroring-connections.md)    | Restituisce una riga per ogni connessione stabilita per il mirroring del database. |
| &nbsp; | &nbsp; |

## <a name="system-tables"></a>Tabelle di sistema

| Tabella di sistema | Descrizione|
| :------ | :----------------------------- |
| [sysdbmaintplan_databases](../../relational-databases/system-tables/sysdbmaintplan-databases-transact-sql.md)   | Restituisce informazioni sui piani di manutenzione di mirroring del database. |
| [sysdbmaintplan_history](../../relational-databases/system-tables/sysdbmaintplan-history-transact-sql.md)    | Restituisce informazioni sulla cronologia dei piani di manutenzione di mirroring del database. |
| [sysdbmaintplan_jobs](../../relational-databases/system-tables/sysdbmaintplan-jobs-transact-sql.md)    |Restituisce informazioni sui processi dei piani manutenzione di mirroring del database.  |
| [sysdbmaintplans](../../relational-databases/system-tables/sysdbmaintplans-transact-sql.md)    | Restituisce informazioni sui piani di mirroring del database.  |
| &nbsp; | &nbsp; |


## <a name="see-also"></a>Vedere anche  
 [Mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   

  
  
