---
title: trace_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.trace_columns
- trace_columns
- trace_columns_TSQL
- sys.trace_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_columns catalog view
ms.assetid: 5c48eb09-9e9b-45dd-b151-ca39b026ece5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: beda27214f6ef805b84e9897e7f0dd48f424a79f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835479"
---
# <a name="systracecolumns-transact-sql"></a>sys.trace_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **trace_columns** vista del catalogo contiene un elenco di tutte le colonne di evento di traccia. Queste colonne non cambiano per una determinata versione di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Per un elenco completo degli eventi di traccia supportati, vedere [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] In alternativa, utilizzare le viste del catalogo di Eventi estesi.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**trace_column_id**|**smallint**|ID univoco della colonna.|  
|**name**|**nvarchar(128)**|Nome univoco della colonna. Questo parametro non è localizzato.|  
|**type_name**|**nvarchar(128)**|Nome del tipo di dati della colonna.|  
|**max_size**|**int**|Dimensioni massime della colonna, in byte.|  
|**is_filterable**|**bit**|Indica se la colonna può essere utilizzata con i filtri.<br /><br /> 0 = False<br /><br /> 1 = True|  
|**is_repeatable**|**bit**|Indica se è possibile fare riferimento alla colonna nei dati di colonne ripetute.<br /><br /> 0 = False<br /><br /> 1 = True|  
|**is_repeated_base**|**bit**|Indica se la colonna viene utilizzata come chiave univoca per fare riferimento a dati ripetuti.<br /><br /> 0 = False<br /><br /> 1 = True|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo dell'oggetto &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.traces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys.trace_categories &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys.trace_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys.trace_event_bindings &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys.trace_subclass_values &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
