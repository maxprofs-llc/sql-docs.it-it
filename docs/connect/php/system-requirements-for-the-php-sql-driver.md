---
title: Requisiti di sistema dei driver Microsoft per PHP per SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/31/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- requirements
ms.assetid: 5db4b75f-c605-4785-9560-399a533c0fc9
author: MightyPen
ms.reviewer: carlrab
ms.author: genemi
ms.openlocfilehash: f384e121d3b4ce0aa7ebcb380ebe5eaaa0ee3d45
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2020
ms.locfileid: "76917817"
---
# <a name="system-requirements-for-the-microsoft-drivers-for-php-for-sql-server"></a>Requisiti di sistema dei driver Microsoft per PHP per SQL Server

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In questo articolo sono riportati i componenti che devono essere installati nel sistema per accedere ai dati in SQL Server o nel database SQL di Azure usando il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)].

Sono ufficialmente supportate le versioni 3.2 e successive dei driver Microsoft PHP per SQL Server. Per informazioni dettagliate sui cicli di vita del supporto e sui requisiti dei driver PHP, vedere la [matrice di supporto](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md).

## <a name="php"></a>PHP

Per informazioni su come scaricare e installare i file binari PHP stabili più recenti, vedere [il sito Web PHP](https://php.net).  I driver Microsoft per PHP per SQL Server richiedono le versioni corrette di PHP come descritto in [Supporto versione PHP](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md#php-version-support).

-   La versione corretta del file di driver deve essere abilitata con la versione di PHP corrispondente. Per informazioni sui diversi file di driver, vedere [Versioni dei driver](#driver-versions).  Per scaricare i driver, vedere [Scaricare i driver Microsoft per PHP per SQL Server](../../connect/php/download-drivers-php-sql-server.md). Per informazioni sulla configurazione del driver per PHP, vedere [Caricare i driver Microsoft per PHP per SQL Server](../../connect/php/loading-the-php-sql-driver.md).

-   È necessario un server Web. Il server Web deve essere configurato per eseguire PHP. Per informazioni sull'hosting di applicazioni PHP con IIS, vedere l'[esercitazione sul sito Web di PHP](http://docs.php.net/manual/da/install.windows.iis7.php).

    Il [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] è stato testato tramite IIS 10 con FastCGI.

    > [!NOTE]
    > Microsoft fornisce il supporto solo per IIS.

## <a name="odbc-driver"></a>Driver ODBC

È necessaria la versione corretta di Microsoft ODBC Driver for SQL Server nel computer in cui è in esecuzione PHP. È possibile scaricare tutte le versioni supportate del driver per le piattaforme supportate in [questa pagina](https://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server?view=sql-server-2017).

Se si scarica la versione di Windows del driver in una versione di Windows a 64 bit, il programma di installazione di ODBC 64-bit installa i driver ODBC sia a 32 bit che a 64 bit. Se si usa una versione a 32 bit di Windows, usare il programma di installazione di ODBC x86. Per le piattaforme non Windows sono disponibili solo le versioni a 64 bit del driver.

|PHP per la versione del driver SQL Server &#8594;<br />&#8595; Versione driver ODBC|5.8|5.6|5.3|5,2|4.3|4.0|3.2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|ODBC Driver 17+ |S|S|S|S| | | |
|Driver ODBC 13.1|S|S|S|S|S|S| |
|Driver ODBC 13  | | | | | |S| |
|Driver ODBC 11  |S|S|S|S|S|S|S|

Se si usa il driver SQLSRV, [sqlsrv_client_info](../../connect/php/sqlsrv-client-info.md) restituisce informazioni sulla versione di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft ODBC Driver for SQL Server usata da [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Se si usa il driver PDO_SQLSRV, è possibile individuarne la versione tramite [PDO::getAttribute](../../connect/php/pdo-getattribute.md).

## <a name="sql-server"></a>SQL Server

Per informazioni sull'uso di PHP con il database SQL di Azure, vedere [Connessione al database SQL di Microsoft Azure](../../connect/php/connecting-to-microsoft-azure-sql-database.md).

|PHP per la versione del driver SQL Server &#8594;<br />&#8595; Versione di SQL Server|5.8|5.6|5.3|5,2|4.3|4.0|3.2|
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Database SQL di Azure (tutte le opzioni di distribuzione)        |S|S|S|S| | | |
|Synapse SQL di Azure  |S|S|S|S| | | |
|SQL Server 2019           |S|S|S|S| | | |
|SQL Server 2017           |S|S|S|S| | | |
|SQL Server 2016           |S|S|S|S|S| | |
|SQL Server 2014           |S|S|S|S|S|S|S|
|SQL Server 2012           |S|S|S|S|S|S|S|
|SQL Server 2008 R2        | |S|S|S|S|S|S|
|SQL Server 2008           | | | | |S|S|S|

## <a name="operating-systems"></a>Sistemi operativi

Per informazioni dettagliate sui sistemi operativi supportati, vedere l'elenco dei [sistemi operativi supportati](../../connect/php/microsoft-php-drivers-for-sql-server-support-matrix.md#supported-operating-systems).

## <a name="driver-versions"></a>Versioni dei driver

In questa sezione sono elencati i file di driver inclusi in ogni versione di [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]. Ogni pacchetto di installazione contiene i file dei driver SQLSRV e PDO_SQLSRV nelle varianti con e senza threading. In Windows sono disponibili anche in varianti a 32 bit e a 64 bit. Per configurare il driver per l'uso con il runtime PHP, seguire le istruzioni di installazione in [Caricamento dei driver Microsoft per PHP per SQL Server](../../connect/php/loading-the-php-sql-driver.md).

Nelle versioni supportate di Linux e macOS i driver appropriati possono essere installati usando il sistema di pacchetti PECL di PHP, seguendo le [istruzioni di installazione di Linux e macOS](../../connect/php/installation-tutorial-linux-mac.md). In alternativa, è possibile scaricare i file binari predefiniti per la piattaforma dalla pagina del progetto GitHub [Driver Microsoft per PHP per SQL Server](https://github.com/Microsoft/msphpsql/releases). Nelle tabelle seguenti sono elencati i file presenti nei pacchetti binari predefiniti.

**Microsoft Driver 5.8 per PHP per SQL Server:**

In Windows sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|Uso con PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|no |32-bit php7.dll|
|32-bit php_sqlsrv_72_ts.dll <br />php_pdo_sqlsrv_72_ts.dll a 32 bit |7.2|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|no |64-bit php7.dll|
|64-bit php_sqlsrv_72_ts.dll <br />php_pdo_sqlsrv_72_ts.dll a 64 bit |7.2|sì|64-bit php7ts.dll|
|32-bit php_sqlsrv_73_nts.dll<br />32-bit php_pdo_sqlsrv_73_nts.dll|7.3|no |32-bit php7.dll|
|32-bit php_sqlsrv_73_ts.dll <br />php_pdo_sqlsrv_73_ts.dll a 32 bit |7.3|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_73_nts.dll<br />64-bit php_pdo_sqlsrv_73_nts.dll|7.3|no |64-bit php7.dll|
|64-bit php_sqlsrv_73_ts.dll <br />php_pdo_sqlsrv_73_ts.dll a 64 bit |7.3|sì|64-bit php7ts.dll|
|32-bit php_sqlsrv_74_nts.dll<br />32-bit php_pdo_sqlsrv_74_nts.dll|7.4|no |32-bit php7.dll|
|32-bit php_sqlsrv_74_ts.dll <br />32-bit php_pdo_sqlsrv_74_ts.dll |7.4|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_74_nts.dll<br />64-bit php_pdo_sqlsrv_74_nts.dll|7.4|no |64-bit php7.dll|
|64-bit php_sqlsrv_74_ts.dll <br />64-bit php_pdo_sqlsrv_74_ts.dll |7.4|sì|64-bit php7ts.dll|

In Linux sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|no |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|sì|
|php_sqlsrv_73_nts.so<br />php_pdo_sqlsrv_73_nts.so|7.3|no |
|php_sqlsrv_73_ts.so <br />php_pdo_sqlsrv_73_ts.so |7.3|sì|
|php_sqlsrv_74_nts.so<br />php_pdo_sqlsrv_74_nts.so|7.4|no |
|php_sqlsrv_74_ts.so <br />php_pdo_sqlsrv_74_ts.so |7.4|sì|

**Microsoft Driver 5.6 per PHP per SQL Server:**

In Windows sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|Uso con PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |32-bit php7.dll|
|32-bit php_sqlsrv_71_ts.dll <br />php_pdo_sqlsrv_71_ts.dll a 32 bit |7.1|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |64-bit php7.dll|
|64-bit php_sqlsrv_71_ts.dll <br />php_pdo_sqlsrv_71_ts.dll a 64 bit |7.1|sì|64-bit php7ts.dll|
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|no |32-bit php7.dll|
|32-bit php_sqlsrv_72_ts.dll <br />php_pdo_sqlsrv_72_ts.dll a 32 bit |7.2|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|no |64-bit php7.dll|
|64-bit php_sqlsrv_72_ts.dll <br />php_pdo_sqlsrv_72_ts.dll a 64 bit |7.2|sì|64-bit php7ts.dll|
|32-bit php_sqlsrv_73_nts.dll<br />32-bit php_pdo_sqlsrv_73_nts.dll|7.3|no |32-bit php7.dll|
|32-bit php_sqlsrv_73_ts.dll <br />php_pdo_sqlsrv_73_ts.dll a 32 bit |7.3|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_73_nts.dll<br />64-bit php_pdo_sqlsrv_73_nts.dll|7.3|no |64-bit php7.dll|
|64-bit php_sqlsrv_73_ts.dll <br />php_pdo_sqlsrv_73_ts.dll a 64 bit |7.3|sì|64-bit php7ts.dll|

In Linux sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|no |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|sì|
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|no |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|sì|
|php_sqlsrv_73_nts.so<br />php_pdo_sqlsrv_73_nts.so|7.3|no |
|php_sqlsrv_73_ts.so <br />php_pdo_sqlsrv_73_ts.so |7.3|sì|

**Microsoft Driver 5.3 per PHP per SQL Server:**

In Windows sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|Uso con PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-bit php_sqlsrv_7_nts.dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|no |32-bit php7.dll|
|32-bit php_sqlsrv_7_ts.dll  <br />php_pdo_sqlsrv_7_ts.dll a 32 bit  |7.0|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_7_nts.dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|no |64-bit php7.dll|
|64-bit php_sqlsrv_7_ts.dll  <br />php_pdo_sqlsrv_7_ts.dll a 64 bit  |7.0|sì|64-bit php7ts.dll|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |32-bit php7.dll|
|32-bit php_sqlsrv_71_ts.dll <br />php_pdo_sqlsrv_71_ts.dll a 32 bit |7.1|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |64-bit php7.dll|
|64-bit php_sqlsrv_71_ts.dll <br />php_pdo_sqlsrv_71_ts.dll a 64 bit |7.1|sì|64-bit php7ts.dll|
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|no |32-bit php7.dll|
|32-bit php_sqlsrv_72_ts.dll <br />php_pdo_sqlsrv_72_ts.dll a 32 bit |7.2|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|no |64-bit php7.dll|
|64-bit php_sqlsrv_72_ts.dll <br />php_pdo_sqlsrv_72_ts.dll a 64 bit |7.2|sì|64-bit php7ts.dll|

In Linux sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|no |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|sì|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|no |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|sì|
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|no |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|sì|

**Microsoft Driver 5.2 per PHP per SQL Server**

In Windows sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|Uso con PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-bit php_sqlsrv_7_nts.dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|no |32-bit php7.dll|
|32-bit php_sqlsrv_7_ts.dll  <br />php_pdo_sqlsrv_7_ts.dll a 32 bit  |7.0|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_7_nts.dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|no |64-bit php7.dll|
|64-bit php_sqlsrv_7_ts.dll  <br />php_pdo_sqlsrv_7_ts.dll a 64 bit  |7.0|sì|64-bit php7ts.dll|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |32-bit php7.dll|
|32-bit php_sqlsrv_71_ts.dll <br />php_pdo_sqlsrv_71_ts.dll a 32 bit |7.1|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |64-bit php7.dll|
|64-bit php_sqlsrv_71_ts.dll <br />php_pdo_sqlsrv_71_ts.dll a 64 bit |7.1|sì|64-bit php7ts.dll|
|32-bit php_sqlsrv_72_nts.dll<br />32-bit php_pdo_sqlsrv_72_nts.dll|7.2|no |32-bit php7.dll|
|32-bit php_sqlsrv_72_ts.dll <br />php_pdo_sqlsrv_72_ts.dll a 32 bit |7.2|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_72_nts.dll<br />64-bit php_pdo_sqlsrv_72_nts.dll|7.2|no |64-bit php7.dll|
|64-bit php_sqlsrv_72_ts.dll <br />php_pdo_sqlsrv_72_ts.dll a 64 bit |7.2|sì|64-bit php7ts.dll|

In Linux sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|no |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|sì|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|no |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|sì|
|php_sqlsrv_72_nts.so<br />php_pdo_sqlsrv_72_nts.so|7.2|no |
|php_sqlsrv_72_ts.so <br />php_pdo_sqlsrv_72_ts.so |7.2|sì|

**Microsoft Driver 4.3 per PHP per SQL Server:**

In Windows sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|Uso con PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|32-bit php_sqlsrv_7_nts.dll <br />32-bit php_pdo_sqlsrv_7_nts.dll |7.0|no |32-bit php7.dll|
|32-bit php_sqlsrv_7_ts.dll  <br />php_pdo_sqlsrv_7_ts.dll a 32 bit  |7.0|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_7_nts.dll <br />64-bit php_pdo_sqlsrv_7_nts.dll |7.0|no |64-bit php7.dll|
|64-bit php_sqlsrv_7_ts.dll  <br />php_pdo_sqlsrv_7_ts.dll a 64 bit  |7.0|sì|64-bit php7ts.dll|
|32-bit php_sqlsrv_71_nts.dll<br />32-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |32-bit php7.dll|
|32-bit php_sqlsrv_71_ts.dll <br />php_pdo_sqlsrv_71_ts.dll a 32 bit |7.1|sì|32-bit php7ts.dll|
|64-bit php_sqlsrv_71_nts.dll<br />64-bit php_pdo_sqlsrv_71_nts.dll|7.1|no |64-bit php7.dll|
|64-bit php_sqlsrv_71_ts.dll <br />php_pdo_sqlsrv_71_ts.dll a 64 bit |7.1|sì|64-bit php7ts.dll|

In Linux sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|no |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|sì|
|php_sqlsrv_71_nts.so<br />php_pdo_sqlsrv_71_nts.so|7.1|no |
|php_sqlsrv_71_ts.so <br />php_pdo_sqlsrv_71_ts.so |7.1|sì|

**Microsoft Driver 4.0 per PHP per SQL Server:**

In Windows sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|Uso con PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|php_sqlsrv_7_nts_x86.dll<br />php_pdo_sqlsrv_7_nts_x86.dll|7.0|no|32-bit php7.dll|
|php_sqlsrv_7_ts_x86.dll<br />php_pdo_sqlsrv_7_ts_x86.dll|7.0|sì|32-bit php7ts.dll|
|php_sqlsrv_7_nts_x64.dll<br />php_pdo_sqlsrv_7_nts_x64.dll|7.0|no|64-bit php7.dll|
|php_sqlsrv_7_ts_x64.dll<br />php_pdo_sqlsrv_7_ts_x64.dll|7.0|sì|64-bit php7ts.dll|

In Linux sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|
|---------------|:---------------:|:----------------:|
|php_sqlsrv_7_nts.so <br />php_pdo_sqlsrv_7_nts.so |7.0|no |
|php_sqlsrv_7_ts.so  <br />php_pdo_sqlsrv_7_ts.so  |7.0|sì|

**Microsoft Driver 3.2 per PHP per SQL Server:**

In Windows sono incluse le seguenti versioni del driver:

|File del driver|Versione di PHP|Thread-safe?|Uso con PHP .dll|
|---------------|:---------------:|:----------------:|---------------------|
|php_sqlsrv_54_nts.dll<br />php_pdo_sqlsrv_54_nts.dll|5.4|no|php5.dll|
|php_sqlsrv_54_ts.dll<br />php_pdo_sqlsrv_54_ts.dll|5.4|sì|php5ts.dll|
|php_sqlsrv_55_nts.dll<br />php_pdo_sqlsrv_55_nts.dll|5.5|no|php5.dll|
|php_sqlsrv_55_ts.dll<br />php_pdo_sqlsrv_55_ts.dll|5.5|sì|php5ts.dll|
|php_sqlsrv_56_nts.dll<br />php_pdo_sqlsrv_56_nts.dll|5.6|no|php5.dll|
|php_sqlsrv_56_ts.dll<br />php_pdo_sqlsrv_56_ts.dll|5.6|sì|php5ts.dll|

## <a name="see-also"></a>Vedere anche

- [Introduzione ai driver Microsoft per PHP per SQL Server](../../connect/php/getting-started-with-the-php-sql-driver.md)
- [Guida alla programmazione per i driver Microsoft per PHP per SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)
- [Riferimento all'API del driver SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)
- [Riferimento all'API del driver PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)
