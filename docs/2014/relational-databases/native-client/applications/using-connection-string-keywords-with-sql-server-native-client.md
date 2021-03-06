---
title: Utilizzo di Connection String Keywords with SQL Server Native Client | Documenti di Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6135c1d2cbf1291465e1346f71010b8befe6f7b5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046402"
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>Utilizzo delle parole chiave delle stringhe di connessione con SQL Server Native Client
  In alcune API di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vengono utilizzate stringhe di connessione per specificare gli attributi di connessione. Le stringhe di connessione sono elenchi di parole chiave con i relativi valori associati. Ogni parola chiave identifica un particolare attributo di connessione.  
  
 **Si noti.** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta l'ambiguità nelle stringhe di connessione per mantenere la compatibilità con le versioni precedenti. È ad esempio possibile specificare alcune parole chiave più volte e utilizzare parole chiave in conflitto con una risoluzione basata sulla posizione o sulla precedenza. È possibile che nelle versioni successive di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client tale ambiguità non sia più supportata. Quando si modificano le applicazioni, è consigliabile utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per eliminare l'eventuale dipendenza dall'ambiguità delle stringhe di connessione.  
  
 Nelle sezioni seguenti vengono descritte le parole chiave che è possibile specificare con il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e gli oggetti ADO (ActiveX Data Objects) quando si utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client come provider di dati.  
  
## <a name="odbc-driver-connection-string-keywords"></a>Parole chiave delle stringhe di connessione per il driver ODBC  
 Le applicazioni ODBC utilizzano stringhe di connessione come parametri il [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) e [SQLBrowseConnect](../../native-client-odbc-api/sqlbrowseconnect.md) funzioni.  
  
 Le stringhe di connessione utilizzate da ODBC presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra parentesi graffe per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori di attributo. Poiché si suppone che la prima parentesi graffa chiusa indichi la fine del valore, l'uso di tali parentesi nei valori non è consentito.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con una stringa di connessione ODBC.  
  
