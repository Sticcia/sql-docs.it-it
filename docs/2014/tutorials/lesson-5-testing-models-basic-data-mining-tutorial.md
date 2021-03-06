---
title: 'Lezione 5: Test di modelli (esercitazione di base di Data Mining) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9a7ddcf-2b01-485f-bbb5-62638b303bc6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 88a9d564b297d277d1566152cc11599bec912ddc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63185437"
---
# <a name="lesson-5-testing-models-basic-data-mining-tutorial"></a>Lezione 5: Test di modelli (esercitazione di base di Data Mining)
  Ora che è stato elaborato il modello tramite il set di training dello scenario relativo al mailing diretto, verranno testati i modelli sul set di testing. La convalida è un passaggio importante del processo di data mining. Prima di distribuire i modelli per il mailing diretto in un ambiente di produzione, è fondamentale verificarne il comportamento in caso di applicazione ai dati real.  
  
 Poiché i dati nel set di testing contengono già valori noti per l'acquisto di biciclette, la correttezza delle stime del modello può essere determinata facilmente. Verrà utilizzato il modello che offre le prestazioni migliori per il [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] reparto marketing per identificare i clienti per la campagna di mailing diretto.  
  
 In questa lezione verranno convalidati i modelli utilizzando più metodi:  
  
1.  Verranno apportate le stime sul set di testing per visualizzare il modello e valutare l'accuratezza è su risultati noti. Si userà una *grafico di accuratezza* per misurarne l'efficacia.  
  
     [Test dell'accuratezza con i grafici di accuratezza &#40;Esercitazione di base sul data mining&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
2.  I modelli verranno quindi testati su un subset filtrato dei dati. Sarà possibile confrontare più modelli nello stesso grafico di accuratezza.  
  
     [Test di un modello filtrato &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
 Per altre informazioni sulla convalida dei modelli in generale, vedere [concetti di Data Mining](../../2014/analysis-services/data-mining/data-mining-concepts.md).  
  
## <a name="first-task-in-lesson"></a>Prima attività della lezione  
 [Test dell'accuratezza con i grafici di accuratezza &#40;Esercitazione di base sul data mining&#41;](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a>Lezione precedente  
 [Lezione 4: Esplorazione dei modelli di Mailing diretto &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a>Lezione successiva  
 [Lezione 6: Creazione e utilizzo di stime &#40;esercitazione di base di Data Mining&#41;](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Scheda grafico di accuratezza &#40;visualizzazione Grafico accuratezza di Data Mining&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)   
 [Grafico di accuratezza &#40;Analysis Services - Data mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)   
 [Test e convalida &#40;Data mining&#41;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md)   
 [Scheda matrice di classificazione &#40;visualizzazione Grafico accuratezza di Data Mining&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md)   
 [Matrice di classificazione &#40;Analysis Services - Data mining&#41;](../../2014/analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)  
  
  
