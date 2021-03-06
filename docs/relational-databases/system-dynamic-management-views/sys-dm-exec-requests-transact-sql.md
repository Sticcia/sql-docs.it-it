---
title: sys.dm_exec_requests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/17/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_requests_TSQL
- sys.dm_exec_requests
- dm_exec_requests_TSQL
- dm_exec_requests
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_requests dynamic management view
ms.assetid: 4161dc57-f3e7-4492-8972-8cfb77b29643
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 87be8cba02cac7f0ff6b1cd0fa966241745e5483
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072235"
---
# <a name="sysdmexecrequests-transact-sql"></a>sys.dm_exec_requests (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Restituisce informazioni su ciascuna richiesta in esecuzione all'interno di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|session_id|**smallint**|ID della sessione a cui la richiesta è correlata. Non ammette i valori Null.|  
|request_id|**int**|ID della richiesta. Valore univoco nel contesto della sessione. Non ammette i valori Null.|  
|start_time|**datetime**|Timestamp relativo all'arrivo della richiesta. Non ammette i valori Null.|  
|status|**nvarchar(30)**|Stato della richiesta. I possibili valori sono i seguenti:<br /><br /> Informazioni preliminari<br />In esecuzione<br />Eseguibile<br />Sospeso<br />Sospeso<br /><br /> Non ammette i valori Null.|  
|comando|**nvarchar(32)**|Identifica il tipo di comando corrente in corso di elaborazione. I tipi di comandi più comuni sono i seguenti:<br /><br /> SELECT<br />INSERT<br />UPDATE<br />DELETE<br />BACKUP LOG<br />BACKUP DATABASE<br />DBCC<br />FOR<br /><br /> Per recuperare il testo della richiesta, utilizzare sys.dm_exec_sql_text con il valore sql_handle corrispondente per la richiesta. I processi interni di sistema impostano il comando in base al tipo di attività effettuata. Di seguito sono riportate le attività:<br /><br /> LOCK MONITOR<br />CHECKPOINTLAZY<br />WRITER<br /><br /> Non ammette i valori Null.|  
|sql_handle|**varbinary(64)**|È un token che identifica in modo univoco il batch o una stored procedure che fa parte della query. Ammette i valori Null.|  
|statement_start_offset|**int**|Numero di caratteri nella stored procedure o nel batch attualmente in esecuzione in cui inizia l'istruzione in esecuzione. Può essere utilizzata in combinazione con la colonna sql_handle, la colonna statement_end_offset e la funzione a gestione dinamica sys.dm_exec_sql_text per recuperare l'istruzione in esecuzione per la richiesta. Ammette i valori Null.|  
|statement_end_offset|**int**|Numero di caratteri nella stored procedure o nel batch attualmente in esecuzione in cui termina l'istruzione in esecuzione. Può essere utilizzata in combinazione con la colonna sql_handle, la colonna statement_end_offset e la funzione a gestione dinamica sys.dm_exec_sql_text per recuperare l'istruzione in esecuzione per la richiesta. Ammette i valori Null.|  
|plan_handle|**varbinary(64)**|È un token che identifica in modo univoco un piano di esecuzione di query per un batch attualmente in esecuzione. Ammette i valori Null.|  
|database_id|**smallint**|ID del database utilizzato per eseguire la richiesta. Non ammette i valori Null.|  
|user_id|**int**|ID dell'utente che ha inviato la richiesta. Non ammette i valori Null.|  
|connection_id|**uniqueidentifier**|ID della connessione nella quale è arrivata la richiesta. Ammette i valori Null.|  
|blocking_session_id|**smallint**|ID della sessione che sta bloccando la richiesta. Se questa colonna è NULL, la richiesta non è bloccata oppure non sono disponibili o identificabili informazioni di sessione per la sessione da cui è bloccata.<br /><br /> -2 = La risorsa di blocco appartiene a una transazione distribuita orfana.<br /><br /> -3 = La risorsa di blocco appartiene a una transazione di recupero posticipata.<br /><br /> -4 = Al momento non è stato possibile determinare l'ID sessione del proprietario del latch di blocco a causa di transizioni nello stato del latch interno.|  
|wait_type|**nvarchar(60)**|Se la richiesta è momentaneamente bloccata, in questa colonna viene restituito il tipo di attesa. Ammette i valori Null.<br /><br /> Per informazioni sui tipi di attese, vedere [DM os_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md).|  
|wait_time|**int**|Se la richiesta è momentaneamente bloccata, in questa colonna viene restituita la durata dell'attesa corrente espressa in millisecondi. Non ammette i valori Null.|  
|last_wait_type|**nvarchar(60)**|Se la richiesta è stata precedentemente bloccata, questa colonna restituisce il tipo dell'ultima attesa. Non ammette i valori Null.|  
|wait_resource|**nvarchar(256)**|Se la richiesta è momentaneamente bloccata, questa colonna restituisce la risorsa per la quale la richiesta è in attesa. Non ammette i valori Null.|  
|open_transaction_count|**int**|Numero di transazioni aperte per la richiesta. Non ammette i valori Null.|  
|open_resultset_count|**int**|Numero di set di risultati aperti per la richiesta. Non ammette i valori Null.|  
|transaction_id|**bigint**|ID della transazione nella quale viene eseguita la richiesta. Non ammette i valori Null.|  
|context_info|**varbinary(128)**|Valore di CONTEXT_INFO della sessione. Ammette i valori Null.|  
|percent_complete|**real**|Percentuale di lavoro completata per i comandi seguenti:<br /><br /> ALTER INDEX REORGANIZE<br />Opzione AUTO_SHRINK con ALTER DATABASE<br />BACKUP DATABASE<br />DBCC CHECKDB<br />DBCC CHECKFILEGROUP<br />DBCC CHECKTABLE<br />DBCC INDEXDEFRAG<br />DBCC SHRINKDATABASE<br />DBCC SHRINKFILE<br />RECOVERY<br />RESTORE DATABASE<br />ROLLBACK<br />TDE ENCRYPTION<br /><br /> Non ammette i valori Null.|  
|estimated_completion_time|**bigint**|Solo interno. Non ammette i valori Null.|  
|cpu_time|**int**|Tempo della CPU utilizzato dalla richiesta, espresso in millisecondi. Non ammette i valori Null.|  
|total_elapsed_time|**int**|Tempo totale, in millisecondi, trascorso dall'arrivo della richiesta. Non ammette i valori Null.|  
|scheduler_id|**int**|ID dell'utilità di pianificazione che sta pianificando la richiesta. Non ammette i valori Null.|  
|task_address|**varbinary(8)**|Indirizzo di memoria allocato all'attività associata alla richiesta. Ammette i valori Null.|  
|reads|**bigint**|Numero di letture effettuate dalla richiesta. Non ammette i valori Null.|  
|writes|**bigint**|Numero di scritture effettuate dalla richiesta. Non ammette i valori Null.|  
|logical_reads|**bigint**|Numero di letture logiche effettuate dalla richiesta. Non ammette i valori Null.|  
|text_size|**int**|Impostazione di TEXTSIZE per la richiesta. Non ammette i valori Null.|  
|language|**nvarchar(128)**|Impostazione di LANGUAGE per la richiesta. Ammette i valori Null.|  
|date_format|**nvarchar(3)**|Impostazione di DATEFORMAT per la richiesta. Ammette i valori Null.|  
|date_first|**smallint**|Impostazione di DATEFIRST per la richiesta. Non ammette i valori Null.|  
|quoted_identifier|**bit**|1 = QUOTED_IDENTIFIER è impostata su ON per la richiesta. Negli altri casi è 0.<br /><br /> Non ammette i valori Null.|  
|arithabort|**bit**|1 = ARITHABORT è impostata su ON per la richiesta. Negli altri casi è 0.<br /><br /> Non ammette i valori Null.|  
|ansi_null_dflt_on|**bit**|1 = ANSI_NULL_DFLT_ON è impostata su ON per la richiesta. Negli altri casi è 0.<br /><br /> Non ammette i valori Null.|  
|ansi_defaults|**bit**|1 = ANSI_DEFAULTS è impostata su ON per la richiesta. Negli altri casi è 0.<br /><br /> Non ammette i valori Null.|  
|ansi_warnings|**bit**|1 = ANSI_WARNINGS è impostata su ON per la richiesta. Negli altri casi è 0.<br /><br /> Non ammette i valori Null.|  
|ansi_padding|**bit**|1 = ANSI_PADDING è impostata su ON per la richiesta.<br /><br /> Negli altri casi è 0.<br /><br /> Non ammette i valori Null.|  
|ansi_nulls|**bit**|1 = ANSI_NULLS è impostata su ON per la richiesta. Negli altri casi è 0.<br /><br /> Non ammette i valori Null.|  
|concat_null_yields_null|**bit**|1 = CONCAT_NULL_YIELDS_NULL è impostata su ON per la richiesta. Negli altri casi è 0.<br /><br /> Non ammette i valori Null.|  
|transaction_isolation_level|**smallint**|Livello di isolamento con cui è stata creata la transazione per questa richiesta. Non ammette i valori Null.<br /><br /> 0 = Non specificato<br /><br /> 1 = ReadUncomitted<br /><br /> 2 = ReadCommitted<br /><br /> 3 = Repeatable<br /><br /> 4 = Serializable<br /><br /> 5 = Snapshot|  
|lock_timeout|**int**|Periodo di timeout del blocco, espresso in millisecondi, per la richiesta. Non ammette i valori Null.|  
|deadlock_priority|**int**|Impostazione di DEADLOCK_PRIORITY per la richiesta. Non ammette i valori Null.|  
|row_count|**bigint**|Numero di righe restituite al client dalla richiesta. Non ammette i valori Null.|  
|prev_error|**int**|Ultimo errore che si è verificato durante l'esecuzione della richiesta. Non ammette i valori Null.|  
|nest_level|**int**|Livello di nidificazione corrente del codice eseguito nella richiesta. Non ammette i valori Null.|  
|granted_query_memory|**int**|Numero di pagine allocate all'esecuzione di una query nella richiesta. Non ammette i valori Null.|  
|executing_managed_code|**bit**|Indica se una richiesta specifica sta eseguendo oggetti CLR (Common Language Runtime) quali routine, tipi e trigger. Il valore rimane impostato per l'intero periodo di permanenza di un oggetto CLR nello stack, anche durante l'esecuzione di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] internamente a CLR. Non ammette i valori Null.|  
|group_id|**int**|ID del gruppo del carico di lavoro a cui appartiene la query. Non ammette i valori Null.|  
|query_hash|**binary(8)**|Valore hash binario calcolato sulla query che consente di identificare query con logica analoga. È possibile utilizzare il valore hash della query per determinare l'utilizzo delle risorse aggregate per query che differiscono solo per valori letterali.|  
|query_plan_hash|**binary(8)**|Valore hash binario calcolato sul piano di esecuzione di query che consente di identificare piani di esecuzioni analoghi. È possibile utilizzare il valore hash del piano di query per individuare il costo cumulativo di query con piani di esecuzione analoghi.|  
|statement_sql_handle|**varbinary(64)**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Handle SQL della singola query. |  
|statement_context_id|**bigint**|**Si applica a**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> La chiave esterna facoltativa alla sys.query_context_settings. |  
|dop |**int** |**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il grado di parallelismo della query. |  
|parallel_worker_count |**int** |**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Il numero di thread di lavoro paralleli riservati se si tratta di una query parallela.  |  
|external_script_request_id |**uniqueidentifier** |**Si applica a**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> L'ID della richiesta dello script esterno associato alla richiesta corrente. |  
|is_resumable |**bit** |**Si applica a**: [!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Indica se la richiesta è un'operazione su indici ripristinabili. |  
|page_resource |**binary(8)** |**Si applica a**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]<br /><br /> Una rappresentazione esadecimale a 8 byte della risorsa di pagina se il `wait_resource` colonna contiene una pagina. |

