---
title: Creare una copia di un modello di Data Mining | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7c5479a43a07a6398ff45635828a2a9c88b7cb11
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62679466"
---
# <a name="make-a-copy-of-a-mining-model"></a>Eseguire una copia di un modello di data mining
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La creazione di una copia di un modello di data mining risulta utile quando si desidera creare rapidamente diversi modelli di data mining basati sugli stessi dati. Dopo aver copiato il modello, è possibile modificare la nuova copia modificando i parametri o aggiungendo un filtro.  
  
 Se ad esempio si dispone di una tabella Customers collegata a una tabella di acquisti, è possibile creare copie per generare modelli di data mining separati in base ai dati demografici di ogni cliente, filtrando in base ad attributi quali età o area geografica.  
  
 Per informazioni sulla copia negli Appunti del contenuto del modello, ad esempio rappresentazione grafica o schemi del modello, per l'uso in altri programmi, vedere [Copiare una vista di un modello di data mining](../../analysis-services/data-mining/copy-a-view-of-a-mining-model.md).  
  
### <a name="to-create-a-related-mining-model"></a>Per creare un modello di data mining correlato  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in Esplora soluzioni, fare clic sulla struttura di data mining che contiene il modello di data mining.  
  
2.  Fare clic sulla scheda **Modelli di data mining** .  
  
3.  Selezionare il modello, quindi fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida.  
  
     oppure  
  
     Selezionare il modello. Scegliere **Nuovo modello di data mining** dal menu **Modello di data mining**.  
  
4.  Digitare un nome per il nuovo modello di data mining e selezionare un algoritmo. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a>Per modificare il filtro sul modello di data mining copiato  
  
1.  Selezionare il modello di data mining.  
  
2.  Nel **delle proprietà** finestra, fare clic sulla casella di testo per il **filtro** proprietà, quindi scegliere la compilazione **(...)**  pulsante.  
  
3.  Cambiare le condizioni di filtro.  
  
     Per altre informazioni sull'uso delle finestre di dialogo Editor filtri, vedere [Applicare un filtro a un modello di data mining](../../analysis-services/data-mining/apply-a-filter-to-a-mining-model.md).  
  
4.  Nella finestra **Proprietà** , nella casella di testo **Parametri algoritmo** , fare clic su **Impostare i parametri per l'algoritmo**e modificare i parametri dell'algoritmo, se lo si desidera.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Filtri per i modelli di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)   
 [Attività e procedure relative al modello di data mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Eliminare un filtro da un modello di data mining](../../analysis-services/data-mining/delete-a-filter-from-a-mining-model.md)  
  
  
