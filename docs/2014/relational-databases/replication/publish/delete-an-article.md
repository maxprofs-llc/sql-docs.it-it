---
title: Eliminare un articolo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- articles [SQL Server replication], dropping
- sp_droparticle
- sp_dropmergearticle
- deleting articles
- removing articles
- dropping articles
ms.assetid: 185b58fc-38c0-4abe-822e-6ec20066c863
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4be2287a1c0d43ccfdfaeaca3378f6d10f100134
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2020
ms.locfileid: "73882277"
---
# <a name="delete-an-article"></a>Eliminazione di un articolo
  In questo argomento viene descritto come eliminare un articolo in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] tramite [!INCLUDE[tsql](../../../includes/tsql-md.md)] o RMO (Replication Management Objects). Per informazioni sulle condizioni per l'eliminazione degli articoli e sulla necessità di creare un nuovo snapshot o reinizializzare le sottoscrizioni in seguito all'eliminazione di un articolo, vedere [Aggiungere ed eliminare articoli in pubblicazioni esistenti](add-articles-to-and-drop-articles-from-existing-publications.md).  
  
  
##  <a name="TsqlProcedure"></a> Con Transact-SQL  
 È possibile eliminare gli articoli a livello di programmazione tramite le stored procedure di replica. Le stored procedure utilizzate dipenderanno dal tipo di pubblicazione a cui appartiene l'articolo.  
  
#### <a name="to-delete-an-article-from-a-snapshot-or-transactional-publication"></a>Per eliminare un articolo da una pubblicazione snapshot o transazionale  
  
1.  Eseguire [sp_droparticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-droparticle-transact-sql) per eliminare un articolo, specificato da **\@article**, da una pubblicazione, specificata da **\@publication**. Specificare il valore **1** per **\@force_invalidate_snapshot**.  
  
2.  (Facoltativo) Per rimuovere completamente l'oggetto pubblicato dal database, eseguire il comando `DROP <objectname>` nel database di pubblicazione del server di pubblicazione.  
  
#### <a name="to-delete-an-article-from-a-merge-publication"></a>Per eliminare un articolo da una pubblicazione di tipo merge  
  
1.  Eseguire [sp_dropmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql) per eliminare un articolo, specificato da **\@article**, da una pubblicazione, specificata da **\@publication**. Se necessario, specificare il valore **1** per **\@force_invalidate_snapshot** e il valore **1** per **\@force_reinit_subscription**.  
  
2.  (Facoltativo) Per rimuovere completamente l'oggetto pubblicato dal database, eseguire il comando `DROP <objectname>` nel database di pubblicazione del server di pubblicazione.  
  
###  <a name="TsqlExample"></a> Esempi (Transact-SQL)  
 Nell'esempio seguente un articolo viene eliminato da una pubblicazione transazionale. Dato che questa modifica rende non valido lo snapshot esistente, viene specificato il valore **1** per il parametro **\@force_invalidate_snapshot**.  
  
 [!code-sql[HowTo#sp_droparticle](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droparticle)]  
  
 Nell'esempio seguente due articoli vengono eliminati da una pubblicazione di tipo merge. Dato che queste modifiche rendono non valido lo snapshot esistente, viene specificato il valore **1** per il parametro **\@force_invalidate_snapshot**.  
  
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergearticle)]
 [!code-sql[HowTo#sp_dropmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergearticles.sql#sp_dropmergearticle)]  
  
##  <a name="RMOProcedure"></a> Utilizzo di RMO (Replication Management Objects)  
 È possibile eliminare articoli a livello di programmazione tramite gli oggetti RMO (Replication Management Objects). Le classi RMO utilizzate per l'eliminazione di un articolo dipendono dal tipo di pubblicazione cui appartiene l'articolo.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a>Per eliminare un articolo che appartiene a una pubblicazione snapshot o transazionale  
  
1.  Creare una connessione al server di pubblicazione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.TransArticle>.  
  
3.  Impostare le proprietà <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>e <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Impostare la connessione del passaggio 1 per la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Controllare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> per verificare che l'articolo esista. Se il valore di questa proprietà è `false`, le proprietà dell'articolo sono state definite in modo non corretto nel passaggio 3 oppure l'articolo non esiste.  
  
6.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> .  
  
7.  Chiudere tutte le connessioni.  
  
#### <a name="to-delete-an-article-that-belongs-to-a-merge-publication"></a>Per eliminare un articolo che appartiene a una pubblicazione di tipo merge  
  
1.  Creare una connessione al server di pubblicazione tramite la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Creare un'istanza della classe <xref:Microsoft.SqlServer.Replication.MergeArticle>.  
  
3.  Impostare le proprietà <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>e <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Impostare la connessione del passaggio 1 per la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Controllare la proprietà <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> per verificare che l'articolo esista. Se il valore di questa proprietà è `false`, le proprietà dell'articolo sono state definite in modo non corretto nel passaggio 3 oppure l'articolo non esiste.  
  
6.  Chiamare il metodo <xref:Microsoft.SqlServer.Replication.Article.Remove%2A> .  
  
7.  Chiudere tutte le connessioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere ed eliminare articoli in pubblicazioni esistenti](add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
