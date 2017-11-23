---
title: Utilizzo delle notifiche delle Query | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|features
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], query notifications
- rowsets [SQL Server], notifications
- SQL Server Native Client, query notifications
- notifications [SQL Server Native Client]
- query notifications [SQL Server], SQL Server Native Client
- canceling rowset changes
- IRowsetNotify interface
- SQLNCLI, query notifications
- SQL Server Native Client OLE DB provider, query notifications
- consumer notification for rowset changes [SQL Server Native Client]
ms.assetid: 2f906fff-5ed9-4527-9fd3-9c0d27c3dff7
caps.latest.revision: "40"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 14cab75f3f5468259504b103bfa0a3e43e23f8ce
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="working-with-query-notifications"></a>Utilizzo delle notifiche delle query
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Le notifiche delle query sono state introdotte in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Basate sull'infrastruttura di Service Broker introdotta in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], tali notifiche consentono di comunicare alle applicazioni che i dati sono stati modificati. Questa caratteristica è particolarmente utile per le applicazioni che forniscono una cache di informazioni provenienti da un database, ad esempio un'applicazione Web, e devono essere notificate quando i dati di origine vengono modificati.  
  
 Le notifiche delle query consentono di richiedere una notifica entro un determinato periodo di timeout quando i dati sottostanti di una query cambiano. La richiesta di notifica specifica le opzioni di notifica che includono il nome del servizio, il testo del messaggio e il valore di timeout per il server. Le notifiche vengono recapitate tramite una coda di Service Broker di cui le applicazioni possono eseguire il polling delle notifiche disponibili.  
  
 La sintassi delle opzioni delle notifiche delle query è la seguente:  
  
 `service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`  
  
 Esempio:  
  
 `service=mySSBService;local database=mydb`  
  
 Le sottoscrizioni di notifica sopravvivono al processo che le avvia, in quanto un'applicazione può creare una sottoscrizione di notifica e quindi terminare. La sottoscrizione rimane valida e la notifica verrà creata se i dati vengono modificati nel periodo di timeout specificato al momento della creazione della sottoscrizione. Una notifica viene identificata dalla query eseguita, dalle opzioni di notifica e dal testo del messaggio e può essere annullata impostandone il valore di timeout su zero.  
  
 Le notifiche vengono inviate una sola volta. Per la notifica continua delle modifiche dei dati, è necessario creare una nuova sottoscrizione rieseguendo la query al termine dell'elaborazione di ogni notifica.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Le applicazioni Client native in genere ricevono notifiche mediante il [!INCLUDE[tsql](../../../includes/tsql-md.md)] [ricezione](../../../t-sql/statements/receive-transact-sql.md) comando per le notifiche di lettura dalla coda associata al servizio specificato nelle opzioni di notifica.  
  
> [!NOTE]  
>  I nomi di tabella devono essere qualificati nelle query per le quali è necessaria la notifica, ad esempio `dbo.myTable`, e devono essere qualificati con nomi in due parti. La sottoscrizione non è valida se vengono utilizzati nomi in tre o quattro parti.  
  
 L'infrastruttura della notifica si basa su una caratteristica di accodamento introdotta in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. In genere, le notifiche generate sul server vengono inviate tramite queste code in modo da essere elaborate in un secondo momento.  
  
 Per utilizzare le notifiche delle query è necessario che sul server siano disponibili una coda e un servizio. Tali elementi possono essere creati utilizzando [!INCLUDE[tsql](../../../includes/tsql-md.md)] come illustrato di seguito:  
  
```  
CREATE QUEUE myQueue  
CREATE SERVICE myService ON QUEUE myQueue   
  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])  
```  
  
> [!NOTE]  
>  Come mostrato sopra, il servizio deve utilizzare il contratto predefinito `http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification`.  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Provider OLE DB di SQL Server Native Client  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta la notifica di tipo consumer per la modifica dei set di righe. Il consumer riceve una notifica a ogni fase di modifica dei set di righe e a ogni tentativo di modifica.  
  
> [!NOTE]  
>  Il passaggio di una query di notifica al server con **ICommand:: Execute** è l'unico modo valido per sottoscrivere le notifiche delle query con il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client.  
  
### <a name="the-dbpropsetsqlserverrowset-property-set"></a>Set di proprietà DBPROPSET_SQLSERVERROWSET  
 Per supportare le notifiche delle query tramite OLE DB, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client consente di aggiungere le seguenti nuove proprietà di proprietà dbpropset_sqlserverrowset.  
  
|Nome|Tipo|Description|  
|----------|----------|-----------------|  
|SSPROP_QP_NOTIFICATION_TIMEOUT|VT_UI4|Numero di secondi durante i quali la notifica di query deve rimanere attiva.<br /><br /> Il valore predefinito è 432000 secondi (5 giorni). Il valore minimo è 1 secondo e il valore massimo è 2^31-1 secondi.|  
|SSPROP_QP_NOTIFICATION_MSGTEXT|VT_BSTR|Testo del messaggio di notifica. Tale testo è definito dall'utente e non presenta un formato predefinito.<br /><br /> Per impostazione predefinita, la stringa è vuota. È possibile specificare un messaggio utilizzando da 1 a 2000 caratteri.|  
|SSPROP_QP_NOTIFICATION_OPTIONS|VT_BSTR|Opzioni di notifica delle query. Tali opzioni vengono specificate in una stringa con *nome*=*valore* sintassi. L'utente è responsabile della creazione del servizio e della lettura delle notifiche all'esterno della coda.<br /><br /> Il valore predefinito è una stringa vuota.|  
  
 Il commit della sottoscrizione di notifica viene sempre eseguito, indipendentemente dall'esecuzione dell'istruzione in una transazione utente o in modalità di commit automatico o a prescindere se la transazione in cui è stata eseguita l'istruzione sia stata sottoposta a commit o a rollback. La notifica server viene generata in seguito a una delle condizioni di notifica non valide seguenti: modifica dello schema o dei dati sottostanti o raggiungimento del periodo di timeout, a seconda dell'evento che si verifica per primo. Le registrazioni della notifica vengono eliminate subito dopo essere state generate. In seguito alla ricezione delle notifiche, è pertanto necessario che venga effettuata nuovamente la sottoscrizione se si desidera ottenere ulteriori aggiornamenti.  
  
 Un'altra connessione o un altro thread può verificare la presenza di notifiche nella coda di destinazione. Esempio:  
  
