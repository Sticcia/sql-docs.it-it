---
title: Creazione multidimensionali di modelli utilizzando SQL Server Data Tools (SSDT) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SSAS, environments
- Analysis Services, development
- SQL Server Analysis Services, environments
- projects [Analysis Services]
- solutions [Analysis Services]
ms.assetid: 132ed779-3ec8-4734-9698-802116d1b017
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 41ddab5d08673ea71cefb7cf44169e8da6777292
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62727259"
---
# <a name="creating-multidimensional-models-using-sql-server-data-tools-ssdt"></a>Creazione di modelli multidimensionali tramite SQL Server Data Tools (SSDT)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre due diversi ambienti per la compilazione, la distribuzione e la gestione di soluzioni [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ovvero [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] e [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. In entrambi questi ambienti viene implementato un sistema di progetto. Per altre informazioni sui progetti di Visual Studio, vedere [Progetti come contenitori](https://go.microsoft.com/fwlink/?LinkId=63960) in MSDN Library.  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] è un ambiente di sviluppo basato su [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2010 nel quale è possibile creare e modificare soluzioni di Business Intelligence. Tramite [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]è possibile creare progetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che contengono le definizioni degli oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (cubi, dimensioni e così via), archiviate nei file XML che includono elementi ASSL ( [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Scripting Language). Questi progetti sono contenuti in soluzioni che possono contenere anche progetti provenienti da altri componenti di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] e [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]consente di sviluppare progetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] nell'ambito di una soluzione indipendente da istanze specifiche di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . È possibile distribuire gli oggetti in un'istanza di un server di prova per eseguire test durante la fase di sviluppo e quindi usare lo stesso progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per distribuire gli oggetti alle istanze di uno o più server dell'area di gestione temporanea o di produzione. I progetti e gli elementi di una soluzione che include [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] possono essere integrati con il controllo del codice sorgente, ad esempio [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual SourceSafe. Per altre informazioni sulla creazione di un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] usando [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vedere [Create an Analysis Services Project &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md). È inoltre possibile utilizzare [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per connettersi direttamente a un'istanza esistente di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] allo scopo di creare e modificare oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] senza utilizzare un progetto e senza archiviare definizioni degli oggetti in file XML. Per altre informazioni, vedere [Database modelli multidimensionali &#40;SSAS&#41;](multidimensional-model-databases-ssas.md)e [Connettersi in modalità online a un database di Analysis Services](connect-in-online-mode-to-an-analysis-services-database.md).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è un ambiente di gestione e amministrazione usato principalmente per amministrare istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]è possibile gestire gli oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (effettuare backup, elaborazioni e così via), nonché creare nuovi oggetti direttamente in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] esistente tramite script XMLA. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mette a disposizione un progetto script di Analysis Server in cui è possibile sviluppare e salvare script scritti in MDX (Multidimensional Expressions), DMX (Data Mining Extensions) e XMLA (XML for Analysis). In genere, i progetti script di Analysis Server vengono usati per l'esecuzione di attività amministrative o per la ricreazione di oggetti come database e cubi nelle istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . È possibile salvare tali progetti come parte di una soluzione e integrarli con il controllo del codice sorgente. Per altre informazioni sulla creazione di un progetto script di Analysis Server in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] usando [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vedere [Progetto script Analysis Services in SQL Server Management Studio](../instances/analysis-services-scripts-project-in-sql-server-management-studio.md).  
  
## <a name="introducing-solutions-projects-and-items"></a>Introduzione a soluzioni, progetti ed elementi  
 Sia [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] che [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] includono progetti organizzati in soluzioni. Una soluzione può contenere più progetti e un progetto contiene in genere più elementi. Durante la creazione di un progetto viene generata automaticamente una nuova soluzione e, se necessario, è possibile aggiungere ulteriori progetti a una soluzione esistente. Gli oggetti contenuti in un progetto dipendono dal tipo di progetto. Gli elementi di ogni contenitore di progetti vengono salvati come file all'interno delle cartelle di progetti nel file system.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] contiene i seguenti progetti corrispondenti al tipo Progetti Business Intelligence.  
  
