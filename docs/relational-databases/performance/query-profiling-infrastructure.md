---
title: Infrastruttura di profilatura delle query | Microsoft Docs
ms.custom: ''
ms.date: 11/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server]
- execution plans [SQL Server]
- query profiling
- lightweight query profiling
- lightweight profiling
- lwp
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753e
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: 221021641787564bb064f1f825da43cff4b27a32
ms.sourcegitcommit: c60784d1099875a865fd37af2fb9b0414a8c9550
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58645563"
---
# <a name="query-profiling-infrastructure"></a>Infrastruttura di profilatura delle query
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Il [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] offre la possibilità di accedere alle informazioni di runtime nei piani di esecuzione delle query. Una delle azioni più importanti quando si verifica un problema di prestazioni consiste nell'individuare in modo preciso il carico di lavoro in esecuzione e la modalità di gestione delle risorse. Per questa ragione, è necessario accedere al [piano di esecuzione effettivo](../../relational-databases/performance/display-an-actual-execution-plan.md).

Sebbene il completamento della query sia un prerequisito per la disponibilità di un piano di query effettivo, le [statistiche di query dinamiche](../../relational-databases/performance/live-query-statistics.md) possono offrire informazioni in tempo reale sul processo di esecuzione della query durante il passaggio dei dati da un [operatore del piano di query](../../relational-databases/showplan-logical-and-physical-operators-reference.md) all'altro. Il piano dinamico delle query visualizza lo stato complessivo delle query e le statistiche di esecuzione a livello di operatore, ad esempio il numero di righe prodotte, il tempo trascorso, lo stato di avanzamento dell'operatore e così via. Poiché questi dati sono disponibili in tempo reale senza dover attendere il completamento della query, queste statistiche di esecuzione sono estremamente utili per il debug di problemi relativi alle prestazioni delle query, ad esempio query a lunga esecuzione e query a esecuzione infinita che non terminano mai.

## <a name="the-standard-query-execution-statistics-profiling-infrastructure"></a>Infrastruttura di profilatura delle statistiche di esecuzione query standard

L'*infrastruttura del profilo delle statistiche di esecuzione query* o profilatura standard deve essere abilitata per raccogliere informazioni sui piani di esecuzione, ovvero il totale delle righe e l'utilizzo della CPU e dell'I/O. I seguenti metodi di raccolta delle informazioni sui piani di esecuzione per una **sessione di destinazione** usano l'infrastruttura di profilatura standard:

- [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md) 
- [SET STATISTICS PROFILE](../../t-sql/statements/set-statistics-profile-transact-sql.md)
- [Statistiche sulle query dinamiche](../../relational-databases/performance/live-query-statistics.md)

> [!NOTE]
> L'uso delle statistiche di query dinamiche con [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] usa l'infrastruttura di profilatura standard.    
> Nelle versioni successive di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], se l'[infrastruttura di profilatura lightweight](#lwp) è abilitata, verrà usata da Statistiche query dinamiche al posto della profilatura standard.

I seguenti metodi di raccolta delle informazioni sui piani di esecuzione per **tutte le sessioni** usano l'infrastruttura di profilatura standard:

-  Evento esteso ***query_post_execution_showplan***. Per abilitare gli eventi estesi, vedere [Monitor System Activity Using Extended Events](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md).  
- Evento traccia **Showplan XML** in [Traccia SQL](../../relational-databases/sql-trace/sql-trace.md) e [SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler.md). Per altre informazioni sull'evento traccia, vedere [Classe di evento Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md).

Durante l'esecuzione di una sessione di eventi estesi che usa l'evento *query_post_execution_showplan*, viene popolata anche la DMV [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md) che abilita le statistiche di query dinamiche per tutte le sessioni usando [Monitoraggio attività](../../relational-databases/performance-monitor/activity-monitor.md) o eseguendo la query direttamente nella DMV. Per altre informazioni, vedere [Live Query Statistics](../../relational-databases/performance/live-query-statistics.md).

## <a name="lwp"></a> Infrastruttura di profilatura delle statistiche di esecuzione query lightweight

A partire da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 e [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] è stata introdotta una nuova *infrastruttura di profilatura delle statistiche di esecuzione query lightweight* o una **profilatura lightweight**. 

> [!NOTE]
> Le stored procedure compilate in modo nativo non sono supportate con la profilatura lightweight.  

### <a name="lightweight-query-execution-statistics-profiling-infrastructure-v1"></a>Infrastruttura di profilatura delle statistiche di esecuzione query lightweight v1

**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 fino a [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). 
  
