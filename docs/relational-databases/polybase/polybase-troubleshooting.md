---
title: Monitorare e risolvere i problemi relativi a PolyBase | Microsoft Docs
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.technology: polybase
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- PolyBase, monitoring
- PolyBase, performance monitoring
helpviewer_keywords:
- PolyBase, troubleshooting
ms.assetid: f119e819-c3ae-4e0b-a955-3948388a9cfe
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3c8c6922aca2d291527412e3384fe6682ba26556
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47687509"
---
# <a name="monitor-and-troubleshoot-polybase"></a>Monitorare e risolvere i problemi relativi a PolyBase

[!INCLUDE[appliesto-ss-xxxx-asdw-pdw-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Per risolvere i problemi relativi a PolyBase, usare le tecniche illustrate in questo argomento.

## <a name="catalog-views"></a>Viste del catalogo

Usare le viste del catalogo elencate di seguito per gestire le operazioni di PolyBase.

|||  
|-|-|  
|Vista|Descrizione|  
|[sys.external_tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-tables-transact-sql.md)|Identifica le tabelle esterne.|  
|[sys.external_data_sources &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-data-sources-transact-sql.md)|Identifica le origini dati esterne.|  
|[sys.external_file_formats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-external-file-formats-transact-sql.md)|Identifica i formati di file esterni.|  

## <a name="dynamic-management-views"></a>DMV  

|||  
|-|-|  
|[sys.dm_exec_compute_node_errors &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-errors-transact-sql.md)|[sys.dm_exec_compute_node_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-status-transact-sql.md)|  
|[sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md)|[sys.dm_exec_distributed_request_steps &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-request-steps-transact-sql.md)|  
|[sys.dm_exec_distributed_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-requests-transact-sql.md)|[sys.dm_exec_distributed_sql_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-distributed-sql-requests-transact-sql.md)|  
|[sys.dm_exec_dms_services &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-services-transact-sql.md)|[sys.dm_exec_dms_workers &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-dms-workers-transact-sql.md)|  
|[sys.dm_exec_external_operations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-external-operations-transact-sql.md)|[sys.dm_exec_external_work &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-external-work-transact-sql.md)|  

Le query PolyBase sono suddivise in una serie di passaggi all'interno di sys.dm_exec_distributed_request_steps. Nella tabella seguente è illustrato il mapping tra il nome del passaggio per la vista a gestione dinamica associata.

|Passaggio PolyBase|Vista a gestione dinamica associata|  
|-|-|
|HadoopJobOperation | sys.dm_exec_external_operations|
|RandomIdOperation | sys.dm_exec_distributed_request_steps|
|HadoopRoundRobinOperation | sys.dm_exec_dms_workers|
|StreamingReturnOperation | sys.dm_exec_dms_workers|
|OnOperation | sys.dm_exec_distributed_sql_requests |

## <a name="to-monitor-polybase-queries-using-dmvs"></a>Per eseguire il monitoraggio delle query di PolyBase con DMV

Per eseguire il monitoraggio e risolvere i problemi relativi alle query di PolyBase, usare le viste DMV seguenti.

1. **Individuare le query con il tempo di esecuzione più lungo**  

   Prendere nota dell'ID esecuzione della query con il tempo di esecuzione più lungo.

   ```sql
    -- Find the longest running query  
   SELECT execution_id, st.text, dr.total_elapsed_time  
   FROM sys.dm_exec_distributed_requests  dr  
         cross apply sys.dm_exec_sql_text(sql_handle) st  
   ORDER BY total_elapsed_time DESC;  
   ```

1. **Individuare il passaggio della query distribuita con il tempo di esecuzione più lungo**  

   Usare l'ID esecuzione annotato nel passaggio precedente. Prendere nota dell'indice del passaggio con il tempo di esecuzione più lungo.

   Verificare il valore di location_type per il passaggio con il tempo di esecuzione più lungo:  

   - Head o Compute: implica un'operazione SQL. Procedere con il passaggio 3a.

      - DMS: implica un'operazione di PolyBase Data Movement Service. Procedere con il passaggio 3b.

      ```sql  
      -- Find the longest running step of the distributed query plan  
      SELECT execution_id, step_index, operation_type, distribution_type,   
      location_type, status, total_elapsed_time, command   
      FROM sys.dm_exec_distributed_request_steps   
      WHERE execution_id = 'QID4547'   
      ORDER BY total_elapsed_time DESC;  
      ```  

1. **Individuare lo stato di esecuzione del processo con tempo di esecuzione più lungo**  

   1. **Individuare lo stato di esecuzione di un passaggio SQL**  

      Usare l'ID esecuzione e l'indice passaggio annotati nei passaggi precedenti. Usare l'ID esecuzione e l'indice passaggio annotati nei passaggi precedenti.

      ```sql  
      -- Find the execution progress of SQL step    
      SELECT execution_id, step_index, distribution_id, status,   
      total_elapsed_time, row_count, command   
      FROM sys.dm_exec_distributed_sql_requests   
      WHERE execution_id = 'QID4547' and step_index = 1;  
      ```  

   1. **Individuare lo stato di esecuzione di un passaggio DMS**

      Usare l'ID esecuzione e l'indice passaggio annotati nei passaggi precedenti.

      ```sql  
      -- Find the execution progress of DMS step    
      SELECT execution_id, step_index, dms_step_index, status,   
      type, bytes_processed, total_elapsed_time  
      FROM sys.dm_exec_dms_workers   
      WHERE execution_id = 'QID4547'   
      ORDER BY total_elapsed_time DESC;
      ```  

1. **Individuare le informazioni su operazioni DMS esterne**  

   Usare l'ID esecuzione e l'indice passaggio annotati nei passaggi precedenti.

   ```sql  
   SELECT execution_id, step_index, dms_step_index, compute_node_id,   
   type, input_name, length, total_elapsed_time, status   
   FROM sys.dm_exec_external_work   
   WHERE execution_id = 'QID4547' and step_index = 7   
   ORDER BY total_elapsed_time DESC;  
   ```  

## <a name="to-view-the--polybase-query-plan-to-be-changed"></a>Per visualizzare il piano di query di PolyBase (da modificare) 

1. In SSMS abilitare **Includi piano di esecuzione effettivo** (CTRL+M) ed eseguire la query.

2. Fare clic sulla scheda **Piano di esecuzione** .

   ![Piano di query di PolyBase](../../relational-databases/polybase/media/polybase-query-plan.png "Piano di query di PolyBase")  

3. Fare clic con il pulsante destro del mouse sull' **operatore Remote Query** e selezionare **Proprietà**.

4. Copiare e incollare il valore di Remote Query in un editor di testo per visualizzare il piano di query remota XML. Di seguito è riportato un esempio.

   ```xml  

   <dsql_query number_nodes="1" number_distributions="8" number_distributions_per_node="8">  
      <sql>ExecuteMemo explain query</sql>  
      <dsql_operations total_cost="0" total_number_operations="6">  
        <dsql_operation operation_type="RND_ID">  
          <identifier>TEMP_ID_74</identifier>  
        </dsql_operation>  
        <dsql_operation operation_type="ON">  
          <location permanent="false" distribution="AllDistributions" />  
          <sql_operations>  
            <sql_operation type="statement">CREATE TABLE [tempdb].[dbo].[TEMP_ID_74] ([SensorKey] INT NOT NULL, [CustomerKey] INT NOT NULL, [GeographyKey] INT, [Speed] FLOAT(53) NOT NULL, [YearMeasured] INT NOT NULL ) WITH(DATA_COMPRESSION=PAGE);</sql_operation>  
          </sql_operations>  
        </dsql_operation>  
        <dsql_operation operation_type="ON">  
          <location permanent="false" distribution="AllDistributions" />  
          <sql_operations>  
            <sql_operation type="statement">EXEC [tempdb].[sys].[sp_addextendedproperty] @name=N'IS_EXTERNAL_STREAMING_TABLE', @value=N'true', @level0type=N'SCHEMA', @level0name=N'dbo', @level1type=N'TABLE', @level1name=N'TEMP_ID_74'</sql_operation>  
          </sql_operations>  
        </dsql_operation>  
        <dsql_operation operation_type="ON">  
          <location permanent="false" distribution="AllDistributions" />  
          <sql_operations>  
            <sql_operation type="statement">UPDATE STATISTICS [tempdb].[dbo].[TEMP_ID_74] WITH ROWCOUNT = 2401, PAGECOUNT = 7</sql_operation>  
          </sql_operations>  
        </dsql_operation>  
        <dsql_operation operation_type="MULTI">  
          <dsql_operation operation_type="STREAMING_RETURN">  
            <operation_cost cost="1" accumulative_cost="1" average_rowsize="24" output_rows="5762.1" />  
            <location distribution="AllDistributions" />  
            <select>SELECT [T1_1].[SensorKey] AS [SensorKey],  
             [T1_1].[CustomerKey] AS [CustomerKey],  
             [T1_1].[GeographyKey] AS [GeographyKey],  
             [T1_1].[Speed] AS [Speed],  
             [T1_1].[YearMeasured] AS [YearMeasured]  
      FROM   (SELECT [T2_1].[SensorKey] AS [SensorKey],  
                     [T2_1].[CustomerKey] AS [CustomerKey],  
                     [T2_1].[GeographyKey] AS [GeographyKey],  
                     [T2_1].[Speed] AS [Speed],  
                     [T2_1].[YearMeasured] AS [YearMeasured]  
              FROM   [tempdb].[dbo].[TEMP_ID_74] AS T2_1  
              WHERE  ([T2_1].[Speed] > CAST (6.50000000000000000E+001 AS FLOAT))) AS T1_1</select>  
          </dsql_operation>  
          <dsql_operation operation_type="ExternalRoundRobinMove">  
            <operation_cost cost="16.594848" accumulative_cost="17.594848" average_rowsize="24" output_rows="19207" />  
            <external_uri>hdfs://10.193.26.177:8020/Demo/car_sensordata.tbl/</external_uri>  
            <destination_table>[TEMP_ID_74]</destination_table>  
          </dsql_operation>  
        </dsql_operation>  
        <dsql_operation operation_type="ON">  
          <location permanent="false" distribution="AllDistributions" />  
          <sql_operations>  
            <sql_operation type="statement">DROP TABLE [tempdb].[dbo].[TEMP_ID_74]</sql_operation>  
          </sql_operations>  
        </dsql_operation>  
      </dsql_operations>  
   </dsql_query>  
   ```  

## <a name="to-monitor-nodes-in-a-polybase-group"></a>Per eseguire il monitoraggio dei nodi in un gruppo PolyBase  

Dopo aver configurato un set di computer come appartenenti al gruppo con scalabilità orizzontale PolyBase, è possibile eseguire il monitoraggio dello stato dei computer. Per informazioni dettagliate sulla creazione di un gruppo con scalabilità orizzontale, vedere [Gruppi con scalabilità orizzontale di PolyBase](../../relational-databases/polybase/polybase-scale-out-groups.md).

1. Connettersi a SQL Server sul nodo head di un gruppo.

2. Eseguire la vista DMV [sys.dm_exec_compute_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-nodes-transact-sql.md) per visualizzare tutti i nodi del gruppo PolyBase.

3. Eseguire la vista DMV [sys.dm_exec_compute_node_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-compute-node-status-transact-sql.md) per visualizzare lo stato di tutti i nodi del gruppo PolyBase.

## <a name="hadoop-name-node-high-availability"></a>Disponibilità elevata di Hadoop Name Node

PolyBase non interagisce con i servizi Name Node HA come Zookeeper o Knox. Tuttavia, esiste una soluzione alternativa comprovata che può essere usata per realizzare la funzionalità.

Soluzione alternativa: utilizzare il nome DNS per reindirizzare le connessioni al Name Node attivo. A questo scopo, è necessario assicurarsi che l'origine dati esterna utilizzi un nome DNS per comunicare con il Name Node. Quando si verifica un failover del Name Node, è necessario modificare l'indirizzo IP associato al nome DNS utilizzato nella definizione dell'origine dati esterna. Ciò reindirizza tutte le nuove connessioni al Name Node corretto. Le connessioni esistenti avranno esito negativo quando si verifica il failover. Per automatizzare questo processo, un "heartbeat" può eseguire il ping del Name Node attivo. Se si verifica un errore di heartbeat, si può presupporre che si sia verificato un failover e si può passare automaticamente all'indirizzo IP secondario.

## <a name="error-messages-and-possible-solutions"></a>Messaggi di errore e possibili soluzioni

Per risolvere gli errori delle tabelle esterne, vedere il blog di Murshed Zaman [https://blogs.msdn.microsoft.com/sqlcat/2016/06/21/polybase-setup-errors-and-possible-solutions/](https://blogs.msdn.microsoft.com/sqlcat/2016/06/21/polybase-setup-errors-and-possible-solutions/ "PolyBase setup errors and possible solutions") (Errori di installazione di PolyBase e possibili soluzioni).

## <a name="see-also"></a>Vedere anche

[Risolvere i problemi di connettività di PolyBase Kerberos](polybase-troubleshoot-connectivity.md)
