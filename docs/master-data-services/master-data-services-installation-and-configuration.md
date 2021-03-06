---
title: Installazione e configurazione di Master Data Services | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: quickstart
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 2d1cd12ff92b45c78eaf3dbe17a08c4e83d0f3b1
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994121"
---
# <a name="master-data-services-installation-and-configuration"></a>Installazione e configurazione di Master Data Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Questo articolo descrive come installare [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] in un computer Windows Server 2012 R2, impostare il database MDS e il sito Web e distribuire i modelli e i dati di esempio. [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) consente alle organizzazioni di gestire una versione attendibile dei dati.   
  
> [!NOTE] 
> È possibile installare [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] in un computer Windows 10 se si usa la Developer Edition che ora supporta [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. 
>>Per altre informazioni sui sistemi operativi supportati nelle diverse edizioni di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], vedere [Requisiti hardware e software per l'installazione di SQL Server 2016](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md). 

Per una panoramica sull'organizzazione dei dati in [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)], vedere [Panoramica di Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md).     
  
 Per informazioni sulle nuove funzionalità di [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], vedere [Novità in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md).  
 
Per i link a video e altre risorse di training per [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)], vedere [Informazioni su SQL Server Master Data Services](../master-data-services/learn-sql-server-master-data-services.md). 
  
> **Scarica**  
> -   Per scaricare [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], passare a  **[Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-ctp/)**.  
> -   Se si ha un account di Azure,  Fare clic **[qui](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)** per creare rapidamente una macchina virtuale in cui è già installato SQL Server.  
> 
> **Impossibile creare un sito Web di MDS**
> >Leggere quest'articolo del supporto tecnico Microsoft per istruzioni sulla risoluzione del problema.
> [Impossibile creare un sito Web di MDS tramite un account con privilegi limitati in SQL Server 2016](https://aka.ms/mdssupport) 

## <a name="internet-explorer-and-silverlight"></a>Internet Explorer e Silverlight
- Quando si installa [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] in un computer Windows Server 2012, potrebbe essere necessario configurare la Sicurezza avanzata di Internet Explorer per consentire lo scripting per il sito dell'applicazione Web. In caso contrario, il passaggio al sito nel computer server avrà esito negativo.
- Per funzionare nell'applicazione Web, è necessario installare Silverlight 5 nel computer client. Se non si possiede la versione richiesta di Silverlight, viene richiesto di installarla quando si passa a un'area dell'applicazione Web in cui è necessaria. Silverlight 5 può essere installato da **[qui](https://www.microsoft.com/silverlight/)**.

## <a name="includessmdsshortmdincludesssmdsshort-mdmd-on-an-azure-virtual-machine"></a>[!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] in una macchina virtuale di Azure
Per impostazione predefinita, quando si seleziona una macchina virtuale di Azure con [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] già installato viene installato anche [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. 

La fase successiva consiste nell'installazione di Internet Information Services (IIS). Vedere la sezione [Installazione e configurazione di IIS](#InstallIIS). 

Se si vogliono apportare modifiche all'installazione di [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)], è disponibile il file setup.exe nel percorso predefinito, `<drive>`:\SQLServer_13.0_Full.
  
## <a name="InstallMDS"></a> Installazione di Master Data Services  
 Per installare [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] usare l'installazione guidata di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]o un prompt dei comandi.  
  
 **Per installare [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] tramite [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup in un computer Windows Server 2012 R2**  
  
1.  Fare doppio clic su Setup.exe e seguire i passaggi dell'installazione guidata.  
  
2.  Nella pagina [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Selezione funzionalità **selezionare** in **Funzionalità condivise**.  
  
     Vengono installati [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], gli assembly, uno snap-in di Windows PowerShell, nonché cartelle e file per i servizi e le applicazioni Web.  
  
     ![mds_SQLServer2016Setup_FeatureSelection](../master-data-services/media/mds-sqlserver2016setup-featureselection.png "mds_SQLServer2016Setup_FeatureSelection")  
  
3.  Eseguire i passaggi dell'Installazione guidata.  

## <a name="InstallIIS"></a> Installazione e configurazione di IIS
  
1.  In [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]fare clic sull'icona **Server Manager** sulla barra delle applicazioni sul **Desktop**.  
  
     ![Icona di Server Manager nella barra delle applicazioni di Windows Server 2012](../master-data-services/media/mds-windowsservertaskbar-servermanagericon.png "Icona di Server Manager nella barra delle applicazioni di Windows Server 2012")  
  
5.  In **Server Manager**fare clic su **Aggiungi ruoli e funzionalità** nel menu **Gestisci** .  
   
     ![Comando del menu Aggiungi ruoli e funzionalità in Server Manager](../master-data-services/media/mds-servermanagerdashboard-addrolesfeaturesmenu.png "Comando del menu Aggiungi ruoli e funzionalità in Server Manager")  
  
6.  Nella pagina **Tipo di installazione** dell' **Aggiunta guidata ruoli e funzionalità**accettare il valore predefinito**Installazione basata su ruoli o basata su funzionalità**e fare clic su **Avanti**.  
  
7.  Fare clic su **Selezionare un server dal pool di server**e quindi fare clic sul server in cui è installato [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
     ![mds_AddRolesFeaturesWizard_ServerSelectionPage](../master-data-services/media/mds-addrolesfeatureswizard-serverselectionpage.png) 
  
8. Nella pagina **Ruoli del server** fare clic su **Server Web** e quindi su **Avanti**. 

   ![mds_AddRolesFeaturesWizard_ServerRolesPage](../master-data-services/media/mds-addrolesfeatureswizard-serverrolespage.png)
   
9. Nella pagina **Funzionalità** verificare che siano selezionate le seguenti funzionalità e quindi fare clic su **Avanti**. Queste funzionalità sono necessarie per [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] in [!INCLUDE[winblue_server_2_md](../includes/winblue-server-2-md.md)].
  
    |Funzionalità|Funzionalità|  
    |--------------|--------------|  
    |![mds_AddRolesFeaturesWizard_FeaturesPage](../master-data-services/media/mds-addrolesfeatureswizard-featurespage.png)|![mds_AddRolesFeaturesWizard_FeaturesPage_WindowsProcActive](../master-data-services/media/mds-addrolesfeatureswizard-featurespage-windowsprocactive.png)|  

10. Nel riquadro a sinistra fare clic su **Ruolo Server Web (IIS)** e quindi su  **Servizi ruolo**.
11. Nella pagina **Servizi ruolo** verificare che siano selezionati i seguenti servizi e quindi fare clic su **Avanti**. Questi servizi sono necessari per [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] in [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)].

    > [!WARNING]  
    >  Non installare il servizio ruolo Pubblicazioni WebDAV. Pubblicazioni WebDAV non è compatibile con [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
     |Servizi ruolo|Servizi ruolo|  
    |-----------------------------|-----------------------------|  
    |![mds_AddRolesFeaturesWizard_RoleServicesPage](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage.png)|![mds_AddRolesFeaturesWizard_RoleServicesPage_PerformSecurity](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage-performsecurity.png)|  
    |![mds_AddRolesFeaturesWizard_RoleServicesPage_AppDevsection](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage-appdevsection.png)|![mds_AddRolesFeaturesWizard_RoleServicesPage_ManageToolssection](../master-data-services/media/mds-addrolesfeatureswizard-roleservicespage-managetoolssection.png)|  
    |||  
  
     Per un elenco delle funzionalità e dei servizi ruolo richiesti per altri sistemi operativi, vedere [Requisiti dell'applicazione Web &#40;Master Data Services&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md).   
  
 Per altre informazioni sull'installazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite il programma di installazione, vedere [Installare SQL Server 2016 dall'Installazione guidata &#40;programma di installazione&#41;](../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
 Per altre informazioni sull'installazione di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tramite un prompt dei comandi, vedere [Installazione di SQL Server 2016 dal prompt dei comandi](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Se si utilizza un prompt dei comandi, [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] è disponibile come parametro della funzionalità.  
  
 Per una breve descrizione con collegamenti a informazioni aggiuntive sulle attività di pre-installazione, vedere [Installazione di Master Data Services](../master-data-services/install-windows/install-master-data-services.md).  
  
##  <a name="SetUpWeb"></a> Impostazione del database e del sito Web  
 **Per impostare il database e il sito Web usando [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]**  

 
> [!WARNING]
>  È necessario [installare IIS](#InstallIIS) prima di avviare Gestione configurazione [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)]. In caso contrario, in Configuration Manager verrà visualizzato un errore di Internet Information Services e non sarà possibile creare l'applicazione Web [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)].  
> 
> **Requisiti del browser**
> >L'applicazione Web [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] funziona solo in Internet Explorer (IE) 9 o versioni successive. IE 8 e le versioni precedenti, Microsoft Edge e Chrome non sono supportati.    
  
1.  Avviare [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]e fare clic su **Configurazione database** nel riquadro sinistro.  
  
2.  Fare clic su **Crea database**e quindi fare clic su **Avanti** nella **Creazione guidata database**.  
  
3.  Nel **Server di Database** , specificare l'istanza di SQL Server. 

    >  [!INCLUDE[sqlv15](../includes/sssqlv15-md.md)] Aggiunge il supporto per l'istanza gestita di SQL Server. Impostare il valore della **istanza di SQL Server** all'host di un Database SQL di Azure a istanza gestita. Ad esempio `xxxxxx.xxxxxx.database.windows.net`.

4. Selezionare il **tipo di autenticazione** e quindi fare clic su **Test connessione** per confermare che sia possibile connettersi al database usando le credenziali per il tipo di autenticazione selezionato. Scegliere **Avanti**.

    >Per [!INCLUDE[sqlv15](../includes/sssqlv15-md.md)], istanza gestita di connettersi al Database SQL di Azure, usare uno dei tipi di autenticazione seguenti:
    >
    >- Autenticazione integrata di Azure Active Directory: **Utente corrente-integrata con Active Directory**
    >- Autenticazione di SQL Server: **Account di SQL Server**.
    >
    >In istanza gestita di Database SQL di Azure, l'utente deve essere un membro del `sysadmin` ruolo predefinito del server.

    > [!NOTE]  
    >  Quando si seleziona il tipo di autenticazione **Utente corrente - sicurezza integrata**, la casella **Nome utente** è di sola lettura e visualizza il nome dell'account utente di Windows connesso al computer. Se si esegue [!INCLUDE[ssCurrent_md](../includes/sscurrent-md.md)] [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] in una macchina virtuale (VM) Azure, nella casella **Nome utente** viene visualizzato il nome della macchina virtuale e il nome utente per l'account amministratore locale nella macchina virtuale. 

    ![mds_2016ConfigManager_CreateDatabaseWizard_ServerPage](../master-data-services/media/mds-2016configmanager-createdatabasewizard-serverpage.png)  
  
4.  Digitare un nome nel campo **Nome database** . Facoltativamente, per selezionare regole di confronto di Windows, deselezionare la casella di controllo **Regole di confronto predefinite di SQL Server** e fare clic su una o più delle opzioni disponibili, ad esempio **Distinzione maiuscole/minuscole**. Scegliere **Avanti**.

    ![mds_2016ConfigManager_CreateDatabaseWizard_DatabasePage](../master-data-services/media/mds-2016configmanager-createdatabasewizard-databasepage.png)  
  
     Per altre informazioni sulle regole di confronto di Windows, vedere [Windows_collation_name (Transact-SQL)](../t-sql/statements/windows-collation-name-transact-sql.md).  
  
5.  Nel campo **Nome utente** specificare l'account di Windows dell'utente che sarà l'utente con privilegi avanzati predefinito di Master Data Services. L'utente con privilegi avanzati ha accesso a tutte le aree funzionali e può aggiungere, eliminare e aggiornare tutti i modelli.  

    ![mds_2016ConfigManager_CreateDatabaseWizard_AdminPage](../master-data-services/media/mds-2016configmanager-createdatabasewizard-adminpage.png)  
  
6.  Fare clic su **Avanti** per visualizzare un riepilogo delle impostazioni per il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] e quindi fare di nuovo clic su **Avanti** per creare il database. Viene visualizzata la pagina **Continua e termina**.

7. Quando il database viene creato e configurato, fare clic su **Fine**.  
  
     Per altre informazioni sulle impostazioni della **Creazione guidata database**, vedere [Procedura guidata Crea database &#40;Gestione configurazione Master Data Services&#41;](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
7.  Nella pagina **Configurazione database** in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] fare clic su **Selezione database**.  
  
8.  Fare clic su **Connetti**, selezionare il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] creato nel passaggio 7 e quindi fare clic su **OK**. 

    ![mds_2016ConfigManager_SelectDatabaseButton_ConnectToDatabaseDialog](../master-data-services/media/mds-2016configmanager-selectdatabasebutton-connecttodatabasedialog.png)  
  
     L'impostazione del database è stata completata. La pagina **Configurazione database** visualizza ora l'istanza di [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a cui si è connessi per [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], il database creato e la versione del database corrente.  

    ![mds_2016ConfigManager_DatabaseConfig_Completed](../master-data-services/media/mds-2016configmanager-databaseconfig-completed.png)   
  
9. In [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]fare clic su **Configurazione Web** nel riquadro sinistro.  
  
10. Nella casella di riepilogo **Sito Web** fare clic su **Sito Web predefinito**e quindi fare clic su **Crea** per creare un'applicazione Web.  
  
    > [!NOTE]  
    >  Quando si seleziona **Sito Web predefinito**, è necessario creare un'applicazione Web. Se si seleziona **Crea nuovo sito Web** nella casella di riepilogo, l'applicazione viene creata automaticamente.  

     ![mds_2016ConfigManager_WebConfig](../master-data-services/media/mds-2016configmanager-webconfig.png)  
  
11. Nella sezione **Pool di applicazioni** eseguire una di queste operazioni.  
  
    -   Immettere lo stesso nome utente specificato nel passaggio 5 per l' **Account amministratore**del database, immettere la password e quindi fare clic su **OK**.  
  
         **Oppure**  
  
    -   Immettere un nome utente diverso, immettere la password e quindi fare clic su OK.  
  
         Non è necessario usare lo stesso account quando si crea il database e l'applicazione Web.  

        ![mds_2016ConfigManager_WebConfig_CreateWebApplication](../master-data-services/media/mds-2016configmanager-webconfig-createwebapplication.png)   
  
     Per altre informazioni sula finestra di dialogo **Crea applicazione Web**, vedere [Finestra di dialogo Crea applicazione Web &#40;Gestione configurazione Master Data Services&#41;](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).  
  
12. Nella pagina **Configurazione Web** nella casella **Applicazione Web** fare clic sull'applicazione creata e quindi fare clic su **Seleziona** nella sezione **Associare l'applicazione al database**.  
  
13. Fare clic su **Connetti**, selezionare il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] che si vuole associare all'applicazione Web e quindi fare clic su **OK**.  
  
     L'impostazione del sito Web è stata completata. La pagina **Configurazione Web** visualizza ora il sito Web selezionato, l'applicazione Web creata e il database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] associato all'applicazione.  

     ![mds_2016ConfigManager_WebConfig_Completed](../master-data-services/media/mds-2016configmanager-webconfig-completed.png)  
 
     
15. Fare clic su **Applica**. Viene visualizzata la finestra di messaggio **Configurazione completata**. Fare clic su **OK** nella finestra di messaggio per avviare l'applicazione Web. L'indirizzo del sito Web è https://*nome server*/*applicazione Web*/. 


![mds_2016ConfigurationComplete_MessageBox](../master-data-services/media/mds-2016configurationcomplete-messagebox.png) 
  
     For more information about the settings on the Web Configuration page, see [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
 È anche possibile usare [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] per specificare altre impostazioni per le applicazioni e i servizi Web associati al database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Ad esempio, è possibile specificare la frequenza con cui i dati vengono caricati o quella con cui viene inviata la posta elettronica della convalida. Per altre informazioni, vedere [Impostazioni di sistema &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md).  
  
##  <a name="deploySample"></a> Distribuzione di modelli di esempio e dati  
 I seguenti tre pacchetti di modelli di esempio sono inclusi con  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].   Questi modelli di esempio includono dati. **Il percorso predefinito dei pacchetti dei modelli di esempio è %programfiles%\Microsoft SQL Server\140\Master Data Services\Samples\Packages.**
  
-   chartofaccounts_en.pkg  
  
-   customer_en.pkg  
  
-   product_en.pkg  
  
 I pacchetti vengono distribuiti con lo strumento MDSModelDeploy. Il percorso predefinito dello strumento MDSModelDeploy è *unità*\Programmi\Microsoft SQL Server\ 140\Master Data Services\Configuration.  
  
 Per informazioni sui prerequisiti per l'esecuzione di questo strumento, vedere [Distribuire un pacchetto di distribuzione di modelli tramite MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
 Per informazioni sugli aggiornamenti dei dati per il supporto delle nuove funzionalità in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vedere [Esempi SQL Server: pacchetti di distribuzione di modelli (MDS)](../master-data-services/sql-server-samples-model-deployment-packages-mds.md).  
  
 **Per distribuire i modelli di esempio**  
  
1.  Copiare i pacchetti di modelli di esempio in *unità*\Programmi\Microsoft SQL Server\140\Master Data Services\Configuration.  
  
2.  Aprire un prompt dei comandi di amministratore e passare a MDSModelDeploy.exe eseguendo il comando seguente.  
  
    ```  
    cd c:\Program Files\Microsoft SQL Server\140\Master Data Services\Configuration  
    ```  
  
3.  Distribuire ogni modello di esempio a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] eseguendo ciascuno dei comandi seguenti.  
  
    > [!IMPORTANT]  
    >  Negli esempi seguenti, il valore del servizio `MDS1` è specificato. Il valore viene usato se è stata selezionata l'opzione  **Sito Web predefinito** durante l'impostazione del sito Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  Vedere la sezione [Impostazione del database e del sito Web](#SetUpWeb) .  
    >   
    >  Se è stato creato un nuovo sito Web o è stato selezionato un altro sito Web, eseguire il comando seguente per determinare il valore del servizio corretto.  
    >   
    >  `MDSModelDeploy listservices`  
    >   
    >  Il primo valore di servizio dell'elenco di valori restituiti è il valore specificato per la distribuzione di un modello.  
    >
    > [!NOTE]
    > Per altre informazioni sui metadati dei modelli di esempio, vedere il file Leggimi disponibile in questa posizione "c:\Programmi\Microsoft SQL Server\140\Master Data Services\Configuration"
    >
   
     **Per distribuire il modello di esempio chartofaccounts_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package chartofaccounts_en.pkg -model ChartofAccounts -service MDS1  
    ```  
  
     **Per distribuire il modello di esempio customer_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package customer_en.pkg -model Customer -service MDS1  
    ```  
  
     **Per distribuire il modello di esempio product_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package product_en.pkg -model Product -service MDS1  
  
    ```  
  
     Quando la distribuzione di un modello è stata completata, viene visualizzato il messaggio **Operazione MDSModelDeploy completata** .  
  
     L'immagine seguente mostra il comando per la distribuzione del modello di esempio product_en.pkg.  
  
     ![Riga di comando per la distribuzione del modello di esempio prodotto](../master-data-services/media/mds-commandprompt-deployingsamplemodel-product.png "Riga di comando per la distribuzione del modello di esempio prodotto")  
  
4.  Per visualizzare i modelli di esempio, eseguire le operazioni seguenti.  
  
    1.  Passare al sito Web di [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] impostato. Vedere la sezione [Impostazione del database e del sito Web](#SetUpWeb) .  
  
         L'indirizzo del sito Web è https://*nome server*/*applicazione Web*/.  
  
    2.  Selezionare un modello dalla casella di riepilogo **Modello** e fare clic su **Visualizzatore**.  
  
         ![Sito Web MDS, pagina iniziale.](../master-data-services/media/mds-mdswebsite-homepage-selectsamplemodel.png "Sito Web MDS, pagina iniziale.")  
  
## <a name="next-step"></a>Passaggio successivo  
 Creare un nuovo modello e le entità per i dati. Vedere [Creare un modello &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md) e [Creare un'entità &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
 Per una panoramica sull'uso di un modello e delle entità per creare una struttura per i dati in [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], vedere [Panoramica di Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
    
## <a name="see-also"></a>Vedere anche  
 [Master Data Services Database](../master-data-services/master-data-services-database.md)   
 [Applicazione Web Gestione dati master](../master-data-services/master-data-manager-web-application.md)   
 [Pagina Configurazione database &#40;Gestione configurazione Master Data Services&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Novità in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md)  
  
  
