---
title: Destinazione file non elaborato | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledest.f1
helpviewer_keywords:
- append options [Integration Services]
- destinations [Integration Services], Raw File
- raw data [Integration Services]
- writing raw data
- Raw File destination
ms.assetid: d311b458-aefc-4b4d-b1a1-4c0ebbb34214
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b7996ed3cc3ea209361790f23f6955f09be035e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "62770858"
---
# <a name="raw-file-destination"></a>file non elaborato - destinazione
  La destinazione file non elaborato scrive dati non elaborati in un file. Poiché il formato dei dati è nativo della destinazione, non è necessaria alcuna conversione e quasi nessuna analisi dei dati. Questo significa che la destinazione file non elaborato è in grado di scrivere i dati più rapidamente rispetto ad altre destinazioni, quali le destinazioni file flat e OLE DB.  
  
 Oltre alla scrittura di dati non elaborati in un file, la destinazione file non elaborato può essere utilizzata anche per generare un file non elaborato vuoto contenente solo le colonne (file di soli metadati), senza dover eseguire il pacchetto. Si utilizza l'origine file non elaborato per recuperare dati non elaborati scritti in precedenza dalla destinazione. È anche possibile puntare l'origine file non elaborato al file di soli metadati.  
  
 Nel formato di file non elaborato sono contenute informazioni di ordinamento. Con la destinazione file non elaborato è possibile salvare tutte le informazioni di ordinamento in cui sono inclusi i flag di confronto per le colonne stringa. Con l'origine file non elaborato è possibile leggere e riconoscere le informazioni di ordinamento. È possibile configurare l'origine file non elaborato in modo da ignorare i flag di ordinamento nel file utilizzando l'editor avanzato. Per altre informazioni sui flag di confronto, vedere [Confronto di dati stringa](comparing-string-data.md).  
  
 Per configurare la destinazione file non elaborato, procedere nel modo seguente:  
  
-   Specificare una modalità di accesso, ovvero il nome del file o una variabile contenente il nome del file in cui la destinazione file non elaborato dovrà scrivere.  
  
-   Indicare se la destinazione file non elaborato deve creare un nuovo file o accodare i dati a un file esistente con lo stesso nome.  
  
 La destinazione file non elaborato viene frequentemente utilizzata per scrivere risultati intermedi di dati parzialmente elaborati durante l'esecuzione dei pacchetti. Se si archiviano i dati non elaborati, sarà possibile rileggerli rapidamente tramite un'origine file non elaborato e quindi trasformarli ulteriormente prima di caricarli nella destinazione finale. È ad esempio possibile eseguire più volte un pacchetto che a ogni esecuzione scrive dati non elaborati in uno o più file e successivamente eseguire un altro pacchetto che utilizza l'origine file non elaborato per leggere i dati da ogni file, utilizza una trasformazione Unione input multipli per unire i dati in un unico set di dati, quindi applica ulteriori trasformazioni che riepilogano i dati prima di caricarli nella destinazione finale, ad esempio una tabella di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!NOTE]  
>  La destinazione file non elaborato supporta dati Null ma non dati BLOB (Binary Large Object).  
  
> [!NOTE]  
>  La destinazione file non elaborato non utilizza alcuna gestione connessione.  
  
 Questa origine include un solo input regolare. Non supporta un output degli errori.  
  
## <a name="append-and-new-file-options"></a>Opzioni Accoda e Nuovo file  
 La proprietà WriteOption include opzioni per accodare dati a un file esistente o crearne uno nuovo.  
  
 La tabella seguente descrive le opzioni disponibili per la proprietà WriteOption.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|Accoda|Accoda i dati a un file esistente. I metadati dei dati accodati devono corrispondere al formato del file.|  
|Crea sempre|Crea sempre un nuovo file.|  
|Crea una sola volta|Crea un nuovo file. Se il file esiste, il componente ha esito negativo.|  
|Tronca e accoda|Tronca un file esistente e quindi vi scrive i dati. I metadati dei dati accodati devono corrispondere al formato del file.|  
  
 Di seguito sono riportati elementi importanti relativi all'accodamento dei dati:  
  
-   L'accodamento dei dati in un file non elaborato esistente non comporta il riordinamento dei dati.  
  
     È necessario assicurarsi che le chiavi ordinate rimangano nell'ordine corretto.  
  
