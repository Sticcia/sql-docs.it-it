---
title: sys.dm_broker_queue_monitors (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_broker_queue_monitors
- sys.dm_broker_queue_monitors_TSQL
- dm_broker_queue_monitors_TSQL
- sys.dm_broker_queue_monitors
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_queue_monitors dynamic management view
ms.assetid: 401207dc-ef4a-4a3f-879c-76dcbb52d6bc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fed9d261f692e9c9e1eee4f7078ca69e8c74594e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760117"
---
# <a name="sysdmbrokerqueuemonitors-transact-sql"></a>sys.dm_broker_queue_monitors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni monitoraggio di coda nell'istanza. Un monitoraggio di coda gestisce l'attivazione di una coda.  
  

|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|Identificatore di oggetto per il database contenente la coda controllata dal monitoraggio. Ammette valori Null.|  
|**queue_id**|**int**|Identificatore di oggetto per la coda controllata dal monitoraggio. Ammette valori Null.|  
|**state**|**nvarchar(32)**|Stato del server di monitoraggio. Ammette valori Null. I possibili valori sono i seguenti:<br /><br /> **INACTIVE**<br /><br /> **RICEVE UNA NOTIFICA**<br /><br /> **RECEIVES_OCCURRING**|  
|**last_empty_rowset_time**|**datetime**|Ultima volta in cui un'istruzione RECEIVE dalla coda ha restituito un risultato vuoto. Ammette valori Null.|  
|**last_activated_time**|**datetime**|Ultima volta in cui il monitoraggio di coda ha attivato una stored procedure. Ammette valori Null.|  
|**tasks_waiting**|**int**|Numero di sessioni in attesa della coda all'interno di un'istruzione RECEIVE. Ammette valori Null.<br /><br /> Nota: Questo numero include qualsiasi sessione che esegue un'istruzione receive, indipendentemente dal fatto che il monitoraggio di coda avviato la sessione. Ciò è valido solo in caso di utilizzo di WAITFOR in combinazione con RECEIVE. Queste attività rimangono essenzialmente in attesa dell'arrivo di messaggi nella coda.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-current-status-queue-monitor"></a>A. Stato corrente del monitoraggio di coda  
 Nello scenario seguente viene restituito lo stato corrente di tutte le code di messaggi.  
  
```  
SELECT t1.name AS [Service_Name],  t3.name AS [Schema_Name],  t2.name AS [Queue_Name],    
CASE WHEN t4.state IS NULL THEN 'Not available'   
ELSE t4.state   
END AS [Queue_State],    
CASE WHEN t4.tasks_waiting IS NULL THEN '--'   
ELSE CONVERT(VARCHAR, t4.tasks_waiting)   
END AS tasks_waiting,   
CASE WHEN t4.last_activated_time IS NULL THEN '--'   
ELSE CONVERT(varchar, t4.last_activated_time)   
END AS last_activated_time ,    
CASE WHEN t4.last_empty_rowset_time IS NULL THEN '--'   
ELSE CONVERT(varchar,t4.last_empty_rowset_time)   
END AS last_empty_rowset_time,   
(   
SELECT COUNT(*)   
FROM sys.transmission_queue t6   
WHERE (t6.from_service_name = t1.name) ) AS [Tran_Message_Count]   
FROM sys.services t1    INNER JOIN sys.service_queues t2   
ON ( t1.service_queue_id = t2.object_id )     
INNER JOIN sys.schemas t3 ON ( t2.schema_id = t3.schema_id )    
LEFT OUTER JOIN sys.dm_broker_queue_monitors t4   
ON ( t2.object_id = t4.queue_id  AND t4.database_id = DB_ID() )    
INNER JOIN sys.databases t5 ON ( t5.database_id = DB_ID() );  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Viste a gestione dinamica relative a Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

