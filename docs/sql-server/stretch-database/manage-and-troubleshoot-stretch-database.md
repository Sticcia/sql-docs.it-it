---
title: Gestire e risolvere i problemi di Stretch Database | Microsoft Docs
ms.date: 06/27/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, managing
- Stretch Database, troubleshooting
- managing Stretch Database
- troubleshooting Stretch Database
ms.assetid: 6334db3e-9297-44df-8d53-211187a95520
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b6e24af8c3117c85e2dbeb90f2482ca55db9eac6
ms.sourcegitcommit: ec1f01b4bb54621de62ee488decf9511d651d700
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2019
ms.locfileid: "56240825"
---
# <a name="manage-and-troubleshoot-stretch-database"></a>Gestione e risoluzione dei problemi di Stretch Database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Per gestire e risolvere i problemi di Stretch Database, usare gli strumenti e i metodi descritti in questo articolo.  
## <a name="manage-local-data"></a>Gestire i dati locali  
  
###  <a name="LocalInfo"></a> Ottenere informazioni su tabelle e database locali abilitati per Stretch Database  
 Aprire le viste del catalogo **sys.databases** e **sys.tables** per visualizzare informazioni sulle tabelle e i database di SQL Server abilitati per l'estensione. Per altre informazioni, vedere [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) e [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md).  
 
 Per visualizzare la quantità di spazio usata da una tabella abilitata per l'estensione in SQL Server, eseguire questa istruzione.
 
 ```sql
USE <Stretch-enabled database name>;
GO
EXEC sp_spaceused '<Stretch-enabled table name>', 'true', 'LOCAL_ONLY';
GO
 ```
   
## <a name="manage-data-migration"></a>Gestire la migrazione dei dati  
  
### <a name="check-the-filter-function-applied-to-a-table"></a>Verificare la funzione di filtro applicata a una tabella  
 Aprire la vista del catalogo **sys.remote_data_archive_tables** e verificare il valore della colonna **filter_predicate** per trovare la funzione usata da Stretch Database per selezionare le righe per la migrazione. Se il valore è null, l'intera tabella è idonea per la migrazione. Per altre informazioni, vedere [sys.remote_data_archive_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md) e [Selezionare le righe di cui eseguire la migrazione tramite una funzione di filtro](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md).  
  
