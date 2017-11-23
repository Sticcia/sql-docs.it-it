---
title: Sys.dm db_missing_index_columns (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_missing_index_columns_TSQL
- sys.dm_db_missing_index_columns_TSQL
- sys.dm_db_missing_index_columns
- dm_db_missing_index_columns
dev_langs: TSQL
helpviewer_keywords:
- sys.dm_db_missing_index_columns dynamic management function
- missing indexes feature [SQL Server], sys.dm_db_missing_index_columns dynamic management function
ms.assetid: 3b24e5ed-0c79-47e5-805c-a0902d0aeb86
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6f2f358532d43453242fea591ab9ac12024230f2
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbmissingindexcolumns-transact-sql"></a>sys.dm_db_missing_index_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce informazioni sulle colonne di una tabella di database in cui manca un indice, escludendo gli indici spaziali. **Sys.dm db_missing_index_columns** è una funzione a gestione dinamica.  

## <a name="syntax"></a>Sintassi  
  
```  
  
sys.dm_db_missing_index_columns(index_handle)  
```  
  
## <a name="arguments"></a>Argomenti  
 *index_handle*  
 Valore intero che identifica in modo univoco un indice mancante. Può essere ricavato dagli oggetti a gestione dinamica seguenti:  
  
 [Sys.dm db_missing_index_details &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)  
  
 [Sys.dm db_missing_index_groups &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)  
  
## <a name="table-returned"></a>Tabella restituita  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**column_id**|**int**|ID della colonna.|  
|**column_name**|**sysname**|Nome della colonna della tabella.|  
|**column_usage**|**varchar (20)**|Modalità di utilizzo della colonna da parte della query. I valori possibili e le relative descrizioni sono:<br /><br /> UGUAGLIANZA: Colonna contribuisce a un predicato che esprime uguaglianza, nel formato seguente: <br />                        *Table. Column* = *constant_value*<br /><br /> DISUGUAGLIANZA: La colonna contribuisce a un predicato che esprime disuguaglianza, ad esempio, un predicato nella forma: *Table. Column* > *constant_value*. Qualsiasi operatore di confronto diverso da "=" esprime disuguaglianza.<br /><br /> Includi: Colonna non viene utilizzata per valutare un predicato, ma viene utilizzato per altri scopi, ad esempio, per coprire una query.|  
  
## <a name="remarks"></a>Osservazioni  
 Le informazioni restituite da **Sys.dm db_missing_index_columns** viene aggiornato quando una query viene ottimizzata attraverso il query optimizer e non è persistente. Le informazioni relative agli indici mancanti vengono mantenute solo fino al riavvio di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Per mantenere tali informazioni anche dopo il riciclo del server, gli amministratori di database devono eseguirne periodicamente copie di backup.  
  
## <a name="transaction-consistency"></a>Consistenza delle transazioni  
 Se in una transazione viene creata o eliminata una tabella, le righe contenenti le informazioni sugli indici mancanti per gli oggetti eliminati vengono rimosse da questo oggetto a gestione dinamica, mantenendo la consistenza delle transazioni.  
  
## <a name="permissions"></a>Permissions  
 Per eseguire query su questa funzione a gestione dinamica, è necessario che agli utenti sia stata concessa l'autorizzazione VIEW SERVER STATE o qualsiasi autorizzazione che include l'autorizzazione VIEW SERVER STATE.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene eseguita una query sulla tabella `Address` e quindi viene eseguita un'ulteriore query utilizzando la vista a gestione dinamica `sys.dm_db_missing_index_columns` per restituire le colonne della tabella per cui manca un indice.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, StateProvinceID, PostalCode  
FROM Person.Address  
WHERE StateProvinceID = 9;  
GO  
SELECT mig.*, statement AS table_name,  
    column_id, column_name, column_usage  
FROM sys.dm_db_missing_index_details AS mid  
CROSS APPLY sys.dm_db_missing_index_columns (mid.index_handle)  
INNER JOIN sys.dm_db_missing_index_groups AS mig ON mig.index_handle = mid.index_handle  
ORDER BY mig.index_group_handle, mig.index_handle, column_id;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sys.dm db_missing_index_details &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-details-transact-sql.md)   
 [Sys.dm db_missing_index_groups &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-groups-transact-sql.md)   
 [Sys.dm db_missing_index_group_stats &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-missing-index-group-stats-transact-sql.md)  
  
  