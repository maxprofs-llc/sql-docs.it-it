---
title: Visualizzare e analizzare le tracce con SQL Server Profiler | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- Profiler [SQL Server Profiler], viewing traces
- SQL Server Profiler, viewing traces
- traces [SQL Server], viewing
- SQL Server Profiler, troubleshooting
- troubleshooting [SQL Server], traces
- events [SQL Server], finding inside trace
- Profiler [SQL Server Profiler], troubleshooting
- traces [SQL Server], events
ms.assetid: 17e821ca-a12e-4192-acc1-96765d9ae266
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fd9b95821ee673e259273f880aefe8606fe81d71
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68211023"
---
# <a name="view-and-analyze-traces-with-sql-server-profiler"></a>Visualizzare e analizzare le tracce con SQL Server Profiler
  Utilizzare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per visualizzare i dati eventi acquisiti in una traccia. 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] consente di visualizzare i dati in base alle proprietà definite della traccia. Per analizzare i dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] è possibile copiarli in un altro programma, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] . [!INCLUDE[ssDE](../../includes/ssde-md.md)]Ottimizzazione guidata può utilizzare un file di traccia contenente eventi SQL batch e RPC (Remote Procedure Call) se la colonna di dati **Text** è inclusa nella traccia. Per assicurarsi di acquisire gli eventi e le colonne corretti da utilizzare con Ottimizzazione guidata [!INCLUDE[ssDE](../../includes/ssde-md.md)] , utilizzare il modello di ottimizzazione predefinito disponibile in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
 Quando si apre una traccia utilizzando [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], non è necessario specificare l'estensione di file trc per il file di traccia, se tale file è stato creato da stored procedure sistema di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] o di Traccia SQL.  
  
> [!NOTE]  
>  
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] è anche in grado di leggere file con estensione log di Traccia SQL e file script SQL generici. Per l'apertura di un file log di Traccia SQL senza estensione log, ad esempio trace.txt, specificare **SQLTrace_Log** come formato del file.  
  
 È possibile configurare il formato di visualizzazione della data e dell'ora di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per semplificare l'analisi delle tracce.  
  
## <a name="troubleshooting-data"></a>Risoluzione dei problemi relativi ai dati  
 
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]consente di risolvere i problemi relativi ai dati raggruppando le tracce o i file di traccia in base alle colonne di dati **Duration**, **CPU**, **Reads**o **Writes** . I dati che possono essere inclusi nella risoluzione dei problemi corrispondono a query con prestazioni insufficienti o che generano un numero estremamente elevato di operazioni di letture logiche.  
  
 È possibile isolare informazioni aggiuntive salvando le tracce in tabelle e utilizzando istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] per eseguire query nei dati di evento. Ad esempio, per individuare gli eventi **SQL:BatchCompleted** per i quali il tempo di attesa è stato eccessivo, eseguire quanto segue:  
  
```  
SELECT  TextData, Duration, CPU  
FROM    trace_table_name  
WHERE   EventClass = 12 -- SQL:BatchCompleted events  
AND     CPU < (Duration * 1000)  
```  
  
> [!NOTE]  
>  Il server indica la durata di un evento in microsecondi (un milionesimo o 10<sup>-6</sup>di secondo) e la quantità di tempo della CPU usato dall'evento in millisecondi (un millesimo o 10<sup>-3</sup>di secondo). Nell'interfaccia utente grafica di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] il valore della colonna **Duration** viene visualizzato in millisecondi. Tuttavia, quando si salva una traccia in un file o in una tabella di database, il valore della colonna **Duration** viene scritto in microsecondi.  
  
## <a name="displaying-object-names-when-viewing-traces"></a>Visualizzazione dei nomi degli oggetti durante la visualizzazione delle tracce  
 Per visualizzare il nome di un oggetto invece dell'identificatore dell'oggetto, ovvero**Object ID**, è necessario acquisire le colonne di dati **Server Name** e **Database ID** insieme alla colonna di dati **Object Name** .  
  
 Se si sceglie di basare il raggruppamento sulla colonna di dati **Object ID** assicurarsi di eseguire innanzitutto il raggruppamento in base alle colonne di dati **Server Name** e **Database ID** e quindi in base alla colonna di dati **Object ID** . . Analogamente, se si sceglie di basare il raggruppamento sulla colonna di dati **Index ID** , assicurarsi di eseguire innanzitutto il raggruppamento in base alle colonne di dati **Server Name**, **Database ID**e **Object ID** e quindi in base alle colonne di dati **Index ID** . È necessario attenersi a tale ordine durante il raggruppamento, poiché gli ID di oggetto e di indice non sono univoci nei server e nei database e negli oggetti relativi agli ID degli indici.  
  
