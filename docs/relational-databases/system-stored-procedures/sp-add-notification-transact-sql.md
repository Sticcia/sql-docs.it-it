---
title: sp_add_notification (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_notification_TSQL
- sp_add_notification
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_notification
ms.assetid: 0525e0a2-ed0b-4e69-8a4c-a9e3e3622fbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a7c6e4531597faf9cacb883cf3ea3432b6e8ff9f
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492521"
---
# <a name="spaddnotification-transact-sql"></a>sp_add_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Imposta una notifica per un avviso.  
  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_add_notification [ @alert_name = ] 'alert' ,   
    [ @operator_name = ] 'operator' ,   
    [ @notification_method = ] notification_method  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @alert_name = ] 'alert'` L'avviso per questa notifica. *avviso* viene **sysname**, non prevede alcun valore predefinito.  
  
`[ @operator_name = ] 'operator'` L'operatore da notificare quando viene generato l'avviso. *operatore* viene **sysname**, non prevede alcun valore predefinito.  
  
`[ @notification_method = ] notification_method` Il metodo mediante il quale l'operatore riceve una notifica. *notification_method* viene **tinyint**, non prevede alcun valore predefinito. *notification_method* può essere uno o più dei valori seguenti combinati con un' **OR** operatore logico.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**1**|Posta elettronica|  
|**2**|Cercapersone|  
|**4**|**net send**|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 None  
  
## <a name="remarks"></a>Note  
 **sp_add_notification** deve essere eseguita la **msdb** database.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] include un semplice strumento grafico per la gestione del sistema di avvisi. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] è lo strumento consigliato per la configurazione di un'infrastruttura di avvisi.  
  
 Per inviare una notifica in risposta a un avviso, è innanzitutto necessario configurare [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent per l'invio di messaggi.  
  
 Gli eventuali errori che si verificano durante l'invio di un messaggio di posta elettronica o di una notifica su cercapersone vengono registrati nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **sysadmin** ruolo predefinito del server possono eseguire **sp_add_notification**.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene aggiunta una notifica di posta elettronica per l'avviso specificato (`Test Alert`).  
  
> **NOTA:** Nell'esempio si presume che l'avviso `Test Alert` sia già esistente e che `François Ajenstat` sia un nome di operatore valido.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_notification  
 @alert_name = N'Test Alert',  
 @operator_name = N'François Ajenstat',  
 @notification_method = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [sp_delete_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-notification-transact-sql.md)   
 [sp_help_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [Stored procedure di sistema &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