###  <a name="Migration"></a> Controllare lo stato della migrazione dei dati  
 Selezionare **Attività | Stretch | Monitoraggio** per un database in SQL Server Management Studio per monitorare la migrazione dei dati in Monitoraggio di Stretch Database. Per altre informazioni, vedere [Monitorare e risolvere i problemi relativi alla migrazione dei dati &#40;Stretch Database&#41;](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
 In alternativa, aprire la DMV **sys.dm_db_rda_migration_status** per visualizzare il numero di batch e righe di dati di cui è stata eseguita la migrazione.  
  
###  <a name="Firewall"></a> Risolvere i problemi relativi alla migrazione dei dati  
 Per consigli sulla risoluzione dei problemi, vedere [Monitorare e risolvere i problemi relativi alla migrazione dei dati &#40;Stretch Database&#41;](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md).  
  
## <a name="manage-remote-data"></a>Gestire i dati remoti  
  
###  <a name="RemoteInfo"></a> Ottenere informazioni su tabelle e database remoti usati da Stretch Database  
 Aprire le viste del catalogo **sys.remote_data_archive_databases** e **sys.remote_data_archive_tables** per visualizzare informazioni sulle tabelle e i database remoti in cui sono memorizzati i dati migrati. Per altre informazioni, vedere [sys.remote_data_archive_databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-databases.md) e [sys.remote_data_archive_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-tables.md).  
 
Per visualizzare la quantità di spazio usata da una tabella abilitata per l'estensione in Azure, eseguire questa istruzione.
 
 ```sql
USE <Stretch-enabled database name>;
GO
EXEC sp_spaceused '<Stretch-enabled table name>', 'true', 'REMOTE_ONLY';
GO
 ```

### <a name="delete-migrated-data"></a>Eliminare i dati migrati  
Per eliminare i dati di cui è già stata eseguita la migrazione in Azure, seguire i passaggi descritti in [sys.sp_rda_reconcile_batch](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-batch-transact-sql.md).  
  
## <a name="manage-table-schema"></a>Gestire lo schema di una tabella

### <a name="dont-change-the-schema-of-the-remote-table"></a>Non modificare lo schema di una tabella remota  
 Non modificare lo schema di una tabella remota di Azure associata a una tabella di SQL Server configurata per Stretch Database. In particolare, non modificare il nome o il tipo di dati di una colonna. La funzionalità Stretch Database formula varie ipotesi relative allo schema della tabella remota in relazione allo schema della tabella di SQL Server. Se si modifica lo schema remoto, Stretch Database smetterà di funzionare per la tabella modificata.  

### <a name="reconcile-table-columns"></a>Riconciliare le colonne della tabella  
Se sono state accidentalmente eliminate colonne dalla tabella remota, eseguire **sp_rda_reconcile_columns** per aggiungere colonne alla tabella remota presenti nella tabella di SQL Server abilitata per l'estensione, ma non nella tabella remota. Per altre informazioni, vedere [sys.sp_rda_reconcile_columns](../../relational-databases/system-stored-procedures/sys-sp-rda-reconcile-columns-transact-sql.md).  
  
  > [!IMPORTANT]
  > Quando **sp_rda_reconcile_columns** crea nuovamente le colonne accidentalmente eliminate dalla tabella remota, non ripristina i dati che erano presenti nelle colonne eliminate.
  
**sp_rda_reconcile_columns** non elimina le colonne della tabella remota presenti nella tabella remota, ma non nella tabella di SQL Server abilitata per l'estensione. Se sono presenti colonne nella tabella remota di Azure che non esistono più nella tabella di SQL Server abilitata per Stretch, queste colonne aggiuntive non impediscono il normale funzionamento di Stretch Database. È possibile rimuovere le colonne aggiuntive manualmente.  
 
## <a name="manage-performance-and-costs"></a>Gestire prestazioni e costi  
  
### <a name="troubleshoot-query-performance"></a>Risolvere i problemi relativi alle prestazioni delle query  
  L'esecuzione di query che includono tabelle abilitate per Estensione database in genere è più lenta rispetto a quanto avveniva prima dell'abilitazione delle tabelle per Estensione database. Se le prestazioni delle query peggiorano notevolmente, esaminare i possibili problemi seguenti.  
  
-   Il server di Azure si trova in un'area geografica diversa rispetto all'istanza di SQL Server? Configurare il server di Azure in modo che si trovi nella stessa area geografica dell'istanza di SQL Server per ridurre la latenza di rete.  
  
-   Le condizioni della rete possono essere peggiorate. Per informazioni su problemi o interruzioni recenti, contattare l'amministratore di rete.  
  
### <a name="increase-azure-performance-level-for-resource-intensive-operations-such-as-indexing"></a>Aumentare il livello di prestazioni di Azure per le operazioni a elevato utilizzo di risorse, quali l'indicizzazione  
 Quando si compila, si ricompila o si riorganizza un indice in una tabella di grandi dimensioni configurata per Stretch Database e si prevede di eseguire molte query sui dati migrati in Azure in questa fase, è opportuno aumentare il livello di prestazioni del database remoto di Azure corrispondente per la durata dell'operazione. Per informazioni sui livelli di prestazioni e i relativi prezzi, vedere [Prezzi di SQL Server Stretch Database](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
  
### <a name="you-cant-pause-the-sql-server-stretch-database-service-on-azure"></a>Non è possibile sospendere il servizio SQL Server Stretch Database in Azure  
 Assicurarsi di selezionare il livello di prestazioni e il piano tariffario corretti. Se si aumenta il livello di prestazioni temporaneamente per un'operazione che usa un numero elevato di risorse, ripristinare il livello precedente al termine dell'operazione. Per informazioni sui livelli di prestazioni e i relativi prezzi, vedere [Prezzi di SQL Server Stretch Database](https://azure.microsoft.com/pricing/details/sql-server-stretch-database/).  
   
 ## <a name="change-the-scope-of-queries"></a>Modificare l'ambito delle query  
 Le query sulle tabelle abilitate per l'estensione restituiscono dati locali e remoti per impostazione predefinita. È possibile modificare l'ambito delle query per tutte le query di tutti gli utenti oppure per una singola query di un amministratore.  
   
 ### <a name="change-the-scope-of-queries-for-all-queries-by-all-users"></a>Modificare l'ambito delle query per tutte le query di tutti gli utenti  
 Per modificare l'ambito di tutte le query di tutti gli utenti, eseguire la stored procedure **sys.sp_rda_set_query_mode**. È possibile ridurre l'ambito per eseguire query solo sui dati locali, disabilitare tutte le query o ripristinare l'impostazione predefinita. Per altre informazioni, vedere [sys.sp_rda_set_query_mode](../../relational-databases/system-stored-procedures/sys-sp-rda-set-query-mode-transact-sql.md).  
   
 ### <a name="queryHints"></a>Modificare l'ambito delle query per una singola query di un amministratore  
 Per modificare l'ambito di una singola query di un membro del ruolo db_owner, aggiungere l'hint per la query **WITH ( REMOTE_DATA_ARCHIVE_OVERRIDE = *valore* )** all'istruzione SELECT. L'hint per la query REMOTE_DATA_ARCHIVE_OVERRIDE può avere i valori seguenti.  
 -   **LOCAL_ONLY**. Eseguire query solo sui dati locali.  
   
 -   **REMOTE_ONLY**. Eseguire query solo sui dati remoti.  
   
 -   **STAGE_ONLY**. Eseguire query solo sui dati della tabella in cui Stretch Database inserisce temporaneamente righe idonee per la migrazione e conserva le righe migrate per il periodo specificato dopo la migrazione. Questo hint per la query è l'unico modo per eseguire query sulla tabella di staging.  
  
Ad esempio, la query seguente restituisce solo risultati locali.  
  
 ```sql  
USE <Stretch-enabled database name>;
GO
SELECT * FROM <Stretch_enabled table name> WITH (REMOTE_DATA_ARCHIVE_OVERRIDE = LOCAL_ONLY) WHERE ... ;
GO
```  
   
 ## <a name="adminHints"></a>Eseguire aggiornamenti ed eliminazioni amministrativi  
 Per impostazione predefinita non è possibile eseguire operazioni UPDATE o DELETE sulle righe idonee per la migrazione o già migrate in una tabella abilitata per l'estensione. Se è necessario risolvere un problema, un membro del ruolo db_owner può eseguire un'operazione UPDATE o DELETE aggiungendo l'hint per la query **WITH ( REMOTE_DATA_ARCHIVE_OVERRIDE = *valore* )** all'istruzione. L'hint per la query REMOTE_DATA_ARCHIVE_OVERRIDE può avere i valori seguenti.  
 -   **LOCAL_ONLY**. Aggiornare o eliminare solo i dati locali.  
   
 -   **REMOTE_ONLY**. Aggiornare o eliminare solo i dati remoti.  
   
 -   **STAGE_ONLY**. Aggiornare o eliminare solo i dati della tabella in cui Stretch Database inserisce temporaneamente righe idonee per la migrazione e conserva le righe migrate per il periodo specificato dopo la migrazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare e risolvere i problemi relativi alla migrazione dei dati &#40;Stretch Database&#41;](../../sql-server/stretch-database/monitor-and-troubleshoot-data-migration-stretch-database.md)   
[Eseguire il backup di database abilitati per Stretch (Stretch Database)](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md)  
[Ripristinare database abilitati per Stretch (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)  
  
  
