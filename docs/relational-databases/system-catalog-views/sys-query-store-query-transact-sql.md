---
title: sys.query_store_query (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/23/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- QUERY_STORE_QUERY
- SYS.QUERY_STORE_QUERY_TSQL
- SYS.QUERY_STORE_QUERY
- QUERY_STORE_QUERY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- query_store_query catalog view
- sys.query_store_query catalog view
ms.assetid: bdee149e-7556-4fc3-8242-925dd4b7b6ac
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||= azure-sqldw-latest||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ac66d9cd1e7585304aeab182ddf6ccabc8560bc0
ms.sourcegitcommit: acb5de9f493238180d13baa302552fdcc30d83c0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/12/2019
ms.locfileid: "59542101"
---
# <a name="sysquerystorequery-transact-sql"></a>sys.query_store_query (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Contiene informazioni sulle query e le statistiche di esecuzione runtime aggregate complessivo associato.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**query_id**|**bigint**|Chiave primaria.|  
|**query_text_id**|**bigint**|Chiave esterna. Joins to [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)|  
|**context_settings_id**|**bigint**|Chiave esterna. Joins to [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md).<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|  
|**object_id**|**bigint**|ID dell'oggetto di database che fa parte della query (stored procedure, trigger, funzioni definite dall'utente CLR/UDAgg, ecc.). 0 se non viene eseguita la query come parte di un oggetto di database (query ad hoc).<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|  
|**batch_sql_handle**|**varbinary(64)**|ID del batch di istruzione della query fa parte di. Popolato solo se la query fa riferimento a tabelle temporanee o variabili di tabella.<br/>**Nota:** Azure SQL Data Warehouse verrà sempre restituito *NULL*.|  
|**query_hash**|**binary(8)**|Hash MD5 della singola query, basata sull'albero query logica. Include gli hint per query optimizer.|  
|**is_internal_query**|**bit**|La query è stata generata internamente.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|  
|**query_parameterization_type**|**tinyint**|Tipo di parametrizzazione:<br /><br /> 0: nessuno<br /><br /> 1 - utente<br /><br /> 2 - semplice<br /><br /> 3 - forzato<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|  
|**query_parameterization_type_desc**|**nvarchar(60)**|Descrizione testuale per il tipo di parametrizzazione automatica.<br/>**Nota:** Azure SQL Data Warehouse verrà sempre restituito *None*.|  
|**initial_compile_start_time**|**datetimeoffset**|Compilare ora di inizio.|  
|**last_compile_start_time**|**datetimeoffset**|Compilare ora di inizio.|  
|**last_execution_time**|**datetimeoffset**|Ora dell'ultima esecuzione si riferisce all'ultima ora di fine del piano di query /.|  
|**last_compile_batch_sql_handle**|**varbinary(64)**|Handle dell'ultimo batch SQL in cui query è stata usata l'ora dell'ultima. Può essere fornita come input per [DM exec_sql_text &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md) per ottenere il testo completo del batch.<br/>**Nota:** Azure SQL Data Warehouse verrà sempre restituito *NULL*.|  
|**last_compile_batch_offset_start**|**bigint**|Informazioni che possono essere fornite a DM exec_sql_text insieme last_compile_batch_sql_handle.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|
|**last_compile_batch_offset_end**|**bigint**|Informazioni che possono essere fornite a DM exec_sql_text insieme last_compile_batch_sql_handle.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|  
|**count_compiles**|**bigint**|Statistiche della compilazione.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre uno (1).|  
|**avg_compile_duration**|**float**|Statistiche di compilazione in microsecondi.|  
|**last_compile_duration**|**bigint**|Statistiche di compilazione in microsecondi.|  
|**avg_bind_duration**|**float**|Statistiche di associazione in microsecondi.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|  
|**last_bind_duration**|**bigint**|Statistiche di associazione.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|  
|**avg_bind_cpu_time**|**float**|Statistiche di associazione.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|  
|**last_bind_cpu_time**|**bigint**|Statistiche di associazione.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|  
|**avg_optimize_duration**|**float**|Statistiche di ottimizzazione espressa in microsecondi.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|
|**last_optimize_duration**|**bigint**|Statistiche di ottimizzazione.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|
|**avg_optimize_cpu_time**|**float**|Statistiche di ottimizzazione espressa in microsecondi.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|
|**last_optimize_cpu_time**|**bigint**|Statistiche di ottimizzazione.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|
|**avg_compile_memory_kb**|**float**|Compilare le statistiche di memoria.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|
|**last_compile_memory_kb**|**bigint**|Compilare le statistiche di memoria.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|
|**max_compile_memory_kb**|**bigint**|Compilare le statistiche di memoria.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|
|**is_clouddb_internal_query**|**bit**|Sempre 0 in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in locale.<br/>**Nota:** Azure SQL Data Warehouse restituirà sempre zero (0).|
  
## <a name="permissions"></a>Permissions  
 Richiede la **VIEW DATABASE STATE** l'autorizzazione.  
  
## <a name="see-also"></a>Vedere anche  
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [sys.query_context_settings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-context-settings-transact-sql.md)   
 [sys.query_store_plan &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-plan-transact-sql.md)   
 [sys.query_store_query_text &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-query-text-transact-sql.md)   
 [sys.query_store_wait_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-wait-stats-transact-sql.md)  
 [sys.query_store_runtime_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-transact-sql.md)   
 [sys.query_store_runtime_stats_interval &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-query-store-runtime-stats-interval-transact-sql.md)   
 [Monitoraggio delle prestazioni tramite Archivio query](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Stored procedure di Archivio query &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/query-store-stored-procedures-transact-sql.md)   
 [sys.fn_stmt_sql_handle_from_sql_stmt &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-stmt-sql-handle-from-sql-stmt-transact-sql.md)  
  
  
