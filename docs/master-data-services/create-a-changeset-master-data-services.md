---
title: Creare un insieme di modifiche (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cfad6f1c-9125-4896-b5f5-a4b9f9593cc4
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 97cc3f748f5d5b94a65eddcbcb54b9d407c7bed6
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/09/2019
ms.locfileid: "65484229"
---
# <a name="create-a-changeset-master-data-services"></a>Creare un insieme di modifiche (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Un insieme di modifiche è una raccolta delle modifiche in sospeso relative ai dati master. Se l'entità richiede l'approvazione delle modifiche, le modifiche in sospeso devono essere salvate in un insieme di modifiche e quindi inviate per l'approvazione da parte dell'amministratore.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   È necessario avere l'autorizzazione per accedere all'area funzionale Visualizzatore. Per altre informazioni, vedere [Autorizzazioni per aree funzionali &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)  
  
-   È necessario almeno l'accesso con diritti di lettura sull'entità o su uno dei relativi attributi.  
  
## <a name="to-create-a-local-changeset"></a>Per creare un insieme di modifiche locale  
  
1.  Nella home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] selezionare il modello e la versione, quindi fare clic su **Visualizzatore**.  
  
2.  Scegliere un'entità nel menu **Entità** .  
  
3.  Nel riquadro di destra selezionare **Insiemi di modifiche** e fare clic su **Crea**.  
  
4.  Immettere un nome per l'insieme di modifiche, quindi fare clic su **Salva**.  
  
     Il nome dell'insieme di modifiche deve essere univoco all'interno di un modello.  
  
## <a name="to-create-a-changeset-for-approval"></a>Per creare un insieme di modifiche per l'approvazione  
  
1.  Nella home page di [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] selezionare il modello e la versione, quindi fare clic su **Visualizzatore**.  
  
2.  Scegliere un'entità nel menu **Entità** .  
  
3.  Apportare modifiche all'entità e fare clic su**OK**.  
  
4.  **Scegli un insieme di modifiche** .  
  
5.  Fare clic su **Nuovo**, immettere un nome per l'insieme di modifiche, quindi scegliere **Salva**. Il nome dell'insieme di modifiche deve essere univoco all'interno di un modello.  
  
6.  Per usare un insieme di modifiche esistente, fare clic su **Esistente** e scegliere l'insieme di modifiche dall'elenco. Sono disponibili soli gli insiemi di modifiche con stato aperto o rifiutato.  
  
## <a name="next-steps"></a>Passaggi successivi  
 [Applicare e aggiornare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire il commit o inviare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [Applicare e rifiutare un insieme di modifiche &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
