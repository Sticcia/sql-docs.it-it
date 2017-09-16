---
title: "Proprietà server (pagina Avanzate) - Reporting Services | Microsoft Docs"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.serverproperties.advanced.f1
ms.assetid: 07b78a84-a6aa-4502-861d-349720ef790e
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 0626dc829e6ae2cd4212dc05deb406740592dc40
ms.contentlocale: it-it
ms.lasthandoff: 08/28/2017

---

# <a name="server-properties-advanced-page---reporting-services"></a>Proprietà server (pagina Avanzate) - Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../../includes/ssrs-appliesto-pbirs.md)]

Questa pagina consente di impostare le proprietà di sistema nel server di report. Le proprietà di sistema possono essere impostate in diversi modi. Questo strumento fornisce un'interfaccia utente grafica che consente di impostare le proprietà senza dovere scrivere codice.

Per aprire questa pagina, avviare SQL Server Management Studio, connettersi a un'istanza del server di report, fare doppio clic sul nome del server di report e selezionare **proprietà**. Selezionare **avanzate** per aprire questa pagina.

## <a name="options"></a>Opzioni

**EnableMyReports**  
Indica se la caratteristica Report personali è abilitata. Un valore **true** indica che la caratteristica è abilitata.  

**MyReportsRole**  
Nome del ruolo utilizzato durante la creazione dei criteri di sicurezza nelle cartelle Report personali dell'utente. Il valore predefinito è **My Reports Role**.  