## <a name="remarks"></a>Note 
Per eseguire codice esterno a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad esempio stored procedure estese e query distribuite, è necessario che un thread venga eseguito esternamente al controllo dell'utilità di pianificazione in modalità non preemptive. A tale scopo, un thread di lavoro passa alla modalità preemptive. I valori temporali restituiti da questa DMW non includono il tempo trascorso in modalità preemptive.

Durante l'esecuzione di richieste in parallelo nelle [modalità riga](../../relational-databases/query-processing-architecture-guide.md#row-mode-execution), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] assegna un thread di lavoro per coordinare i thread di lavoro responsabili per il completamento di attività assegnate. In questa vista DMV solo il thread coordinator è visibile per la richiesta. Le colonne **legge**, **scrive**, **logical_reads**, e **row_count** sono **non aggiornato** per il thread coordinatore. Le colonne **wait_type**, **wait_time**, **last_wait_type**, **wait_resource**, e **granted_query_memory** vengono **aggiornato solo** per il thread coordinator. Per altre informazioni, vedere la [Thread e Guida all'architettura delle attività](../../relational-databases/thread-and-task-architecture-guide.md).

## <a name="permissions"></a>Permissions
Se l'utente dispone `VIEW SERVER STATE` autorizzazione per il server, è possibile visualizzare le sessioni in esecuzione tutte nell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]; in caso contrario, l'utente verrà visualizzato solo nella sessione corrente. `VIEW SERVER STATE` non è possibile concedere [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] in modo `sys.dm_exec_requests` sarà sempre limitata alla connessione corrente.
  
