---
title: syscollector_execution_stats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_execution_stats
- syscollector_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- syscollector_execution_stats view
- data collector view
ms.assetid: 23e35ac5-fbbf-4922-970c-f4fac44c1263
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b89823af1295b329046395a8f3c345401ca61805
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62760186"
---
# <a name="syscollectorexecutionstats-transact-sql"></a>syscollector_execution_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fornisce informazioni sull'esecuzione delle attività per un set di raccolta o un pacchetto.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**log_id**|**bigint**|Identifica ogni esecuzione del set di raccolta. Utilizzato per unire questa vista agli altri log dettagliati. Non ammette i valori Null.|  
|**task_name**|**nvarchar(128)**|Nome dell'attività del pacchetto o del set di raccolta a cui sono destinate queste informazioni. Non ammette i valori Null.|  
|**execution_row_count_in**|**int**|Il numero di righe elaborate all'inizio del flusso di dati. Ammette i valori Null.|  
|**execution_row_count_out**|**int**|Il numero di righe elaborate alla fine del flusso di dati. Ammette i valori Null.|  
|**execution_row_count_errors**|**int**|Numero di righe in cui si è verificato un errore durante il flusso di dati. Ammette i valori Null.|  
|**execution_time_ms**|**int**|Intervallo di tempo, in millisecondi, da attendere per il completamento dell'attività. Ammette i valori Null.|  
|**log_time**|**datetime**|L'ora di registrazione di queste informazioni. Non ammette i valori Null.|  
  
## <a name="permissions"></a>Permissions  
 Richiede l'autorizzazione SELECT per **dc_operator**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Viste dell'agente di raccolta dati &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Raccolta dati](../../relational-databases/data-collection/data-collection.md)  
  
  