A partire [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 e [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)], con l'introduzione della profilatura lightweight è stato ridotto l'overhead delle prestazioni per raccogliere informazioni sui piani di esecuzione. A differenza della profilatura standard, la profilatura lightweight non raccoglie informazioni di runtime della CPU. La profilatura lightweight continua comunque a raccogliere il totale di righe conteggio delle righe e le informazioni sull'utilizzo dell'I/O.

È stato anche introdotto un nuovo evento esteso ***query_thread_profile*** che usa la profilatura lightweight. Questo evento esteso espone le statistiche di esecuzione di ogni operatore offrendo informazioni più approfondite sulle prestazioni di ogni nodo e thread. È possibile configurare una sessione di esempio che usa questo evento esteso come illustrato nell'esempio che segue:

```sql
CREATE EVENT SESSION [NodePerfStats] ON SERVER
ADD EVENT sqlserver.query_thread_profile(
  ACTION(sqlos.scheduler_id,sqlserver.database_id,sqlserver.is_system,
    sqlserver.plan_handle,sqlserver.query_hash_signed,sqlserver.query_plan_hash_signed,
    sqlserver.server_instance_name,sqlserver.session_id,sqlserver.session_nt_username,
    sqlserver.sql_text))
ADD TARGET package0.ring_buffer(SET max_memory=(25600))
WITH (MAX_MEMORY=4096 KB,
  EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,
  MAX_DISPATCH_LATENCY=30 SECONDS,
  MAX_EVENT_SIZE=0 KB,
  MEMORY_PARTITION_MODE=NONE,
  TRACK_CAUSALITY=OFF,
  STARTUP_STATE=OFF);
```

> [!NOTE]
> Per altre informazioni sull'overhead delle prestazioni della profilatura di query, vedere il post di blog [Developers Choice: Query progress - anytime, anywhere](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/) (Scelta degli sviluppatori: Avanzamento delle query, sempre e dovunque). 

Durante l'esecuzione di una sessione di eventi estesi che usa l'evento *query_thread_profile*, viene popolata anche la DMV [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md) tramite la profilatura lightweight e vengono abilitate le statistiche di query dinamiche per tutte le sessioni usando [Monitoraggio attività](../../relational-databases/performance-monitor/activity-monitor.md) o eseguendo la query direttamente nella DMV.

### <a name="lightweight-query-execution-statistics-profiling-infrastructure-v2"></a>Infrastruttura di profilatura delle statistiche di esecuzione query lightweight v2

**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 fino a [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]). 

