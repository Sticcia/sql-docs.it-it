---
title: Sys.dm_os_sys_memory (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_os_sys_memory
- sys.dm_os_sys_memory_TSQL
- sys.dm_os_sys_memory
- dm_os_sys_memory_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_os_sys_memory dynamic management view
ms.assetid: 1ca58814-1caa-44c1-b307-ff0bdcbbef62
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: bec663451e720a350b4cbf9c295d8e3946981a0e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmossysmemory-transact-sql"></a>sys.dm_os_sys_memory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Restituisce le informazioni sulla memoria dal sistema operativo.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]è vincolato da e risponde a condizioni di memoria esterna al livello del sistema operativo e i limiti fisici dell'hardware sottostante. La determinazione dello stato complessivo del sistema è un'importante parte della valutazione dell'utilizzo della memoria di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Per chiamare questo metodo dal [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] o [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilizzare il nome **sys.dm_pdw_nodes_os_sys_memory**.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**total_physical_memory_kb**|**bigint**|Dimensione totale della memoria fisica disponibile per il sistema operativo, espressa in kilobyte (KB).|  
|**available_physical_memory_kb**|**bigint**|Dimensione della memoria fisica disponibile, espressa in KB.|  
|**total_page_file_kb**|**bigint**|Dimensione del limite del commit riportata dal sistema operativo, espressa in KB|  
|**available_page_file_kb**|**bigint**|Totale di file di paging non utilizzati, espresso in KB.|  
|**system_cache_kb**|**bigint**|Totale di memoria cache del sistema, espressa in KB.|  
|**kernel_paged_pool_kb**|**bigint**|Totale del pool paginato del kernel, espresso in KB.|  
|**kernel_nonpaged_pool_kb**|**bigint**|Totale del pool non paginato del kernel, espresso in KB.|  
|**system_high_memory_signal_state**|**bit**|Stato della notifica relativa alle risorse elevate della memoria di sistema. Un valore 1 indica che Windows ha impostato un segnale di memoria elevato. Per ulteriori informazioni, vedere [CreateMemoryResourceNotification](http://go.microsoft.com/fwlink/?LinkId=82427) in MSDN library.|  
|**system_low_memory_signal_state**|**bit**|Stato della notifica relativa alle risorse insufficienti della memoria di sistema. Un valore 1 indica che Windows ha impostato un segnale di memoria basso. Per ulteriori informazioni, vedere [CreateMemoryResourceNotification](http://go.microsoft.com/fwlink/?LinkId=82427) in MSDN library.|  
|**system_memory_state_desc**|**nvarchar(256)**|Descrizione dello stato della memoria. Vedere la tabella riportata di seguito.|  
|**pdw_node_id**|**int**|**Si applica a**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L'identificatore per il nodo che utilizza questo tipo di distribuzione.|  
  
|Condizione|Valore|  
|---------------|-----------|  
|system_high_memory_signal_state = 1<br /><br /> e<br /><br /> system_low_memory_signal_state = 0|La quantità di memoria fisica disponibile è elevata.|  
|system_high_memory_signal_state = 0<br /><br /> e<br /><br /> system_low_memory_signal_state = 1|La quantità di memoria fisica disponibile è bassa.|  
|system_high_memory_signal_state = 0<br /><br /> e<br /><br /> system_low_memory_signal_state = 0|L'utilizzo della memoria fisica è costante|  
|system_high_memory_signal_state = 1<br /><br /> e<br /><br /> system_low_memory_signal_state = 1|La stato della memoria fisica è in fase di transizione<br /><br /> Il segnale massimo e minimo non devono mai essere attivi contemporaneamente. Tuttavia, modifiche rapide a livello di sistema operativo possono fare sì che entrambi i valori sembrino essere attivi in un'applicazione della modalità utente. La visualizzazione di entrambi i segnali attivi verrà interpretata come una stato della transizione.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Relative al sistema operativo SQL Server viste a gestione dinamica &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  

