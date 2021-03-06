---
title: Determinare se una tabella o una stored procedure deve essere trasferita a OLTP in memoria | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- Analyze, Migrate, Report
- AMR
ms.assetid: c1ef96f1-290d-4952-8369-2f49f27afee2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de6a778f9cdbfb7ab916f40a5250ca4f9e20c811
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63072378"
---
# <a name="determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp"></a>Determinare se una tabella o una stored procedure deve essere trasferita a OLTP in memoria
  L'agente di raccolta prestazioni transazioni in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] consente di valutare se OLTP In memoria migliorerà le prestazioni dell'applicazione di database. Nel report dell'analisi delle prestazioni delle transazioni viene inoltre indicata la quantità di operazioni che è necessario eseguire per abilitare OLTP in memoria nell'applicazione. Una volta identificata la tabella basata su disco da trasferire in OLTP in memoria, è possibile usare [Ottimizzazione guidata per la memoria](memory-optimization-advisor.md)per semplificarne la migrazione. Analogamente, l' [Native Compilation Advisor](native-compilation-advisor.md) semplifica il trasferimento di una stored procedure a una stored procedure compilata in modo nativo.  
  
 In questo argomento viene illustrato come effettuare le seguenti operazioni:  
  
-   Configurare il data warehouse di gestione.  
  
-   Configurare la raccolta dati.  
  
-   Generare report di analisi delle prestazioni delle transazioni per identificare le stored procedure e le tabelle critiche per le prestazioni.  
  
 Per informazioni sulle metodologie di migrazione, vedere [In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx) (OLTP in memoria: considerazioni sulla migrazione e sui modelli di carico di lavoro comuni).  
  
 L'agente di raccolta delle prestazioni delle transazioni e i report di analisi delle prestazioni delle transazioni sono utili per eseguire le attività seguenti:  
  
-   Analizzare il carico di lavoro per determinare se OLTP in memoria consentirà di migliorare le prestazioni. L'agente di raccolta delle prestazioni delle transazioni raccoglie e valuta le caratteristiche relative alle prestazioni del carico di lavoro. . Il report di analisi delle prestazioni delle transazioni consiglia quindi tabelle e stored procedure per cui la conversione in OLTP in memoria potrebbe risultare utile.  
  
-   Facilitare la pianificazione e l'esecuzione della migrazione a OLTP in memoria. Il percorso di migrazione da una tabella basata su disco a una tabella ottimizzata per la memoria può richiedere tempi lunghi. L'Ottimizzazione guidata per la memoria consente di identificare le incompatibilità presenti nella tabella che devono essere rimosse prima dello spostamento della tabella in OLTP in memoria. Lo strumento di ottimizzazione per la memoria consente inoltre di comprendere l'impatto che la migrazione di una tabella a una tabella ottimizzata per la memoria avrà sull'applicazione.  
  
     È possibile verificare se OLTP in memoria può costituire un vantaggio per l'applicazione, quando si desidera pianificare la migrazione a OLTP in memoria e ogni volta che si procede alla migrazione di alcune tabelle e stored procedure a OLTP in memoria.  
  
    > [!IMPORTANT]  
    >  Le prestazioni di un sistema di database dipendono da molti fattori, non tutti osservabili e misurabili tramite l'agente di raccolta delle prestazioni delle transazioni. Pertanto, il report di analisi delle prestazioni delle transazioni non è in grado di garantire che i miglioramenti effettivi delle prestazioni corrisponderanno alle eventuali stime eseguite.  
  
 L'agente di raccolta prestazioni transazioni e la possibilità di generare un report di analisi delle prestazioni delle transazioni vengono installati quando si seleziona **strumenti di gestione-Basic** oppure **strumenti di gestione-avanzati** Quando si installa [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
## <a name="best-practices"></a>Procedure consigliate  
 Il flusso di lavoro consigliato è illustrato nel diagramma di flusso seguente. I nodi gialli rappresentano le procedure facoltative:  
  
 ![Flusso di lavoro AMR](../../database-engine/media/amr-1.gif "flusso di lavoro AMR")  
  
 È possibile utilizzare qualsiasi metodo per definire dati di riferimento per le prestazioni, inclusi, a titolo esemplificativo, i log del contatore delle prestazioni o Monitoraggio attività di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Di seguito sono riportate le informazioni da utilizzare nei dati di riferimento per le prestazioni e nei confronti:  
  