[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 include una versione rivista della profilatura lightweight con un overhead minimo. La profilatura lightweight può essere anche abilitata a livello globale tramite il [flag di traccia 7412](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md) per le versioni indicate nella sezione precedente *Si applica a*. Una nuova DMF [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md) viene introdotta per restituire il piano di esecuzione query per le richieste in elaborazione.

A partire da [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 CU3 e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU11, se la profilatura lightweight non è abilitata globalmente, è possibile usare il nuovo argomento **QUERY_PLAN_PROFILE** dell'[hint per la query USE HINT](../../t-sql/queries/hints-transact-sql-query.md#use_hint) per abilitare la profilatura a livello di query per qualsiasi sessione. Al termine dell'esecuzione di una query contenente questo nuovo hint, viene generato anche un nuovo evento esteso ***query_plan_profile*** che fornisce l'XML di un piano di esecuzione effettivo simile all'evento esteso *query_post_execution_showplan*. 

> [!NOTE]
> L'evento esteso *query_plan_profile* si avvale anche della profilatura leggera benché non venga usato l'hint per la query. 

Una sessione di esempio che usa l'evento esteso *query_plan_profile* può essere configurata come illustrato nell'esempio seguente:

```sql
CREATE EVENT SESSION [PerfStats_LWP_Plan] ON SERVER
ADD EVENT sqlserver.query_plan_profile(
  ACTION(sqlos.scheduler_id,sqlserver.database_id,sqlserver.is_system,
    sqlserver.plan_handle,sqlserver.query_hash_signed,sqlserver.query_plan_hash_signed,
    sqlserver.server_instance_name,sqlserver.session_id,sqlserver.session_nt_username,
    sqlserver.sql_text))
ADD TARGET package0.ring_buffer(SET max_memory=(25600))
WITH (MAX_MEMORY=4096 KB,
  EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,
  MAX_DISPATCH_LATENCY=30 SECONDS,
  MAX_EVENT_SIZE=0 KB,
  MEMORY_PARTITION_MODE=NONE,
  TRACK_CAUSALITY=OFF,
  STARTUP_STATE=OFF);
```

### <a name="lightweight-query-execution-statistics-profiling-infrastructure-v3"></a>Infrastruttura di profilatura delle statistiche di esecuzione query lightweight v3

**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (a partire da [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)])

[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] include una nuova versione rivista della profilatura lightweight che raccoglie il totale di righe per tutte le esecuzioni. La profilatura lightweight è abilitata per impostazione predefinita in [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] e il flag di traccia 7412 non ha alcun effetto.

È stata introdotta una nuova DMF [sys.dm_exec_query_plan_stats](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-stats-transact-sql.md) per restituire l'equivalente dell'ultimo piano di esecuzione effettivo noto per la maggior parte delle query. Un nuovo evento esteso *query_post_execution_plan_profile* raccoglie l'equivalente di un piano di esecuzione effettivo in base alla profilatura leggera, a differenza di *query_post_execution_showplan* che usa la profilatura standard. 

È possibile configurare una sessione di esempio che usa l'evento esteso *query_post_execution_plan_profile* come illustrato nell'esempio seguente:

```sql
CREATE EVENT SESSION [PerfStats_LWP_All_Plans] ON SERVER
ADD EVENT sqlserver.query_post_execution_plan_profile(
  ACTION(sqlos.scheduler_id,sqlserver.database_id,sqlserver.is_system,
    sqlserver.plan_handle,sqlserver.query_hash_signed,sqlserver.query_plan_hash_signed,
    sqlserver.server_instance_name,sqlserver.session_id,sqlserver.session_nt_username,
    sqlserver.sql_text))
ADD TARGET package0.ring_buffer(SET max_memory=(25600))
WITH (MAX_MEMORY=4096 KB,
  EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,
  MAX_DISPATCH_LATENCY=30 SECONDS,
  MAX_EVENT_SIZE=0 KB,
  MEMORY_PARTITION_MODE=NONE,
  TRACK_CAUSALITY=OFF,
  STARTUP_STATE=OFF);
```

## <a name="remarks"></a>Remarks

> [!IMPORTANT]
> A causa di un possibile AV casuale, durante l'esecuzione di una stored procedure di monitoraggio che fa riferimento a [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md), assicurarsi che sia installato [KB 4078596](http://support.microsoft.com/help/4078596) in [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] e [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)].

A partire dalla profilatura lightweight v2 con overhead ridotto, qualsiasi server che non è già basato su CPU può eseguire la profilatura lightweight **in modo continuo** e consentire ai professionisti di database di inserirsi in qualsiasi esecuzione in corso in qualsiasi momento, ad esempio usando Monitoraggio attività o eseguendo direttamente una query in `sys.dm_exec_query_profiles` e ottenere il piano di query con le statistiche di runtime.

Per altre informazioni sull'overhead delle prestazioni della profilatura di query, vedere il post di blog [Developers Choice: Query progress - anytime, anywhere](https://techcommunity.microsoft.com/t5/SQL-Server/Developers-Choice-Query-progress-anytime-anywhere/ba-p/385004) (Scelta degli sviluppatori: Avanzamento delle query, sempre e dovunque). 

> [!NOTE]
> Se l'infrastruttura di profilatura standard è già abilitata, gli eventi estesi che sfruttano la profilatura leggera useranno le informazioni disponibili nella profilatura standard. Si supponga ad esempio che sia in esecuzione una sessione di evento esteso che usa `query_post_execution_showplan` e che venga avviata un'altra sessione che usa `query_post_execution_plan_profile`. La seconda sessione userà le informazioni provenienti dalla profilatura standard.

## <a name="see-also"></a>Vedere anche  
 [Monitoraggio e ottimizzazione delle prestazioni](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [Strumenti per il monitoraggio e l'ottimizzazione delle prestazioni](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [Aprire Monitoraggio attività &#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)     
 [Monitoraggio attività](../../relational-databases/performance-monitor/activity-monitor.md)     
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
 [Monitorare l'attività del sistema mediante gli eventi estesi](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)      
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)     
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)     
 [Flag di traccia](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)    
 [Guida di riferimento a operatori Showplan logici e fisici](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
 [piano di esecuzione effettivo](../../relational-databases/performance/display-an-actual-execution-plan.md)    
 [Statistiche sulle query dinamiche](../../relational-databases/performance/live-query-statistics.md)      
 [Developers Choice: Query progress - anytime, anywhere](https://techcommunity.microsoft.com/t5/SQL-Server/Developers-Choice-Query-progress-anytime-anywhere/ba-p/385004) (Scelta degli sviluppatori: Avanzamento delle query, sempre e dovunque)