## <a name="examples"></a>Esempi  
  
### <a name="a-finding-the-query-text-for-a-running-batch"></a>A. Ricerca del testo della query per un batch in esecuzione

 Nell'esempio seguente viene eseguita una query su `sys.dm_exec_requests` per trovare la query specifica e copiare `sql_handle` dall'output.  

```sql
SELECT * FROM sys.dm_exec_requests;  
GO  
```  

Per ottenere il testo dell'istruzione, utilizzare il `sql_handle` copiato con la funzione di sistema `sys.dm_exec_sql_text(sql_handle)`.  

```sql
SELECT * FROM sys.dm_exec_sql_text(< copied sql_handle >);  
GO  
```

### <a name="b-finding-all-locks-that-a-running-batch-is-holding"></a>b. Ricerca di tutti i blocchi contenuti in un batch in esecuzione

Le seguenti query di esempio **exec_requests** per trovare il batch specifico e copiare il `transaction_id` dall'output.

```sql
SELECT * FROM sys.dm_exec_requests;  
GO
```

Quindi, per trovare le informazioni di blocco, usare l'insieme copiato `transaction_id` con la funzione di sistema **DM tran_locks**.  

```sql
SELECT * FROM sys.dm_tran_locks
WHERE request_owner_type = N'TRANSACTION'
    AND request_owner_id = < copied transaction_id >;
GO  
```