|Parola chiave|Descrizione|  
|-------------|-----------------|  
|`Addr`|Sinonimo di "Address".|  
|`Address`|Indirizzo di rete del server che esegue un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. `Address` è in genere il nome di rete del server, ma può corrispondere ad altri nomi, ad esempio una pipe, un indirizzo IP o un indirizzo socket e una porta TCP/IP.<br /><br /> Se si specifica un indirizzo IP, assicurarsi che i protocolli TCP/IP o Named Pipes siano abilitati in Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Il valore di `Address` ha la precedenza sul valore passato a `Server` nelle stringhe di connessione ODBC quando si utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Tenere anche presente che se si specifica `Address=;` verrà stabilita una connessione al server specificato nella parola chiave `Server`, mentre se si specifica `Address= ;, Address=.;`, `Address=localhost;` e `Address=(local);` verrà stabilita una connessione al server locale.<br /><br /> La sintassi completa per la parola chiave `Address` è la seguente:<br /><br /> [*protocol*`:`]*indirizzi*[`,`*porta &#124;\pipe\pipename*]<br /><br /> *protocollo* può essere `tcp` (TCP/IP), `lpc` (shared memory) o `np` (named pipe). Per altre informazioni sui protocolli, vedere [Configure Client Protocols](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Se nessuno di essi *protocol* né la `Network` parola chiave viene specificato, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client viene utilizzato l'ordine dei protocolli specificato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* indica la porta a cui connettersi nel server specificato. Per impostazione predefinita, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene utilizzata la porta 1433.|  
|`AnsiNPW`|Se l'opzione è impostata su "yes", nel driver vengono utilizzati i comportamenti definiti da ANSI per la gestione dei confronti NULL, del riempimento dei dati di tipo carattere, degli avvisi e della concatenazione NULL. Se impostata su "no", i comportamenti definiti da ANSI non vengono esposti. Per altre informazioni sui comportamenti ANSI NPW, vedere [effetti delle opzioni ISO](../../native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|`APP`|Nome dell'applicazione che chiama [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) (facoltativo). Se specificato, questo valore viene archiviato nel **program_name** colonna **program_name** e viene restituito da [sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) e il [APP_NAME](/sql/t-sql/functions/app-name-transact-sql)le funzioni.|  
|`ApplicationIntent`|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono `ReadOnly` e `ReadWrite`. Ad esempio: ApplicationIntent=ReadOnly<br /><br /> Il valore predefinito è `ReadWrite`. Per altre informazioni sulle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per il supporto del Client nativo [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client il supporto per la disponibilità elevata, ripristino di emergenza](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`AttachDBFileName`|Nome del file primario di un database collegabile. Includere il percorso completo e utilizzare la sequenza di escape dei caratteri \ se si utilizza una variabile di tipo stringa di caratteri C:<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> Questo database viene collegato e diventa il database predefinito per la connessione. Usare `AttachDBFileName` è anche necessario specificare il nome del database in entrambi i [SQLDriverConnect](../../native-client-odbc-api/sqldriverconnect.md) parametro del DATABASE o l'attributo di connessione SQL_COPT_CURRENT_CATALOG. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|`AutoTranslate`|Se impostata su "yes", le stringhe di caratteri ANSI inviate tra il client e il server vengono convertite in Unicode per ridurre al minimo i problemi di corrispondenza dei caratteri estesi tra le tabelle codici sul client e sul server.<br /><br /> Dati SQL_C_CHAR del client inviati a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **char**, **varchar**, oppure **testo** colonna, parametro o variabile è convertita da caratteri in Unicode utilizzando il client Tabella codici ANSI (ACP), quindi vengono convertiti da Unicode a caratteri utilizzando l'ACP del server.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **Char**, **varchar**, o **testo** dati inviati a una variabile SQL_C_CHAR del client sono convertiti da caratteri in Unicode utilizzando l'ACP del server, quindi vengono convertiti da Unicode a caratteri utilizzando il client ACP.<br /><br /> Queste conversioni vengono eseguite sul client dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e richiedono che sul client sia disponibile la stessa tabella codici ANSI (ACP) utilizzata sul server.<br /><br /> Queste impostazioni non influiscono sulle conversioni eseguite per i trasferimenti seguenti:<br /><br /> -Dati client SQL_C_WCHAR Unicode inviati **char**, **varchar**, o **testo** nel server.<br />-   **Char**, **varchar**, o **testo** data server inviati a una variabile SQL_C_WCHAR Unicode sul client.<br />-I dati client SQL_C_CHAR ANSI inviati in Unicode **nchar**, **nvarchar**, o **ntext** nel server.<br />-Unicode **nchar**, **nvarchar**, o **ntext** data server inviati a una variabile SQL_C_CHAR ANSI sul client.<br /><br /> Se impostata su "no", la conversione dei caratteri non viene eseguita.<br /><br /> Il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver ODBC di Native Client non converte i dati SQL_C_CHAR carattere ANSI del client inviati a **char**, **varchar**, oppure **testo** variabili, parametri, o di colonne nel server. Non viene eseguita alcuna conversione **char**, **varchar**, o **testo** i dati inviati dal server alle variabili SQL_C_CHAR sul client.<br /><br /> Se il client e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilizzano ACP differenti, i caratteri estesi potrebbero essere interpretati in modo errato.|  
|`Database`|Nome del database [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] predefinito per la connessione. Se non si specifica `Database`, viene utilizzato il database definito per l'accesso. Il database predefinito dell'origine dati ODBC esegue l'override del database predefinito specificato per l'accesso. Il database deve essere un database esistente, a meno che non si specifichi anche `AttachDBFileName`. Se `AttachDBFileName` viene specificato anche, punta al file primario viene collegato e dato il nome del database specificato da `Database`.|  
|`Driver`|Nome del driver restituito da [SQLDrivers](../../native-client-odbc-api/sqldrivers.md). Il valore della parola chiave per il driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client è "{SQL Server Native Client 11.0}". La parola chiave `Server` è necessaria se viene specificato `Driver` e se `DriverCompletion` è impostato su SQL_DRIVER_NOPROMPT.<br /><br /> Per altre informazioni sui nomi dei driver, vedere [usando l'intestazione di SQL Server Native Client e i file di libreria](using-the-sql-server-native-client-header-and-library-files.md).|  
|`DSN`|Nome di un'origine dati di sistema o di un utente ODBC esistente. Questa parola chiave ha la precedenza su qualsiasi valore specificato nelle parole chiave `Server`, `Network` e `Address`.|  
|`Encrypt`|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|`Fallback`|Questa parola chiave è deprecata e la relativa impostazione viene ignorata dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|`Failover_Partner`|Nome del server partner di failover da utilizzare se non è possibile stabilire una connessione al server primario.|  
|`FailoverPartnerSPN`|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal driver.|  
|`FileDSN`|Nome di un'origine dati dei file ODBC esistente.|  
|`Language`|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (facoltativo). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] può memorizzare messaggi per più lingue **sysmessages**. In caso di connessione a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] con più lingue, `Language` specifica il set di messaggi utilizzato per la connessione.|  
|`MARS_Connection`|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione. I valori riconosciuti sono "yes" e "no". Il valore predefinito è "no".|  
|`MultiSubnetFailover`|Specificare sempre `multiSubnetFailover=Yes` in caso di connessione al listener del gruppo di disponibilità di un gruppo di disponibilità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] o a un'istanza del cluster di failover di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Con `multiSubnetFailover=Yes` è possibile configurare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per fornire un rilevamento più veloce di una connessione al server attualmente attivo. I valori possibili sono `Yes` e `No`. Ad esempio:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Il valore predefinito è `No`. Per altre informazioni sulle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per il supporto del Client nativo [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client il supporto per la disponibilità elevata, ripristino di emergenza](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Net`|Sinonimo di "Network".|  
|`Network`|I valori validi sono **dbnmpntw** (named pipe) e **dbmssocn** (TCP/IP).<br /><br /> Non è possibile specificare sia un valore per la parola chiave `Network`, sia un prefisso di protocollo nella parola chiave `Server`.|  
|`PWD`|Password per l'account di accesso a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] specificato nel parametro UID. Non è necessario specificare la parola chiave `PWD` se l'account di accesso dispone di una password NULL o quando si utilizza l'autenticazione di Windows (`Trusted_Connection = yes`).|  
|`QueryLog_On`|Se impostata su "yes", la registrazione dei dati di query con esecuzione prolungata viene abilitata per la connessione. Se impostata su "no", i dati di query con esecuzione prolungata non vengono registrati.|  
|`QueryLogFile`|Nome e percorso completo di un file da utilizzare per registrare dati nelle query con esecuzione prolungata.|  
|`QueryLogTime`|Stringa di cifre che specifica la soglia (in millisecondi) per la registrazione delle query con esecuzione prolungata. Tutte le query che non ottengono una risposta nell'intervallo di tempo specificato vengono scritte nel file di log delle query con esecuzione prolungata.|  
|`QuotedId`|Se impostata su "yes", QUOTED_IDENTIFIERS viene impostata su ON per la connessione e in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono utilizzate le regole ISO relative all'uso delle virgolette nelle istruzioni SQL. Se impostata su no, QUOTED_IDENTIFIERS viene impostata su OFF per la connessione. In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vengono quindi seguite le regole [!INCLUDE[tsql](../../../includes/tsql-md.md)] legacy relative all'utilizzo delle virgolette nelle istruzioni SQL. Per altre informazioni, vedere [effetti delle opzioni ISO](../../native-client-odbc-queries/executing-statements/effects-of-iso-options.md).|  
|`Regional`|Se impostata su "yes", nel driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vengono utilizzate le impostazioni client per la conversione dei dati di valuta, data e ora in dati di tipo carattere. La conversione viene eseguita in una sola direzione. Il driver non riconosce i formati standard non ODBC per le stringhe di data o i valori di valuta all'interno, ad esempio, di un parametro utilizzato in un'istruzione INSERT o UPDATE. Se impostata su "no", nel driver vengono utilizzate le stringhe standard ODBC per rappresentare i dati di valuta, data e ora convertiti in dati di tipo carattere.|  
|`SaveFile`|Nome di un file di origine dati ODBC nel quale vengono salvati gli attributi della connessione corrente se la connessione riesce.|  
|`Server`|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Il valore deve corrispondere al nome di un server in rete, a un indirizzo IP o al nome di un alias di Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La parola chiave `Address` ha la precedenza sulla parola chiave `Server`.<br /><br /> È possibile connettersi all'istanza predefinita nel server locale specificando uno dei valori seguenti:<br /><br /> -   `Server=;`<br />-   `Server=.;`<br />-   `Server=(local);`<br />-   `Server=(localhost);`<br />-   **Server=(localdb)\\** _instancename_ `;`<br /><br /> Per altre informazioni sul supporto per LocalDB, vedere [SQL Server Native Client il supporto per LocalDB](../features/sql-server-native-client-support-for-localdb.md).<br /><br /> Per specificare un'istanza denominata di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], aggiungere **\\** _NomeIstanza_.<br /><br /> Se non viene specificato un server, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Se si specifica un indirizzo IP, assicurarsi che i protocolli TCP/IP o Named Pipes siano abilitati in Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> La sintassi completa per la parola chiave `Server` è la seguente:<br /><br /> `Server=`[*protocol*`:`]*Server*[`,`*port*]<br /><br /> *protocollo* può essere `tcp` (TCP/IP), `lpc` (shared memory) o `np` (named pipe).<br /><br /> Nell'esempio seguente si illustra come specificare una named pipe:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Questa riga specifica un protocollo Named Pipes, una named pipe nel computer locale (`\\.\pipe`), il nome dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) e il nome predefinito della named pipe (`sql/query`).<br /><br /> Se non si specifica un *protocol* né la `Network` parola chiave viene specificato, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client viene utilizzato l'ordine dei protocolli specificato in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* indica la porta a cui connettersi nel server specificato. Per impostazione predefinita, in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] viene utilizzata la porta 1433.<br /><br /> Gli spazi vengono ignorati all'inizio del valore passato a `Server` nelle stringhe di connessione ODBC quando si utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|`ServerSPN`|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal driver.|  
|`StatsLog_On`|Se impostata su "yes", abilita l'acquisizione dei dati relativi alle prestazioni del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Se impostata su "no", i dati relativi alle prestazioni del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client non sono disponibili nella connessione.|  
|`StatsLogFile`|Nome e percorso completo di un file utilizzato per registrare le statistiche sulle prestazioni del driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|`Trusted_Connection`|Se impostata su "yes", indica al driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare la Modalità di autenticazione di Windows per la convalida dell'accesso. In caso contrario, indica al driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare un nome utente e una password di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per la convalida dell'accesso e richiede la specifica delle parole chiave UID e PWD.|  
|`TrustServerCertificate`|Se utilizzata con `Encrypt`, abilita la crittografia tramite un certificato server autofirmato.|  
|`UID`|Account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] valido. Quando si utilizza l'autenticazione di Windows non è necessario specificare l'UID.|  
|`UseProcForPrepare`|Questa parola chiave è deprecata e la relativa impostazione viene ignorata dal driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|`WSID`|ID della workstation. In genere, si tratta del nome di rete del computer nel quale risiede l'applicazione (facoltativo). Se specificato, questo valore viene archiviato nel **program_name** colonna **hostname** e viene restituito da [sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) e il [HOST_NAME](/sql/t-sql/functions/host-name-transact-sql)(funzione).|  
  
 **Impostazioni di conversione internazionali si applicano a valuta, numerico, data e tipi di dati ora. L'impostazione di conversione è applicabile solo alla conversione di output ed è visibile solo quando si valuta, numerico, data o i valori di ora vengono convertiti in stringhe di caratteri**.  
  
 Nel driver ODBC di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vengono utilizzate le impostazioni locali del Registro di sistema per l'utente corrente. Il driver non rispetta le impostazioni locali del thread corrente se l'applicazione le imposta dopo la connessione, ad esempio, la chiamata **SetThreadLocale**.  
  
 La modifica del comportamento internazionale di un'origine dati può generare un errore nell'applicazione. Un'applicazione che analizza le stringhe relative alla data e ne prevede la visualizzazione in base a quanto definito da ODBC, potrebbe essere influenzata negativamente dalla modifica di questo valore.  
  
