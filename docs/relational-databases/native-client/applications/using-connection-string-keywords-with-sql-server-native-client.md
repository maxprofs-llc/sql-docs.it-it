---
title: Native client, parole chiave di connessione SQL
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 33612f7e4303ad9d02e4c6d3b7980e750e3a594b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "75258746"
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>Utilizzo delle parole chiave delle stringhe di connessione con SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  In alcune API di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vengono utilizzate stringhe di connessione per specificare gli attributi di connessione. Le stringhe di connessione sono elenchi di parole chiave con i relativi valori associati. Ogni parola chiave identifica un particolare attributo di connessione.  

> [!IMPORTANT]
> Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB di Native Client (SQLNCLI) rimane deprecato e non è consigliabile utilizzarlo per nuove attività di sviluppo. Usare invece il nuovo [Microsoft OLE DB Driver per SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) che verrà aggiornato con le funzionalità server più recenti.    
> Per informazioni, vedere [utilizzo delle parole chiave delle stringhe di connessione con OLE DB driver per SQL Server](../../../connect/oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).

> [!NOTE]
> 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta l'ambiguità nelle stringhe di connessione per mantenere la compatibilità con le versioni precedenti. È ad esempio possibile specificare alcune parole chiave più volte e utilizzare parole chiave in conflitto con una risoluzione basata sulla posizione o sulla precedenza. Quando si modificano le applicazioni, è consigliabile utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per eliminare l'eventuale dipendenza dall'ambiguità delle stringhe di connessione.  
  
 Nelle sezioni seguenti vengono descritte le parole chiave che è possibile specificare con il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e gli oggetti ADO (ActiveX Data Objects) quando si utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client come provider di dati.  
  
## <a name="odbc-driver-connection-string-keywords"></a>Parole chiave della stringa di connessione del driver ODBC  
 Le applicazioni ODBC utilizzano stringhe di connessione come parametri per le funzioni [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) e [SQLBrowseConnect](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) .  
  
 Le stringhe di connessione utilizzate da ODBC presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra parentesi graffe per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori di attributo. Poiché si suppone che la prima parentesi graffa chiusa indichi la fine del valore, l'uso di tali parentesi nei valori non è consentito.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con una stringa di connessione ODBC.  
  
