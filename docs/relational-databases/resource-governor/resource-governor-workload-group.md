---
title: Gruppo di carico di lavoro di Resource Governor | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Resource Governor, workload group
- workload groups [SQL Server]
- workload groups [SQL Server], overview
ms.assetid: a84c3c3f-55b6-4a30-9c42-13f082d9281e
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f67e0fd5de601ceb4d808f42fa710c02fa23d3d1
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="resource-governor-workload-group"></a>Gruppo di carico di lavoro di Resource Governor
  In Resource Governor in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un gruppo di carico di lavoro viene utilizzato come contenitore per richieste di sessione che presentano criteri di classificazione simili. Un carico di lavoro consente il monitoraggio complessivo delle sessioni e di definire i criteri per le sessioni. Ogni gruppo di carico di lavoro si trova in un pool di risorse che rappresenta un subset delle risorse fisiche di un'istanza del [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Una volta avviata, la sessione viene assegnata a un gruppo di carico di lavoro specifico tramite la funzione di classificazione di Resource Governor e deve essere eseguita utilizzando i criteri assegnati al gruppo di carico di lavoro e alle risorse definite per il pool di risorse.  
  
## <a name="workload-group-concepts"></a>Concetti sui gruppi di carico di lavoro  
 Un gruppo di carico di lavoro serve come contenitore per richieste di sessione simili tra loro, secondo i criteri di classificazione applicati a ciascuna richiesta. Un gruppo del carico di lavoro consente l'aggregazione del monitoraggio dell'utilizzo delle risorse e l'applicazione di criteri uniformi a tutte le richieste nel gruppo. Un gruppo definisce i criteri per i propri membri.  
  
> [!NOTE]  
>  È possibile spostare i gruppi del carico di lavoro definiti dall'utente da un pool di risorse all'altro.  
  
 In Resource Governor sono disponibili due gruppi del carico di lavoro, il gruppo interno e il gruppo predefinito. Un utente non può modificare un gruppo classificato come gruppo interno, ma può monitorarlo. Le richieste vengono classificate nel gruppo predefinito quando si verificano le condizioni seguenti:  
  
-   Non è presente alcun criterio per classificare una richiesta.  
  
-   È stato eseguito un tentativo di classificare la richiesta in un gruppo inesistente.  
  
-   Si è verificato un errore di classificazione generale.  
  
 In Resource Governor sono inoltre disponibili istruzioni DDL per la creazione, la modifica e l'eliminazione dei gruppi di carico di lavoro.  
  
## <a name="workload-group-tasks"></a>Attività del gruppo di carico di lavoro  
  
|Descrizione dell'attività|Argomento|  
|----------------------|-----------|  
|Viene descritto come creare un gruppo di carico di lavoro.|[Creare un gruppo di carico di lavoro](../../relational-databases/resource-governor/create-a-workload-group.md)|  
|Viene descritto come modificare le impostazioni di un gruppo di carico di lavoro.|[Modificare le impostazioni dei gruppi di carico di lavoro](../../relational-databases/resource-governor/change-workload-group-settings.md)|  
|Viene descritto come eliminare un gruppo di carico di lavoro.|[Eliminare un gruppo di carico di lavoro](../../relational-databases/resource-governor/delete-a-workload-group.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)   
 [Abilitare Resource Governor](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Pool di risorse di Resource Governor](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Funzione di classificazione di Resource Governor](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [Configurare Resource Governor utilizzando un modello](../../relational-databases/resource-governor/configure-resource-governor-using-a-template.md)   
 [Visualizzare proprietà di Resource Governor](../../relational-databases/resource-governor/view-resource-governor-properties.md)  
  
  