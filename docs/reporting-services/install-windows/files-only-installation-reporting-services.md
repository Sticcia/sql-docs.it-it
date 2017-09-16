---
title: Solo i file di installazione (Reporting Services) | Documenti Microsoft
ms.custom: 
ms.date: 03/30/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- files-only installation [Reporting Services]
- installation options [Reporting Services]
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
caps.latest.revision: 22
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f9548290288b30b5a25d57083a7a2c4813a6609c
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="files-only-installation-reporting-services"></a>Installazione di tipo "solo file" (Reporting Services)
  Con*installazione di tipo "solo file"* si intende un'installazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in cui il programma di installazione crea la struttura di cartelle per i file di programma di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , copia i file su disco, registra il servizio del server di report nel computer locale, configura l'account del servizio, concede autorizzazioni file all'account del servizio e registra il provider WMI per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Un'installazione di tipo "solo file" include le caratteristiche di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] seguenti: servizio del server di report (che ospita il servizio Web ReportServer, l'applicazione di elaborazione in background e Gestione report), Generatore report, strumento di configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] e utilità della riga di comando di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (rsconfig.exe, rskeymgmt.exe e rs.exe). Non è invece applicabile alle caratteristiche condivise, ad esempio [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] o [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], che devono essere specificate come elementi distinti, se installate.  
  
 Diversamente da altre modalità di installazione, un server di report installato in modalità "solo file" non è operativo al termine dell'installazione. Sarà necessaria una configurazione aggiuntiva per portare online il server di report utilizzando il [Gestione configurazione Reporting Services &#40; Modalità nativa &#41; ](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="when-to-select-files-only-installation-mode"></a>Casi in cui selezionare la modalità di installazione "solo file"  
 Eseguire un'installazione di tipo "solo file" nei casi seguenti:  
  
-   Si desidera connettere il server di report a un database del server di report remoto.  
  
-   Si desidera installare il server di report come istanza denominata.  
  
-   Si applicano requisiti di distribuzione che includono l'utilizzo di impostazioni o funzionalità personalizzate e si desidera disporre di controllo completo sui tempi e le modalità di configurazione del server.  
  
-   Si installa un cluster di failover di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] che include [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="how-to-perform-a-files-only-installation"></a>Come eseguire un'installazione di tipo "solo file"  
 L'installazione di tipo "solo file" rappresenta l'impostazione predefinita per [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 È possibile specificare un'installazione di tipo "solo file" tramite la riga di comando o nell'Installazione guidata. Negli argomenti seguenti vengono fornite istruzioni dettagliate:  
  
-   [Installare SQL Server 2016 dall'installazione guidata &#40; Programma di installazione &#41; ](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md).  
  
-   [Installazione di SQL Server 2016 dal prompt dei comandi](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).  
  
#### <a name="example-command-line-script"></a>Esempio di script da riga di comando  
 Per maggiore chiarezza, l'esempio include /RSINSTALLMODE="FilesOnlyMode". Poiché la modalità "solo file" rappresenta l'impostazione predefinita, è tuttavia possibile omettere questa parte di codice e ottenere comunque un'installazione in modalità "solo file".  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### <a name="installation-wizard"></a>Installazione guidata  
 Quando si seleziona [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nella pagina Selezione caratteristiche, viene visualizzata la pagina Configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , che consente di specificare la modalità di installazione. Per specificare un'installazione di tipo "solo file", selezionare **Installa senza configurare il server di report** nella pagina Configurazione di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="see-also"></a>Vedere anche  
 [Verificare un'installazione di Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)   
 [Configurare Account di servizio del Server di Report &#40; Gestione configurazione SSRS &#41;](../../reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Configurare gli URL di Server di Report &#40; Gestione configurazione SSRS &#41;](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
 [Configurare una connessione di Database Server di Report &#40; Gestione configurazione SSRS &#41;](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Installare la modalità SharePoint di Reporting Services](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)   
 [Installare un server di report in modalità nativa di Reporting Services](~/reporting-services/install-windows/install-reporting-services-native-mode-report-server.md)   
 [Strumenti di Reporting Services](../../reporting-services/tools/reporting-services-tools.md)  
  
  

