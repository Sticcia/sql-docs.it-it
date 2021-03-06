---
title: sysarticlecolumns (vista di sistema) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns view
ms.assetid: a8dd8d13-c827-45c4-87ba-802725301382
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1ffa8c9c45e1810fb4a81deed34f7c6c2e4a0ca0
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756546"
---
# <a name="sysarticlecolumns-system-view-transact-sql"></a>sysarticlecolumns (vista di sistema) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **sysarticlecolumns** Vista espone informazioni aggiuntive sulle colonne negli articoli pubblicati. Questa vista è archiviata nel database di distribuzione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifica un articolo.|  
|**colid**|**int**|Identifica una colonna di un articolo.|  
|**is_udt**|**int**|Indica se il tipo di dati della colonna è un tipo definito dall'utente (UDT). Un valore pari **1** indica una colonna con tipo definito dall'utente.|  
|**is_xml**|**int**|Indica se la colonna è un' **xml** colonna. Un valore pari **1** indica un' **xml** colonna.|  
|**is_max**|**int**|Indica se la colonna è una colonna di tipo di dati di valori di grandi dimensioni (**varchar (max)**, **nvarchar (max)** oppure **varbinary (max)**). Un valore pari **1** indica una colonna con valori di grandi dimensioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
