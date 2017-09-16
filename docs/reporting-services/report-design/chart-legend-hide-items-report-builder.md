---
title: Nascondere elementi legenda nel grafico (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: 92256240-0cd5-4be4-8904-d1e3b93cb6b3
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 06f1cf8cde2eb9a9c9aa261188e64aa2fc7afe4b
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="chart-legend---hide-items-report-builder"></a>Legenda del grafico - Nascondi elementi (Generatore Report)
Per impostazione predefinita, qualsiasi serie aggiunta a un grafico senza forme in un report impaginato di [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] verrà aggiunta come elemento nella legenda. Per grafici a torta, ad anello, a imbuto e a piramide, qualsiasi serie aggiunta al grafico determina l'aggiunta di punti dati singoli nella legenda.  
  
 È possibile nascondere qualsiasi elemento della legenda. Quando si nasconde un elemento della legenda, questo rimane comunque visualizzato nel grafico. Ciò si rivela utile nelle situazioni in cui non si desidera mostrare ulteriori informazioni per una serie aggiunta al grafico. Se ad esempio è stata aggiunta una serie calcolata come una media mobile al grafico, potrebbe essere necessario nascondere questa voce nella legenda in modo che vengano mostrate informazioni aggiuntive solo per la serie originale.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-hide-an-item-from-display-in-the-legend"></a>Per nascondere un elemento visualizzato nella legenda  
  
1.  Fare clic con il pulsante destro del mouse sulla serie da nascondere e scegliere **Proprietà serie**.  
  
2.  Fare clic su **Legenda**. Selezionare l'opzione **Non mostrare questa serie in una legenda** .  
  
    > [!NOTE]  
    >  Non è possibile nascondere una serie per un solo gruppo. Se è stato aggiunto un campo all'area **Gruppi di serie** , verranno nascoste tutte le serie che appartengono a questo gruppo.  
  
## <a name="see-also"></a>Vedere anche  
 [Formattazione della legenda in un grafico &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/chart-legend-formatting-report-builder.md)   
 [Formattazione dei punti dati in un grafico &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/formatting-data-points-on-a-chart-report-builder-and-ssrs.md)   
 [Modificare il testo di un elemento della legenda &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/chart-legend-change-item-text-report-builder.md)   
 [Aggiungere una media mobile per un grafico &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)   
 [Finestra di dialogo Proprietà legenda, generale &#40; Generatore report e SSRS &#41;](http://msdn.microsoft.com/library/db718f8f-f185-422f-871c-96f0749e5893)  
  
  