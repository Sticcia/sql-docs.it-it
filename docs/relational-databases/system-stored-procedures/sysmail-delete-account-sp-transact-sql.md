---
title: sysmail_delete_account_sp (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
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
- sysmail_delete_account_sp
- sysmail_delete_account_sp_TSQL
dev_langs: TSQL
helpviewer_keywords: sysmail_delete_account_sp
ms.assetid: 2adcac78-4a4a-407e-9666-1d9c43c73cc2
caps.latest.revision: "40"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9bed6fa3219e9918c2f9f237b9f660d1dcb0a72f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysmaildeleteaccountsp-transact-sql"></a>sysmail_delete_account_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Elimina un account SMTP di Posta elettronica database. Per eliminare un account, è inoltre possibile utilizzare Configurazione guidata posta elettronica database.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sysmail_delete_account_sp { [ @account_id = ] account_id | [ @account_name = ] 'account_name' }   
```  
  
## <a name="arguments"></a>Argomenti  
 [  **@account_id**  =] *account_id*  
 Numero di ID dell'account da eliminare. *account_id* è **int**, non prevede alcun valore predefinito. Entrambi *account_id* o *account_name* deve essere specificato.  
  
 [  **@account_name**  =] **'***account_name***'**  
 Nome dell'account da eliminare. *account_name* è **sysname**, non prevede alcun valore predefinito. Entrambi *account_id* o *account_name* deve essere specificato.  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="result-sets"></a>Set di risultati  
 Nessuno  
  
## <a name="remarks"></a>Osservazioni  
 Questa procedura elimina l'account specificato anche se è utilizzato da un profilo. Un profilo che non include account non è in grado di inviare correttamente messaggi di posta elettronica.  
  
 La stored procedure **sysmail_delete_account_sp** nel **msdb** database ed è di proprietà di **dbo** dello schema. La procedura deve essere eseguita con un nome in tre parti se il database corrente non è **msdb**.  
  
## <a name="permissions"></a>Permissions  
 Autorizzazioni di esecuzione per questa routine per impostazione predefinita ai membri del **sysadmin** ruolo predefinito del server.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene illustrata un'operazione di eliminazione dell'account di Posta elettronica database denominato `AdventureWorks Administrator`.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_account_sp  
    @account_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Posta elettronica database](../../relational-databases/database-mail/database-mail.md)   
 [Creare un Account di posta elettronica Database](../../relational-databases/database-mail/create-a-database-mail-account.md)   
 [Oggetti di configurazione di posta elettronica database](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [sysmail_add_account_sp &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sysmail-add-account-sp-transact-sql.md)   
 [sysmail_delete_profileaccount_sp &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sysmail-delete-profile-sp-transact-sql.md)   
 [sysmail_delete_profileaccount_sp &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sysmail-delete-profileaccount-sp-transact-sql.md)   
 [sysmail_help_account_sp &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sysmail-help-account-sp-transact-sql.md)   
 [sysmail_help_profile_sp &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sysmail-help-profile-sp-transact-sql.md)   
 [sysmail_help_profileaccount_sp &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sysmail-help-profileaccount-sp-transact-sql.md)   
 [sysmail_update_profileaccount_sp &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sysmail-update-profileaccount-sp-transact-sql.md)  
  
  