## <a name="finding-specific-events-within-a-trace"></a>Individuazione di eventi specifici in una traccia  
 Per individuare e raggruppare gli eventi in una traccia, eseguire la procedura seguente:  
  
1.  Creare la traccia.  
  
    -   Nella definizione della traccia includere le colonne di dati **Event Class**, **ClientProcessID**e **Start Time** oltre alle altre colonne di dati che si desidera acquisire. Per altre informazioni, vedere [Creare una traccia &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md).  
  
    -   Raggruppare i dati acquisiti in base alla colonna di dati **Event Class**e salvare la traccia in un file o in una tabella. Per raggruppare i dati acquisiti, fare clic su **Organizza colonne** nella scheda **Selezione eventi** della finestra di dialogo Proprietà traccia. Per altre informazioni, vedere [Organizzare le colonne visualizzate in una traccia &#40;SQL Server Profiler&#41;](organize-columns-displayed-in-a-trace-sql-server-profiler.md).  
  
    -   Avviare la traccia e quindi arrestarla quando è trascorso l'intervallo di tempo appropriato o dopo l'acquisizione di un determinato numero di eventi.  
  
2.  Determinare quali eventi si desidera individuare.  
  
    -   Aprire il file o la tabella di traccia ed espandere il nodo della classe di evento desiderata, ad esempio **Deadlock Chain**. Per altre informazioni, vedere [Aprire un file di traccia &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md) o Ottimizzazione guidata [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md).  
  
    -   Eseguire una ricerca nei dati della traccia fino a individuare gli eventi desiderati. Per semplificare la ricerca dei valori desiderati nella traccia, scegliere **Trova** dal menu **Modifica** di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] . Prendere nota dei valori delle colonne di dati **ClientProcessID** e **Start Time** degli eventi tracciati.  
  
3.  Visualizzare gli eventi nel contesto.  
  
    -   Visualizzare le proprietà della traccia ed eseguire il raggruppamento in base alla colonna di dati **ClientProcessID**anziché alla colonna di dati **Event Class** .  
  
    -   Espandere il nodo di ogni ID di processo client che si desidera visualizzare. Eseguire una ricerca manuale nella traccia oppure usare il comando **Trova** per individuare i valori **Start Time**degli eventi desiderati, annotati in precedenza. Gli eventi vengono visualizzati in ordine cronologico con gli altri eventi che appartengono a ogni ID processo client selezionato. Ad esempio, gli eventi **Deadlock** e **Deadlock Chain**, acquisiti all'interno della traccia, vengono visualizzati immediatamente dopo gli eventi **SQL:BatchStarting**all'interno dell'ID processo client espanso.  
  
 È possibile utilizzare la stessa tecnica per individuare eventuali eventi raggruppati. Dopo avere trovato gli eventi desiderati, raggrupparli in base a **ClientProcessID**, **ApplicationName**o a un'altra classe di evento, per visualizzare le attività correlate in ordine cronologico.  
  
## <a name="see-also"></a>Vedere anche  
 [Visualizzare una traccia salvata &#40;&#41;Transact-SQL](../../relational-databases/sql-trace/view-a-saved-trace-transact-sql.md)   
 [sys.fn_trace_getinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql)   
 [Visualizza informazioni sui filtri &#40;SQL Server Profiler&#41;](view-filter-information-sql-server-profiler.md)   
 [Visualizzazione delle informazioni sui filtri &#40;&#41;Transact-SQL](../../relational-databases/sql-trace/view-filter-information-transact-sql.md)   
 [Aprire un file di traccia &#40;SQL Server Profiler&#41;](open-a-trace-file-sql-server-profiler.md)   
 [Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](open-a-trace-table-sql-server-profiler.md)  
  
  