```  
WAITFOR (RECEIVE * FROM MyQueue);   // Where MyQueue is the queue name.   
```  
  
 Si noti che selezionare * non elimina la voce dalla coda, diversamente da RECEIVE \* dallo utilizza. Di conseguenza un thread del server viene bloccato se la coda è vuota. Se al momento della chiamata sono presenti voci nella coda, vengono restituite immediatamente. In caso contrario, la chiamata resta in attesa finché non viene creata una voce della coda.  
  
```  
RECEIVE * FROM MyQueue  
```  
  
 Questa istruzione restituisce immediatamente un set di risultati vuoto se la coda è vuota. In caso contrario, restituisce tutte le notifiche della coda.  
  
 Se le proprietà SSPROP_QP_NOTIFICATION_MSGTEXT e SSPROP_QP_NOTIFICATION_OPTIONS sono diverse da Null e non vuote, l'intestazione TDS delle notifiche delle query contenente le tre proprietà definite sopra viene inviata al server a ogni esecuzione del comando. Se una di esse è Null o vuota, l'intestazione non viene inviata e viene generato DB_E_ERRORSOCCURRED, o DB_S_ERRORSOCCURRED se le proprietà sono entrambe contrassegnate come facoltative, e il valore dello stato viene impostato su DBPROPSTATUS_BADVALUE. La convalida viene effettuata in fase di esecuzione/preparazione. Analogamente, DB_S_ERRORSOCCURED viene generato quando le proprietà di notifica delle query sono impostate per le connessioni a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le versioni precedenti [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Il valore dello stato in questo caso è DBPROPSTATUS_NOTSUPPORTED.  
  
 L'avvio di una sottoscrizione non garantisce il corretto recapito dei messaggi successivi. Inoltre, non viene effettuato alcun controllo della validità del nome di servizio specificato.  
  
> [!NOTE]  
>  La preparazione delle istruzioni non causerà mai l'avvio della sottoscrizione. Tale operazione verrà effettuata solo mediante l'esecuzione delle istruzioni. L'uso dei servizi OLE DB di base non influisce sulle notifiche delle query.  
  
 Per ulteriori informazioni sul set di proprietà DBPROPSET_SQLSERVERROWSET, vedere [proprietà set di righe e i comportamenti](../../../relational-databases/native-client-ole-db-rowsets/rowset-properties-and-behaviors.md).  
  
## <a name="sql-server-native-client-odbc-driver"></a>Driver ODBC di SQL Server Native Client  
 Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC Native Client supporta le notifiche delle query mediante l'aggiunta di tre nuovi attributi per il [SQLGetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md) e [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) funzioni:  
  
-   SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
  
-   SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS  
  
-   SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT  
  
 Se le proprietà SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT e SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS sono diverse da Null, l'intestazione TDS delle notifiche delle query contenente i tre attributi definiti sopra verrà inviata al server ogni volta che il comando viene eseguito. Se una di esse è Null, l'intestazione non viene inviata e viene restituito SQL_SUCCESS_WITH_INFO. La convalida viene eseguita su [funzione SQLPrepare](http://go.microsoft.com/fwlink/?LinkId=59360), **SqlExecDirect**, e **SqlExecute**, tutti i cui esecuzione non riesce se gli attributi non sono validi. Analogamente, quando questi attributi di notifica delle query vengono impostati per le versioni [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] precedenti a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], l'esecuzione non riesce e viene restituito SQL_SUCCESS_WITH_INFO.  
  
> [!NOTE]  
>  La preparazione delle istruzioni non causerà mai l'avvio della sottoscrizione. Tale operazione verrà effettuata solo mediante l'esecuzione delle istruzioni.  
  
## <a name="special-cases-and-restrictions"></a>Casi e restrizioni speciali  
 I tipi di dati seguenti non sono supportati per le notifiche:  
  
-   **text**  
  
-   **ntext**  
  
-   **image**  
  
 Se viene effettuata una richiesta di notifica per una query che restituisce uno di questi tipi, la notifica viene generata immediatamente, indicando che la sottoscrizione di notifica non è riuscita.  
  
 Se una richiesta di sottoscrizione viene eseguita per un batch o una stored procedure, verrà eseguita una richiesta di sottoscrizione separata per ogni istruzione eseguita all'interno del batch o della stored procedure. Le istruzioni EXECUTE non registreranno una notifica, ma invieranno la richiesta di notifica al comando eseguito. Nel caso di un batch, il contesto verrà applicato alle istruzioni eseguite e verranno applicate le stesse regole illustrate in precedenza.  
  
 L'inoltro di una query per una notifica inviata dallo stesso utente nello stesso contesto di database e con modello, valori di parametro, ID di notifica e posizione di recapito identici a quelli di una sottoscrizione attiva esistente comporterà il rinnovo della sottoscrizione esistente e la reimpostazione del nuovo timeout specificato. Se, pertanto, viene richiesta una notifica per query identiche, ne verrà inviata una sola. Questa restrizione è applicabile a una query duplicata in un batch o a una query in una stored procedure chiamata più volte.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità di SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  