---
title: Conflitti di unione [Master Data Services] | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 797219ad-5109-4666-94d3-dd1d59440a33
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 993e46a9795aa8528f4e1a1744dbf9dd5b27f89f
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65488914"
---
# <a name="merge-conflicts-master-data-services"></a>Conflitti di unione [Master Data Services]

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]se si prova a pubblicare dati modificati da un altro utente, la pubblicazione non riesce e viene visualizzato un errore di conflitto. Per risolvere questo errore, è possibile usare la funzionalità Conflitti di unione e ripubblicare le modifiche.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre dell'autorizzazione per accedere all'area funzionale **Esplora** .  
  
-   È necessario avere almeno l'autorizzazione Aggiornamento per l'oggetto modello foglia dell'entità da aggiornare.  
  
### <a name="to-merge-conflicts"></a>Per gestire i conflitti di unione  
  
1.  Nella pagina **Visualizzatore** aggiornare l'attributo del membro.  
  
2.  Se lo stesso attributo del membro è stato modificato da un altro utente, viene visualizzata la finestra di dialogo **Conflitti di unione** .  
  
3.  Nella finestra di dialogo **Conflitti di unione** è possibile:  
  
    -   Scegliere **Più recente** e fare clic su **Applica** per annullare le modifiche in sospeso e ricaricare la versione più recente dal server.  
  
    -   Scegliere **Originale** e fare clic su **Applica** per applicare la versione originale nel foglio di lavoro.  
  
    -   Scegliere **Personale** e fare clic su **Applica** per mantenere le modifiche locali esistenti.  
  
4.  Dopo aver fatto clic su **Applica**, è possibile apportare altre modifiche ed eseguire di nuovo la pubblicazione. In alternativa, è possibile fare clic su **Annulla** per annullare l'aggiornamento e ricaricare la versione più recente dal server.  
  
## <a name="see-also"></a>Vedere anche  
 [Membri &#40;Master Data Services&#41;](../master-data-services/members-master-data-services.md)  
  
  
