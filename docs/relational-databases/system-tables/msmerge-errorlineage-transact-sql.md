---
title: MSmerge_errorlineage (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_errorlineage_TSQL
- MSmerge_errorlineage
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_errorlineage system table
ms.assetid: 3bcbd328-c958-4cd4-a573-3c35539fa919
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d07a3fadfd2439c35b9d5255ff94d58c79bbbae5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794173"
---
# <a name="msmergeerrorlineage-transact-sql"></a>MSmerge_errorlineage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Il **MSmerge_errorlineage** tabella contiene righe che sono state eliminate nel Sottoscrittore, ma la cui eliminazione non viene propagata al server di pubblicazione. Questa tabella è archiviata nei database di pubblicazione e di sottoscrizione.  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Valore integer assegnato alla tabella pubblicata per la replica di tipo merge. Corrisponde al campo del nome alternativo nella **sysmergearticles** tabella.|  
|**rowguid**|**uniqueidentifier**|Identificatore di riga.|  
|**derivazione**|**varbinary(501)**|Archivia un elenco di cronologia dei Sottoscrittori e dei server di pubblicazione in cui sono stati eseguiti aggiornamenti a una riga. Consente di rilevare e risolvere eventuali situazioni di conflitto.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tabelle di replica &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Viste della replica &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
