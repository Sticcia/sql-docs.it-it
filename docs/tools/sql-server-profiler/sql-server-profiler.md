---
title: SQL Server Profiler | Documenti Microsoft
ms.custom: 
ms.date: 10/24/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Profiler [SQL Server Profiler], about SQL Server Profiler
- traces [SQL Server], SQL Server Profiler
- database monitoring [SQL Server], SQL Server Profiler
- tuning databases [SQL Server], SQL Server Profiler
- SQL Server Profiler
- server performance [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler]
- tracing [SQL Server]
- monitoring performance [SQL Server], SQL Server Profiler
- events [SQL Server], SQL Server Profiler
- SQL Server Profiler, about SQL Server Profiler
- tools [SQL Server], SQL Server Profiler
- database performance [SQL Server], SQL Server Profiler
- trace [SQL Server]
ms.assetid: 3ad5f33d-559e-41a4-bde6-bb98792f7f1a
caps.latest.revision: 46
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 55fa14d4d8e28f602c49613cf81e981c12856177
ms.contentlocale: it-it
ms.lasthandoff: 08/02/2017

---
# <a name="sql-server-profiler"></a>SQL Server Profiler
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]è un'interfaccia per creare e gestire le tracce e analizzare e riprodurre i risultati della traccia. Gli eventi vengono salvati in un file di traccia che può essere analizzato o usato successivamente per riprodurre una serie specifica di passaggi allo scopo di diagnosticare un problema.  
  
