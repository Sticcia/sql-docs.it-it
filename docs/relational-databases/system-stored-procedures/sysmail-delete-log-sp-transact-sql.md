---
title: sysmail_delete_log_sp (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_delete_log_sp_TSQL
- sysmail_delete_log_sp
dev_langs: TSQL
helpviewer_keywords: sysmail_delete_log_sp
ms.assetid: e94b37a1-70ad-46a5-86c0-721892156f7c
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d479d84bda33ff7b1ef2877f0d783f9588d84e4a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysmaildeletelogsp-transact-sql"></a>sysmail_delete_log_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina eventi dal log di Posta elettronica database. È possibile eliminare tutti gli eventi nel log oppure solo quelli che soddisfano un particolare criterio relativo alla data o al tipo.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_delete_log_sp  [ [ @logged_before = ] 'logged_before' ]  
    [, [ @event_type = ] 'event_type' ]  
  
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@logged_before**  =] **'***logged_before***'**  
 Elimina le voci anteriori alla data e ora specificate dal *logged_before* argomento. *logged_before* è **datetime** con valore predefinito è NULL. che indica tutte le date.  
  
 [  **@event_type**  =] **'***event_type***'**  
 Elimina le voci del tipo specificato come di log di *event_type*. *event_type* è **varchar(15)** prevede alcun valore predefinito. Le voci valide sono **successo**, **avviso**, **errore**, e **informativo**. NULL indica tutti i tipi di eventi.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **sysmail_delete_log_sp** stored procedure per eliminare definitivamente le voci dal log di posta elettronica Database. Un argomento facoltativo consente di eliminare solo i record meno recenti tramite l'impostazione di una data e un'ora. Gli eventi con una data anteriore a quella specificata nell'argomento verranno eliminati. Un argomento facoltativo consente di eliminare solo gli eventi di un determinato tipo, specificato come il **event_type** argomento.  
  
 L'eliminazione delle voci dal log di Posta elettronica database non comporta la rimozione dei messaggi di posta elettronica dalle tabelle di Posta elettronica database. Utilizzare [sysmail_delete_mailitems_sp](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md) eliminare posta elettronica dalle tabelle di posta elettronica Database.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server può accedere a questa procedura.  
  
## <a name="examples"></a>Esempi  
  
### <a name="a-deleting-all-events"></a>A. Eliminazione di tutti gli eventi  
 Nell'esempio seguente vengono eliminati tutti gli eventi nel log di Posta elettronica database.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp ;  
GO  
```  
  
### <a name="b-deleting-the-oldest-events"></a>B. Eliminazione degli eventi meno recenti  
 Nell'esempio seguente vengono eliminati gli eventi nel log di Posta elettronica database con una data anteriore al 9 ottobre 2005.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp  
    @logged_before = 'October 9, 2005' ;  
GO  
```  
  
### <a name="c-deleting-all-events-of-a-certain-type"></a>C. Eliminazione di tutti gli eventi di un determinato tipo  
 Nell'esempio seguente vengono eliminati i messaggi di operazione riuscita nel log di Posta elettronica database.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_log_sp  
    @event_type = 'success' ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sysmail_event_log &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sysmail-event-log-transact-sql.md)   
 [sysmail_delete_mailitems_sp &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sysmail-delete-mailitems-sp-transact-sql.md)   
 [Creare un processo di SQL Server Agent per l'archiviazione di messaggi e log eventi di Posta elettronica database](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md)  
  
  