|Parola chiave|Descrizione|  
|-------------|-----------------|  
|**Addr**|Sinonimo di "Address".|  
|**Indirizzo**|Indirizzo di rete del server che esegue un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Address** è in genere il nome di rete del server, ma può corrispondere ad altri nomi, ad esempio una pipe, un indirizzo IP o un indirizzo socket e una porta TCP/IP.<br /><br /> Se si specifica un indirizzo IP, assicurarsi che i protocolli TCP/IP o Named Pipes siano abilitati in Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Il valore di **Address** ha la precedenza sul valore passato al **Server** nelle stringhe di connessione ODBC quando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] si utilizza Native Client. Si noti anche `Address=;` che si connetterà al server specificato nella parola chiave **Server** `Address= ;, Address=.;`, `Address=localhost;`mentre, `Address=(local);` e tutte le causeranno una connessione al server locale.<br /><br /> La sintassi completa per la parola chiave **Address** è la seguente:<br /><br /> [_protocollo_**:**] *Indirizzo*[**,**_porta &#124; \pipe\pipename_]<br /><br /> il *protocollo* può essere **TCP** (TCP/IP), **LPC** (Shared Memory) o **NP** (Named Pipes). Per ulteriori informazioni sui protocolli, vedere [configure client Protocols](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Se non si specifica né il *protocollo* né la parola [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] chiave di **rete** , in native client verrà utilizzato [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l'ordine dei protocolli specificato in Configuration Manager.<br /><br /> *Port* è la porta a cui connettersi nel server specificato. Per impostazione predefinita, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene utilizzata la porta 1433.|  
|**AnsiNPW**|Se l'opzione è impostata su "yes", nel driver vengono utilizzati i comportamenti definiti da ANSI per la gestione dei confronti NULL, del riempimento dei dati di tipo carattere, degli avvisi e della concatenazione NULL. Se impostata su "no", i comportamenti definiti da ANSI non vengono esposti. Per ulteriori informazioni sui comportamenti ANSI NPW, vedere [effetti delle opzioni ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|**APP**|Nome dell'applicazione che chiama [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) (facoltativo). Se specificato, questo valore viene archiviato nella colonna **master. dbo. sysprocesses** **program_name** e viene restituito dalle funzioni [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) e [APP_NAME](../../../t-sql/functions/app-name-transact-sql.md) .|  
|**ApplicationIntent**|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**. Il valore predefinito è **ReadWrite**.  Ad esempio:<br /><br /> `ApplicationIntent=ReadOnly`<br /><br /> Per ulteriori informazioni sul [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto di Native Client per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native client supporto per la disponibilità elevata e il ripristino di emergenza](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|Nome del file primario di un database collegabile. Includere il percorso completo e utilizzare la sequenza di escape dei caratteri \ se si utilizza una variabile di tipo stringa di caratteri C:<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> Questo database viene collegato e diventa il database predefinito per la connessione. Per utilizzare **AttachDBFilename** , è necessario specificare anche il nome del database nel parametro del database [SQLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) o nell'attributo di connessione SQL_COPT_CURRENT_CATALOG. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**AutoTranslate**|Se impostata su "yes", le stringhe di caratteri ANSI inviate tra il client e il server vengono convertite in Unicode per ridurre al minimo i problemi di corrispondenza dei caratteri estesi tra le tabelle codici sul client e sul server.<br /><br /> I dati SQL_C_CHAR client inviati a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] una variabile, un parametro o una colonna **char**, **varchar**o **Text** vengono convertiti da caratteri a Unicode utilizzando la tabella codici ANSI (ACP) del client, quindi convertiti da Unicode in caratteri utilizzando l'ACP del server.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]i dati di tipo **char**, **varchar**o **Text** inviati a una variabile client SQL_C_CHAR vengono convertiti da caratteri a Unicode utilizzando il server ACP, quindi vengono convertiti da Unicode in caratteri utilizzando l'ACP del client.<br /><br /> Queste conversioni vengono eseguite sul client dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e richiedono che sul client sia disponibile la stessa tabella codici ANSI (ACP) utilizzata sul server.<br /><br /> Queste impostazioni non influiscono sulle conversioni eseguite per i trasferimenti seguenti:<br /><br /> \*Unicode SQL_C_WCHAR i dati client inviati a **char**, **varchar**o **Text** sul server.<br /><br /> &#42; dati del server di tipo **char**, **varchar**o **text** inviati a una variabile SQL_C_WCHAR Unicode nel client.<br /><br /> \*ANSI SQL_C_CHAR i dati client inviati a Unicode **nchar**, **nvarchar**o **ntext** sul server.<br /><br /> \*Dati del server Unicode **nchar**, **nvarchar**o **ntext** inviati a una variabile SQL_C_CHAR ANSI nel client.<br /><br /> Se impostata su "no", la conversione dei caratteri non viene eseguita.<br /><br /> Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC di Native client non converte il carattere ANSI client SQL_C_CHAR dati inviati a variabili, parametri o colonne di tipo **char**, **varchar**o **Text** nel server. Non viene eseguita alcuna conversione sui dati di tipo **char**, **varchar**o **text** inviati dal server per SQL_C_CHAR variabili nel client.<br /><br /> Se il client e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzano ACP differenti, i caratteri estesi potrebbero essere interpretati in modo errato.|  
|**Database**|Nome del database [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] predefinito per la connessione. Se il **database** non è specificato, viene utilizzato il database predefinito definito per l'account di accesso. Il database predefinito dell'origine dati ODBC esegue l'override del database predefinito specificato per l'accesso. Il database deve essere un database esistente a meno che non sia specificato anche **AttachDBFilename** . Se viene specificato anche **AttachDBFilename** , viene collegato il file primario a cui fa riferimento e viene fornito il nome del database specificato dal **database**.|  
|**Driver**|Nome del driver restituito da [SQLDrivers](../../../relational-databases/native-client-odbc-api/sqldrivers.md). Il valore della parola chiave per il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client è "{SQL Server Native Client 11.0}". La parola chiave **Server** è obbligatoria se è specificato il **driver** e **DriverCompletion** è impostato su SQL_DRIVER_NOPROMPT.<br /><br /> Per ulteriori informazioni sui nomi dei driver, vedere [utilizzo dei file di intestazione e di libreria SQL Server Native Client](../../../relational-databases/native-client/applications/using-the-sql-server-native-client-header-and-library-files.md).|  
|**DSN**|Nome di un'origine dati di sistema o di un utente ODBC esistente. Questa parola chiave sostituisce tutti i valori che possono essere specificati nelle parole chiave **Server**, **rete**e **Indirizzo** .|  
|**Crittografare**|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|**Fallback**|Questa parola chiave è deprecata e la relativa impostazione viene ignorata dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**Failover_Partner**|Nome del server partner di failover da utilizzare se non è possibile stabilire una connessione al server primario.|  
|**FailoverPartnerSPN**|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal driver.|  
|**FileDSN**|Nome di un'origine dati dei file ODBC esistente.|  
|**Lingua**|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (facoltativo). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]consente di archiviare messaggi per più lingue in **sysmessages**. Se ci si connette [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] a un con più lingue, **Language** specifica il set di messaggi utilizzato per la connessione.|  
|**MARS_Connection**|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione. I valori riconosciuti sono "yes" e "no". Il valore predefinito è "no".|  
|**MultiSubnetFailover**|Specificare sempre **MultiSubnetFailover = Yes** quando ci si connette al listener del gruppo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] disponibilità di un gruppo [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di disponibilità o di un'istanza del cluster di failover. **MultiSubnetFailover = Yes** Configura [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per fornire un rilevamento più veloce e una connessione al server attualmente attivo. I valori possibili sono **Sì** e **No**. Il valore predefinito è **No**. Ad esempio:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Per ulteriori informazioni sul [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto di Native Client per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native client supporto per la disponibilità elevata e il ripristino di emergenza](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**NET**|Sinonimo di "Network".|  
|**Rete**|I valori validi sono **dbnmpntw** (Named Pipes) e **dbmssocn** (TCP/IP).<br /><br /> Non è possibile specificare sia un valore per la parola chiave **Network** che un prefisso di protocollo nella parola chiave **Server** .|  
|**PWD**|Password per l'account di accesso a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specificato nel parametro UID. Non è necessario specificare **pwd** se per l'account di accesso è presente una password null o quando`Trusted_Connection = yes`si utilizza l'autenticazione di Windows ().|  
|**QueryLog_On**|Se impostata su "yes", la registrazione dei dati di query con esecuzione prolungata viene abilitata per la connessione. Se impostata su "no", i dati di query con esecuzione prolungata non vengono registrati.|  
|**QueryLogFile**|Nome e percorso completo di un file da utilizzare per registrare dati nelle query con esecuzione prolungata.|  
|**QueryLogTime**|Stringa di cifre che specifica la soglia (in millisecondi) per la registrazione delle query con esecuzione prolungata. Tutte le query che non ottengono una risposta nell'intervallo di tempo specificato vengono scritte nel file di log delle query con esecuzione prolungata.|  
|**QuotedId**|Se impostata su "yes", QUOTED_IDENTIFIERS viene impostata su ON per la connessione e in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono utilizzate le regole ISO relative all'uso delle virgolette nelle istruzioni SQL. Se impostata su no, QUOTED_IDENTIFIERS viene impostata su OFF per la connessione. In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono quindi seguite le regole [!INCLUDE[tsql](../../../includes/tsql-md.md)] legacy relative all'utilizzo delle virgolette nelle istruzioni SQL. Per ulteriori informazioni, vedere [effetti delle opzioni ISO](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|**Regionale**|Se impostata su "yes", nel driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vengono utilizzate le impostazioni client per la conversione dei dati di valuta, data e ora in dati di tipo carattere. La conversione viene eseguita in una sola direzione. Il driver non riconosce i formati standard non ODBC per le stringhe di data o i valori di valuta all'interno, ad esempio, di un parametro utilizzato in un'istruzione INSERT o UPDATE. Se impostata su "no", nel driver vengono utilizzate le stringhe standard ODBC per rappresentare i dati di valuta, data e ora convertiti in dati di tipo carattere.|  
|**SaveFile**|Nome di un file di origine dati ODBC nel quale vengono salvati gli attributi della connessione corrente se la connessione riesce.|  
|**Server**|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore deve corrispondere al nome di un server in rete, a un indirizzo IP o al nome di un alias di Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La parola chiave **Address** sostituisce la parola chiave **Server** .<br /><br /> È possibile connettersi all'istanza predefinita nel server locale specificando uno dei valori seguenti:<br /><br /> **Server =;**<br /><br /> **Server =.;**<br /><br /> **Server = (locale);**<br /><br /> **Server = (locale);**<br /><br /> **Server = (localhost);**<br /><br /> **Server = (database locale\\ )** _NomeIstanza_ **;**<br /><br /> Per ulteriori informazioni sul supporto del database locale, vedere [supporto SQL Server Native Client per](../../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)local DB.<br /><br /> Per specificare un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], aggiungere **\\** _NomeIstanza_.<br /><br /> Se non viene specificato un server, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Se si specifica un indirizzo IP, assicurarsi che i protocolli TCP/IP o Named Pipes siano abilitati in Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La sintassi completa per la parola chiave **Server** è la seguente:<br /><br /> **Server =**[_protocollo_**:**]*Server*[**,**_porta_]<br /><br /> il *protocollo* può essere **TCP** (TCP/IP), **LPC** (Shared Memory) o **NP** (Named Pipes).<br /><br /> Nell'esempio seguente si illustra come specificare una named pipe:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Questa riga specifica un protocollo Named Pipes, una named pipe nel computer locale (`\\.\pipe`), il nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) e il nome predefinito della named pipe (`sql/query`).<br /><br /> Se non viene specificato né un *protocollo* né la parola chiave [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] di **rete** , in native client verrà utilizzato l' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ordine dei protocolli specificato in Configuration Manager.<br /><br /> *Port* è la porta a cui connettersi nel server specificato. Per impostazione predefinita, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene utilizzata la porta 1433.<br /><br /> Gli spazi vengono ignorati all'inizio del valore passato al **Server** nelle stringhe di connessione ODBC quando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] si utilizza Native Client.|  
|**ServerSPN**|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal driver.|  
|**StatsLog_On**|Se impostata su "yes", abilita l'acquisizione dei dati relativi alle prestazioni del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Se impostata su "no", i dati relativi alle prestazioni del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client non sono disponibili nella connessione.|  
|**StatsLogFile**|Nome e percorso completo di un file utilizzato per registrare le statistiche sulle prestazioni del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**Trusted_Connection**|Se impostata su "yes", indica al driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare la Modalità di autenticazione di Windows per la convalida dell'accesso. In caso contrario, indica al driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare un nome utente e una password di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per la convalida dell'accesso e richiede la specifica delle parole chiave UID e PWD.|  
|**TrustServerCertificate**|Quando viene usato con **Encrypt**, Abilita la crittografia tramite un certificato server autofirmato.|  
|**UID**|Account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] valido. Quando si utilizza l'autenticazione di Windows non è necessario specificare l'UID.|  
|**UseProcForPrepare**|Questa parola chiave è deprecata e la relativa impostazione viene ignorata dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**WSID**|ID della workstation. In genere, si tratta del nome di rete del computer nel quale risiede l'applicazione (facoltativo). Se specificato, questo valore viene archiviato nel **nome host** della colonna **master. dbo. sysprocesses** e viene restituito da [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) e dalla funzione [HOST_NAME](../../../t-sql/functions/host-name-transact-sql.md) .|  
  
