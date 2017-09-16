---
title: "Gli strumenti di SQL e le utilità per SQL Server, Database SQL di Azure e SQL Data Warehouse | Documenti Microsoft"
ms.custom: 
ms.date: 08/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 0
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: eccbe54c561e009858f6192126abc57e3399082c
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---
# <a name="tools-and-utilities-for-azure-sql-database-sql-server-and-sql-data-warehouse"></a>Strumenti e utilità per Database SQL di Azure, SQL Server e SQL Data Warehouse

[!INCLUDE[tsql-appliesto-ss2008-all_md](../includes/tsql-appliesto-ss2008-all-md.md)]  

![](../includes/media/sql-database-tools.png)In questo articolo fornisce un elenco degli strumenti disponibili per l'utilizzo di SQL Server, Database SQL di Azure, SQL Data Warehouse e le applicazioni basate su SQL Server. 

Se si desidera passare direttamente in e avviare la creazione di tabelle, esecuzione di query, fondamentalmente progettare e gestire il database, quindi [ **SQL Server Management Studio (SSMS)** ](../ssms/download-sql-server-management-studio-ssms.md) è molto probabile che lo strumento come. SQL Server Management Studio è disponibile e viene eseguito in Windows.

Se si esegue Linux o Mac OS, provare a [codice di Visual Studio](https://code.visualstudio.com/) con il [ **mssql per Visual Studio Code** ](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) estensione. Questi strumenti sono per lo sviluppo di Microsoft SQL Server, Database SQL di Azure e SQL Data Warehouse con un'ampia gamma di funzionalità e sono inoltre disponibili. Vedere [usare codice di Visual Studio per creare ed eseguire script Transact-SQL per SQL Server](../linux/sql-server-linux-develop-use-vscode.md).


## <a name="sql-tools"></a>Strumenti di SQL 
 
| Strumento | Description |
|:--|:--|
| [SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md) | Utilizzare SQL Server Management Studio (SSMS) per eseguire una query, progettazione e gestione di SQL Server, Database SQL di Azure e Azure SQL Data Warehouse. |
| [SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md) | Trasformare Visual Studio in un ambiente di sviluppo potenti per SQL Server, Database SQL di Azure e Azure SQL Data Warehouse. |
| [Codice di Visual Studio](https://code.visualstudio.com/)| Codice di Visual Studio funziona su Linux, macOS e Windows. Dopo aver installato Visual Studio Code, installare il [estensione mssql](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql) per lo sviluppo di Microsoft SQL Server, Database SQL di Azure e SQL Data Warehouse. |
| [Gestione configurazione](../tools/configuration-manager/sql-server-configuration-manager-help.md) | Utilizzare Gestione configurazione SQL Server per configurare servizi di SQL Server e configurare la connettività di rete.|
| [SQL Server Migration Assistant](../ssma/sql-server-migration-assistant.md) | Utilizzare SQL Server Migration Assistant per automatizzare la migrazione di database a SQL Server da Microsoft Access, DB2, MySQL, Oracle e Sybase.|
| [Riesecuzione distribuita](../tools/distributed-replay/install-distributed-replay-overview.md) | Utilizzare la funzionalità di riesecuzione distribuita che consentono di valutare l'impatto dei futuri aggiornamenti di SQL Server. Inoltre è possibile utilizzare Distributed Replay per valutare l'impatto dell'hardware e aggiornamenti del sistema operativo e l'ottimizzazione di SQL Server. |
| [ssbdiagnose](../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md) | L'utilità ssbdiagnose segnala i problemi in conversazioni di Service Broker o la configurazione di servizi di Service Broker. |


## <a name="sql-command-prompt-utilities"></a>Utilità della riga di comando SQL

  Le utilità del prompt dei comandi consentono di generare script di operazioni [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Nella tabella seguente è riportato l'elenco delle utilità del prompt dei comandi fornite con [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
|**Utility**|**Descrizione**|**Posizione di installazione**|  
|-----------------|---------------------|----------------------|  
|[Utilità bcp](../tools/bcp-utility.md)|Usata per copiare i dati tra un'istanza di [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] e un file di dati in un formato specificato dall'utente.|\<*unità*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Utilità dta](../tools/dta/dta-utility.md)|Consente di analizzare un carico di lavoro e proporre strutture di progettazione fisica per ottimizzare le prestazioni del server per il carico di lavoro specifico.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità dtexec](../integration-services/packages/dtexec-utility.md)|Utilizzata per configurare ed eseguire un pacchetto di [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Una versione di interfaccia utente di questa utilità del prompt dei comandi è denominata **DTExecUI**e visualizza l'Utilità di esecuzione pacchetti.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Utilità dtutil](../integration-services/dtutil-utility.md)|Consente di gestire i pacchetti SSIS.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]DTS\Binn|  
|[Distribuire soluzioni di modelli con l'utilità di distribuzione](../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|Consente di distribuire progetti di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in istanze di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VShell\Common7\IDE|  
|[MSSQL-scripter (anteprima pubblica)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/05/17/try-new-sql-server-command-line-tools-to-generate-t-sql-scripts-and-monitor-dynamic-management-views/)|Utilizzato per generare script di creare e inserire T-SQL per oggetti di database di SQL Server, Database SQL di Azure e Azure SQL Data Warehouse.|Vedere il nostro [repository GitHub](https://github.com/Microsoft/sql-xplat-cli) per informazioni su download e l'utilizzo.| 
|[Utilità osql](../tools/osql-utility.md)|Consente di immettere istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] , procedure di sistema e file script al prompt dei comandi.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità profiler](../tools/profiler-utility.md)|Consente di avviare [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] dal prompt dei comandi.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità RS.exe &#40;SSRS&#41;](../reporting-services/tools/rs-exe-utility-ssrs.md)|Consente di eseguire script progettati per la gestione di server di report [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[utilità rsconfig &#40;SSRS&#41;](../reporting-services/tools/rsconfig-utility-ssrs.md)|Consente di configurare una connessione a un server di report.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità rskeymgmt &#40;SSRS&#41;](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|Consente di gestire le chiavi di crittografia in un server di report.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Applicazione sqlagent90](../tools/sqlagent90-application.md)|Utilizzata per avviare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent da un prompt dei comandi.|\<unità >: \Programmi\Microsoft SQL Server\\<*instance_name*> \MSSQL\Binn|  
|[Utilità sqlcmd](../tools/sqlcmd-utility.md)|Consente di immettere istruzioni [!INCLUDE[tsql](../includes/tsql-md.md)] , procedure di sistema e file script al prompt dei comandi.|\<*unità*: > \Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn|  
|[Utilità SQLdiag](../tools/sqldiag-utility.md)|Utilizzata per raccogliere informazioni di diagnostica per il Servizio Supporto Tecnico Clienti [!INCLUDE[msCoName](../includes/msconame-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Applicazione sqllogship](../tools/sqllogship-application.md)|Consente di eseguire operazioni di backup, copia e ripristino da altre applicazioni, nonché di eseguire le attività di pulizia associate per una configurazione per il log shipping, senza eseguire i processi di backup, copia e ripristino.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[Utilità SqlLocalDB](../tools/sqllocaldb-utility.md)|Modalità di esecuzione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] destinata agli sviluppatori.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\|  
|[Utilità sqlmaint](../tools/sqlmaint-utility.md)|Utilizzata per eseguire i piani di manutenzione dei database creati nelle precedenti versioni di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|\<unità >: \Programmi\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Binn|  
|[Utilità sqlps](../tools/sqlps-utility.md)|Consente di eseguire comandi e script di PowerShell, nonché di caricare e registrare il provider e i cmdlet di PowerShell per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn|  
|[sqlservr](../tools/sqlservr-application.md)|Consente di avviare e arrestare un'istanza di [!INCLUDE[ssDE](../includes/ssde-md.md)] dal prompt dei comandi per la risoluzione dei problemi.|\<unità >: \Programmi\Microsoft SQL Server\MSSQL13. MSSQLSERVER\MSSQL\Binn|  
|[Utilità Ssms](../tools/sql-server-management-studio/ssms-utility.md)|Consente di avviare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] dal prompt dei comandi.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]Tools\Binn\VSShell\Common7\IDE|  
|[Utilità tablediff](../tools/tablediff-utility.md)|Consente di confrontare i dati di due tabelle e rilevare l'eventuale non convergenza dei dati. Risulta particolarmente utile per la risoluzione dei problemi relativi alla topologia di replica.|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]COM|  

## <a name="sql-command-prompt-utilities-syntax-conventions"></a>Convenzioni della sintassi utilità della riga di comando SQL  
  
|**Convenzione**|**Utilizzo**|  
|--------------------|------------------|  
|MAIUSCOLE|Istruzioni e termini utilizzati a livello di sistema operativo.|  
|`monospace`|Esempi di comandi e codice di programmazione.|  
|*corsivo*|Parametri specificati dall'utente.|  
|**grassetto**|Comandi, parametri e altri elementi della sintassi che devono essere digitati esattamente come indicato.|  


