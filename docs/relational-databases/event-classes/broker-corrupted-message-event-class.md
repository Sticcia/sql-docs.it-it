---
title: Classe di evento Broker:Corrupted Message | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Broker:Corrupted Message event class
ms.assetid: 084bf198-2138-438e-bdc7-4ff1e04300f7
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0ef3eaafc0d9eb5953db7d26c594020466c1e488
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745989"
---
# <a name="brokercorrupted-message-event-class"></a>Broker:Corrupted Message - classe di evento
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crea un evento **Broker:Corrupted Message** quando Service Broker riceve un messaggio danneggiato.  
  
## <a name="brokercorrupted-message-event-class-data-columns"></a>Colonne di dati della classe di evento Broker:Corrupted Message  
  
|Colonna di dati|Tipo|Descrizione|Numero colonna|Filtrabile|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|Nome dell'applicazione client in cui è stata creata la connessione a un'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Questa colonna viene popolata con i valori passati dall'applicazione e non con il nome visualizzato del programma.|10|Sì|  
|**BigintData1**|**bigint**|Numero di sequenza del messaggio.|52|no|  
|**BinaryData**|**image**|Corpo del messaggio.|2|Sì|  
|**ClientProcessID**|**int**|ID assegnato dal computer host al processo in cui è in esecuzione l'applicazione client. Questa colonna di dati viene popolata se l'ID del processo client viene fornito dal client.|9|Sì|  
|**DatabaseID**|**int**|ID del database specificato nell'istruzione USE *database* oppure ID del database predefinito, se per una determinata istanza non viene eseguita un'istruzione USE *database* . [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] visualizza il nome del database se la colonna di dati **ServerName** è acquisita nella traccia e il server è disponibile. Determinare il valore per un database utilizzando la funzione DB_ID.|3|Sì|  
|**Errore**|**int**|Numero di ID del messaggio in **sys.messages** relativo al testo dell'evento.|31|no|  
|**EventClass**|**int**|Tipo di classe di evento acquisita. Corrisponde sempre a **161** per **Broker:Corrupted Message**.|27|no|  
|**EventSequence**|**int**|Numero di sequenza dell'evento.|51|no|  
|**FileName**|**nvarchar**|Indirizzo di rete dell'endpoint remoto.|36|no|  
|**GUID**|**uniqueidentifier**|ID della conversazione alla quale appartiene il messaggio. Questo identificatore viene trasmesso come parte del messaggio e viene condiviso da entrambi i lati della conversazione.|54|no|  
|**Host Name**|**nvarchar**|Nome del computer in cui è in esecuzione il client. Questa colonna di dati viene popolata se il nome host viene fornito dal client. Per determinare il nome host, usare la funzione HOST_NAME.|8|Sì|  
|**IntegerData**|**int**|Numero di frammento del messaggio.|25|Sì|  
|**IsSystem**|**int**|Indica se l'evento è stato generato per un processo di sistema o un processo utente. 1 = sistema, 0 = utente.|60|no|  
|**LoginSid**|**image**|ID di sicurezza (SID) dell'utente connesso. Il SID è univoco per ogni account di accesso nel server.|41|Sì|  
|**NTDomainName**|**nvarchar**|Dominio di Windows a cui appartiene l'utente.|7|Sì|  
|**NTUserName**|**nvarchar**|Nome dell'utente proprietario della connessione che ha generato questo evento.|6|Sì|  
|**ObjectName**|**nvarchar**|Nome del servizio dell'altro lato della conversazione e stringa di connessione utilizzata dal database remoto per connettersi al database.|34|no|  
|**RoleName**|**nvarchar**|Ruolo dell'endpoint che riceve il messaggio. I possibili valori sono i seguenti.<br /><br /> **initiator**: L'endpoint che riceve il messaggio è l'iniziatore della conversazione.<br /><br /> **target**:                 L'endpoint che riceve il messaggio è la destinazione della conversazione.|38|no|  
|**ServerName**|**nvarchar**|Nome dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tracciata.|26|no|  
|**Severity**|**int**|Gravità dell'errore che ha determinato l'eliminazione del messaggio in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|29|no|  
|**SPID**|**int**|ID del processo server assegnato da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] al processo associato al client.|12|Sì|  
|**StartTime**|**datetime**|Ora di inizio dell'evento, se disponibile.|14|Sì|  
|**State**|**int**|Indica la posizione che ha generato l'evento all'interno del codice sorgente di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Ogni punto che può generare questo evento è contraddistinto da un codice di stato diverso. Questo codice di stato consente al supporto tecnico Microsoft di individuare la posizione in cui è stato generato l'evento.|30|no|  
|**TextData**|**ntext**|Descrizione del danneggiamento rilevato.|1|Sì|  
|**TransactionID**|**bigint**|ID della transazione assegnato dal sistema.|4|no|  
  
 La colonna **TextData** dell'evento contiene un messaggio che descrive il problema correlato al messaggio.  
  
  