> **Nota:** Le impostazioni di conversione regionali si applicano ai tipi di dati Currency, numeric, date e Time. L'impostazione di conversione è applicabile solo alla conversione di output ed è visibile solo quando i valori di valuta, data, ora o numerici vengono convertiti in stringhe di caratteri.  
  
 Nel driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vengono utilizzate le impostazioni locali del Registro di sistema per l'utente corrente. Il driver non rispetta le impostazioni locali del thread corrente se l'applicazione la imposta dopo la connessione, ad esempio, chiamando **SetThreadLocale**.  
  
 La modifica del comportamento internazionale di un'origine dati può generare un errore nell'applicazione. Un'applicazione che analizza le stringhe relative alla data e ne prevede la visualizzazione in base a quanto definito da ODBC, potrebbe essere influenzata negativamente dalla modifica di questo valore.  
  
## <a name="ole-db-provider-connection-string-keywords"></a>Parole chiave delle stringhe di connessione per il provider OLE DB  
 Quando si utilizzano le applicazioni OLE DB, è possibile inizializzare gli oggetti origine dati in due modi diversi:  
  
-   **IDBInitialize:: Initialize**  
  
-   **IDataInitialize:: GetDataSource**  
  
 Nel primo caso è possibile utilizzare una stringa del provider per inizializzare le proprietà di connessione impostando la proprietà DBPROP_INIT_PROVIDERSTRING nel set di proprietà DBPROPSET_DBINIT. Nel secondo caso è possibile passare una stringa di inizializzazione al metodo **IDataInitialize::GetDataSource** per inizializzare le proprietà di connessione. Entrambi i metodi inizializzano le stesse proprietà di connessione OLE DB, sebbene con set di parole chiave differenti. Il set di parole chiave usato con **IDataInitialize::GetDataSource** rappresenta almeno la descrizione delle proprietà contenute nel gruppo delle proprietà di inizializzazione.  
  
 Per qualsiasi impostazione di stringa del provider con una proprietà OLE DB corrispondente impostata su un valore predefinito o impostata in modo esplicito su un valore, tramite il valore della proprietà OLE DB verrà eseguito l'override dell'impostazione nella stringa del provider.  
  
 Per le proprietà booleane impostate nelle stringhe del provider mediante i valori DBPROP_INIT_PROVIDERSTRING vengono utilizzati i valori "yes" e "no". Per le proprietà booleane impostate nelle stringhe di inizializzazione con **IDataInitialize::GetDataSource** vengono usati i valori "true" e "false".  
  
 Le applicazioni che usano **IDataInitialize::GetDataSource** supportano anche le parole chiave usate da **IDBInitialize::Initialize**, ma solo per le proprietà che non hanno un valore predefinito. Se in un'applicazione viene usata sia la parola chiave **IDataInitialize::GetDataSource** che la parola chiave **IDBInitialize::Initialize** nella stringa di inizializzazione, viene usata l'impostazione della parola chiave **IDataInitialize::GetDataSource**. Nelle applicazioni è consigliabile non specificare le parole chiave **IDBInitialize::Initialize** nelle stringhe di connessione **IDataInitialize:GetDataSource**, perché questo comportamento potrebbe non essere supportato nelle versioni successive.  
  
