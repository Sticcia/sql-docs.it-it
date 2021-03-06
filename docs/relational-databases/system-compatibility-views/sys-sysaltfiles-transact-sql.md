---
title: sys.sysaltfiles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysaltfiles_TSQL
- sys.sysaltfiles
- sysaltfiles_TSQL
- sysaltfiles
dev_langs:
- TSQL
helpviewer_keywords:
- sysaltfiles system table
- sys.sysaltfiles compatibility view
ms.assetid: 698dec23-5336-4108-87a5-f8e407f8da09
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 941b51b6e05fd88a8b59b8e4f3b28ee145affe3d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47636559"
---
# <a name="syssysaltfiles-transact-sql"></a>sys.sysaltfiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In casi particolari contiene le righe corrispondenti ai file di un database.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**fileid**|**smallint**|Numero di identificazione del file. Questo valore è univoco per ogni database.|  
|**ID del gruppo**|**smallint**|Numero di identificazione del filegroup.|  
|**size**|**int**|Dimensioni del file espresse in pagine da 8 KB.|  
|**maxsize**|**int**|Dimensioni massime del file espresse in pagine da 8 KB.<br /><br /> 0 = Nessun aumento.<br /><br /> -1 = La dimensione del file aumenterà finché il disco è pieno.<br /><br /> 268435456 = La dimensione del file di log aumenterà fino al valore massimo di 2 TB.<br /><br /> Nota: I database che vengono aggiornati con una dimensione del file di log senza limiti segnalerà -1 per le dimensioni massime del file di log.|  
|**aumento delle dimensioni**|**int**|Aumento delle dimensioni del database.<br /><br /> 0 = Nessun aumento. I possibili valori sono un numero di pagine o una percentuale delle dimensioni del file, a seconda del valore di status. Se **lo stato** è 0x100000, **growth** è la percentuale di dimensioni del file; in caso contrario, è il numero di pagine.|  
|**status**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**perf**|**int**|Riservato.|  
|**dbid**|**smallint**|Numero di identificazione del database a cui appartiene il file.|  
|**name**|**sysname**|Nome logico del file.|  
|**Nome del file**|**nvarchar(260)**|Nome del dispositivo fisico, incluso il percorso completo del file.|  
  
## <a name="see-also"></a>Vedere anche  
 [Mapping di tabelle di sistema a viste di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Viste della compatibilità &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