-   Utilizzo della CPU da parte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Utilizzo di memoria da parte di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Attività di I/O di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Velocità effettiva delle transazioni dell'istanza durante l'elaborazione delle transazioni.  
  
 L'agente di raccolta delle prestazioni delle transazioni acquisisce dati ogni 15 minuti. Per ottenere risultati utili, eseguire l'agente di raccolta per almeno un'ora. Per ottenere i risultati migliori, eseguire l'agente di raccolta quanto basta ad acquisire i dati per gli scenari principali. Generare un report di analisi delle prestazioni delle transazioni solo dopo aver completato la raccolta dei dati.  
  
 Configurare l'agente di raccolta delle prestazioni delle transazioni affinché venga eseguito nell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in produzione e raccolga i dati in un'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in un ambiente di sviluppo (test) per garantire un overhead minimo. Per informazioni su come salvare dati in un database Data Warehouse di gestione su un server remoto [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dell'istanza, vedere [configurare la raccolta dati in un'istanza remota di SQL Server](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md#xxx).  
  
## <a name="performance-impacts"></a>Impatto sulle prestazioni  
 L'agente di raccolta delle prestazioni delle transazioni è costituito da due set di raccolta dati:  
  
-   Analisi di utilizzo delle tabelle  
  
-   Analisi di stored procedure  
  
 I set di raccolta raccolgono i dati da tre DMV ogni quindici minuti e caricano i dati nel database configurato come data warehouse di gestione. Il caricamento dei dati raccolti influisce minimamente sulle prestazioni.  
  
## <a name="use-the-transaction-performance-collector"></a>Utilizzare l'agente di raccolta delle prestazioni delle transazioni  
 Per i passaggi seguenti è richiesto [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
> [!IMPORTANT]  
>  Non modificare lo schema, ad esempio aggiungendo o rimuovendo database o creando o eliminando tabelle, durante la profilatura. Se si modifica lo schema di un database mentre si stanno raccogliendo dati, il database non potrà essere incluso in modo accurato nel report.  
  
### <a name="configure-management-data-warehouse"></a>Configurare il data warehouse di gestione  
 Il data warehouse di gestione deve essere configurato per utilizzare l'agente di raccolta delle prestazioni delle transazioni.  
  
 La versione dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su cui verranno raccolti dati (profilo) deve essere la stessa o una versione precedente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui è configurato il data warehouse di gestione.  
  
1.  In Esplora oggetti espandere **Gestione**.  
  
2.  Fare clic destro **raccolta di dati** e selezionare **attività** e quindi **Configura Data Warehouse di gestione**. Il **configurazione guidata di gestione Data Warehouse** inizia.  
  
3.  Fare clic su **successivo** per selezionare il database che verrà utilizzato come Data Warehouse di gestione.  
  
4.  Fare clic su **New** per creare un nuovo database per contenere i dati del profilo. Al termine della creazione del database, fare clic su **successivo** nella procedura guidata.  
  
5.  Il passaggio successivo consente di aggiungere utenti e account di accesso. È possibile eseguire il mapping degli account di accesso alle appartenenze ai ruoli dell'istanza del data warehouse di gestione. Questa operazione non è necessaria per raccogliere i dati dell'istanza locale. Se non si raccolgono dati dell'istanza locale, è possibile concedere l'appartenenza al ruolo del database `mdw_admin` all'account che eseguirà le transazioni sottoposte a profilatura. Al termine, fare clic su **successivo**.  
  
6.  Accertarsi che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent sia in esecuzione.  
  
7.  Nella schermata successiva fare clic su **fine** per uscire dalla procedura guidata.  
  
### <a name="configure-data-collection-on-a-local-includessnoversionincludesssnoversion-mdmd-instance"></a>Configurare la raccolta dati in un'istanza locale di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]  
 Per la raccolta dati è necessario che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent sia avviato. È sufficiente configurare un agente di raccolta dati su un server.  
  
 È possibile configurare un agente di raccolta dati su un SQL Server 2012 o versione successiva di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Per configurare la raccolta dati da caricare in un database del data warehouse di gestione nella stessa istanza  
  
1.  Nelle **Esplora oggetti**, espandere **gestione**.  
  
2.  Fare clic destro **la raccolta dei dati**, selezionare **attività**e quindi **Configura raccolta dati**. Il **configurazione guidata raccolta dati** inizia.  
  
3.  Fare clic su **successivo** per selezionare il database che verrà raccolti i dati del profilo.  
  
4.  Selezionare l'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] corrente e un database del data warehouse di gestione in tale istanza.  
  
5.  Nella casella **selezionare i set di agenti di raccolta dati si desidera abilitare**, selezionare **i set di raccolta prestazioni transazioni**. Fare clic su **successivo** al termine.  
  
6.  Verificare le selezioni. Fare clic su **nuovamente** per modificare le impostazioni. Fare clic su **Fine** al termine.  
  
###  <a name="xxx"></a> Configurare la raccolta dei dati in un server remoto [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] istanza  
 Per la raccolta dati è necessario che [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent sia avviato nell'istanza che raccoglierà i dati.  
  
 È possibile configurare un agente di raccolta dati su un SQL Server 2012 o versione successiva di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Per poter caricare dati in un database del data warehouse di gestione in un'istanza diversa da quella in cui verrà eseguita la profilatura delle transazioni, è necessario un proxy di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent configurato con le credenziali corrette per un agente di raccolta dati. Per abilitare un proxy di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent, è innanzitutto necessario definire le credenziali con un account di accesso abilitato per il dominio, che deve essere membro del gruppo `mdw_admin` per il database del data warehouse di gestione. Vedere [come: Creare una credenziale (SQL Server Management Studio)](../security/authentication-access/create-a-credential.md) per informazioni su come creare una credenziale.  
  
 Per configurare la raccolta dati da caricare in un database del data warehouse di gestione in un'istanza diversa  
  
1.  Nell'istanza che contiene gli oggetti basati su disco che si desidera eseguire la migrazione a OLTP In memoria, espandere la **gestione** nodo in Esplora oggetti.  
  
2.  Fare clic destro **la raccolta dei dati** e selezionare **attività** e quindi **Configura raccolta dati**. Il **configurazione guidata raccolta dati** inizia.  
  
3.  Fare clic su **successivo** per selezionare il database che verrà raccolti i dati del profilo.  
  
4.  Accertarsi che un database del data warehouse di gestione sia presente nell'altra istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
5.  Selezionare un'altra istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] e un database del data warehouse di gestione in tale istanza.  
  
     La versione dell'istanza di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] su cui verranno raccolti dati (profilo) deve essere la stessa o una versione precedente di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in cui è configurato il data warehouse di gestione.  
  
6.  Nella casella **selezionare i set di agenti di raccolta dati si desidera abilitare**, selezionare **i set di raccolta prestazioni transazioni**.  
  
7.  Selezionare **Usa un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] proxy dell'agente per i caricamenti remoti**.  
  
8.  Fare clic su **successivo** al termine.  
  
9. Selezionare il proxy.  
  
     Per creare un nuovo proxy di [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent  
  
    1.  Fare clic su **New** per visualizzare i **nuovo Account Proxy** nella finestra di dialogo.  
  
    2.  Nel **nuovo Account Proxy** nella finestra di dialogo immettere il nome del proxy, selezionare le credenziali e immettere facoltativamente una descrizione. Fare quindi clic **entità**.  
  
    3.  Fare clic su **Add** e selezionare **Msdb** ruolo.  
  
    4.  Selezionare `dc_proxy` e fare clic su **OK**. Quindi fare clic su **OK** nuovamente.  
  
     Dopo aver selezionato il proxy corretto, fare clic su **successivo**.  
  
10. Per configurare il set di raccolta di sistema, controllare **set di raccolta di sistema** e fare clic su **successivo**.  
  
11. Verificare le selezioni. Fare clic su **nuovamente** per modificare le impostazioni. Clicck **fine** al termine.  
  
 A questo punto, i set di raccolta dati dovrebbero essere configurati e in esecuzione nell'istanza.  
  
### <a name="generate-reports"></a>Generare report  
 È possibile generare report di analisi delle prestazioni transazioni del database del Data Warehouse di gestione facendo clic destro e selezionando **Reports**, quindi **Data Warehouse di gestione**e quindi **Panoramica dell'analisi delle prestazioni transazioni**.  
  
 Il report raccoglie informazioni su tutti i database utente nel server del carico di lavoro. Se il database del data warehouse di gestione è nel computer locale, nel report verranno visualizzati i database del data warehouse di gestione.  
  
 Una stored procedure con un alto rapporto di tempo di utilizzo della CPU rispetto al tempo trascorso è una candidata per la migrazione. Il report include tutti i riferimenti alle tabelle perché le stored procedure compilate in modo nativo possono fare riferimento solo alle tabelle ottimizzate per la memoria che possono costituire un'aggiunta al costo di migrazione.  
  
 Il report dettagli per una tabella è costituito da tre sezioni:  
  
-   Sezione relativa alle statistiche sull'analisi  
  
     In questa sezione è inclusa una singola tabella in cui sono indicate le statistiche raccolte sulle analisi nella tabella di database. Le colonne sono:  
  
    -   Percentuale di accessi totali. Percentuale di analisi e ricerche in questa tabella rispetto all'attività dell'intero database. Più alta è questa percentuale, molto più frequente è l'utilizzo della tabella confrontata con altre tabelle del database.  
  
    -   Statistiche di ricerca/Statistiche analisi intervallo. In questa colonna vengono registrati il numero di ricerche di punti e di analisi di intervalli (analisi di indici e scansioni di tabelle) eseguite sulla tabella durante la profilatura. La media per ogni transazione è una stima.  
  
    -   Guadagno di interoperabilità e Guadagno nativo. In queste colonne si stima il vantaggio in termini di prestazioni di una ricerca di punto o di un'analisi di intervalli qualora la tabella venisse convertita in una tabella ottimizzata per la memoria.  
  
-   Sezione relativa alle statistiche sulle contese  
  
     In questa sezione è inclusa una tabella in cui viene mostrata la contesa nella tabella di database. Per altre informazioni sui database latch e blocchi, vedi [architettura di blocco](https://msdn.microsoft.com/library/aa224738\(v=sql.80\).aspx). Le colonne sono le seguenti:  
  
    -   Percentuale di attese totali. Percentuale di attese di blocchi e di latch in questa tabella di database rispetto all'attività del database. Più alta è questa percentuale, molto più frequente è l'utilizzo della tabella confrontata con altre tabelle del database.  
  
    -   Statistiche latch. In queste colonne viene registrato il numero di attese di latch per query che interessano questa tabella. Per informazioni sui latch, vedere [latch](https://msdn.microsoft.com/library/aa224727\(v=SQL.80\).aspx). Più elevato è questo numero, maggiore è la contesa di latch nella tabella.  
  
    -   Statistiche blocchi. In questo gruppo di colonne viene registrato il numero di acquisizioni e attese dei blocchi di pagina per query per la tabella. Per altre informazioni sui blocchi, vedere [informazioni sul blocco in SQL Server](https://msdn.microsoft.com/library/aa213039\(v=SQL.80\).aspx). Più attese vi sono, maggiore è la contesa di blocchi nella tabella.  
  
-   Sezione relativa alle difficoltà nella migrazione  
  
     In questa sezione è inclusa una tabella in cui vengono mostrate le difficoltà di conversione della tabella di database in una tabella ottimizzata per la memoria. Un grado di difficoltà più elevato indica una maggiore difficoltà di conversione della tabella. Per visualizzare i dettagli per convertire questa tabella di database, usare il [Ottimizzazione guidata per la memoria](memory-optimization-advisor.md).  
  
 Le statistiche di contese e sulle analisi nel report dettagli della tabella vengono raccolte e aggregate dal [DM db_index_operational_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-operational-stats-transact-sql).  
  
 Il report dettagli per una stored procedure è costituito da due sezioni:  
  
-   Sezione relativa alle statistiche di esecuzione  
  
     In questa sezione è inclusa una tabella in cui sono indicate le statistiche raccolte sulle esecuzioni della stored procedure. Le colonne sono le seguenti:  
  
    -   Ora di memorizzazione nella cache. Ora di memorizzazione nella cache di questo piano di esecuzione. Se la stored procedure viene ritirata dalla cache dei piani e poi reinserita, verranno indicate le ore per ogni memorizzazione nella cache.  
  
    -   Tempo totale CPU. Tempo totale CPU utilizzato dalla stored procedure durante la profilatura. Più alto è questo numero, maggiore è l'utilizzo della CPU da parte della stored procedure.  
  
    -   Tempo di esecuzione totale. Tempo di esecuzione totale utilizzato dalla stored procedure durante la profilatura. Maggiore è la differenza tra questo numero e il tempo CPU, minore è l'utilizzo della CPU in modo efficace da parte della stored procedure.  
  
    -   Totale riscontri cache mancati. Numero di mancati riscontri nella cache (letture dall'archiviazione fisica) causato dalle esecuzioni della stored procedure durante la profilatura.  
  
    -   Conteggio esecuzioni. Numero di esecuzioni della stored procedure durante la profilatura.  
  
-   Sezione relativa ai riferimenti a tabelle  
  
     In questa sezione è inclusa una tabella in cui vengono mostrate le tabelle a cui fa riferimento questa stored procedure. Prima di convertire la stored procedure in una stored procedure compilata a livello nativo, tutte queste tabelle devono essere convertite in tabelle ottimizzate per la memoria e devono rimanere nello stesso server e database.  
  
 Statistiche di esecuzione report dettagli della stored procedure vengono raccolte e aggregate dal [DM exec_procedure_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql). I riferimenti sono ottenuti da [Sys. sql_expression_dependencies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql).  
  
 Per visualizzare informazioni dettagliate su come convertire una stored procedure a una stored procedure compilata in modo nativo, usare il [Assistente compilazione nativa](native-compilation-advisor.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Migrazione a OLTP in memoria](migrating-to-in-memory-oltp.md)  
  
  
