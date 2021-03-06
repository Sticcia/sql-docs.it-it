---
title: L'aggiornamento di un'applicazione da MDAC a SQL Server Native Client | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQLNCLI, vs. MDAC
- SQL Server Native Client, vs. MDAC
- data access [SQL Server Native Client], vs. MDAC
- SQL Server Native Client, updating applications
ms.assetid: 2860efdd-c59a-4deb-8a0e-5124a8f4e6dd
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4de00026a0d48a9850d7c13b18525c1a1d84820f
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2018
ms.locfileid: "52511804"
---
# <a name="updating-an-application-to-sql-server-native-client-from-mdac"></a>Aggiornamento di un'applicazione da MDAC a SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Esistono alcune differenze tra [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e Microsoft Data Access Components (MDAC). A partire da Windows Vista, i componenti di accesso ai dati vengono chiamati Windows Data Access Components o Windows DAC (applicazione livello dati). Sebbene entrambe le tecnologie consentano l'accesso nativo ai dati dei database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client è stato appositamente progettato per esporre le nuove caratteristiche di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] pur mantenendo la compatibilità con le versioni precedenti.  
  
 In questo argomento viene illustrato come aggiornare l'applicazione MDAC (o Windows DAC) in base alla versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client inclusa in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Che consentono di aggiornare l'applicazione corrente con la versione di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client fornito [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)], vedere [aggiornamento di un'applicazione da SQL Server 2005 Native Client](../../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md).  
  
 Inoltre, sebbene MDAC contenga componenti per l'utilizzo di OLE DB, ODBC e ActiveX Data Objects (ADO), [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client implementa solo OLE DB e ODBC, anche se ADO può accedere alla funzionalità di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e MDAC presentano inoltre alcune differenze nelle aree seguenti:  
  
-   Gli utenti che utilizzano ADO per accedere a un provider di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client potrebbero riscontrare una funzionalità di filtro meno avanzata quando accedono a un provider OLE DB SQL.  
  
-   Se un'applicazione ADO utilizza [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e tenta di aggiornare una colonna calcolata, viene generato un errore. Con MDAC l'aggiornamento è stato accettato ma ignorato.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client è un singolo file DLL (libreria a collegamento dinamico) autonomo. Il numero di interfacce esposte pubblicamente è stato ridotto al minimo, per facilitare la distribuzione e limitare al tempo stesso i rischi legati alla sicurezza.  
  
-   Sono supportate solo le interfacce OLE DB e ODBC.  
  
-   Il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e i nomi dei driver ODBC sono diversi da quelli utilizzati con MDAC.  
  
-   Le funzionalità accessibili all'utente fornite dai componenti MDAC sono disponibili durante l'utilizzo di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Le più importanti sono le seguenti: pool di connessioni, supporto ADO e supporto del cursore del client. Quando una di esse viene utilizzata, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client fornisce solo la connettività del database. MDAC fornisce funzionalità come la traccia, i controlli di gestione e i contatori delle prestazioni.  
  
-   Le applicazioni possono utilizzare i servizi di base di OLE DB con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ma in presenza del motore del cursore di OLE DB, è necessario selezionare l'opzione relativa alla compatibilità dei tipi di dati per evitare qualsiasi problema potenziale che potrebbe insorgere quando il motore del cursore non conosce i nuovi tipi di dati di [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta l'accesso ai database di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] precedenti.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client non include l'integrazione XML. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta la selezione... PER una query XML, ma non supporta le altre funzionalità XML. Tuttavia [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta la **xml** tipo di dati introdotti [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta la configurazione delle librerie di rete sul lato client utilizzando solo gli attributi della stringa di connessione. Per una configurazione delle libreria di rete più completa, è necessario utilizzare Gestione configurazione [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client non è compatibile con odbcbcp.dll. Le applicazioni che usano entrambi ODBC e **bcp** API devono essere ricompilate in modo collegate a sqlncli11.lib, per poter utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client non è supportato dal provider Microsoft OLE DB per ODBC (MSDASQL). Se si utilizza il driver MDAC SQLODBC con MSDASQL o il driver MDAC SQLODBC con ADO, utilizzare OLE DB in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   Le stringhe di connessione MDAC consentono un valore booleano (**true**) per il **Trusted_Connection** (parola chiave). Oggetto [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stringa di connessione di Native Client deve usare **yes** o **alcun**.  
  
-   Gli avvisi e gli errori non hanno subito modifiche particolarmente rilevanti. Quelli restituiti dal server mantengono ora lo stesso livello di gravità quando vengono passati a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Se l'intercettazione di determinati avvisi ed errori riveste un'importanza particolare, è necessario assicurarsi che l'applicazione sia stata sottoposta a test approfonditi.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client prevede un controllo degli errori più rigido rispetto a MDAC. Ciò significa che le applicazioni che non sono completamente conformi alle specifiche ODBC e OLE DB potrebbero avere un comportamento diverso. Ad esempio, il provider SQLOLEDB non ha applicato la regola che i nomi dei parametri devono iniziare con '\@' per i parametri del risultato, ma il [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] provider OLE DB Native Client esegue.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e MDAC gestiscono i problemi di connessione in modo diverso. MDAC, ad esempio, restituisce valori delle proprietà memorizzati nella cache per una connessione non riuscita, mentre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client segnala un errore all'applicazione chiamante.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client non genera eventi di Visual Studio Analyzer, bensì eventi di traccia di Windows.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client non può essere utilizzato con perfmon. Perfmon è un strumento di Windows disponibile solo con i DSN che utilizzano il driver MDAC SQLODBC incluso in Windows.  
  
