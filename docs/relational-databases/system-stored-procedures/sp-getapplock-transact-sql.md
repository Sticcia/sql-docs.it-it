---
title: sp_getapplock (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_getapplock_TSQL
- sp_getapplock
dev_langs:
- TSQL
helpviewer_keywords:
- application locks
- sp_getapplock
ms.assetid: e1e85908-9f31-47cf-8af6-88c77e6f24c9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c79a3e34ea6ca1bbebfa35a77020b81618514133
ms.sourcegitcommit: c19696d3d67161ce78aaa5340964da3256bf602d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2018
ms.locfileid: "52617581"
---
# <a name="spgetapplock-transact-sql"></a>sp_getapplock (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Acquisisce un blocco su una risorsa di applicazione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_getapplock [ @Resource = ] 'resource_name' ,  
     [ @LockMode = ] 'lock_mode'   
     [ , [ @LockOwner = ] 'lock_owner' ]   
     [ , [ @LockTimeout = ] 'value' ]  
     [ , [ @DbPrincipal = ] 'database_principal' ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argomenti  
 [ @Resource=] '*resource_name*'  
 Stringa contenente un nome che identifica la risorsa di blocco. L'applicazione deve garantire che il nome della risorsa sia univoco. Il nome specificato viene sottoposto internamente ad hashing per creare un valore che è possibile archiviare in Gestione blocchi di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *resource_name* viene **nvarchar(255** non prevede alcun valore predefinito. Se una stringa di risorsa è più lunga **nvarchar(255**, esso verrà troncato a **nvarchar(255**.  
  
 *resource_name* è binario rispetto ed è pertanto tra maiuscole e minuscole indipendentemente dalle impostazioni delle regole di confronto del database corrente.  
  
> [!NOTE]  
>  Dopo l'acquisizione di un blocco a livello di applicazione, è possibile recuperare solo i primi 32 caratteri in testo normale. La parte rimanente viene sottoposta a hashing.  
  
 [ @LockMode=] '*lock_mode*'  
 Modalità di blocco da acquisire per una particolare risorsa. *lock_mode* è di tipo **nvarchar(32)** e non dispone di valore predefinito. Il valore può essere uno dei seguenti, ovvero **Shared**, **Update**, **IntentShared**, **IntentExclusive**, o **esclusivo**.  
  
 [ @LockOwner=] '*lock_owner*'  
 Proprietario del blocco, ovvero il valore di *lock_owner* al momento della richiesta del blocco. *lock_owner* è **nvarchar(32)**. Il valore può essere **Transaction** (impostazione predefinita) o **Session**. Quando la *lock_owner* valore è **transazione**, predefinito o specificato in modo esplicito, sp_getapplock deve essere eseguito in una transazione.  
  
 [ @LockTimeout=] '*valore*'  
 Valore di timeout del blocco espresso in millisecondi. Il valore predefinito è lo stesso come il valore restituito da@LOCK_TIMEOUT. Per indicare che una richiesta di blocco deve restituire un codice restituito-1 invece di attendere il blocco quando la richiesta non può essere soddisfatta immediatamente, specificare 0.  
  
 [ @DbPrincipal=] '*database_principal*'  
 Utente, ruolo o ruolo applicazione al quale sono state assegnate autorizzazioni per un oggetto di un database. Il chiamante della funzione deve essere un membro del *database_principal*, dbo o db_owner ruolo predefinito del database per chiamare la funzione correttamente. Il valore predefinito è public.  
  
## <a name="return-code-values"></a>Valori restituiti  
 \>= 0 (esito positivo), or < 0 (esito negativo)  
  
|Value|Risultato|  
|-----------|------------|  
|0|Il blocco è stato concesso in modo sincrono.|  
|1|Il blocco è stato concesso dopo il rilascio di altri blocchi incompatibili.|  
|-1|La richiesta di blocco è scaduta.|  
|-2|La richiesta di blocco è stata annullata.|  
|-3|La richiesta di blocco è stata scelta come vittima del deadlock.|  
|-999|Indica un errore di convalida di un parametro o un altro errore di chiamata.|  
  
## <a name="remarks"></a>Note  
 I blocchi acquisiti per una risorsa sono associati alla transazione o alla sessione corrente. I blocchi associati alla transazione corrente vengono rilasciati in corrispondenza del commit o del rollback della transazione. I blocchi associati alla sessione vengono rilasciati al termine della sessione. In caso di arresto del server per qualsiasi motivo, vengono rilasciati tutti i blocchi.  
  
 La risorsa di blocco creata da sp_getapplock è valida per il database corrente nella sessione corrente. Ogni risorsa di blocco viene identificata tramite la combinazione dei valori seguenti:  
  
-   ID del database contenente la risorsa di blocco.  
  
-   Entità di database specificata nel parametro @DbPrincipal.  
  
-   Nome di blocco specificato nel parametro @Resource.  
  
 Solo un membro dell'entità di database specificata nel parametro @DbPrincipal può acquisire blocchi a livello di applicazione che specificano tale entità. I membri dei ruoli dbo e db_owner vengono considerati in modo implicito membri di tutti i ruoli.  
  
 È possibile rilasciare un blocco in modo esplicito tramite sp_releaseapplock. Se un'applicazione richiama sp_getapplock più volte per la stessa risorsa di blocco, per rilasciare il blocco è necessario richiamare sp_releaseapplock lo stesso numero di volte.  Quando un blocco viene aperto con la `Transaction` proprietario di blocco, di blocco viene rilasciato quando è stato eseguito il commit o il rollback della transazione.
  
 Se sp_getapplock viene chiamata più volte per una stessa risorsa di blocco ma la modalità di blocco specificata in una delle richieste è diversa da quella già esistente, verrà eseguita un'unione delle due modalità di blocco. Nella maggior parte dei casi la modalità di blocco viene promossa in base alla modalità che risulta più restrittiva tra quella esistente e quella nuova. Tale modalità viene quindi mantenuta fino al rilascio definitivo del blocco, anche se vengono eseguite chiamate di rilascio del blocco prima di tale momento. Nella sequenza di chiamate seguente, ad esempio, la risorsa viene mantenuta in modalità `Exclusive` anziché in modalità `Shared`.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Shared';  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Exclusive';  
EXEC @result = sp_releaseapplock @Resource = 'Form1';  
COMMIT TRANSACTION;  
GO  
```  
  
 Un deadlock con un blocco a livello di applicazione non comporta il rollback della transazione che ha richiesto il blocco. Le eventuali operazioni di rollback richieste a causa del valore restituito devono essere eseguite in modo manuale. È pertanto consigliabile includere nel codice il controllo degli errori, in modo che venga avviata un'istruzione ROLLBACK TRANSACTION o un'azione alternativa se vengono restituiti valori specifici, ad esempio -3.  
  
 Esempio:  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Exclusive';  
IF @result = -3  
BEGIN  
    ROLLBACK TRANSACTION;  
END  
ELSE  
BEGIN  
    EXEC @result = sp_releaseapplock @Resource = 'Form1';  
    COMMIT TRANSACTION;  
END;  
GO  
```  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per identificare la risorsa viene utilizzato l'ID del database corrente. Pertanto, se si esegue sp_getapplock su database diversi, vengono acquisiti blocchi separati su risorse diverse anche se i valori dei parametri sono identici.  
  
 Utilizzare la vista a gestione dinamica sys.dm_tran_locks o la stored procedure sp_lock system per esaminare le informazioni di blocco oppure utilizzare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per monitorare i blocchi.  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'appartenenza al ruolo public.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene inserito un blocco condiviso, associato alla transazione corrente, nella risorsa `Form1` del database `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
BEGIN TRAN;  
DECLARE @result int;  
EXEC @result = sp_getapplock @Resource = 'Form1',   
               @LockMode = 'Shared';  
COMMIT TRAN;  
GO  
```  
  
 Nell'esempio seguente viene specificato `dbo` come entità di database.  
  
```  
BEGIN TRAN;  
EXEC sp_getapplock @DbPrincipal = 'dbo', @Resource = 'AdventureWorks2012',   
     @LockMode = 'Shared';  
COMMIT TRAN;  
GO  
```  
  
## <a name="see-also"></a>Vedere anche  
 [APPLOCK_MODE &#40;Transact-SQL&#41;](../../t-sql/functions/applock-mode-transact-sql.md)   
 [APPLOCK_TEST &#40;Transact-SQL&#41;](../../t-sql/functions/applock-test-transact-sql.md)   
 [sp_releaseapplock &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-releaseapplock-transact-sql.md)  
  
  
