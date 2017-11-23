---
title: sysmail_allitems (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysmail_allitems_TSQL
- sysmail_allitems
dev_langs: TSQL
helpviewer_keywords: sysmail_allitems database mail view
ms.assetid: 21fb8432-7677-4435-902f-64a58bba4cbb
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0abb8eb792b85eed60df52f70a2c13c2e3f920d8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="sysmailallitems-transact-sql"></a>sysmail_allitems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contiene una riga per ogni messaggio elaborato da Posta elettronica database. Utilizzare questa vista quando si desidera controllare lo stato di tutti i messaggi.  
  
 Per visualizzare solo i messaggi con lo stato non riuscito, utilizzare [sysmail_faileditems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-faileditems-transact-sql.md). Per visualizzare solo i messaggi non inviati, utilizzare [sysmail_unsentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-unsentitems-transact-sql.md). Per visualizzare solo i messaggi che sono stati inviati, utilizzare [sysmail_sentitems &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sysmail-sentitems-transact-sql.md).  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**mailitem_id**|**int**|Identificatore dell'elemento di posta nella coda della posta.|  
|**profile_id**|**int**|Identificatore del profilo utilizzato per l'invio del messaggio.|  
|**destinatari**|**varchar(max)**|Indirizzi di posta elettronica dei destinatari del messaggio.|  
|**copy_recipients**|**varchar(max)**|Indirizzi di posta elettronica degli utenti che ricevono una copia del messaggio.|  
|**blind_copy_recipients**|**varchar(max)**|Indirizzi di posta elettronica degli utenti che ricevono una copia del messaggio, ma i cui nomi non sono indicati nell'intestazione del messaggio.|  
|**Oggetto**|**nvarchar(510)**|Oggetto del messaggio.|  
|**corpo**|**varchar(max)**|Corpo del messaggio.|  
|**body_format**|**varchar (20)**|Formato del corpo del messaggio. I possibili valori sono TEXT e HTML.|  
|**importanza**|**varchar(6)**|Il **importanza** parametro del messaggio.|  
|**sensibilità**|**varchar(12)**|Il **sensibilità** parametro del messaggio.|  
|**file_attachments**|**varchar(max)**|Elenco delimitato da punti e virgola dei nomi dei file allegati al messaggio di posta elettronica.|  
|**attachment_encoding**|**varchar (20)**|Tipo di allegato del messaggio di posta elettronica.|  
|**query**|**varchar(max)**|Query eseguita dal programma di posta elettronica.|  
|**execute_query_database**|**sysname**|Contesto di database all'interno del quale il programma di posta elettronica ha eseguito la query.|  
|**attach_query_result_as_file**|**bit**|Quando il valore è 0, i risultati della query sono inclusi nel corpo del messaggio di posta elettronica, dopo il contenuto del corpo. Quando il valore è 1, i risultati sono restituiti come file allegato.|  
|**query_result_header**|**bit**|Quando il valore è 1, i risultati della query includono le intestazioni di colonna. Quando il valore è 0, i risultati della query non includono le intestazioni di colonna.|  
|**query_result_width**|**int**|Il **query_result_width** parametro del messaggio.|  
|**query_result_separator**|**Char (1)**|Carattere utilizzato per separare le colonne nell'output della query.|  
|**exclude_query_output**|**bit**|Il **exclude_query_output** parametro del messaggio. Per ulteriori informazioni, vedere [sp_send_dbmail &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md).|  
|**append_query_error**|**bit**|Il **append_query_error** parametro del messaggio. 0 indica che Posta elettronica database non deve inviare il messaggio di posta elettronica se la query contiene un errore.|  
|**send_request_date**|**datetime**|Data e ora di inserimento del messaggio nella coda della posta.|  
|**send_request_user**|**sysname**|Utente che ha inviato il messaggio. Corrisponde al contesto utente della procedura di Posta elettronica database e non al campo Da del messaggio.|  
|**sent_account_id**|**int**|Identificatore dell'account di Posta elettronica database utilizzato per l'invio del messaggio.|  
|**sent_status**|**varchar (8)**|Stato del messaggio. I valori possibili sono:<br /><br /> **inviato** -è stata inviata la posta elettronica.<br /><br /> **non inviato** -posta elettronica Database sta ancora tentando di inviare il messaggio.<br /><br /> **nuovo tentativo** -Impossibile inviare il messaggio di posta elettronica Database ma sta tentando di inviare di nuovo.<br /><br /> **non è stato possibile** -Impossibile inviare il messaggio di posta elettronica Database.|  
|**sent_date**|**datetime**|Data e ora di invio del messaggio.|  
|**last_mod_date**|**datetime**|Data e ora dell'ultima modifica della riga.|  
|**last_mod_user**|**sysname**|Autore dell'ultima modifica della riga.|  
  
## <a name="remarks"></a>Osservazioni  
 Utilizzare il **sysmail_allitems** visualizzazione per visualizzare lo stato di tutti i messaggi elaborati da posta elettronica Database. Quando si risolvono i problemi relativi a Posta elettronica database, questa vista può consentire di identificare la natura del problema in quanto indica gli attributi dei messaggi che sono stati inviati e gli attributi dei messaggi che non sono stati inviati.  
  
 Le tabelle di sistema esposte da questa vista contengono tutti i messaggi e può causare il **msdb** crescita del database. Eliminare periodicamente i messaggi meno recenti da questa vista al fine di limitare le dimensioni delle tabelle. Per ulteriori informazioni, vedere [creare un processo di SQL Server Agent per archiviare i messaggi di posta elettronica Database e i registri eventi](../../relational-databases/database-mail/create-a-sql-server-agent-job-to-archive-database-mail-messages-and-event-logs.md).  
  
## <a name="permissions"></a>Permissions  
 Concesso a **sysadmin** ruolo predefinito del server e **DatabaseMailUserRole** ruolo del database. Quando viene utilizzata da un membro del **sysadmin** ruolo predefinito del server, questa vista mostra tutti i messaggi. Tutti gli altri utenti vedono semplicemente i messaggi che hanno cercato di inviare personalmente.  
  
  