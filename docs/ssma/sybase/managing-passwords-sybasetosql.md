---
title: Gestione delle password (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Exporting or Importing Encrypted Passwords
- Sybase Console,Managing Passwords
- Sybase Console,Securing Password
ms.assetid: 9b6a70f9-6840-4140-a059-bb7bd7ccc67c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 14cd4a9c4fb3c49bfa3bd5778e4872bd7b002017
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "68028904"
---
# <a name="managing-passwords-sybasetosql"></a>Gestione delle password (SybaseToSQL)
In questa sezione viene illustrata la protezione delle password del database e la procedura per importarli o esportarli tra server:  
  
1.  Sicurezza della password  
  
2.  Esportazione o importazione della password crittografata  
  
## <a name="securing-password"></a>Sicurezza della password  
SSMA consente di proteggere la password di un database.  
  
Per implementare una connessione protetta, attenersi alla procedura seguente:  
  
Specificare una password valida utilizzando uno dei tre metodi seguenti:  
  
1.  **Testo non crittografato:** Digitare la password del database nell'attributo value del nodo ' password '. Si trova nel nodo definizione server della sezione server del file di script o di connessione al server.  
  
    Le password in testo non crittografato non sono sicure. Pertanto, nell'output della console verrà visualizzato il seguente messaggio di avviso: *"server &lt;-ID&gt; password è disponibile in formato testo non protetto, l'applicazione console SSMA fornisce un'opzione per proteggere la password tramite crittografia. per ulteriori informazioni, vedere l'opzione-SecurePassword nel file della Guida di SSMA."*  
  
    **Password crittografate:** La password specificata, in questo caso, viene archiviata in formato crittografato nel computer locale in ProtectedStorage. SSMA.  
  
    -   **Protezione delle password**  
  
        -   Eseguire `SSMAforSybaseConsole.exe` con `-securepassword` e aggiungere switch alla riga di comando passando la connessione al server o il file di script contenente il nodo password nella sezione relativa alla definizione del server.  
  
        -   Al prompt, all'utente viene richiesto di immettere la password del database e di confermarla.  
  
            Gli ID di definizione del server e le password crittografate corrispondenti vengono archiviati in un file nel computer locale  
            
            Esempio 1:  
            
                Specify password
                
                C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -add all -s "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\AssessmentReportGenerationSample.xml" -v "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ VariableValueFileSample.xml"
                
                Enter password for server_id 'XXX_1': xxxxxxx
                
                Re-enter password for server_id 'XXX_1': xxxxxxx
            
            Esempio 2:
            
                C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -add "source_1,target_1" -c "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ServersConnectionFileSample.xml" - v "D:\Program Files\Microsoft SQL Server Migration Assistant for Sybase\Sample Console Scripts\ VariableValueFileSample.xml" -o
                
                Enter password for server_id 'source_1': xxxxxxx
                
                Re-enter password for server_id 'source_1': xxxxxxx
                
                Enter password for server_id 'target_1': xxxxxxx
                
                Re-enter password for server_id 'target _1': xxxxxxx  
    
    -   **Rimozione delle password crittografate**  
  
        Eseguire `SSMAforSybaseConsole.exe` con l'`-securepassword` opzione e `-remove` nella riga di comando passando gli ID server per rimuovere le password crittografate dal file di archiviazione protetto presente nel computer locale.  
  
        Esempio:  
        
            C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -remove all
            C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -remove "source_1,target_1"  
  
    -   **Elenco di ID server le cui password sono crittografate**  
  
        Eseguire `SSMAforSybaseConsole.exe` con `-securepassword` e `-list` passare alla riga di comando per elencare tutti gli ID server le cui password sono state crittografate.  
  
        Esempio:  
        
            C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -list  
  
    > [!NOTE]  
    > 1.  La password in testo non crittografato indicato nel file di connessione dello script o del server ha la precedenza sulla password crittografata in un file protetto.  
    > 2.  Se nella sezione server del file di connessione del server o del file di script non è presente alcuna password o se non è stata protetta nel computer locale, nella console viene richiesto di immettere la password.  
  
## <a name="exporting-or-importing-encrypted-passwords"></a>Esportazione o importazione di password crittografate  
L'applicazione console SSMA consente di esportare le password di database crittografate presenti in un file nel computer locale in un file protetto e viceversa. Consente di rendere le password crittografate indipendenti dal computer. La funzionalità di esportazione consente di leggere l'ID e la password del server dall'archiviazione protetta locale e di salvare le informazioni in un file crittografato. All'utente viene richiesto di immettere la password per il file protetto. Verificare che la password immessa sia di 8 caratteri o superiore. Questo file protetto è portabile tra computer diversi. La funzionalità di importazione legge le informazioni relative all'ID server e alla password dal file protetto. All'utente viene richiesto di immettere la password per il file protetto e di accodare le informazioni all'archivio locale protetto.  
  
Esempio:  

    Export password
    
    Enter password for protecting the exported file
    
    C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -export all "machine1passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforSybaseConsole.EXE -p -e "SybaseDB_1_1,Sql_1" "machine2passwords.file"
    
    Enter password for protecting the exported file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
Esempio:  

    Import an encrypted password
    
    Enter password for protecting the imported file
    
    C:\SSMA\SSMAforSybaseConsole.EXE -securepassword -import all "machine1passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx
    
    C:\SSMA\SSMAforSybaseConsole.EXE -p -i "SybaseDB_1,Sql_1" "machine2passwords.file"
    
    Enter password to import the servers from encrypted file: xxxxxxxx
    
    Please confirm password: xxxxxxxx  
  
## <a name="see-also"></a>Vedere anche  
[Esecuzione della console SSMA (Sybase)](https://msdn.microsoft.com/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
