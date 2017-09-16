---
title: Creare una copia di un modello di Data Mining | Documenti Microsoft
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining models [Analysis Services], copying
- mining models [Analysis Services], creating
- mining models [Analysis Services], how-to topics
- copying mining models
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: aaa773a470cb0c2fea7929e3e6b331cfb0e7ed31
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="make-a-copy-of-a-mining-model"></a>Eseguire una copia di un modello di data mining
  La creazione di una copia di un modello di data mining risulta utile quando si desidera creare rapidamente diversi modelli di data mining basati sugli stessi dati. Dopo aver copiato il modello, è possibile modificare la nuova copia modificando i parametri o aggiungendo un filtro.  
  
 Se ad esempio si dispone di una tabella Customers collegata a una tabella di acquisti, è possibile creare copie per generare modelli di data mining separati in base ai dati demografici di ogni cliente, filtrando in base ad attributi quali età o area geografica.  
  
 Per informazioni sulla copia negli Appunti del contenuto del modello, ad esempio rappresentazione grafica o schemi del modello, per l'uso in altri programmi, vedere [Copiare una vista di un modello di data mining](../../analysis-services/data-mining/copy-a-view-of-a-mining-model.md).  
  
### <a name="to-create-a-related-mining-model"></a>Per creare un modello di data mining correlato  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Esplora soluzioni, fare clic sulla struttura di data mining che contiene il modello di data mining.  
  
2.  Fare clic sulla scheda **Modelli di data mining** .  
  
3.  Selezionare il modello, quindi fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida.  
  
     -oppure-  
  
     Selezionare il modello. Scegliere **Nuovo modello di data mining** dal menu **Modello di data mining**.  
  
4.  Digitare un nome per il nuovo modello di data mining e selezionare un algoritmo. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a>Per modificare il filtro sul modello di data mining copiato  
  
1.  Selezionare il modello di data mining.  
  
2.  Nella finestra **Proprietà** fare clic nella casella di testo relativa alla proprietà **Filtro** , quindi sul pulsante di compilazione **(…)** .  
  
3.  Cambiare le condizioni di filtro.  
  
     Per altre informazioni sull'uso delle finestre di dialogo Editor filtri, vedere [Applicare un filtro a un modello di data mining](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md).  
  
4.  Nella finestra **Proprietà** , nella casella di testo **Parametri algoritmo** , fare clic su **Impostare i parametri per l'algoritmo**e modificare i parametri dell'algoritmo, se lo si desidera.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Filtri per i modelli di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Eliminare un filtro da un modello di data mining](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  