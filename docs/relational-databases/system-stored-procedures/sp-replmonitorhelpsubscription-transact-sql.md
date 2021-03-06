---
title: sp_replmonitorhelpsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpsubscription_TSQL
- sp_replmonitorhelpsubscription
helpviewer_keywords:
- sp_replmonitorhelpsubscription
ms.assetid: a681b2db-c82d-4624-a10c-396afb0ac42f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 92cd44dcc30a0843409c908cb3cc3a76276519aa
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528203"
---
# <a name="spreplmonitorhelpsubscription-transact-sql"></a>sp_replmonitorhelpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce informazioni sullo stato corrente delle sottoscrizioni appartenenti a una o più pubblicazioni nel server di pubblicazione e restituisce una riga per ogni sottoscrizione restituita. Questa stored procedure, utilizzata per il monitoraggio della replica, viene eseguita nel database di distribuzione del server di distribuzione.  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_replmonitorhelpsubscription [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @mode = ] mode ]  
    [ , [ @topnum = ] topnum ]   
    [ , [ @exclude_anonymous = ] exclude_anonymous ]   
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>Argomenti  
`[ @publisher = ] 'publisher'` È il nome del server di pubblicazione viene monitorato lo stato dei quali. *server di pubblicazione* viene **sysname**, con un valore predefinito NULL. Se **null**, vengono restituite informazioni per tutti i server di pubblicazione che utilizzano il server di distribuzione.  
  
`[ @publisher_db = ] 'publisher_db'` È il nome del database pubblicato. *publisher_db* viene **sysname**, con un valore predefinito NULL. Se NULL, vengono restituite informazioni su tutti i database pubblicati nel server di pubblicazione.  
  
`[ @publication = ] 'publication'` Il nome della pubblicazione da monitorare. *pubblicazione* viene **sysname**, con un valore predefinito NULL.  
  
`[ @publication_type = ] publication_type` Se il tipo di pubblicazione. *publication_type* viene **int**, i possibili valori sono i seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**0**|Pubblicazione transazionale.|  
|**1**|Pubblicazione snapshot.|  
|**2**|Pubblicazione di tipo merge.|  
|NULL (predefinito)|La replica tenta di determinare il tipo di pubblicazione.|  
  
`[ @mode = ] mode` Informazioni di monitoraggio è la modalità di filtraggio da utilizzare per la restituzione di sottoscrizione. *modalità* viene **int**, i possibili valori sono i seguenti.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|**0** (predefinito)|Restituisce tutte le sottoscrizioni.|  
|**1**|Restituisce solo le sottoscrizioni con errori.|  
|**2**|Restituisce solo le sottoscrizioni che hanno generato avvisi correlati alla misurazione del valore soglia.|  
|**3**|Restituisce solo le sottoscrizioni con errori o che hanno generato avvisi correlati alla misurazione del valore soglia.|  
|**4**|Restituisce i primi 25 sottoscrizioni peggiori.|  
|**5**|Restituisce le 50 sottoscrizioni con le prestazioni peggiori.|  
|**6**|Restituisce solo le sottoscrizioni in fase di sincronizzazione.|  
|**7**|Restituisce solo le sottoscrizioni che non sono in fase di sincronizzazione.|  
  
`[ @topnum = ] topnum` Limita il set di risultati al solo il numero specificato di sottoscrizioni all'inizio dei dati restituiti. *topnum* viene **int**, non prevede alcun valore predefinito.  
  
`[ @exclude_anonymous = ] exclude_anonymous` Indica se le sottoscrizioni pull anonime vengono escluse dal set di risultati. *exclude_anonymous* viene **bit**, il valore predefinito è **0**; il valore **1** indica che le sottoscrizioni anonime vengono escluse e il valore **0**  indica che vengono incluse.  
  
`[ @refreshpolicy = ] refreshpolicy` Solo uso interno.  
  
## <a name="result-sets"></a>Set di risultati  
  