### <a name="c-finding-all-currently-blocked-requests"></a>C. Ricerca di tutte le richieste attualmente bloccate

Le seguenti query di esempio **exec_requests** per trovare informazioni relative alle richieste bloccate.  

```sql
SELECT session_id ,status ,blocking_session_id  
    ,wait_type ,wait_time ,wait_resource
    ,transaction_id
FROM sys.dm_exec_requests
WHERE status = N'suspended';  
GO  
```  

### <a name="d-ordering-existing-requests-by-cpu"></a>D. Le richieste esistenti per la CPU di ordinamento

```sql
SELECT 
   req.session_id
   , req.start_time
   , cpu_time 'cpu_time_ms'
   , object_name(st.objectid,st.dbid) 'ObjectName' 
   , substring
      (REPLACE
        (REPLACE
          (SUBSTRING
            (ST.text
            , (req.statement_start_offset/2) + 1
            , (
               (CASE statement_end_offset
                  WHEN -1
                  THEN DATALENGTH(ST.text)  
                  ELSE req.statement_end_offset
                  END
                    - req.statement_start_offset)/2) + 1)
       , CHAR(10), ' '), CHAR(13), ' '), 1, 512)  AS statement_text  
FROM sys.dm_exec_requests AS req  
   CROSS APPLY sys.dm_exec_sql_text(req.sql_handle) as ST
   ORDER BY cpu_time desc;
GO
```

## <a name="see-also"></a>Vedere anche

- [Funzioni e viste a gestione dinamica](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)
- [Funzioni e viste a gestione dinamica relative all'esecuzione](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)
- [sys.dm_os_memory_clerks](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)
- [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)
- [sys.dm_exec_query_memory_grants](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-memory-grants-transact-sql.md)
- [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)
- [sys.dm_exec_sql_text &#40](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)  