-   Quando [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client è connesso a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] e versioni successive, l'errore del server 16947 viene restituito come SQL_ERROR. Tale errore si verifica quando tramite un'eliminazione o un aggiornamento posizionato non è possibile aggiornare o eliminare una riga. Con MDAC, in caso di connessione a una versione qualsiasi di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], l'errore del server 16947 viene restituito come avviso (SQL_SUCCESS_WITH_INFO).  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client implementa il **IDBDataSourceAdmin** dell'interfaccia, che è un'interfaccia OLE DB facoltativa non implementata in precedenza, ma solo il **CreateDataSource** di questo facoltativo (metodo) interfaccia viene implementata. [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
-   Il provider OLE DB di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client restituisce sinonimi nei set di righe degli schemi TABLES e TABLE_INFO, con TABLE_TYPE impostato su SYNONYM.  
  
-   I valori del tipo di dati restituiti **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **xml**, **udt**, o altri tipi di oggetti di grandi dimensioni non possono essere restituiti a versioni client precedenti a [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Se si desidera utilizzare questi tipi come valori restituiti, è necessario utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
-   A differenza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, MDAC consente l'esecuzione delle istruzioni seguenti all'inizio delle transazioni manuali e implicite. L'esecuzione deve avvenire in modalità autocommit.  
  
    -   Tutte le operazioni full-text (DLL indice e catalogo)  
  
    -   Tutte le operazioni del database (creazione, modifica ed eliminazione del database)  
  
    -   Riconfigurazione  
  
    -   Shutdown  
  
    -   Esecuzione del comando Kill  
  
    -   Backup  
  
-   Quando le applicazioni MDAC si connettono a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], i tipi di dati introdotti in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] vengono visualizzati come tipi di dati compatibili con [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)], come mostrato nella tabella seguente.  
  
    |Tipo di SQL Server 2005|Tipo di SQL Server 2000|  
    |--------------------------|--------------------------|  
    |**ntext**|**text**|  
    |**nvarchar(max)**|**ntext**|  
    |**varbinary(max)**|**image**|  
    |**udt**|**varbinary**|  
    |**xml**|**ntext**|  
  
     Questo mapping dei tipi influisce sui valori restituiti per i metadati delle colonne. Ad esempio, un **testo** colonna ha una dimensione massima di 2.147.483.647, ma [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ODBC Native Client segnala la dimensione massima dei **varchar (max)** colonne come SQL_SS_LENGTH_UNLIMITED e [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]OLE DB native Client segnala la dimensione massima del **varchar (max)** colonne come 2.147.483.647 o -1, a seconda della piattaforma.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta l'ambiguità nelle stringhe di connessione. In pratica, alcune parole chiave possono essere specificate più volte e, qualora siano in conflitto, viene adottata una risoluzione basata sulla posizione o sulla precedenza per garantire la compatibilità con le versioni precedenti. È possibile che nelle versioni successive di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client tale ambiguità non sia più supportata. Quando si modificano le applicazioni, è consigliabile utilizzare [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client per eliminare l'eventuale dipendenza dall'ambiguità delle stringhe di connessione.  
  
-   Se si utilizza una chiamata ODBC o OLE DB per avviare le transazioni, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client e MDAC presentano un comportamento diverso. Con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client le transazioni hanno inizio immediatamente, mentre con MDC si attende il primo accesso al database. Ciò può influenzare il comportamento di stored procedure e batch in quanto [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] richiede \@ \@TRANCOUNT sia lo stesso dopo che un batch o stored procedure termina com'era quando la stored procedure o batch avviato.  
  
-   Con [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ITransactionLocal::BeginTransaction causerà una transazione deve essere avviata immediatamente. Con MDAC l'avvio della transazione viene ritardato fino all'esecuzione da parte dell'applicazione di un'istruzione che ha richiesto una transazione in modalità implicita. Per altre informazioni, vedere [SET IMPLICIT_TRANSACTIONS &#40;Transact-SQL&#41;](../../../t-sql/statements/set-implicit-transactions-transact-sql.md).  
  
-   Possono verificarsi errori quando si usa [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] driver del Client nativo con System.Data.Odbc per accedere a un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] computer server che espone nuove [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specifici tipi di dati o funzionalità. System.Data.Odbc fornisce un'implementazione ODBC generica e successivamente non espone fornitore funzionalità o estensioni specifiche. Il driver di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client viene aggiornato per supportare a livello nativo le caratteristiche più aggiornate di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Per risolvere questo problema, è possibile ripristinare MDAC o eseguire la migrazione a SqlClient.  
  
 Sia [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client che MDAC supportano l'isolamento delle transazioni Read Committed mediante il controllo delle versioni delle righe, ma solo [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client supporta l'isolamento delle transazioni snapshot. In termini di programmazione, l'isolamento della transazione Read Committed mediante il controllo delle versioni delle righe equivale a una transazione Read Committed.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di applicazioni con SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