> [!NOTE]  
>  Una stringa di connessione passata a **IDataInitialize::GetDataSource** viene convertita in proprietà e applicata tramite **IDBProperties::SetProperties**. Se i Servizi componenti hanno rilevato la descrizione della proprietà in **IDBProperties::GetPropertyInfo**, la proprietà verrà applicata come autonoma. In caso contrario, verrà applicata mediante la proprietà DBPROP_PROVIDERSTRING. Ad esempio, se si specifica l'origine dati della stringa di connessione **= Server1; Server = Server2**, l' **origine dati** verrà impostata come proprietà, ma il **server** passerà a una stringa del provider.  
  
 Se si indicano più istanze per la stessa proprietà specifica del provider, verrà utilizzato il primo valore della prima proprietà.  
  
 Le stringhe di connessione usate nelle applicazioni OLE DB che usano DBPROP_INIT_PROVIDERSTRING con **IDBInitialize::Initialize** presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra parentesi graffe per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori di attributo. Poiché si suppone che la prima parentesi graffa chiusa indichi la fine del valore, l'uso di tali parentesi nei valori non è consentito.  
  
 Uno spazio dopo il segno = in una parola chiave di una stringa di connessione verrà interpretato come valore letterale, anche se il valore è racchiuso tra virgolette.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con DBPROP_INIT_PROVIDERSTRING.  
  
