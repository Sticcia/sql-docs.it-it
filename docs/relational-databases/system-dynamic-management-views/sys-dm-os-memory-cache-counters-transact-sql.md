---
title: sys.dm_os_memory_cache_counters (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_counters_TSQL
- dm_os_memory_cache_counters_TSQL
- sys.dm_os_memory_cache_counters
- dm_os_memory_cache_counters
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_counters dynamic management view
ms.assetid: ca7bd036-d661-4c17-b00a-e1a975bd8932
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 19beaafe3e73265eb12f825190ee8aafcdf59897
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63047399"
---
# <a name="sysdmosmemorycachecounters-transact-sql"></a>sys.dm_os_memory_cache_counters (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Viene restituito uno snapshot dello stato di una cache in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. **Sys.dm_os_memory_cache_counters** fornisce informazioni di run-time sulle voci di cache allocate, il relativo utilizzo e l'origine di memoria per le voci della cache.  
  
> **NOTA:** Per chiamare questo elemento dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] oppure [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], usare il nome **sys.dm_pdw_nodes_os_memory_cache_counters**.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Indica l'indirizzo (chiave primaria) dei contatori associati a una cache specifica. Non ammette i valori Null.|  
|**name**|**nvarchar(256)**|Specifica il nome della cache. Non ammette i valori Null.|  
|**type**|**nvarchar(60)**|Indica il tipo di cache associato a questa voce. Non ammette i valori Null.|  
|**single_pages_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità, in kilobyte, della memoria a pagina singola allocata. Corrisponde alla quantità di memoria allocata tramite l'allocatore di pagine singole. Si riferisce alla pagine di 8 KB prelevate direttamente dal pool di buffer per questa cache. Non ammette i valori Null.|  
|**pages_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Specifica la quantità di memoria, in kilobyte, allocata nella cache. Non ammette i valori Null.|  
|**multi_pages_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità, in kilobyte, della memoria a più pagine allocata. Corrisponde alla quantità di memoria allocata tramite l'allocatore di pagine multiple del nodo di memoria. Questa memoria viene allocata all'esterno del pool di buffer e utilizza l'allocatore virtuale dei nodi di memoria. Non ammette i valori Null.|  
|**pages_in_use_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] tramite [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Specifica la quantità di memoria, in kilobyte, allocata e in uso nella cache. Ammette i valori Null.  I valori per gli oggetti di tipo `USERSTORE_<*>` non vengono rilevati.  Viene riportato NULL.|  
|**single_pages_in_use_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità, in kilobyte, della memoria a pagina singola utilizzata. Ammette i valori Null. Queste informazioni non vengono rilevate per gli oggetti di tipo USERSTORE_\<* > e questi valori saranno NULL.|  
|**multi_pages_in_use_kb**|**bigint**|**Si applica a**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] tramite [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].<br /><br /> Quantità, in kilobyte, della memoria a più pagine utilizzata. Ammette valori Null. Queste informazioni non vengono rilevate per gli oggetti di tipo USERSTORE_\<* >, e questi valori saranno NULL.|  
|**entries_count**|**bigint**|Indica il numero di voci nella cache. Non ammette i valori Null.|  
|**entries_in_use_count**|**bigint**|Indica il numero di voci della cache utilizzate. Non ammette i valori Null.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo in questa distribuzione.|  
  
## <a name="permissions"></a>Permissions 

Sul [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], è necessario `VIEW SERVER STATE` autorizzazione.   
Sul [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], è necessario il `VIEW DATABASE STATE` autorizzazione nel database.   

## <a name="see-also"></a>Vedere anche  
  [Viste a gestione dinamica relative al sistema di operativo SQL Server &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


