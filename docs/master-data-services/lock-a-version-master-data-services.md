---
title: Bloccare una versione (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4c2478cfa5753c094284f44c13cf0037bf927a5a
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488346"
---
# <a name="lock-a-version-master-data-services"></a>Bloccare una versione (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]bloccare una versione di un modello per evitare modifiche ai membri del modello e ai relativi attributi.  
  
> [!NOTE]  
>  Quando viene bloccata una versione, gli utenti con privilegi avanzati e gli amministratori del modello possono continuare ad aggiungere, modificare e rimuovere membri. Gli altri utenti con autorizzazione per il modello possono solo visualizzare membri.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
-   Lo stato della versione deve essere **Aperto**.  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale Gestione versioni. Per altre informazioni, vedere [Autorizzazioni per aree funzionali &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md).  
  
### <a name="to-lock-a-version"></a>Per bloccare una versione  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Gestione versioni**.  
  
2.  Nella pagina **Gestisci versioni** selezionare la riga relativa alla versione che si vuole bloccare.  
  
3.  Fare clic su **Blocca**.  
  
4.  Nella finestra di dialogo di conferma fare clic su **OK**.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
-   [Convalidare una versione usando le regole di business &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [Eseguire il commit di una versione &#40;Master Data Services&#41;](../master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Versioni &#40;Master Data Services&#41;](../master-data-services/versions-master-data-services.md)   
 [Sbloccare una versione &#40;Master Data Services&#41;](../master-data-services/unlock-a-version-master-data-services.md)  
  
  