|Parola chiave|Proprietà di inizializzazione|Descrizione|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Sinonimo di "Address".|  
|**Indirizzo**|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi degli indirizzi valida, vedere la descrizione della parola chiave **Address** ODBC più avanti in questo argomento.|  
|**APP**|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.<br /><br /> Il valore predefinito è **ReadWrite**. Per ulteriori informazioni sul [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto di Native Client per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native client supporto per la disponibilità elevata e il ripristino di emergenza](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare **AttachDBFilename**, è necessario specificare anche il nome del database con la parola chiave del database stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**Conversione automatica**|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "yes" e "no".|  
|**Database**|DBPROP_INIT_CATALOG|Nome del database.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati da utilizzare. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di SQL Server 2000.|  
|**Crittografare**|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Lingua**|SSPROPT_INIT_CURRENTLANGUAGE|Lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione se il server è [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|**NET**|SSPROP_INIT_NETWORKLIBRARY|Sinonimo di "Network".|  
|**Rete**|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|**Libreria di rete**|SSPROP_INIT_NETWORKLIBRARY|Sinonimo di "Network".|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "yes" e "no" come valori. Se impostata su "no", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate|  
|**PWD**|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi degli indirizzi valida, vedere la descrizione della parola chiave ODBC del **Server** in questo argomento.|  
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Timeout**|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Se impostata su "yes", indica al provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare la Modalità di autenticazione di Windows per la convalida dell'accesso. In caso contrario, indica al provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare un nome utente e una password di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per la convalida dell'accesso e richiede la specifica delle parole chiave UID e PWD.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "yes" e "no" come valori. Il valore predefinito è "no", il quale indica che il certificato server verrà convalidato.|  
|**UID**|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Questa parola chiave è deprecata e la relativa impostazione viene ignorata dal provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**WSID**|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 Le stringhe di connessione usate nelle applicazioni OLE DB che usano **IDataInitialize::GetDataSource** presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 L'utilizzo delle proprietà deve essere conforme alla sintassi consentita nel relativo ambito.  Per **WSID** vengono ad esempio usate le parentesi graffe (**{}**) come virgolette e per **Application Name** vengono usate le virgolette semplici (**'**) o doppie (**"**). Solo per le proprietà delle stringhe è possibile utilizzare le virgolette. Se si tenta di utilizzare le virgolette con una proprietà Integer o enumerata, verrà generato un errore che indica che la stringa di connessione non è conforme alla specifica OLE DB.  
  
 È consigliabile racchiudere i valori di attributo tra virgolette semplici o doppie per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori. Se raddoppiato, il carattere virgoletta può essere visualizzato anche per i valori.  
  
 Uno spazio dopo il segno = in una parola chiave di una stringa di connessione verrà interpretato come valore letterale, anche se il valore è racchiuso tra virgolette.  
  
 Se una stringa di connessione include più di una delle proprietà elencate nella tabella seguente, verrà utilizzato il valore dell'ultima proprietà.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere usate con **IDataInitialize::GetDataSource**:  
  
|Parola chiave|Proprietà di inizializzazione|Descrizione|  
|-------------|-----------------------------|-----------------|  
|**Nome applicazione**|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|**Finalità dell'applicazione**|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.<br /><br /> Il valore predefinito è **ReadWrite**. Per ulteriori informazioni sul [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto di Native Client per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native client supporto per la disponibilità elevata e il ripristino di emergenza](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**Conversione automatica**|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "true" e "false".|  
|**Timeout connessione**|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|**Lingua corrente**|SSPROPT_INIT_CURRENTLANGUAGE|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Origine dati**|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi degli indirizzi valida, vedere la descrizione della parola chiave ODBC del **Server** , più avanti in questo argomento.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati da utilizzare. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|  
|**Partner di failover**|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|**Nome SPN del partner di failover**|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Catalogo iniziale**|DBPROP_INIT_CATALOG|Nome del database.|  
|**Nome file iniziale**|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per usare **AttachDBFileName**, è necessario specificare anche il nome del database con la parola chiave DATABASE della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**Sicurezza integrata**|DBPROP_AUTH_INTEGRATED|Accetta il valore "SSPI" per l'autenticazione di Windows.|  
|**Connessione MARS**|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione. I valori riconosciuti sono "true" e "false". Il valore predefinito è "false".|  
|**Indirizzo di rete**|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi degli indirizzi valida, vedere la descrizione della parola chiave **Address** ODBC più avanti in questo argomento.|  
|**Libreria di rete**|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|**Dimensioni pacchetto**|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|**Password**|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Mantieni informazioni di sicurezza**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "true" e "false" come valori. Se il valore è impostato su "false", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate|  
|**Provider**||Per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, deve essere "SQLNCLI11".|  
|**SPN server**|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Certificato server attendibile**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "true" e "false" come valori. Il valore predefinito è "false", il quale indica che il certificato server verrà convalidato.|  
|**Usare la crittografia per i dati**|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "true" e "false". Il valore predefinito è "false".|  
|**ID utente**|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**ID workstation**|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 **Nota** Nella stringa di connessione la proprietà "vecchia password" imposta SSPROP_AUTH_OLD_PASSWORD, ovvero la password corrente (probabilmente scaduta) che non è disponibile tramite una proprietà della stringa del provider.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Parole chiave delle stringhe di connessione per gli oggetti ADO (ActiveX Data Objects)  
 Le applicazioni ADO impostano la proprietà **ConnectionString** degli oggetti **ADODBConnection** o forniscono una stringa di connessione come parametro al metodo **Open** degli oggetti **ADODBConnection**.  
  
 Le applicazioni ADO supportano anche le parole chiave usate dal metodo **IDBInitialize::Initialize** OLE DB, ma solo per le proprietà che non hanno un valore predefinito. Se in un'applicazione vengono usate sia le parole chiave ADO che le parole chiave **IDBInitialize::Initialize** nella stringa di inizializzazione, verrà usata l'impostazione della parola chiave ADO. Nelle applicazioni è consigliabile utilizzare solo le parole chiave delle stringhe di connessione ADO.  
  
 Le stringhe di connessione utilizzate da ADO presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra virgolette doppie per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori. I valori attributo non possono contenere virgolette doppie.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con una stringa di connessione ADO:  
  
|Parola chiave|Proprietà di inizializzazione|Descrizione|  
|-------------|-----------------------------|-----------------|  
|**Finalità dell'applicazione**|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono **ReadOnly** e **ReadWrite**.<br /><br /> Il valore predefinito è **ReadWrite**. Per ulteriori informazioni sul [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] supporto di Native Client per [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native client supporto per la disponibilità elevata e il ripristino di emergenza](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|**Nome applicazione**|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|**Conversione automatica**|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "true" e "false".|  
|**Timeout connessione**|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|**Lingua corrente**|SSPROPT_INIT_CURRENTLANGUAGE|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Origine dati**|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi degli indirizzi valida, vedere la descrizione della parola chiave ODBC del **Server** in questo argomento.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati che verrà utilizzata. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di SQL Server 2000.|  
|**Partner di failover**|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|**Nome SPN del partner di failover**|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Catalogo iniziale**|DBPROP_INIT_CATALOG|Nome del database.|  
|**Nome file iniziale**|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare **AttachDBFilename**, è necessario specificare anche il nome del database con la parola chiave del database stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|**Sicurezza integrata**|DBPROP_AUTH_INTEGRATED|Accetta il valore "SSPI" per l'autenticazione di Windows.|  
|**Connessione MARS**|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione se il server è [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. I valori riconosciuti sono "true" e "false". Il valore predefinito è "false".|  
|**Indirizzo di rete**|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi degli indirizzi valida, vedere la descrizione della parola chiave **Address** ODBC in questo argomento.|  
|**Libreria di rete**|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|**Dimensioni pacchetto**|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|**Password**|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Mantieni informazioni di sicurezza**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "true" e "false" come valori. Se il valore è impostato su "false", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate.|  
|**Provider**||Per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, deve essere "SQLNCLI11".|  
|**SPN server**|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|**Certificato server attendibile**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "true" e "false" come valori. Il valore predefinito è "false", il quale indica che il certificato server verrà convalidato.|  
|**Usare la crittografia per i dati**|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "true" e "false". Il valore predefinito è "false".|  
|**ID utente**|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**ID workstation**|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 **Nota** Nella stringa di connessione la proprietà "vecchia password" imposta SSPROP_AUTH_OLD_PASSWORD, ovvero la password corrente (probabilmente scaduta) che non è disponibile tramite una proprietà della stringa del provider.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