## <a name="ole-db-provider-connection-string-keywords"></a>Parole chiave delle stringhe di connessione per il provider OLE DB  
 Quando si utilizzano le applicazioni OLE DB, è possibile inizializzare gli oggetti origine dati in due modi diversi:  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 Nel primo caso è possibile utilizzare una stringa del provider per inizializzare le proprietà di connessione impostando la proprietà DBPROP_INIT_PROVIDERSTRING nel set di proprietà DBPROPSET_DBINIT. Nel secondo caso è possibile passare una stringa di inizializzazione al metodo **IDataInitialize::GetDataSource** per inizializzare le proprietà di connessione. Entrambi i metodi inizializzano le stesse proprietà di connessione OLE DB, sebbene con set di parole chiave differenti. Il set di parole chiave usato con **IDataInitialize::GetDataSource** rappresenta almeno la descrizione delle proprietà contenute nel gruppo delle proprietà di inizializzazione.  
  
 Per qualsiasi impostazione di stringa del provider con una proprietà OLE DB corrispondente impostata su un valore predefinito o impostata in modo esplicito su un valore, tramite il valore della proprietà OLE DB verrà eseguito l'override dell'impostazione nella stringa del provider.  
  
 Per le proprietà booleane impostate nelle stringhe del provider mediante i valori DBPROP_INIT_PROVIDERSTRING vengono utilizzati i valori "yes" e "no". Per le proprietà booleane impostate nelle stringhe di inizializzazione con **IDataInitialize::GetDataSource** vengono usati i valori "true" e "false".  
  
 Le applicazioni che usano **IDataInitialize::GetDataSource** supportano anche le parole chiave usate da **IDBInitialize::Initialize**, ma solo per le proprietà che non hanno un valore predefinito. Se in un'applicazione viene usata sia la parola chiave **IDataInitialize::GetDataSource** che la parola chiave **IDBInitialize::Initialize** nella stringa di inizializzazione, viene usata l'impostazione della parola chiave **IDataInitialize::GetDataSource**. Nelle applicazioni è consigliabile non specificare le parole chiave **IDBInitialize::Initialize** nelle stringhe di connessione **IDataInitialize:GetDataSource**, perché questo comportamento potrebbe non essere supportato nelle versioni successive.  
  
 **Nota:** Una stringa di connessione passata a **IDataInitialize::GetDataSource** viene convertita in proprietà e applicata tramite **IDBProperties::SetProperties**. Se i Servizi componenti hanno rilevato la descrizione della proprietà in **IDBProperties::GetPropertyInfo**, la proprietà verrà applicata come autonoma. In caso contrario, verrà applicata mediante la proprietà DBPROP_PROVIDERSTRING. Ad esempio, se si specifica una stringa di connessione **Zdroj dat Source=Server1; Server server=Server2**, `Data Source` verrà impostato come proprietà, ma `Server` entra in una stringa del provider.  
  
 Se si indicano più istanze per la stessa proprietà specifica del provider, verrà utilizzato il primo valore della prima proprietà.  
  
 Le stringhe di connessione usate nelle applicazioni OLE DB che usano DBPROP_INIT_PROVIDERSTRING con **IDBInitialize::Initialize** presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra parentesi graffe per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori di attributo. Poiché si suppone che la prima parentesi graffa chiusa indichi la fine del valore, l'uso di tali parentesi nei valori non è consentito.  
  
 Uno spazio dopo il segno = in una parola chiave di una stringa di connessione verrà interpretato come valore letterale, anche se il valore è racchiuso tra virgolette.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con DBPROP_INIT_PROVIDERSTRING.  
  
