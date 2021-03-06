---
title: sp_deletemergeconflictrow (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_deletemergeconflictrow
- sp_deletemergeconflictrow_TSQL
helpviewer_keywords:
- sp_deletemergeconflictrow
ms.assetid: 64cf1186-28b8-4cd9-88f1-a7808a9c8d60
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5bef3e4902562edde0adb2a4f495c51e6a82b091
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58535283"
---
# <a name="spdeletemergeconflictrow-transact-sql"></a>sp_deletemergeconflictrow (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vengono eliminate righe da una tabella dei conflitti o la [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) tabella. Questa stored procedure viene eseguita nella stessa posizione di archiviazione della tabella con conflitti in qualsiasi database.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_deletemergeconflictrow [ [ @conflict_table = ] 'conflict_table' ]  
    [ , [ @source_object = ] 'source_object' ]  
    { , [ @rowguid = ] 'rowguid'  
        , [ @origin_datasource = ] 'origin_datasource' ] }  
    [ , [ @drop_table_if_empty = ] 'drop_table_if_empty' ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @conflict_table = ] 'conflict_table'` È il nome della tabella dei conflitti. *conflict_table* viene **sysname**, il valore predefinito è **%**. Se il *conflict_table* è specificato come NULL oppure **%**, il conflitto si presuppone che sia un conflitto di eliminazione e la riga corrispondente *rowguid* e*origin_datasource* e *source_object* viene eliminato dal [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) tabella.  
  
`[ @source_object = ] 'source_object'` È il nome della tabella di origine. *source_object* viene **nvarchar(386)**, con un valore predefinito è NULL.  
  
`[ @rowguid = ] 'rowguid'` È l'identificatore di riga per il conflitto di eliminazione. *ROWGUID* viene **uniqueidentifier**, non prevede alcun valore predefinito.  
  
`[ @origin_datasource = ] 'origin_datasource'` È l'origine del conflitto. *origin_datasource* viene **nvarchar (255)**, non prevede alcun valore predefinito.  
  
`[ @drop_table_if_empty = ] 'drop_table_if_empty'` Flag che indica che il *conflict_table* è deve essere eliminata se risulta vuota. *drop_table_if_empty* viene **varchar (10)**, con un valore predefinito è FALSE.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_deletemergeconflictrow** viene utilizzata nella replica di tipo merge.  
  
 [MSmerge_conflicts_info &#40;Transact-SQL&#41; ](../../relational-databases/system-tables/msmerge-conflicts-info-transact-sql.md) tabella è una tabella di sistema e non viene eliminata dal database, anche se è vuota.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server oppure **db_owner** ruolo predefinito del database possono eseguire **sp_deletemergeconflictrow**.  
  
## <a name="see-also"></a>Vedere anche  
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
