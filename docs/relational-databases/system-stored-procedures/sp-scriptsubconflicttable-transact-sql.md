---
title: sp_scriptsubconflicttable (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_scriptsubconflicttable
- sp_scriptsubconflicttable_TSQL
helpviewer_keywords:
- sp_scriptsubconflicttable
ms.assetid: 13867145-3dad-47a4-8d50-a65175418479
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 91b4cca35fa5de3b6f19190a476ea82a69b53d81
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526313"
---
# <a name="spscriptsubconflicttable-transact-sql"></a>sp_scriptsubconflicttable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Genera script per la creazione di una tabella dei conflitti nel Sottoscrittore per un determinato articolo di sottoscrizione in coda. Lo script generato viene quindi eseguito nel database di sottoscrizione del Sottoscrittore. Questa stored procedure viene eseguita nel database di pubblicazione del server di pubblicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_scriptsubconflicttable [@publication =] 'publication'    , [@article =] 'article'  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @publication = ] 'publication'` È il nome della pubblicazione che contiene l'articolo. Deve essere un nome univoco all'interno del database. *pubblicazione* viene **sysname**, non prevede alcun valore predefinito.  
  
`[ @article = ] 'article'` È il nome dell'articolo della sottoscrizione. *articolo* viene **sysname**, non prevede alcun valore predefinito.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**cmdtext**|**nvarchar(4000)**|Restituisce lo script [!INCLUDE[tsql](../../includes/tsql-md.md)] per la creazione della tabella dei conflitti nel Sottoscrittore per l'articolo di sottoscrizione in coda. Lo script viene eseguito nel database di sottoscrizione del Sottoscrittore.|  
  
## <a name="remarks"></a>Note  
 **sp_scriptsubconflicttable** viene usato per i sottoscrittori con sottoscrizioni in cui lo snapshot iniziale viene applicato manualmente. La tabella dei conflitti è una tabella facoltativa nel Sottoscrittore.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server oppure **db_owner** ruolo predefinito del database possono eseguire **sp_scriptsubconflicttable**.  
  
## <a name="see-also"></a>Vedere anche  
 [Rilevamento e risoluzione dei conflitti per l'aggiornamento in coda](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