|Parola chiave|Proprietà di inizializzazione|Descrizione|  
|-------------|-----------------------------|-----------------|  
|`Addr`|SSPROP_INIT_NETWORKADDRESS|Sinonimo di "Address".|  
|`Address`|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi valida per gli indirizzi, vedere la descrizione della parola chiave ODBC `Address`, più avanti in questo argomento.|  
|`APP`|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|`ApplicationIntent`|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono `ReadOnly` e `ReadWrite`.<br /><br /> Il valore predefinito è `ReadWrite`. Per altre informazioni sulle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per il supporto del Client nativo [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client il supporto per la disponibilità elevata, ripristino di emergenza](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`AttachDBFileName`|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare `AttachDBFileName`, è necessario specificare anche il nome del database con la parola chiave Database della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "yes" e "no".|  
|`Database`|DBPROP_INIT_CATALOG|Nome del database.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati da utilizzare. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di SQL Server 2000.|  
|`Encrypt`|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|`FailoverPartner`|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|`FailoverPartnerSPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|`Language`|SSPROPT_INIT_CURRENTLANGUAGE|Lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`MarsConn`|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione se il server è [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. I valori possibili sono "yes" e "no". Il valore predefinito è "no".|  
|`Net`|SSPROP_INIT_NETWORKLIBRARY|Sinonimo di "Network".|  
|`Network`|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Sinonimo di "Network".|  
|`PacketSize`|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|`PersistSensitive`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "yes" e "no" come valori. Se impostata su "no", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate|  
|`PWD`|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Server`|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi valida per gli indirizzi, vedere la descrizione della parola chiave ODBC `Server` in questo argomento.|  
|`ServerSPN`|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|`Timeout`|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|`Trusted_Connection`|DBPROP_AUTH_INTEGRATED|Se impostata su "yes", indica al provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare la Modalità di autenticazione di Windows per la convalida dell'accesso. In caso contrario, indica al provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client di utilizzare un nome utente e una password di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per la convalida dell'accesso e richiede la specifica delle parole chiave UID e PWD.|  
|`TrustServerCertificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "yes" e "no" come valori. Il valore predefinito è "no", il quale indica che il certificato server verrà convalidato.|  
|`UID`|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`UseProcForPrepare`|SSPROP_INIT_USEPROCFORPREP|Questa parola chiave è deprecata e la relativa impostazione viene ignorata dal provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|`WSID`|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 Le stringhe di connessione usate nelle applicazioni OLE DB che usano **IDataInitialize::GetDataSource** presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 L'utilizzo delle proprietà deve essere conforme alla sintassi consentita nel relativo ambito.  Per `WSID` vengono ad esempio utilizzate le parentesi graffe (`{}`) come virgolette e per `Application Name` vengono utilizzate le virgolette semplici (`'`) o doppie (`"`). Solo per le proprietà delle stringhe è possibile utilizzare le virgolette. Se si tenta di utilizzare le virgolette con una proprietà Integer o enumerata, verrà generato un errore che indica che la stringa di connessione non è conforme alla specifica OLE DB.  
  
 È consigliabile racchiudere i valori di attributo tra virgolette semplici o doppie per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori. Se raddoppiato, il carattere virgoletta può essere visualizzato anche per i valori.  
  
 Uno spazio dopo il segno = in una parola chiave di una stringa di connessione verrà interpretato come valore letterale, anche se il valore è racchiuso tra virgolette.  
  
 Se una stringa di connessione include più di una delle proprietà elencate nella tabella seguente, verrà utilizzato il valore dell'ultima proprietà.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere usate con **IDataInitialize::GetDataSource**:  
  
|Parola chiave|Proprietà di inizializzazione|Descrizione|  
|-------------|-----------------------------|-----------------|  
|`Application Name`|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|`Application Intent`|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono `ReadOnly` e `ReadWrite`.<br /><br /> Il valore predefinito è `ReadWrite`. Per altre informazioni sulle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per il supporto del Client nativo [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client il supporto per la disponibilità elevata, ripristino di emergenza](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "true" e "false".|  
|`Connect Timeout`|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|`Current Language`|SSPROPT_INIT_CURRENTLANGUAGE|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Data Source`|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi valida per gli indirizzi, vedere la descrizione della parola chiave ODBC `Server`, più avanti in questo argomento.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati da utilizzare. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)].|  
|`Failover Partner`|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|`Failover Partner SPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|`Initial Catalog`|DBPROP_INIT_CATALOG|Nome del database.|  
|`Initial File Name`|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare `AttachDBFileName`, è necessario specificare anche il nome del database con la parola chiave DATABASE della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|`Integrated Security`|DBPROP_AUTH_INTEGRATED|Accetta il valore "SSPI" per l'autenticazione di Windows.|  
|`MARS Connection`|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione. I valori riconosciuti sono "true" e "false". Il valore predefinito è "false".|  
|`Network Address`|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi valida per gli indirizzi, vedere la descrizione della parola chiave ODBC `Address`, più avanti in questo argomento.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|`Packet Size`|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|`Password`|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Persist Security Info`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "true" e "false" come valori. Se il valore è impostato su "false", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate|  
|`Provider`||Per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, deve essere "SQLNCLI11".|  
|`Server SPN`|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|`Trust Server Certificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "true" e "false" come valori. Il valore predefinito è "false", il quale indica che il certificato server verrà convalidato.|  
|`Use Encryption for Data`|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "true" e "false". Il valore predefinito è "false".|  
|`User ID`|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Workstation ID`|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 **Nota** Nella stringa di connessione la proprietà "Vecchia password" imposta SSPROP_AUTH_OLD_PASSWORD, ovvero la password corrente (probabilmente scaduta) che non è disponibile tramite una proprietà della stringa del provider.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Parole chiave delle stringhe di connessione per gli oggetti ADO (ActiveX Data Objects)  
 Le applicazioni ADO impostano la proprietà **ConnectionString** degli oggetti **ADODBConnection** o forniscono una stringa di connessione come parametro al metodo **Open** degli oggetti **ADODBConnection**.  
  
 Le applicazioni ADO supportano anche le parole chiave usate dal metodo **IDBInitialize::Initialize** OLE DB, ma solo per le proprietà che non hanno un valore predefinito. Se in un'applicazione vengono usate sia le parole chiave ADO che le parole chiave **IDBInitialize::Initialize** nella stringa di inizializzazione, verrà usata l'impostazione della parola chiave ADO. Nelle applicazioni è consigliabile utilizzare solo le parole chiave delle stringhe di connessione ADO.  
  
 Le stringhe di connessione utilizzate da ADO presentano la sintassi seguente:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 È consigliabile racchiudere i valori di attributo tra virgolette doppie per evitare i problemi determinati dalla presenza di caratteri non alfanumerici nei valori. I valori attributo non possono contenere virgolette doppie.  
  
 Nella tabella seguente vengono descritte le parole chiave che possono essere utilizzate con una stringa di connessione ADO:  
  
|Parola chiave|Proprietà di inizializzazione|Descrizione|  
|-------------|-----------------------------|-----------------|  
|`Application Intent`|SSPROP_INIT_APPLICATIONINTENT|Dichiara il tipo di carico di lavoro dell'applicazione in caso di connessione a un server. I valori possibili sono `ReadOnly` e `ReadWrite`.<br /><br /> Il valore predefinito è `ReadWrite`. Per altre informazioni sulle [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] per il supporto del Client nativo [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], vedere [SQL Server Native Client il supporto per la disponibilità elevata, ripristino di emergenza](../features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).|  
|`Application Name`|SSPROP_INIT_APPNAME|Stringa che identifica l'applicazione.|  
|`Auto Translate`|SSPROP_INIT_AUTOTRANSLATE|Sinonimo di "AutoTranslate".|  
|`AutoTranslate`|SSPROP_INIT_AUTOTRANSLATE|Configura la conversione dei caratteri OEM/ANSI. I valori riconosciuti sono "true" e "false".|  
|`Connect Timeout`|DBPROP_INIT_TIMEOUT|Tempo di attesa in secondi per il completamento dell'inizializzazione dell'origine dati.|  
|`Current Language`|SSPROPT_INIT_CURRENTLANGUAGE|Nome della lingua di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Data Source`|DBPROP_INIT_DATASOURCE|Nome di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Se non viene specificato un nome, viene stabilita una connessione all'istanza predefinita nel computer locale.<br /><br /> Per ulteriori informazioni sulla sintassi valida per gli indirizzi, vedere la descrizione della parola chiave ODBC `Server` in questo argomento.|  
|`DataTypeCompatibility`|SSPROP_INIT_DATATYPECOMPATIBILITY|Specifica la modalità di gestione dei tipi di dati che verrà utilizzata. I valori riconosciuti sono "0" per i tipi di dati del provider e "80" per i tipi di dati di SQL Server 2000.|  
|`Failover Partner`|SSPROP_INIT_FAILOVERPARTNER|Nome del server di failover utilizzato per il mirroring del database.|  
|`Failover Partner SPN`|SSPROP_INIT_FAILOVERPARTNERSPN|Nome SPN del partner di failover. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|`Initial Catalog`|DBPROP_INIT_CATALOG|Nome del database.|  
|`Initial File Name`|SSPROP_INIT_FILENAME|Nome del file primario, incluso il nome completo del percorso, di un database collegabile. Per utilizzare `AttachDBFileName`, è necessario specificare anche il nome del database con la parola chiave DATABASE della stringa del provider. Se il database è stato collegato in precedenza, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] non lo ricollega e utilizza il database collegato come impostazione predefinita per la connessione.|  
|`Integrated Security`|DBPROP_AUTH_INTEGRATED|Accetta il valore "SSPI" per l'autenticazione di Windows.|  
|`MARS Connection`|SSPROP_INIT_MARSCONNECTION|Abilita o disabilita MARS (Multiple Active Result Sets) nella connessione se il server è [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] o versione successiva. I valori riconosciuti sono "true" e "false". Il valore predefinito è "false".|  
|`Network Address`|SSPROP_INIT_NETWORKADDRESS|Indirizzo di rete di un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.<br /><br /> Per ulteriori informazioni sulla sintassi valida per gli indirizzi, vedere la descrizione della parola chiave ODBC `Address` in questo argomento.|  
|`Network Library`|SSPROP_INIT_NETWORKLIBRARY|Libreria di rete utilizzata per stabilire una connessione a un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] nell'organizzazione.|  
|`Packet Size`|SSPROP_INIT_PACKETSIZE|Dimensioni del pacchetto di rete. Il valore predefinito è 4096.|  
|`Password`|DBPROP_AUTH_PASSWORD|Password di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Persist Security Info`|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Accetta le stringhe "true" e "false" come valori. Se il valore è impostato su "false", l'oggetto origine dati non è in grado di rendere persistenti le informazioni di autenticazione riservate.|  
|`Provider`||Per [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, deve essere "SQLNCLI11".|  
|`Server SPN`|SSPROP_INIT_SERVERSPN|Nome SPN del server. Il valore predefinito è una stringa vuota. In presenza di una stringa vuota, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client utilizza il nome SPN predefinito generato dal provider.|  
|`Trust Server Certificate`|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Accetta le stringhe "true" e "false" come valori. Il valore predefinito è "false", il quale indica che il certificato server verrà convalidato.|  
|`Use Encryption for Data`|SSPROP_INIT_ENCRYPT|Specifica se i dati devono essere crittografati prima del relativo invio in rete. I valori possibili sono "true" e "false". Il valore predefinito è "false".|  
|`User ID`|DBPROP_AUTH_USERID|Nome dell'account di accesso di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`Workstation ID`|SSPROP_INIT_WSID|Identificatore della workstation.|  
  
 **Nota** Nella stringa di connessione la proprietà "Vecchia password" imposta SSPROP_AUTH_OLD_PASSWORD, ovvero la password corrente (probabilmente scaduta) che non è disponibile tramite una proprietà della stringa del provider.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  
