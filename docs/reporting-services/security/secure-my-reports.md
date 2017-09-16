---
title: Proteggere i report personali | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- denying My Reports folder access
- private folders [Reporting Services]
- user workspace [Reporting Services]
- security [Reporting Services], My Reports folder
- My Reports folder [Reporting Services]
ms.assetid: 3b23a382-13b8-4196-9a93-7fe62d03a63c
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 162f43fc4f81c228d90839c75d1959d71eff9322
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="secure-my-reports"></a>Proteggere i report personali
  La caratteristica Report personali è un'area di lavoro gestita dall'utente nella quale è possibile eseguire varie operazioni sui report. Per garantire che la cartella Report personali possa essere utilizzata in base alle caratteristiche per cui è stata progettata, le autorizzazioni necessarie per questa cartella sono meno restrittive rispetto a quelle di altre cartelle disponibili a livello generale. Per gli utenti con autorizzazioni di sola visualizzazione ed esecuzione di report in altre cartelle, potrebbe essere necessario un set di autorizzazioni più ampio che consenta di gestire le cartelle Report personali e il contenuto di cui sono proprietari. In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sono disponibili un'assegnazione e una definizione di ruoli specifici per questo scopo.  
  
> [!NOTE]  
>  La funzionalità Report personali è disponibile solo in Gestione report, Non è disponibile in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## <a name="role-assignment-for-my-reports"></a>Assegnazione di ruolo per la funzionalità Report personali  
 L'assegnazione di ruolo per la funzionalità Report personali include elementi predefiniti e viene creata automaticamente per ogni utente che attiva una cartella Report personali. L'assegnazione automatica della sicurezza da parte del server di report è particolarmente utile per le organizzazioni nelle quali la funzionalità Report personali viene ampiamente utilizzata, in quanto ciò consente di evitare che gli amministratori definiscano le impostazioni di accesso per ogni utente di questa funzionalità.  
  
 Un'assegnazione di ruolo per la funzionalità **Report personali** è costituita dai componenti seguenti:  
  
-   Cartella report personali che si trova nelle cartelle degli utenti dell'utente\\*\<nome utente >*\My cartella di report.  
  
-   L'account utente, che viene determinato quando la cartella Report personali viene attivata. La cartella viene attivata quando un utente fa clic su una cartella Report personali in Gestione report oppure quando viene eseguita la pubblicazione di un report in una cartella Report personali da Progettazione report. La cartella viene inoltre attivata quando un utente richiede proprietà tramite il collegamento Report personali.  
  
-   Definizione di ruolo predefinita per la funzionalità Report personali.  
  
## <a name="role-definition-for-my-reports"></a>Definizione di ruolo per la funzionalità Report personali  
 La definizione di ruolo per la funzionalità **Report personali** include attività che supportano la gestione del contenuto di una cartella Report personali. Il ruolo **Report personali** è finalizzato a un unico scopo. Sebbene sia possibile sceglierlo per tutti i criteri di sicurezza a livello di elemento, è sconsigliabile utilizzarlo in questo modo per evitare che in seguito sia necessario modificarlo per soddisfare altri requisiti relativi alle cartelle. Se si riserva il ruolo **Report personali** alla caratteristica Report personali, gli utenti potranno godere dei vantaggi di un sistema più coerente.  
  
 Per impostazione predefinita, solo gli amministratori del server di report sono autorizzati a modificare il ruolo **Report personali** . È possibile personalizzare il ruolo **Report personali** modificando le attività in esso contenute. È inoltre possibile sostituirlo con un altro ruolo.  
  
## <a name="denying-access-to-my-reports"></a>Negazione delle autorizzazioni di accesso alla funzionalità Report personali  
 È possibile impedire a determinati utenti di accedere alla funzionalità Report personali eseguendo le operazioni seguenti:  
  
-   Disabilitazione della funzionalità Report personali nella pagina Impostazioni sito. Per altre informazioni, vedere [Abilitare e disabilitare la funzionalità Report personali](../../reporting-services/report-server/enable-and-disable-my-reports.md).  
  
-   Rimozione di tutte le attività dal ruolo **Report personali** .  
  
 Quando si disabilita la funzionalità Report personali, il collegamento alla cartella Report personali viene rimosso da Gestione report. La struttura di cartelle sottostante che supporta la funzionalità Report personali, ovvero la cartella Cartelle utenti e le relative sottocartelle, sarà comunque disponibile e accessibile da un utente che ne conosce il percorso. Se si rimuovono le attività dal ruolo **Report personali** , l'accesso alla cartella verrà impedito.  
  
## <a name="see-also"></a>Vedere anche  
 [Proteggere i report e risorse](../../reporting-services/security/secure-reports-and-resources.md)   
 [Cartelle condivise sicure](../../reporting-services/security/secure-folders.md)   
 [Concessione di autorizzazioni in un Server di Report in modalità nativa](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  