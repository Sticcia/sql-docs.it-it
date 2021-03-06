---
title: sys.dm_db_mirroring_connections (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_mirroring_connections
- dm_db_mirroring_connections
- sys.dm_db_mirroring_connections_TSQL
- dm_db_mirroring_connections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_mirroring_connections dynamic management view
ms.assetid: e4df91b6-0240-45d0-ae22-cb2c0d52e0b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 624e3d8cd6bd92d07bf655e29060ed8809922cc2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815359"
---
# <a name="database-mirroring---sysdmdbmirroringconnections"></a>Database Mirroring - DM db_mirroring_connections
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per ogni connessione stabilita per il mirroring del database.  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**connection_id**|**uniqueidentifier**|Identificatore della connessione.|  
|**transport_stream_id**|**uniqueidentifier**|Identificatore del [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connessione di interfaccia di rete (SNI) utilizzato dalla connessione per le comunicazioni TCP/IP.|  
|**state**|**smallint**|Stato corrente della connessione. I valori possibili sono:<br /><br /> 1 = NEW<br /><br /> 2 = CONNECTING<br /><br /> 3 = CONNECTED<br /><br /> 4 = LOGGED_IN<br /><br /> 5 = CHIUSO|  
|**state_desc**|**nvarchar(60)**|Stato corrente della connessione. I valori possibili sono:<br /><br /> NEW<br /><br /> CONNECTING<br /><br /> CONNECTED<br /><br /> LOGGED_IN<br /><br /> CLOSED|  
|**connect_time**|**datetime**|Data e ora di apertura della connessione.|  
|**login_time**|**datetime**|Data e ora in cui è stato eseguito l'accesso per la connessione.|  
|**authentication_method**|**nvarchar(128)**|Nome del metodo di autenticazione di Windows, ad esempio NTLM o KERBEROS. Questo valore proviene da Windows.|  
|**principal_name**|**nvarchar(128)**|Nome dell'account di accesso convalidato per le autorizzazioni di connessione. Per l'autenticazione di Windows, corrisponde al nome dell'utente remoto. Per l'autenticazione basata su certificati, corrisponde al proprietario del certificato.|  
|**remote_user_name**|**nvarchar(128)**|Nome dell'utente peer dell'altro database utilizzato dall'autenticazione di Windows.|  
|**last_activity_time**|**datetime**|Data e ora dell'ultimo utilizzo della connessione per l'invio o la ricezione di informazioni.|  
|**is_accept**|**bit**|Specifica se la connessione ha avuto origine sul lato remoto.<br /><br /> 1 = La connessione è una richiesta accettata dall'istanza remota.<br /><br /> 0 = La connessione è stata avviata dall'istanza locale.|  
|**login_state**|**smallint**|Stato del processo di accesso per la connessione. I valori possibili sono:<br /><br /> 0 = INITIAL<br /><br /> 1 = WAIT LOGIN NEGOTIATE<br /><br /> 2 = ONE ISC<br /><br /> 3 = ONE ASC<br /><br /> 4 = TWO ISC<br /><br /> 5 = TWO ASC<br /><br /> 6 = WAIT ISC Confirm<br /><br /> 7 = WAIT ASC Confirm<br /><br /> 8 = WAIT REJECT<br /><br /> 9 = WAIT PRE-MASTER SECRET<br /><br /> 10 = WAIT VALIDATION<br /><br /> 11 = WAIT ARBITRATION<br /><br /> 12 = ONLINE<br /><br /> 13 = ERROR|  
|**login_state_desc**|**nvarchar(60)**|Descrizione dello stato corrente dell'accesso dal computer remoto. I valori possibili sono:<br /><br /> È in corso l'inizializzazione dell'handshake della connessione.<br /><br /> L'handshake della connessione è in attesa del messaggio relativo alla negoziazione dell'accesso.<br /><br /> L'handshake della connessione ha inizializzato e inviato il contesto di sicurezza per l'autenticazione.<br /><br /> L'handshake della connessione ha ricevuto e accettato il contesto di sicurezza per l'autenticazione.<br /><br /> L'handshake della connessione ha inizializzato e inviato il contesto di sicurezza per l'autenticazione. È disponibile un meccanismo facoltativo per l'autenticazione dei peer.<br /><br /> L'handshake della connessione ha ricevuto e inviato il contesto di sicurezza accettato per l'autenticazione. È disponibile un meccanismo facoltativo per l'autenticazione dei peer.<br /><br /> L'handshake della connessione è in attesa del messaggio di conferma dell'inizializzazione del contesto di sicurezza.<br /><br /> L'handshake della connessione è in attesa del messaggio di conferma dell'accettazione del contesto di sicurezza.<br /><br /> L'handshake della connessione è in attesa del messaggio di rifiuto SSPI per l'autenticazione non riuscita.<br /><br /> L'handshake della connessione è in attesa del messaggio relativo al segreto pre-master.<br /><br /> L'handshake della connessione è in attesa del messaggio di convalida.<br /><br /> L'handshake della connessione è in attesa del messaggio relativo all'arbitraggio.<br /><br /> L'handshake della connessione è completo ed è online (pronto) per lo scambio di messaggi.<br /><br /> Errore di connessione.|  
|**peer_certificate_id**|**int**|ID di oggetto locale del certificato utilizzato dall'istanza remota per l'autenticazione. Il proprietario del certificato deve disporre delle autorizzazioni CONNECT per l'endpoint del mirroring del database.|  
|**encryption_algorithm**|**smallint**|Algoritmo di crittografia utilizzato per la connessione. Ammette valori Null. I valori possibili sono:<br /><br /> **Valore:** 0<br /><br /> **Descrizione:** None<br /><br /> **Opzione DDL:** disabilitato<br /><br /> **Valore:** 1<br /><br /> **Descrizione:** RC4<br /><br /> **Opzione DDL:** {richiesto &#124; obbligatorio algoritmo RC4}<br /><br /> **Valore:** 2<br /><br /> **Descrizione:** AES<br /><br /> **Opzione DDL:** obbligatorio algoritmo AES<br /><br /> **Valore:** 3<br /><br /> **Descrizione:** None, RC4<br /><br /> **Opzione DDL:** {supportati &#124; Supported algoritmo RC4}<br /><br /> **Valore:** 4<br /><br /> **Descrizione:** none, AES<br /><br /> **Opzione DDL:** Supported algoritmo RC4<br /><br /> **Valore:** 5<br /><br /> **Descrizione:** RC4, AES<br /><br /> **Opzione DDL:** obbligatorio algoritmo RC4 AES<br /><br /> **Valore:** 6<br /><br /> **Descrizione:** AES, RC4<br /><br /> **Opzione DDL:** necessari algoritmo AES RC4<br /><br /> **Valore:** 7<br /><br /> **Descrizione:** NONE, RC4, AES<br /><br /> **Opzione DDL:** supportati algoritmo RC4 AES<br /><br /> **Valore:** 8<br /><br /> **Descrizione:** NONE, AES, RC4<br /><br /> **Opzione DDL:** Supported algoritmo AES RC4<br /><br /> **Nota:** l'algoritmo RC4 è supportato solo per compatibilità con le versioni precedenti. È possibile crittografare il nuovo materiale usando RC4 o RC4_128 solo quando il livello di compatibilità del database è 90 o 100. (Non consigliato.) Usare un algoritmo più recente, ad esempio uno degli algoritmi AES. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] e versioni successive il materiale crittografato utilizzando RC4 o RC4_128 può essere decrittografato in qualsiasi livello di compatibilità.|  
|**encryption_algorithm_desc**|**nvarchar(60)**|Rappresentazione testuale dell'algoritmo di crittografia. Ammette valori Null. I valori possibili sono:<br /><br /> **Descrizione:** None<br /><br /> **Opzione DDL:** disabilitato<br /><br /> **Descrizione:** RC4<br /><br /> **Opzione DDL:** {richiesto &#124; obbligatorio algoritmo RC4}<br /><br /> **Descrizione:** AES<br /><br /> **Opzione DDL:** necessari algoritmo AES<br /><br /> **Descrizione:** NONE, RC4<br /><br /> **Opzione DDL:** {supportati &#124; algoritmo RC4 è supportato}<br /><br /> **Descrizione:** NONE, AES<br /><br /> **Opzione DDL:** algoritmo RC4 è supportato<br /><br /> **Descrizione:** RC4, AES<br /><br /> **Opzione DDL:** necessari algoritmo RC4 AES<br /><br /> **Descrizione:** AES, RC4<br /><br /> **Opzione DDL:** necessari algoritmo AES RC4<br /><br /> **Descrizione:** NONE, RC4, AES<br /><br /> **Opzione DDL:** supportati algoritmo RC4 AES<br /><br /> **Descrizione:** NONE, AES, RC4<br /><br /> **Opzione DDL:** algoritmo AES RC4 è supportato|  
|**receives_posted**|**smallint**|Numero di ricezioni di rete asincrone non ancora completate per la connessione.|  
|**is_receive_flow_controlled**|**bit**|Specifica se le ricezioni di rete sono state posticipate a causa del controllo di flusso, poiché la rete è occupata.<br /><br /> 1 = True|  
|**sends_posted**|**smallint**|Numero di invii di rete asincroni non ancora completati per la connessione.|  
|**is_send_flow_controlled**|**bit**|Specifica se gli invii di rete sono stati posticipati a causa del controllo di flusso di rete, poiché la rete è occupata.<br /><br /> 1 = True|  
|**total_bytes_sent**|**bigint**|Numero totale di byte inviati dalla connessione.|  
|**total_bytes_received**|**bigint**|Numero totale di byte ricevuti dalla connessione.|  
|**total_fragments_sent**|**bigint**|Numero totale di frammenti di messaggi per il mirroring del database inviati dalla connessione.|  
|**total_fragments_received**|**bigint**|Numero totale di frammenti di messaggi per il mirroring del database ricevuti dalla connessione.|  
|**total_sends**|**bigint**|Numero totale di richieste di invio in rete generate dalla connessione.|  
|**total_receives**|**bigint**|Numero totale di richieste di ricezione in rete generate dalla connessione.|  
|**peer_arbitration_id**|**uniqueidentifier**|Identificatore interno dell'endpoint. Ammette valori Null.|  
  
## <a name="permissions"></a>Permissions  
 È richiesta l'autorizzazione VIEW SERVER STATE per il server.  
  
## <a name="physical-joins"></a>Join fisici  
 ![join per Sys. join_dm_db_mirroring_connections](../../relational-databases/system-dynamic-management-views/media/join-dm-db-mirroring-connections.gif "join per Sys. join_dm_db_mirroring_connections")  
  
## <a name="relationship-cardinalities"></a>Cardinalità delle relazioni  
  
|Da|Per|Relazione|  
|----------|--------|------------------|  
|**dm_db_mirroring_connections.connection_id**|**dm_exec_connections.connection_id**|Uno-a-uno|  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni e viste a gestione dinamica &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Monitoraggio del mirroring del database &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
  