-   L'accodamento dei dati in un file non elaborato esistente non comporta la modifica dei metadati del file (informazioni sull'ordinamento).  
  
 Ad esempio, in un pacchetto vengono letti i dati ordinati sul ProductKey (PK). Con il flusso di dati del pacchetto, i dati vengono accodati in un file non elaborato esistente. Alla prima esecuzione del pacchetto, vengono ricevute tre righe (PK 1000, 1100, 1200). Nel file non elaborato sono ora contenuti i dati riportati di seguito.  
  
-   1000, productA  
  
-   1100, productB  
  
-   1200, productC  
  
 Alla seconda esecuzione del pacchetto, vengono ricevute due nuove righe (PK 1001, 1300). Nel file non elaborato sono ora contenuti i dati riportati di seguito.  
  
-   1000, productA  
  
-   1100, productB  
  
-   1200, productC  
  
-   1001, productD  
  
-   1300, productE  
  
 I nuovi dati vengono accodati alla fine del file non elaborato e le chiavi ordinate (PK) non sono disponibili. Inoltre, l'operazione di accodamento non ha modificato i metadati del file (informazioni di ordinamento). Se il file viene letto utilizzando l'origine file non elaborato, tramite il componente viene indicato che il file è ancora ordinato su PK anche se i dati nel file non sono più nell'ordine corretto.  
  
 Per mantenere le chiavi ordinate nell'ordine corretto mentre si accodano i dati, è possibile progettare il flusso di dati del pacchetto nel modo seguente:  
  
1.  Recuperare le nuove righe tramite l'origine A.  
  
2.  Recuperare le righe esistenti da RawFile1 utilizzando l'origine B.  
  
3.  Combinare gli input delle origini A e B tramite la trasformazione Unione input multipli.  
  
4.  Ordinare su PK.  
  
5.  Scrivere in RawFile2 utilizzando la destinazione file non elaborato.  
  
     RawFile1 viene bloccato perché ne viene eseguita la lettura nel flusso di dati.  
  
6.  Sostituire RawFile1 con RawFile2.  
  
### <a name="using-the-raw-file-destination-in-a-loop"></a>Utilizzo della destinazione file non elaborato in un ciclo  
 Se il flusso di dati che utilizza la destinazione file non elaborato si trova in un ciclo, può rivelarsi utile creare il file una sola volta e quindi accodare i dati al file quando il ciclo viene ripetuto. Per accodare i dati al file, è necessario che i dati accodati corrispondano al formato del file esistente.  
  
 Per creare il file nella prima iterazione del ciclo e quindi accodare righe nelle iterazioni successive, è necessario eseguire le operazioni seguenti in fase di progettazione:  
  
1.  Impostare la proprietà WriteOption su **CreateOnce** o **CreateAlways**ed eseguire un'iterazione del ciclo. Il file viene creato e viene garantita così la corrispondenza tra i metadati dei dati accodati e il file.  
  
2.  Reimpostare la proprietà WriteOption su **Append** e impostare la proprietà ValidateExternalMetadata `False`su.  
  
 Se si usa l'opzione **TruncateAppend** invece di **Append** , le righe aggiunte in qualsiasi iterazione precedente verranno troncate e quindi verranno accodate nuove righe. Per usare l'opzione **TruncateAppend** , è anche necessario che i dati corrispondano al formato del file.  
  
## <a name="configuration-of-the-raw-file-destination"></a>Configurazione della destinazione file non elaborato  
 È possibile impostare le proprietà tramite Progettazione [!INCLUDE[ssIS](../../includes/ssis-md.md)] o a livello di codice.  
  
 Nella finestra di dialogo **Editor avanzato** sono disponibili le proprietà che è possibile impostare a livello di codice. Per ulteriori informazioni sulle proprietà che è possibile impostare nella finestra di dialogo **Editor avanzato** o a livello di codice, fare clic su uno degli argomenti seguenti:  
  
-   [Proprietà comuni](../common-properties.md)  
  
-   [Proprietà personalizzate del file non elaborato](raw-file-custom-properties.md)  
  
## <a name="related-tasks"></a>Attività correlate  
 Per informazioni su come impostare le proprietà del componente, vedere [Impostazione delle proprietà di un componente flusso di dati](set-the-properties-of-a-data-flow-component.md).  
  
## <a name="related-content"></a>Contenuto correlato  
 Post di blog sugli [aspetti positivi dei file non elaborati](http://www.sqlservercentral.com/blogs/stratesql/archive/2011/1/1/31-days-of-ssis-_1320_-raw-files-are-awesome-_2800_1_2F00_31_2900_.aspx)nel sito Web sqlservercentral.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Origine file non elaborato](raw-file-source.md)   
 [Flusso di dati](data-flow.md)  
  
  