**EnableClientPrinting**  
Determina se il controllo ActiveX RSClientPrint è disponibile per il download dal server di report. I valori validi sono **true** e **false**. Il valore predefinito è **true**. Per altre informazioni sulle impostazioni aggiuntive necessarie per questo controllo, vedere [Abilitare e disabilitare la stampa sul lato client per Reporting Services](../../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  

**EnableExecutionLogging**  
Indica se la registrazione per l'esecuzione di report è attivata. Il valore predefinito è **true**. Per altre informazioni sul log di esecuzione del server di report, vedere [Vista ExecutionLog ed ExecutionLog3 del server di report](../../reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view.md).  

**ExecutionLogDaysKept**  
Numero di giorni durante i quali le informazioni sulle esecuzioni dei report vengono conservate nel log di esecuzione. I valori validi per questa proprietà sono compresi tra **-1** e **2**,**147**,**483**,**647**. Se il valore è **-1** le voci non vengono eliminate dalla tabella del log di esecuzione. Il valore predefinito è **60**.  

> [!NOTE] 
> Se si imposta un valore **0** verranno *eliminate* tutte le voci dal log di esecuzione. Il valore **-1** manterrà le voci del log di esecuzione e non verrà eliminato.

**SessionTimeout**  
Intervallo, in secondi, durante il quale una sessione rimane attiva. Il valore predefinito è **600**.  

**SharePointIntegratedMode**  
Proprietà di sola lettura che indica la modalità del server. Se il valore è False, il server di report è in esecuzione in modalità nativa.  

**SiteName**  
Nome del sito del server di report visualizzato nel titolo della pagina del portale Web. Il valore predefinito è [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Questa proprietà può essere una stringa vuota. La lunghezza massima è di 8.000 caratteri.  

**StoredParametersLifetime**  
Specifica il numero massimo di giorni per cui è possibile conservare un parametro archiviato. I valori validi sono compresi tra **-1**, **+1** e **2,147,483,647**. Il valore predefinito è **180** giorni.  

**StoredParametersThreshold**  
Specifica il numero massimo di valori dei parametri che possono essere archiviati nel server di report. I valori validi sono compresi tra **-1**, **+1** e **2,147,483,647**. Il valore predefinito è **1500**.  

**UseSessionCookies**  
Indica se il server di report deve utilizzare cookie di sessione per le comunicazioni con i browser dei client. Il valore predefinito è **true**.  

**ExternalImagesTimeout**  
Determina l'intervallo di tempo consentito per il recupero di un file di immagine esterno prima del timeout della connessione. Il valore predefinito è **600** secondi.  

**SnapshotCompression**  
Definisce come vengono compressi gli snapshot. Il valore predefinito è **SQL**. I valori validi sono i seguenti:

|Valori|Description|
|---------|---------|
|**SQL**|Gli snapshot vengono compressi quando vengono archiviati nel database del server di report. Questa impostazione corrisponde al comportamento corrente.|
|**Nessuno**|Gli snapshot non vengono compressi.|
|**Tutto**|Gli snapshot vengono compressi per tutte le opzioni di archiviazione, che includono il database del server di report o nel file system.|

**SystemReportTimeout**  
Valore di timeout  predefinito per l'elaborazione dei report, espresso in secondi, per tutti i report gestiti nello spazio dei nomi del server di report. È possibile eseguire l'override del valore a livello di report. Se questa proprietà è impostata, il server di report tenta di arrestare l'elaborazione di un report quando scade il tempo specificato. I valori validi sono compresi tra **-1** e **2**,**147**,**483**,**647**. Se il valore è **-1**durante l'elaborazione non si verifica alcun timeout dei report nello spazio dei nomi. Il valore predefinito è **1800**.  

**SystemSnapshotLimit**  
Numero massimo di snapshot archiviati per un report. I valori validi sono compresi tra **-1** e **2**,**147**,**483**,**647**. Se il valore è **-1**, non vi sono limiti per gli snapshot.  

**EnableIntegratedSecurity**  
Determina se la sicurezza integrata di Windows è supportata per le connessioni alle origini dati dei report. Il valore predefinito è **True**. I valori validi sono i seguenti:

|Valori|Description|
|---------|---------|
|**True**|Sicurezza integrata di Windows è abilitata.|
|**False**|Sicurezza integrata di Windows non è abilitata. Le origini dati dei report configurate per l'utilizzo della sicurezza integrata di Windows non verranno eseguite.|

**EnableLoadReportDefinition**  
Selezionare questa opzione per specificare se gli utenti possono eseguire report ad hoc da un report di Generatore report. Selezionando questa opzione si imposta la proprietà **EnableLoadReportDefinition** sul server di report.  

Se si deseleziona questa opzione, la proprietà viene impostata su False e nel server di report non sarà possibile generare report click-through per i report che utilizzano un modello di report come origine dati. Qualsiasi chiamata al metodo LoadReportDefinition verrà bloccata.  

La disattivazione di questa opzione consente di attenuare i rischi di attacchi Denial of Service condotti da utenti malintenzionati tramite overload del server di report con richieste LoadReportDefinition.  

**EnableRemoteErrors**  
Include informazioni esterne sugli errori, ad esempio, informazioni sull'errore relative alle origini dati del report, nei messaggi di errore restituiti agli utenti che richiedono i report dai computer remoti. I valori validi sono **true** e **false**. Il valore predefinito è **false**. Per altre informazioni, vedere [Abilita errori remoti &#40;Reporting Services&#41;](../../reporting-services/report-server/enable-remote-errors-reporting-services.md).  

**EnableReportDesignClientDownload**  
Specifica se il pacchetto di installazione di Generatore report può essere scaricato dal server di report. Se si deseleziona questa impostazione, l'URL di Generatore report non funziona. Per altre informazioni, vedere [Configurare l'accesso a Generatore report](../../reporting-services/report-server/configure-report-builder-access.md).  

**EditSessionCacheLimit**  
Consente di specificare il numero di voci della cache di dati che possono essere attive in una sessione di modifica del report. Il numero predefinito è 5.  

**EditSessionTimeout**  
Consente di specificare il numero di secondi prima del timeout di una sessione di modifica del report. Il valore predefinito è 7200 secondi (2 ore).  

**EnableCustomVisuals** ***(alimentazione solo Server di Report di Business Intelligence)***  
PowerBI ReportServer consentono la visualizzazione degli oggetti visivi personalizzati di Power BI. I valori sono True, False.  Il valore predefinito è True.  

**EnablePowerBIReportExportData** ***(alimentazione solo Server di Report di Business Intelligence)***  
PowerBI ReportServer consentono l'esportazione dei dati da oggetti visivi di Power BI. I valori sono True, False.  Il valore predefinito è True.  

**EnableTestConnectionDetailedErrors**  
Indica se messaggi di errore dettagliati vengono inviati al computer client quando gli utenti verificano le connessioni all'origine dati utilizzando il server di report. Il valore predefinito è **true**. Se l'opzione viene impostata su **false**, vengono inviati solo messaggi di errore generici.

**AccessControlAllowCredentials**  
Indica se la risposta alla richiesta del client può essere esposta quando il flag 'credenziali' è impostato su true. Il valore predefinito è **false**.

**AccessControlAllowHeaders** un elenco separati da virgole delle intestazioni che il server consentirà quando un client effettua una richiesta. Questa proprietà può essere una stringa vuota, specifica * consentirà tutte le intestazioni.

**AccessControlAllowMethods** un elenco separati da virgole dei metodi HTTP che il server consentirà quando un client effettua una richiesta. I valori predefiniti sono (GET, PUT, POST, PATCH, DELETE), specificando * consentirà a tutti i metodi.

**AccessControlAllowOrigin** un elenco separati da virgole di origini che il server consentirà quando un client effettua una richiesta. Il valore predefinito è vuoto che impedisce tutte le richieste, specificando * consentirà tutte le origini quando le credenziali non sono impostate; Se vengono specificate credenziali, è necessario specificare un elenco esplicito di origine.

**AccessControlExposeHeaders** un elenco separati da virgole delle intestazioni che il server dovrà esporre ai client. Il valore predefinito è vuoto.

**AccessControlMaxAge** specifica il numero di secondi che possono essere memorizzati nella cache i risultati della richiesta preliminare. Il valore predefinito è 600 (10 minuti).

## <a name="see-also"></a>Vedere anche

[Impostare proprietà Server di Report &#40; Management Studio &#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
[Eseguire la connessione a un server di report in Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
[Proprietà di Reporting Services](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties.md)   
[Guida sensibile al contesto del server di report in Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
[Proprietà di sistema del server di report](../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
[Utilizzare script per l'esecuzione di attività di distribuzione e di amministrazione](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)   
[Abilitare e disabilitare la funzionalità Report personali](../../reporting-services/report-server/enable-and-disable-my-reports.md)  

Ulteriori domande? [Provare a porre il forum di Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)