---
title: Creare una gerarchia derivata (Master Data Services) | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- derived hierarchies, creating
- creating derived hierarchies [Master Data Services]
ms.assetid: fec653c4-11cc-46a2-8dd8-b605341ebb40
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 29edeb9cb8fd885c5339cb8f9329e0d9f16db78d
ms.contentlocale: it-it
ms.lasthandoff: 09/07/2017

---
# <a name="create-a-derived-hierarchy-master-data-services"></a>Creare una gerarchia derivata (Master Data Services)
  In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]creare una gerarchia derivata quando si desidera una gerarchia basata su livelli tramite cui viene assicurato il posizionamento dei membri al corretto livello. Le gerarchie derivate sono basate sulle relazioni tra attributi basati su dominio che esistono in un modello.  
  
> [!NOTE]  
>  Se non esiste un valore di attributo basato su dominio per un determinato membro, tale membro non verrà incluso nella gerarchia derivata. Vedere [Richiedere valori di attributo &#40;Master Data Services&#41;](../master-data-services/require-attribute-values-master-data-services.md) per richiedere un valore di attributo basato su dominio per tutti i membri.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per eseguire questa procedura:  
  
-   È necessario disporre di autorizzazione per accedere all'area funzionale **Amministrazione sistema** .  
  
-   È necessario essere un amministratore del modello. Per altre informazioni, vedere [Amministratori &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-create-a-derived-hierarchy"></a>Per creare una gerarchia derivata  
  
1.  In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], fare clic su **Amministrazione sistema**.  
  
2.  Scegliere **Gestisci** dalla barra dei menu e fare clic su **Gerarchie derivate**.  
  
3.  Nella pagina **Gestione gerarchia derivata** selezionare un modello dall'elenco **Modello** .  
  
4.  Scegliere **Aggiungi**.  
  
5.  Nella pagina **Aggiungi gerarchia derivata** digitare un nome per la gerarchia nella casella **Nome gerarchia derivata** .  
  
    > [!TIP]  
    >  Usare un nome che descriva i livelli della gerarchia, ad esempio **Prodotto-Subcategoria-Categoria**.  
  
6.  Fare clic su **Salva gerarchia derivata**.  
  
7.  Nel riquadro **Entità e gerarchie disponibili** della pagina **Modifica gerarchia derivata** fare clic su un'entità o una gerarchia e trascinarla in **Rilasciare l'elemento padre qui** nel riquadro **Livelli correnti** .  
  
8.  Continuare a trascinare entità o gerarchie fino a che la gerarchia non è completa.  
  
9. Fare clic su **Indietro**.  
  
## <a name="see-also"></a>Vedere anche  
 [Gerarchie derivate &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)   
 [Gerarchie derivate con estremità esplicite &#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md)   
 [Attributi basati su dominio &#40;Master Data Services&#41;](../master-data-services/domain-based-attributes-master-data-services.md)  
  
  