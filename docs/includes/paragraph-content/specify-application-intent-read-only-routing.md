---
title: File di inclusione
description: File di inclusione
services: sql-database
author: MightyPen
ms.service: sql-database
ms.topic: include
ms.date: 04/05/2018
ms.author: genemi
ms.custom: include file
ms.openlocfilehash: 0e7d549c2f3b02349007815019cc47647f172f73
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68213538"
---
## <a name="specifying-application-intent"></a>Specificazione della finalità dell'applicazione

La parola chiave **ApplicationIntent** può essere specificata nella stringa di connessione. I valori assegnabili sono **ReadWrite** oppure **ReadOnly**. Il valore predefinito è **ReadWrite**.

Quando **ApplicationIntent = ReadOnly**, il client richiede un carico di lavoro di lettura durante la connessione. Il server applica la finalità al momento della connessione e durante un'istruzione di database **USE**.

La parola chiave **ApplicationIntent** non funziona con i database legacy di sola lettura.  


#### <a name="targets-of-readonly"></a>Destinazioni di ReadOnly

Quando una connessione sceglie **ReadOnly**, la connessione viene assegnata a una delle configurazioni speciali seguenti che potrebbero essere disponibili per il database:

- [Always On](~/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)
    - Un database può consentire o impedire carichi di lavoro di lettura nel database Always On di destinazione. Questa scelta viene controllata usando la clausola **ALLOW_CONNECTIONS** delle istruzioni Transact-SQL **PRIMARY_ROLE** e **SECONDARY_ROLE**.

- [Replica geografica](https://docs.microsoft.com/azure/sql-database/sql-database-geo-replication-overview)

- [Scalabilità orizzontale in lettura](https://docs.microsoft.com/azure/sql-database/sql-database-read-scale-out)

Se nessuna di queste destinazioni speciali è disponibile, viene letto il database normale.

&nbsp;

La parola chiave **ApplicationIntent** abilita il *routing di sola lettura*.


## <a name="read-only-routing"></a>Routing di sola lettura

Il routing di sola lettura è una funzionalità che può garantire la disponibilità di una replica di sola lettura di un database. Per abilitare il routing di sola lettura, si applicano tutte le condizioni seguenti:

- È necessario connettersi a un listener del gruppo di disponibilità Always On.

- La parola chiave della stringa di connessione **ApplicationIntent** deve essere impostata su **ReadOnly**.

- Il gruppo di disponibilità deve essere configurato dall'amministratore del database per abilitare il routing di sola lettura.

Più connessioni che usano il routing di sola lettura potrebbero non connettersi tutte alla stessa replica di sola lettura. Le modifiche nella sincronizzazione del database o nella configurazione di routing del server possono comportare connessioni client a repliche di sola lettura diverse. È possibile assicurarsi che tutte le richieste di sola lettura si connettano alla stessa replica di sola lettura. Verificare questa condizione *non* passando un listener del gruppo di disponibilità alla parola chiave della stringa di connessione **Server**. Specificare invece il nome dell'istanza di sola lettura.

Il routing di sola lettura potrebbe richiedere più tempo rispetto alla connessione al database primario. L'attesa maggiore dipende dal fatto che il routing di sola lettura si connette prima al database primario e quindi cerca il miglior database secondario leggibile disponibile. A causa di questi passaggi aggiuntivi, è consigliabile aumentare il timeout di accesso ad almeno 30 secondi.

