---
title: Classe di evento Auto Stats | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Auto Stats event class
ms.assetid: cd613fce-01e1-4d8f-86cc-7ffbf0759f9e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 354c2e39716dc0cfa215e4392945bf9aa5899da0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63012366"
---
# <a name="auto-stats-event-class"></a>Auto Stats - classe di evento
  La classe di evento **Auto Stats** indica che si è verificato un evento di aggiornamento automatico delle statistiche di indice e di colonna.  
  
## <a name="auto-stats-event-class-data-columns"></a>Colonne di dati della classe di evento Auto Stats  
  
|Nome colonna di dati|Tipo di dati|Descrizione|ID colonna|Filtrabile|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**ApplicationName**|**nvarchar**|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Yes|  
|**ClientProcessID**|**int**|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se tramite il client viene indicato l'ID del processo client.|9|Yes|  
|**DatabaseID**|**int**|ID del database specificato nell'istruzione USE *database* oppure ID del database predefinito, se per una determinata istanza non viene eseguita un'istruzione USE *database* . [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Yes|  
|**DatabaseName**|**nvarchar**|Nome del database nel quale viene eseguita l'istruzione dell'utente.|35|Yes|  
|**Durata**|**bigint**|Durata dell'evento in microsecondi.|13|Yes|  
|**EndTime**|**datetime**|Ora di fine dell'evento.|15|Yes|  
|**Errore**|**int**|Numero di errore di un evento specifico. Corrisponde spesso al numero di errore archiviato nella vista del catalogo **sys.messages** .|31|Yes|  
|**EventClass**|**int**|Tipo di evento = 58.|27|no|  
|**EventSequence**|**int**|Sequenza di un determinato evento all'interno della richiesta.|51|No|  
|**EventSubClass**|**int**|Tipo di sottoclasse di evento:<br /><br /> 1: Statistiche create/aggiornate in modo sincrono; **TextData** colonna indica le statistiche e indica se sono stati creati o aggiornati.<br /><br /> 2: Aggiornamento statistiche asincrono; processo in coda.<br /><br /> 3: Aggiornamento statistiche asincrono; processo di avvio.<br /><br /> 4: Aggiornamento statistiche asincrono; processo completato.|21|Yes|  
|**GroupID**|**int**|ID del gruppo del carico di lavoro in cui viene generato l'evento di Traccia SQL.|66|Yes|  
|**HostName**|**nvarchar**|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client. Per determinare il nome host, usare la funzione HOST_NAME.|8|Yes|  
|**IndexID**|**int**|ID della voce di statistiche/indice nell'oggetto interessato dall'evento. Per determinare l'ID dell'indice per un oggetto, utilizzare la colonna **index_id** della vista del catalogo **sys.indexes** .|24|Yes|  
|**IntegerData**|**int**|Numero delle raccolte di statistiche correttamente aggiornate.|25|Yes|  
|**IntegerData2**|**int**|Numero di sequenza del processo.|55|Yes|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Yes|  
|**LoginName**|**nvarchar**|Nome dell'account di accesso dell'utente (account di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di Windows nel formato DOMINIO\nomeutente).|11|Yes|  
|**LoginSid**|**image**|ID di sicurezza (SID) dell'utente connesso. Queste informazioni sono disponibili nella vista del catalogo **sys.server_principals** . Il SID è univoco per ogni account di accesso nel server.|41|Yes|  
|**NTDomainName**|**nvarchar**|Dominio Windows di appartenenza dell'utente.|7|Yes|  
|**NTUserName**|**nvarchar**|Nome utente di Windows.|6|Yes|  
|**ObjectID**|**int**|ID dell'oggetto assegnato dal sistema.|22|Yes|  
|**RequestID**|**int**|ID della richiesta contenente l'istruzione.|49|Yes|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|**SessionLoginName**|**nvarchar**|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, **SessionLoginName** indica Login1 e **LoginName** indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Yes|  
|**SPID**|**int**|ID della sessione in cui si è verificato l'evento.|12|Yes|  
|**StartTime**|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Yes|  
|**Esito positivo**|**int**|0 = errore.<br /><br /> 1 = esito positivo.<br /><br /> 2 = ignorato a causa di limitazione del server (MSDE).|23|Yes|  
|**TextData**|**ntext**|Il contenuto della colonna dipende dal fatto che le statistiche vengano aggiornate in modo sincrono (**EventSubClass** 1) o asincrono (**EventSubClass** 2, 3 o 4):<br /><br /> 1: Elenca le statistiche aggiornate/create<br /><br /> 2, 3 o 4: VALORE NULL. **IndexID** colonna viene popolata con l'ID di indice/statistiche per le statistiche aggiornate.|1|Yes|  
|**TransactionID**|**bigint**|ID della transazione assegnato dal sistema.|4|Yes|  
|**Tipo**|**int**|Tipo di processo.|57|Yes|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
