---
title: Formattazione di intervalli su un misuratore (Generatore Report e SSRS) | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffdec8ca-3e95-41cd-850b-9e8c83be4b49
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a4c28739a1b35655f74a16a6757958e0e1bc6e47
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="formatting-ranges-on-a-gauge-report-builder-and-ssrs"></a>Formattazione di intervalli su un misuratore (Generatore report e SSRS)
 In un report impaginato di [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] , l'intervallo del misuratore è un'area sulla scala del misuratore tramite cui viene indicata un'importante sottosezione dei valori sul misuratore. L'uso di un intervallo del misuratore consente di indicare visivamente quando il valore dell'indicatore di misura rientra in un determinato intervallo di valori. Gli intervalli sono definiti da un valore iniziale e un valore finale.  
  
 È anche possibile utilizzare gli intervalli per definire le diverse sezioni di un misuratore. Su un misuratore con valori compresi tra 0 e 10 è ad esempio possibile definire un intervallo rosso contenente i valori da 0 a 3, un intervallo giallo contenente i valori da 4 a 7 e un intervallo verde contenente i valori da 8 a 10. Se il valore iniziale specificato è maggiore di quello finale specificato, i valori vengono scambiati in modo che quello iniziale diventi quello finale e viceversa.  
  
 È possibile posizionare l'intervallo con una procedura analoga a quella che consente di posizionare gli indicatori di misura su una scala. La posizione dell'intervallo dipende dalle proprietà **Posizione** e **Distanza dalla scala** . Per altre informazioni, vedere [Misuratori &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione di Scale su un misuratore &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Formattazione di indicatori di misura su un misuratore &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Impostare un valore minimo o massimo su un misuratore &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/set-a-minimum-or-maximum-on-a-gauge-report-builder-and-ssrs.md)   
 [Esercitazione: Aggiunta di un indicatore KPI per il Report &#40; Generatore report &#41;](../../reporting-services/tutorial-adding-a-kpi-to-your-report-report-builder.md)   
 [I misuratori &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/gauges-report-builder-and-ssrs.md)  
  
  