|Nome colonna|Tipo di dati|Descrizione|  
|-----------------|---------------|-----------------|  
|**status**|**int**|Analizza lo stato di tutti gli agenti di replica associati alla pubblicazione e restituisce lo stato più elevato trovato nell'ordine seguente:<br /><br /> **6** = non è riuscita<br /><br /> **5** = nuovo tentativo in corso<br /><br /> **2** = arrestato<br /><br /> **4** = inattivo<br /><br /> **3** = in corso<br /><br /> **1** = avviato|  
|**warning**|**int**|Avviso correlato alla soglia massima generato da una sottoscrizione appartenente alla pubblicazione. Può essere il risultato OR logico di uno o più dei valori seguenti.<br /><br /> **1** = expiration - una sottoscrizione di una pubblicazione transazionale non sia stata sincronizzata entro la soglia di periodo di conservazione.<br /><br /> **2** = latency - il tempo necessario per replicare i dati da un server di pubblicazione transazionale al sottoscrittore supera la soglia, espresso in secondi.<br /><br /> **4** = mergeexpiration - una sottoscrizione a una pubblicazione di tipo merge non sia stata sincronizzata entro la soglia di periodo di conservazione.<br /><br /> **8** = mergefastrunduration - il tempo impiegato per completare la sincronizzazione di una sottoscrizione di tipo merge supera la soglia, espresso in secondi, tramite una connessione di rete veloce.<br /><br /> **16** = mergeslowrunduration - il tempo impiegato per completare la sincronizzazione di una sottoscrizione di tipo merge supera la soglia, espresso in secondi, tramite una connessione di rete lenta o remota.<br /><br /> **32** = mergefastrunspeed: la velocità di recapito delle righe durante la sincronizzazione di una sottoscrizione di tipo merge è minore della soglia, in righe al secondo, su una connessione di rete veloce.<br /><br /> **64** = mergeslowrunspeed: la velocità di recapito delle righe durante la sincronizzazione di una sottoscrizione di tipo merge è minore della soglia, in righe al secondo, su una connessione di rete lenta o remota.|  
|**subscriber**|**sysname**|Nome del Sottoscrittore.|  
|**subscriber_db**|**sysname**|Nome del database utilizzato per la sottoscrizione.|  
|**publisher_db**|**sysname**|Nome del database di pubblicazione.|  
|**publication**|**sysname**|Nome di una pubblicazione.|  
|**publication_type**|**int**|Tipo di pubblicazione. I possibili valori sono i seguenti:<br /><br /> **0** = pubblicazione transazionale<br /><br /> **1** = pubblicazione snapshot<br /><br /> **2** = pubblicazione di tipo merge|  
|**subtype**|**int**|Tipo di sottoscrizione. I possibili valori sono i seguenti:<br /><br /> **0** = Push<br /><br /> **1** = Pull<br /><br /> **2** = anonima|  
|**latency**|**int**|Latenza più alta, espressa in secondi, per le modifiche dei dati propagate dall'agente di lettura log o dagli agenti di distribuzione per una pubblicazione transazionale.|  
|**latencythreshold**|**int**|Latenza massima per una pubblicazione transazionale, superata la quale viene generato un avviso.|  
|**agentnotrunning**|**int**|Indica da quante ore l'agente non viene eseguito.|  
|**agentnotrunningthreshold**|**int**|Indica dopo quante ore di mancata esecuzione dell'agente viene generato un avviso.|  
|**timetoexpiration**|**int**|Indica il numero di ore che mancano alla scadenza della sottoscrizione, se questa non viene sincronizzata.|  
|**expirationthreshold**|**int**|Indica quante ore prima della scadenza della sottoscrizione deve essere generato un avviso.|  
|**last_distsync**|**datetime**|Data e ora dell'ultima esecuzione dell'agente di distribuzione.|  
|**distribution_agentname**|**sysname**|Nome del processo dell'agente di distribuzione per la sottoscrizione a una pubblicazione transazionale.|  
|**mergeagentname**|**sysname**|Nome del processo dell'agente di merge per la sottoscrizione di una pubblicazione di tipo merge.|  
|**mergesubscriptionfriendlyname**|**sysname**|Nome descrittivo della sottoscrizione.|  
|**mergeagentlocation**|**sysname**|Nome del server in cui viene eseguito l'agente di merge.|  
|**mergeconnectiontype**|**int**|Connessione utilizzata per la sincronizzazione di una sottoscrizione di una pubblicazione di tipo merge. I possibili valori sono i seguenti:<br /><br /> **1** = rete locale (LAN)<br /><br /> **2** = connessione remota<br /><br /> **3** = sincronizzazione web.|  
|**mergePerformance**|**int**|Prestazioni dell'ultima sincronizzazione confrontate con tutte le sincronizzazioni per la sottoscrizione, ottenute dividendo la velocità di recapito dell'ultima sincronizzazione per la media di tutte le velocità di recapito precedenti.|  
|**mergerunspeed**|**float**|Velocità di recapito dell'ultima sincronizzazione per la sottoscrizione.|  
|**mergerunduration**|**int**|Tempo necessario per completare l'ultima sincronizzazione della sottoscrizione.|  
|**monitorranking**|**int**|Valore di rango utilizzato per ordinare le sottoscrizioni nel set di risultati. I possibili valori sono i seguenti:<br /><br /> Per una pubblicazione transazionale:<br /><br /> **60** = errore<br /><br /> **56** = avviso: prestazioni critiche<br /><br /> **52** = avviso: scadenza imminente o avvenuta<br /><br /> **50** = avviso: sottoscrizione non inizializzata<br /><br /> **40** = nuovo tentativo non riuscito del comando<br /><br /> **30** = non in esecuzione (esito positivo)<br /><br /> **20** = in esecuzione (avvio, in esecuzione o inattivo)<br /><br /> Per una pubblicazione di tipo merge:<br /><br /> **60** = errore<br /><br /> **56** = avviso: prestazioni critiche<br /><br /> **54** = avviso: merge con esecuzione prolungata<br /><br /> **52** = avviso: scadenza imminente<br /><br /> **50** = avviso: sottoscrizione non inizializzata<br /><br /> **40** = nuovo tentativo non riuscito del comando<br /><br /> **30** = in esecuzione (avvio, in esecuzione o inattivo)<br /><br /> **20** = non in esecuzione (esito positivo)|  
|**distributionagentjobid**|**binary(16)**|ID del processo dell'agente di distribuzione per le sottoscrizioni di una pubblicazione transazionale.|  
|**mergeagentjobid**|**binary(16)**|ID del processo dell'agente di merge per le sottoscrizioni di una pubblicazione di tipo merge.|  
|**distributionagentid**|**int**|ID del processo dell'agente di distribuzione per la sottoscrizione.|  
|**distributionagentprofileid**|**int**|ID del profilo dell'agente utilizzato dall'agente di distribuzione.|  
|**mergeagentid**|**int**|ID del processo dell'agente di merge per la sottoscrizione.|  
|**mergeagentprofileid**|**int**|ID del profilo dell'agente utilizzato dall'agente di merge.|  
  
## <a name="return-code-values"></a>Valori restituiti  
 **0** (esito positivo) o **1** (errore)  
  
## <a name="remarks"></a>Note  
 **sp_replmonitorhelpsubscription** viene utilizzato con tutti i tipi di replica.  
  
 **sp_replmonitorhelpsubscription** Ordina il set di risultati di base alla gravità dello stato della sottoscrizione, che è determinata dal valore del *monitorranking*. Le righe di tutte le sottoscrizioni in errore, ad esempio, vengono ordinate prima delle righe delle sottoscrizioni con avviso.  
  
## <a name="permissions"></a>Permissions  
 Solo i membri del **db_owner** oppure **replmonitor** ruolo predefinito del database nel database di distribuzione possono eseguire **sp_replmonitorhelpsubscription**.  
  
## <a name="see-also"></a>Vedere anche  
 [Monitorare la replica a livello di programmazione](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