>**IMPORTANTE**  
> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] verrà deprecato per le caratteristiche Trace Capture e Trace Replay del [!INCLUDE[ssDE](../../includes/ssde-md.md)] . Queste funzionalità **sono** disponibili in SQL Server 2016 ma verranno rimosse in una versione successiva.
>   
>  Anche lo spazio dei nomi *Microsoft.SqlServer.Management.Trace* che contiene gli oggetti Trace e Replay di Microsoft SQL Server verranno deprecati.                     
**Si noti** che [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per i carichi di lavoro di Analysis Services NON verrà deprecato e continuerà a essere supportato.
>
> Inviare i commenti e domande nella **[pagina Connect](https://connect.microsoft.com/SQLServer/Feedback)**

 ## <a name="where-is-the-profiler"></a>Dove si trova il Profiler?
 
 È possibile avviare il Profiler in molti modi da SQL Server Management Studio. [Di seguito è un argomento che elenca le modalità per avviare il Profiler.](https://msdn.microsoft.com/library/ms173799.aspx)
  
## <a name="capture-and-replay-trace-data"></a>Acquisire e riprodurre i dati di traccia 
Nella tabella seguente vengono mostrate le funzionalità che si consiglia di usare in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] per acquisire e riprodurre i dati di traccia.
  
||||  
|-|-|-|  
|**\ Carico di lavoro**|**Motore relazionale**|**Analysis Services**|  
|**Acquisizione traccia**|Interfaccia utente grafica degli[eventi estesi](https://msdn.microsoft.com/library/bb630282.aspx) in SQL Server Management Studio|SQL Server Profiler|  
|**Riproduzione della traccia**|[Riesecuzione distribuita](https://msdn.microsoft.com/library/ff878183.aspx)|SQL Server Profiler|  
  
## <a name="sql-server-profiler"></a>SQL Server Profiler  
 Microsoft [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] è un'interfaccia utente grafica della funzionalità Traccia SQL che consente di monitorare un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] o di Analysis Services. È possibile acquisire e salvare i dati di ogni evento in un file o in una tabella per operazioni di analisi successive. È ad esempio possibile monitorare un ambiente di produzione per verificare quali stored procedure hanno effetto sulle prestazioni a causa di un'esecuzione troppo lenta. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]viene usato per attività quali:  
  
-   Esecuzione dei singoli passaggi di query problematiche allo scopo di individuare la causa del problema.  
  
-   Individuazione e diagnosi di query con esecuzione rallentata.  
  
-   Acquisizione della serie di istruzioni [!INCLUDE[tsql](../../includes/tsql-md.md)] che hanno causato un problema. La traccia salvata può essere quindi utilizzata per replicare il problema in un server di prova nel quale è possibile eseguire la diagnosi.  
  
-   Monitoraggio delle prestazioni di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] per l'ottimizzazione dei carichi di lavoro. Per informazioni sull'ottimizzazione della progettazione fisica del database per i carichi di lavoro del database, vedere [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).  
  
-   Correlazione dei contatori delle prestazioni per la diagnosi dei problemi.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] supporta inoltre il controllo delle azioni eseguite sulle istanze di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. I controlli registrano le azioni relative alla sicurezza per un'analisi successiva da parte di un amministratore della sicurezza.  
  
## <a name="sql-server-profiler-concepts"></a>Concetti relativi a SQL Server Profiler  
 Per utilizzare [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], è necessario conoscere il significato dei termini che descrivono la modalità di funzionamento dello strumento.  
  
>**NOTA** Quando si usa SQL Server Profiler è utile comprendere il funzionamento di Traccia SQL. Per altre informazioni, vedere [SQL Trace](../../relational-databases/sql-trace/sql-trace.md).  
  
 **Evento**  
 Un evento è un'azione generata all'interno di un'istanza di [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Sono esempi di eventi:  
  
-   Connessioni, errori di connessione e disconnessioni.  
  
-   Istruzioni Transact-SQL SELECT, INSERT, UPDATE e DELETE.  
  
-   Stato di batch RPC (Remote Procedure Call).  
  
-   Inizio o fine di una stored procedure.  
  
-   Inizio o fine delle istruzioni contenute nelle stored procedure.  
  
-   Inizio o fine di un batch SQL.  
  
-   Errore registrato nel log degli errori di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Blocco acquisito o rilasciato su un oggetto di database.  
  
-   Cursore aperto.  
  
-   Controlli delle autorizzazioni di sicurezza.  
  
 Tutti i dati generati da un evento vengono visualizzati in un'unica riga della traccia. La riga è intersecata da colonne di dati che riportano una descrizione dettagliata dell'evento.  
  
 **EventClass**  
 Una classe di evento è un tipo di evento che è possibile tracciare. La classe di evento contiene tutti i dati che possono essere restituiti da un evento. Sono esempi di classi di evento:  
  
-   **SQL:BatchCompleted**  
  
-   **Audit Login**  
  
-   **Audit Logout**  
  
-   **Blocco: acquisito**  
  
-   **Blocco: rilasciato**  
  
 **EventCategory**  
 Una categoria di eventi definisce la modalità con la quale gli eventi vengono raggruppati all'interno di [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Ad esempio, tutte le classi degli eventi di blocco sono raggruppate nella categoria **Blocchi** . Le categorie di eventi sono tuttavia disponibili soltanto in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. Il termine non si applica alla modalità di raggruppamento degli eventi del motore.  
  
 **DataColumn**  
 Una colonna di dati è un attributo di una classe di evento acquisita nella traccia. Poiché la classe di evento determina il tipo di dati che è possibile raccogliere, non è possibile applicare tutte le colonne di dati a tutte le classi. In una traccia che acquisisce la classe di evento **Lock:Acquired** , ad esempio, la colonna di dati **BinaryData** contiene il valore dell'ID o della riga della pagina bloccata, mentre la colonna di dati **IntegerData** non contiene alcun valore perché non è applicabile alla classe di evento acquisita.  
  
 **Modello**  
 Un modello consente di definire la configurazione predefinita per una traccia. In particolare, include le classi di evento di cui si desidera eseguire il monitoraggio con [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]. È ad esempio possibile creare un modello e specificare gli eventi, le colonne di dati e i filtri da utilizzare. I modelli non vengono eseguiti, ma salvati in un file con estensione tdf. Dopo il salvataggio, i modelli consentono di controllare i dati di traccia acquisiti quando viene avviata una traccia basata sul modello.  
  
 **Traccia**  
 Una traccia consente di acquisire i dati in base alle classi di eventi, alle colonne di dati e ai filtri selezionati. È ad esempio possibile creare una traccia per il monitoraggio delle eccezioni. A tale scopo, selezionare la classe di evento **Exception** e le colonne di dati **Error**, **State**e **Severity** . Affinché i risultati della traccia includano dati significativi, è necessario raccogliere i dati di queste tre colonne. È quindi possibile eseguire una traccia configurata in tale modo e raccogliere i dati in tutti gli eventi **Exception** che si verificano nel server. I dati di traccia possono essere salvati o utilizzati immediatamente per attività di analisi. Le tracce possono essere riprodotte in un secondo momento, sebbene alcuni eventi, quali quelli **Exception** , non vengano mai riprodotti. È inoltre possibile salvare la traccia come modello e compilare tracce simili in futuro.  
  
 Sono disponibili due metodi per tracciare un'istanza di SQL Server, ovvero tramite [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] oppure stored procedure di sistema.  
  
 **Filtra**  
 Quando si crea una traccia o un modello, è possibile definire i criteri per applicare un filtro ai dati acquisiti dall'evento. Per impedire che le tracce assumano dimensioni eccessive, è possibile filtrarle in modo da raccogliere solo un subset dei dati di evento. È, ad esempio, possibile limitare i nomi utenti di Microsoft Windows della traccia a utenti specifici, riducendo in tal modo la dimensione dei dati di output.  
  
 Se non si imposta un filtro, tutti gli eventi delle classi di evento selezionate vengono restituiti nell'output di traccia.  
  
## <a name="sql-server-profiler-tasks"></a>Attività di SQL Server Profiler  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Vengono elencati i modelli predefiniti forniti in SQL Server per esaminare determinati tipi di eventi e le autorizzazioni richieste per la riproduzione delle tracce.|[Modelli e autorizzazioni di SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)|  
|Viene illustrato come eseguire SQL Server Profiler.|[Autorizzazioni necessarie per eseguire SQL Server Profiler](../../tools/sql-server-profiler/permissions-required-to-run-sql-server-profiler.md)|  
|Viene illustrato come creare una traccia.|[Creare una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-sql-server-profiler.md)|  
|Viene illustrato come specificare eventi e colonne di dati per un file di traccia.|[Specificare eventi e colonne di dati per un file di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)|  
|Viene illustrato come salvare i risultati della traccia in un file.|[Salvare i risultati della traccia in un file &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-file-sql-server-profiler.md)|  
|Viene illustrato come salvare i risultati della traccia in una tabella.|[Salvare i risultati della traccia in una tabella &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/save-trace-results-to-a-table-sql-server-profiler.md)|  
|Viene illustrato come filtrare gli eventi in una traccia.|[Filtrare eventi in una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)|  
|Viene illustrato come visualizzare informazioni sui filtri.|[Visualizzare informazioni sui filtri &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/view-filter-information-sql-server-profiler.md)|  
|Viene illustrato come modificare un filtro.|[Modificare un filtro &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)|  
|Viene illustrato come impostare le dimensioni massime di un file di traccia (SQL Server Profiler).|[Impostare le dimensioni massime di un file di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-file-size-for-a-trace-file-sql-server-profiler.md)|  
|Viene illustrato come impostare le dimensioni massime di una tabella di traccia.|[Impostare le dimensioni massime di una tabella di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-a-maximum-table-size-for-a-trace-table-sql-server-profiler.md)|  
|Viene illustrato come avviare una traccia.|[Avviare una traccia](../../tools/sql-server-profiler/start-a-trace.md)|  
|Viene illustrato come avviare automaticamente una traccia dopo la connessione a un server.|[Avviare una traccia automaticamente dopo la connessione a un server &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)|  
|Viene illustrato come filtrare gli eventi in base all'ora di inizio.|[Filtrare gli eventi in base all'ora di inizio &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-start-time-sql-server-profiler.md)|  
|Viene illustrato come filtrare gli eventi in base all'ora di fine.|[Filtrare gli eventi in base all'ora di fine &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-based-on-the-event-end-time-sql-server-profiler.md)|  
|Viene illustrato come filtrare gli ID del processo server (SPID) in una traccia.|[Filtrare gli ID del processo server &#40;SPIDs&#41; in una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-server-process-ids-spids-in-a-trace-sql-server-profiler.md)|  
|Viene illustrato come sospendere una traccia.|[Sospendere una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)|  
|Viene illustrato come arrestare una traccia.|[Arrestare in pausa una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)|  
|Viene illustrato come eseguire una traccia dopo la sospensione o l'arresto.|[Eseguire una traccia dopo la sospensione o l'arresto &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)|  
|Viene illustrato come cancellare il contenuto di una finestra di traccia.|[Cancellare il contenuto di una finestra di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)|  
|Viene illustrato come chiudere una finestra di traccia.|[Chiudere una finestra di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/close-a-trace-window-sql-server-profiler.md)|  
|Viene illustrato come impostare i valori predefiniti per la definizione della traccia.|[Impostare i valori predefiniti per una definizione di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-definition-defaults-sql-server-profiler.md)|  
|Viene illustrato come impostare i valori predefiniti per la visualizzazione della traccia.|[Impostare i valori predefiniti per la visualizzazione di una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-trace-display-defaults-sql-server-profiler.md)|  
|Viene illustrato come aprire un file di traccia.|[Aprire un file di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-file-sql-server-profiler.md)|  
|Viene illustrato come aprire una tabella di traccia.|[Aprire una tabella di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/open-a-trace-table-sql-server-profiler.md)|  
|Viene illustrato come riprodurre una tabella di traccia.|[Riprodurre una tabella di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-table-sql-server-profiler.md)|  
|Viene illustrato come riprodurre un file di traccia.|[Riprodurre un file di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-trace-file-sql-server-profiler.md)|  
|Viene illustrato come riprodurre un solo evento alla volta.|[Riprodurre un solo evento alla volta &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-single-event-at-a-time-sql-server-profiler.md)|  
|Viene illustrato come eseguire la riproduzione fino a un punto di interruzione.|[Riprodurre fino a un punto di interruzione &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-breakpoint-sql-server-profiler.md)|  
|Viene illustrato come eseguire la riproduzione in corrispondenza di un cursore.|[Riprodurre fino a un cursore &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-to-a-cursor-sql-server-profiler.md)|  
|Viene illustrato come riprodurre uno script Transact-SQL.|[Riprodurre uno script Transact-SQL &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/replay-a-transact-sql-script-sql-server-profiler.md)|  
|Viene illustrato come creare un modello di traccia.|[Creare un modello di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-trace-template-sql-server-profiler.md)|  
|Viene illustrato come modificare un modello di traccia.|[Modificare un modello di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/modify-a-trace-template-sql-server-profiler.md)|  
|Viene illustrato come impostare le opzioni di traccia globali.|[Impostare opzioni di traccia globali &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/set-global-trace-options-sql-server-profiler.md)|  
|Viene illustrato come trovare un valore o una colonna di dati durante l'esecuzione di una traccia.|[Trovare un valore o una colonna di dati durante l'esecuzione di una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/find-a-value-or-data-column-while-tracing-sql-server-profiler.md)|  
|Viene illustrato come creare un modello basato su una traccia in esecuzione.|[Ottenere un modello da una traccia in esecuzione &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-running-trace-sql-server-profiler.md)|  
|Viene illustrato come derivare un modello da un file o tabella di traccia.|[Derivare un modello da un file di traccia o da una tabella di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/derive-a-template-from-a-trace-file-or-trace-table-sql-server-profiler.md)|  
|Viene illustrato come creare uno script Transact-SQL per l'esecuzione di una traccia.|[Creare uno script Transact-SQL per l'esecuzione di una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/create-a-transact-sql-script-for-running-a-trace-sql-server-profiler.md)|  
|Viene illustrato come esportare un modello di traccia.|[Esportare un modello di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/export-a-trace-template-sql-server-profiler.md)|  
|Viene illustrato come importare un modello di traccia.|[Esportare un modello di traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/import-a-trace-template-sql-server-profiler.md)|  
|Viene illustrato come estrarre uno script da una traccia.|[Estrarre uno script da una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/extract-a-script-from-a-trace-sql-server-profiler.md)|  
|Viene illustrato come eseguire la correlazione tra una traccia e i dati dei log delle prestazioni di Windows.|[Correlare una traccia e i dati dei registri di prestazioni di Windows &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data-sql-server-profiler.md)|  
|Viene illustrato come organizzare le colonne visualizzate in una traccia.|[Organizzare le colonne visualizzate in una traccia &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/organize-columns-displayed-in-a-trace-sql-server-profiler.md)|  
|Viene illustrato come avviare SQL Server Profiler.|[Avviare SQL Server Profiler](../../tools/sql-server-profiler/start-sql-server-profiler.md)|  
|Viene illustrato come salvare tracce e modelli di traccia.|[Salvare tracce e modelli di traccia](../../tools/sql-server-profiler/save-traces-and-trace-templates.md)|  
|Viene illustrato come modificare i modelli di traccia.|[Modificare modelli di traccia](../../tools/sql-server-profiler/modify-trace-templates.md)|  
|Viene illustrato come eseguire la correlazione tra una traccia e i dati dei log delle prestazioni di Windows.|[Correlare una traccia con i dati di Log delle prestazioni di Windows](../../tools/sql-server-profiler/correlate-a-trace-with-windows-performance-log-data.md)|  
|Viene illustrato come visualizzare e analizzare tracce con SQL Server Profiler.|[Visualizzare e analizzare le tracce con SQL Server Profiler](../../tools/sql-server-profiler/view-and-analyze-traces-with-sql-server-profiler.md)|  
|Viene illustrato come visualizzare e analizzare i deadlock con SQL Server Profiler.|[Analizzare deadlock con SQL Server Profiler](../../tools/sql-server-profiler/analyze-deadlocks-with-sql-server-profiler.md)|  
|Viene illustrato come analizzare query con risultati SHOWPLAN in SQL Server Profiler.|[Analizzare query con risultati SHOWPLAN in SQL Server Profiler](../../tools/sql-server-profiler/analyze-queries-with-showplan-results-in-sql-server-profiler.md)|  
|Viene illustrato come filtrare tracce con SQL Server Profiler.|[Filtrare le tracce con SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md)|  
|Viene illustrato come utilizzare le funzionalità di riproduzione di SQL Server Profiler.|[Riprodurre le tracce](../../tools/sql-server-profiler/replay-traces.md)|  
|Vengono elencati gli argomenti della Guida sensibile al contesto di SQL Server Profiler.|[Guida sensibile al contesto di SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-f1-help.md)|  
|Vengono elencate le stored procedure di sistema utilizzate da [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] per monitorare prestazioni e attività.|[Stored procedure di SQL Server Profiler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-profiler-stored-procedures-transact-sql.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Categoria di eventi blocchi](../../relational-databases/event-classes/locks-event-category.md)   
 [Categoria di eventi sessioni](../../relational-databases/event-classes/sessions-event-category.md)   
 [Categoria di eventi stored procedure](../../relational-databases/event-classes/stored-procedures-event-category.md)   
 [Categoria di eventi TSQL](../../relational-databases/event-classes/tsql-event-category.md)   
 [Monitoraggio delle prestazioni e dell'attività del server](../../relational-databases/performance/server-performance-and-activity-monitoring.md)  
  
  
