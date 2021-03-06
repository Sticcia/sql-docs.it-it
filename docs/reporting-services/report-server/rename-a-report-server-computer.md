---
title: Rinominare un computer del server di report | Microsoft Docs
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- renaming report servers
ms.assetid: 82fc4ba2-291a-4939-a025-271b8d687c54
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 15c69293cbe602cd69e4e0dfe0f0c29deb79347c
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: it-IT
ms.lasthandoff: 05/14/2019
ms.locfileid: "65581423"
---
# <a name="rename-a-report-server-computer"></a>Rinominare un computer del server di report
  La ridenominazione di un computer provoca una corrispondente modifica del nome del server Web e dell'istanza di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , se presente sullo stesso computer. In alcuni casi, dopo una modifica del nome del computer potrebbe non essere possibile accedere a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Utilizzare la procedura descritta in questo argomento per riconfigurare un server di report dopo la modifica del nome del computer.  
  
## <a name="renaming-a-sql-server-database-engine"></a>Ridenominazione di un Motore di database di SQL Server  
 Se si rinomina l'istanza del  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] che esegue il database del server di report, effettuare le operazioni seguenti:  
  
1.  Avviare lo strumento di configurazione Reporting Services e connettersi al server di report che utilizza il database del server di report sul server rinominato.  
  
2.  Aprire la pagina Impostazione database.  
  
3.  In **Nome server**digitare o selezionare il nome del server di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , quindi fare clic su **Connetti**.  
  
4.  Fare clic su **Applica**.  
  
 Se il server di report utilizza un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)] locale, è possibile usare *(locale)* o *(locale)\nomeistanza* per specificare il server. Se si usa *(locale)* per fare riferimento al server, è possibile rinominare il server e le connessioni continueranno a funzionare. Se si utilizza un server remoto, o se [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] è configurato con il nome del server, è necessario aggiornare le informazioni di connessione al database ogni volta che si modifica il nome server.  
  
## <a name="renaming-a-report-server-computer"></a>Ridenominazione di un computer server di report  
 Se si rinomina un computer in cui viene eseguito un server di report, eseguire le operazioni seguenti:  
  
1.  Aprire RSReportServer.config in un editor di testo e modificare l'impostazione **UrlRoot** per riflettere il nuovo nome server. L'impostazione **UrlRoot** viene utilizzata nelle estensioni per il recapito per comporre l'URL utilizzato per accedere agli elementi archiviati sul server di report. Per modificare l'indirizzo URL del server di report è necessario aggiornare l'impostazione **UrlRoot** in modo che le sottoscrizioni continuino a recapitare i report come previsto.  
  
2.  Nello stesso file, se impostato, modificare l'impostazione **ReportServerUrl** per riflettere il nuovo nome del server. Si noti che questa impostazione non viene utilizzata in ogni installazione. Se è vuota, non eseguire alcuna operazione.  
  
    > [!NOTE]  
    >  Se si utilizza Windows Internet Naming Service (WINS) sulla rete aziendale, il server di report e Gestione report potrebbero continuare a essere disponibili con il nome precedente per un determinato periodo di tempo. WINS esegue il mapping di un indirizzo IP a ogni computer incluso nel servizio. Dopo che WINS ha aggiornato l'indirizzo IP per il computer rinominato, il precedente nome del computer non potrà più essere utilizzato per accedere a un server di report o a Gestione report.  
  
## <a name="see-also"></a>Vedere anche  
 [File di configurazione RsReportServer.config](../../reporting-services/report-server/rsreportserver-config-configuration-file.md)   
 [Gestione configurazione Reporting Services &#40;modalità nativa&#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Server di report di Reporting Services &#40;modalità nativa&#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)   
 [Avviare e arrestare il servizio del server di report](../../reporting-services/report-server/start-and-stop-the-report-server-service.md)   
 [utilità rsconfig &#40;SSRS&#41;](../../reporting-services/tools/rsconfig-utility-ssrs.md)  
  
  
