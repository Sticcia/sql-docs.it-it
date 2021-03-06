---
title: Autorizzazioni dei membri della gerarchia (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 497bbda56028394547414aff5b360473445da9c1
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65485890"
---
# <a name="hierarchy-member-permissions-master-data-services"></a>Autorizzazioni membri gerarchie (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Le autorizzazioni membri gerarchia sono facoltative e devono essere utilizzate solo quando si desidera che un utente abbia accesso limitato a membri specifici. Se non si assegnano autorizzazioni nella scheda **Membri gerarchia** , le autorizzazioni dell'utente sono basate esclusivamente su quelle assegnate nella scheda **Modelli** .  
  
 Le autorizzazioni dei membri della gerarchia vengono assegnate nell'area funzionale [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Autorizzazioni utenti e gruppi **della scheda** Membri gerarchia **nell'interfaccia utente di** . Queste autorizzazioni determinano a quali membri può accedere un utente nell'area funzionale **Esplora** dell'interfaccia utente.  
  
 Nella scheda **Membri gerarchia** ogni gerarchia è rappresentata come albero. Quando si assegna un'autorizzazione a un nodo dell'albero, tutti i figli la ereditano, a meno che non sia stato assegnata in modo esplicito a un livello inferiore.  
  
> [!NOTE]  
>  Quando si assegna un'autorizzazione a un nodo di una gerarchia, a tutti i membri inclusi negli altri nodi dello stesso livello o di un livello superiore l'autorizzazione viene negata.  
  
 In **Esplora**le autorizzazioni per i membri vengono applicate in tutte le posizioni in cui il membro viene visualizzato. Ad esempio, un membro con l'autorizzazione di **lettura** può leggere tutte le entità, gerarchie e raccolte alle quali appartiene.  
  
 Le autorizzazioni membri gerarchia si applicano alla versione del modello cui sono assegnate e a eventuali copie future della versione. Non si applicano a versioni precedenti a quella a cui sono assegnate.  
  
|Autorizzazione|Descrizione|  
|----------------|-----------------|  
|**lettura**|I membri vengono visualizzati.<br /><br /> <br /><br /> Nota: se si assegna solo l'autorizzazione **Lettura** a **Root**, i membri in **Root** sono di sola lettura. Nelle gerarchie e nelle raccolte esplicite, tuttavia, l'utente può spostare i membri in **Root** e aggiungere nuovi membri in questa posizione.|  
|**Creare**|L'autorizzazione di creazione non è disponibile nell'autorizzazione dei membri della gerarchia.|  
|**Update**|I membri vengono visualizzati e l'utente può modificarli. L'utente può inoltre spostare i membri in qualsiasi gerarchia o raccolta esplicita cui essi appartengono.|  
|**Elimina**|I membri vengono visualizzati e l'utente può eliminarli.|  
|**Nega**|I membri non vengono visualizzati.|  
  
 Nella scheda **Membri gerarchia** le autorizzazioni assegnate non vengono applicate immediatamente. La frequenza con cui le autorizzazioni vengono applicate dipende dall'**impostazione relativa all'intervallo di elaborazione della sicurezza dei membri** nella tabella Impostazioni sistema del database [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . È possibile applicare immediatamente autorizzazioni di membri seguendo i passaggi descritti in [Applicare immediatamente autorizzazioni membri &#40;Master Data Services&#41;](../master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
> [!NOTE]  
>  Non è possibile assegnare autorizzazioni membri gerarchie a gerarchie ricorsive, gerarchie derivate con estremità esplicite e a gerarchie derivate con livelli nascosti.  
  
## <a name="possible-overlapping-permissions"></a>Possibili autorizzazioni sovrapposte  
 Quando si assegnano autorizzazioni ai membri, è possibile che sia necessario risolvere eventuali autorizzazioni sovrapposte.  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a>Quando un membro appartiene a più gerarchie  
 Due o più gerarchie possono contenere lo stesso membro.  
  
-   Se a un nodo della gerarchia viene assegnata l'autorizzazione di **aggiornamento** e a un altro viene assegnata l'autorizzazione di **lettura**, i membri del nodo avranno solo l'autorizzazione di **lettura**.  
  
-   Se a un nodo della gerarchia viene assegnata l'autorizzazione di **aggiornamento** e di **creazione** e a un altro viene assegnata l'autorizzazione di **aggiornamento** e di **eliminazione** , i membri del nodo possono essere aggiornati.  
  
-   Se a un nodo della gerarchia viene assegnata una qualsiasi combinazione delle autorizzazioni **Create**/**Read**/**Update**/**Delete** e a un altro nodo vengono assegnate le autorizzazioni **Deny** , l'accesso ai membri del nodo viene negato.  
  
## <a name="external-resources"></a>Risorse esterne  
 Post del blog sui [miglioramenti della sicurezza](https://go.microsoft.com/fwlink/p/?LinkId=615376)su msdn.com.  
  
## <a name="see-also"></a>Vedere anche  
 [Assegnare autorizzazioni membri gerarchia &#40;Master Data Services&#41;](../master-data-services/assign-hierarchy-member-permissions-master-data-services.md)   
 [Modalità di determinazione delle autorizzazioni &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)   
 [Membri &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)   
 [Gerarchie &#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md)   
 [Applicare immediatamente autorizzazioni membri &#40;Master Data Services&#41;](../master-data-services/immediately-apply-member-permissions-master-data-services.md)  
  
  