|Progetto|Descrizione|  
|-------------|-----------------|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Progetto|Contiene le definizioni degli oggetti per un singolo database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Per altre informazioni sulle modalità di creazione di un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , vedere [Create an Analysis Services Project &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md).|  
|Importa database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 2008|Include una procedura guidata che consente di creare un nuovo progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] importando le definizioni degli oggetti da un database esistente di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Progetto|Contiene le definizioni degli oggetti per un set di pacchetti di [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Per altre informazioni, vedere [SQL Server Integration Services](../../integration-services/sql-server-integration-services.md).|  
|Creazione guidata progetto report|Include una procedura guidata che consente di eseguire in modo semplificato i passaggi necessari per il processo di creazione di un progetto report tramite [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Per altre informazioni, vedere [Reporting Services &#40;SSRS&#41;](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).|  
|Progetto modello di report|Contiene le definizioni degli oggetti per un modello di report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Per altre informazioni, vedere [Reporting Services &#40;SSRS&#41;](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).|  
|Progetto server di report|Contiene le definizioni degli oggetti per uno o più report di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Per altre informazioni, vedere [Reporting Services &#40;SSRS&#41;](../../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).|  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] contiene anche diversi tipi di progetto relativi a varie query o script, come illustrato nella tabella seguente.  
  
|Progetto|Descrizione|  
|-------------|-----------------|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Script|Contiene script DMX, MDX e XMLA per [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], nonché connessioni alle istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] che consentono l'esecuzione di tali script. Per altre informazioni, vedere [Progetto script Analysis Services in SQL Server Management Studio](../instances/analysis-services-scripts-project-in-sql-server-management-studio.md).|  
|Script di SQL Server Compact|Contiene script SQL per SQL Server Compact Edition, nonché connessioni a istanze di SQL Server Compact Edition rispetto alle quali è possibile eseguire questi script.|  
|Script SQL Server|Contiene script [!INCLUDE[tsql](../../includes/tsql-md.md)] e XQuery per un'istanza del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , nonché connessioni alle istanze del [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] che consentono l'esecuzione di tali script. Per altre informazioni, vedere [Motore di database di SQL Server](../../database-engine/sql-server-database-engine-overview.md).|  
  
 Per altre informazioni su soluzioni e progetti, vedere la sezione relativa alla gestione di soluzioni, progetti e file nella documentazione di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .NET o in MSDN Library.  
  
## <a name="choosing-between-sql-server-management-studio-and-sql-server-data-tools"></a>Scelta tra SQL Server Management Studio e strumenti di dati di SQL Server  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] è progettato per l'amministrazione e la configurazione di oggetti esistenti in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] è progettato per lo sviluppo di soluzioni di Business Intelligence in cui è inclusa la funzionalità di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 Di seguito vengono illustrate alcune differenze tra [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] offre un ambiente integrato per la connessione a istanze di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] allo scopo di configurare, gestire e amministrare oggetti all'interno di un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Tramite script è inoltre possibile usare [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] per creare o modificare oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ma [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] non offre un'interfaccia grafica per la progettazione e la definizione di oggetti.  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] offre un ambiente di sviluppo integrato per lo sviluppo di soluzioni di Business Intelligence. È possibile usare [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità progetto, in cui vengono si avvale di definizioni XML degli oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]e [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] contenuti in progetti e soluzioni. Utilizzando [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità progetto, le modifiche a oggetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] vengono apportate alle definizioni XML degli oggetti e non vengono applicate direttamente a un oggetto in un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fino alla distribuzione della soluzione. È inoltre possibile utilizzare [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] in modalità online, ovvero connettendosi direttamente a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e utilizzando gli oggetti di un database esistente.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] consente di migliorare lo sviluppo di applicazioni di Business Intelligence poiché è possibile usare i progetti di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in un ambiente multiutente incluso nel controllo del codice sorgente senza disporre di una connessione attiva a un'istanza di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] consente l'accesso diretto agli oggetti esistenti per l'esecuzione di query e per il testing e può essere usato per implementare più rapidamente i database di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] per cui è stato precedentemente generato uno script. Tuttavia, dopo avere distribuito un progetto nell'ambiente di produzione, è necessario prestare attenzione nell'usare un database [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] e i relativi oggetti con [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] e [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] per evitare di sovrascrivere le modifiche apportate agli oggetti direttamente in un database esistente e quelle apportate al progetto [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] da cui è stata generata la soluzione distribuita. Per altre informazioni, vedere [Utilizzo di progetti e database di Analysis Services durante la fase di sviluppo](work-with-analysis-services-projects-and-databases-in-development.md)e [Utilizzo di progetti e database di Analysis Services in un ambiente di produzione](work-with-analysis-services-projects-and-databases-in-production.md).  
  
## <a name="in-this-section"></a>In questa sezione  
  
-   [Creare un progetto di Analysis Services &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md)  
  
-   [Configurare proprietà di progetti di Analysis Services &#40;SSDT&#41;](configure-analysis-services-project-properties-ssdt.md)  
  
-   [Compilare progetti di Analysis Services &#40;SSDT&#41;](build-analysis-services-projects-ssdt.md)  
  
-   [Distribuire progetti di Analysis Services &#40;SSDT&#41;](deploy-analysis-services-projects-ssdt.md)  
  
-   [Utilizzo di progetti e database di Analysis Services durante la fase di sviluppo](work-with-analysis-services-projects-and-databases-in-development.md)  
  
-   [Utilizzo di progetti e database di Analysis Services in un ambiente di produzione](work-with-analysis-services-projects-and-databases-in-production.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Creare un progetto di Analysis Services &#40;SSDT&#41;](create-an-analysis-services-project-ssdt.md)   
 [Progetto script Analysis Services in SQL Server Management Studio](../instances/analysis-services-scripts-project-in-sql-server-management-studio.md)   
 [Database modelli multidimensionali &#40;SSAS&#41;](multidimensional-model-databases-ssas.md)  
  
  
