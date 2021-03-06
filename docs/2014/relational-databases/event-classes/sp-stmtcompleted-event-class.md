---
title: Classe di evento SP:StmtCompleted | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SP:StmtCompleted event class
ms.assetid: 9e8147a4-aeeb-49a6-80f8-df753d0f34cc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 056f9adb309f4f65ed1553efa80db597e7598e02
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63050957"
---
# <a name="spstmtcompleted-event-class"></a>SP:StmtCompleted - classe di evento
  La classe di evento SP:StmtCompleted indica che è stata completata un'istruzione [!INCLUDE[tsql](../../includes/tsql-md.md)] all'interno di una stored procedure.  
  
## <a name="spstmtcompleted-event-class-data-columns"></a>Colonne di dati della classe di evento SP:StmtCompleted  
  
|Nome colonna di dati|`Data type`|Descrizione|ID colonna|Filtrabile|  
|----------------------|-------------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Yes|  
|ClientProcessID|`int`|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se tramite il client viene indicato l'ID del processo client.|9|Yes|  
|CPU|`int`|Tempo della CPU in millisecondi utilizzato dall'evento.|18|Yes|  
|DatabaseID|`int`|ID del database nel quale viene eseguita la stored procedure. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Yes|  
|DatabaseName|`nvarchar`|Nome del database nel quale viene eseguita la stored procedure.|35|Yes|  
|Duration|`bigint`|Durata dell'evento in microsecondi.|13|Yes|  
|EndTime|`datetime`|Ora di fine dell'evento. Questa colonna non viene popolata per le classi degli eventi di avvio, ad esempio SQL:BatchStarting o SP:Starting.|15|Yes|  
|EventClass|`int`|Tipo di evento = 45.|27|No|  
|EventSequence|`int`|Sequenza di un determinato evento all'interno della richiesta.|51|no|  
|GroupID|`int`|ID del gruppo del carico di lavoro in cui viene generato l'evento di Traccia SQL.|66|Yes|  
|HostName|`nvarchar`|Nome del computer in cui viene eseguito il client. Questa colonna di dati viene popolata se il client fornisce il nome host. Per determinare il nome host, usare la funzione HOST_NAME.|8|Yes|  
|IntegerData|`int`|Valore integer che dipende dalla classe di evento acquisita nella traccia.|25|Yes|  
|IntegerData2|`int`|Offset finale (in byte) dell'istruzione in esecuzione.|55|Yes|  
|IsSystem|`int`|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|Yes|  
|LineNumber|`int`|Numero di riga dell'istruzione in esecuzione.|5|Yes|  
|LoginName|`nvarchar`|Nome dell'account di accesso dell'utente (account di accesso di sicurezza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] o credenziali di accesso di [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows nel formato DOMINIO\nomeutente).|11|Yes|  
|LoginSid|`image`|ID di sicurezza (SID) dell'utente connesso. Queste informazioni sono disponibili nella vista del catalogo sys.server_principals. Il SID è univoco per ogni account di accesso nel server.|41|Yes|  
|NestLevel|`int`|Valore intero che rappresenta i dati restituiti da @@NESTLEVEL.|29|Yes|  
|NTDomainName|`nvarchar`|Dominio Windows di appartenenza dell'utente.|7|Yes|  
|NTUserName|`nvarchar`|Nome utente di Windows.|6|Yes|  
|ObjectID|`int`|ID dell'oggetto assegnato dal sistema.|22|Yes|  
|ObjectName|`nvarchar`|Nome dell'oggetto a cui si fa riferimento.|34|Yes|  
|ObjectType|`int`|Valore che rappresenta il tipo di oggetto coinvolto nell'evento. Questo valore corrisponde alla colonna type nella vista del catalogo sys.objects. Per i valori, vedere [Colonna ObjectType per gli eventi di traccia](objecttype-trace-event-column.md).|28|Yes|  
|Offset|`int`|Offset iniziale dell'istruzione nella stored procedure o nel batch.|61|Yes|  
|Reads|`bigint`|Numero di letture logiche del disco eseguite dal server per conto dell'evento.|16|Yes|  
|RequestID|`int`|ID della richiesta contenente l'istruzione.|49|Yes|  
|RowCounts|`bigint`|Numero di righe interessate da un evento.|48|Yes|  
|ssSqlProfiler|`nvarchar`|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|No|  
|SessionLoginName|`nvarchar`|Nome dell'account di accesso dell'utente che ha avviato la sessione. Se ad esempio si stabilisce la connessione a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] con l'account di accesso Login1 e si esegue un'istruzione con l'account di accesso Login2, SessionLoginName indica Login1 e LoginName indica Login2. In questa colonna sono visualizzati sia gli account di accesso di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che quelli di Windows.|64|Yes|  
|SourceDatabaseID|`int`|ID del database in cui esiste l'oggetto.|62|Yes|  
|SPID|`int`|ID della sessione in cui si è verificato l'evento.|12|Yes|  
|StartTime|`datetime`|Ora di inizio dell'evento, se disponibile.|14|Yes|  
|TextData|`ntext`|Valore di testo che dipende dalla classe di evento acquisita nella traccia.|1|Yes|  
|TransactionID|`bigint`|ID della transazione assegnato dal sistema.|4|Yes|  
|Writes|`bigint`|Numero di scritture fisiche su disco eseguite dal server per conto dell'evento.|17|Yes|  
|XactSequence|`bigint`|Token utilizzato per descrivere la transazione corrente.|50|Yes|  
  
## <a name="see-also"></a>Vedere anche  
 [Eventi estesi](../extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
