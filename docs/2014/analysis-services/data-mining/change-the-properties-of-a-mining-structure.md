---
title: Modificare le proprietà di una struttura di Data Mining | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], properties
ms.assetid: 03b16897-2e36-42b8-9f7d-db1b9b898401
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 56942ebc74e1a0b49303f842ec2668a46f6f209f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62689342"
---
# <a name="change-the-properties-of-a-mining-structure"></a>Modificare le proprietà di una struttura di data mining
  Sono disponibili due tipi di proprietà su una struttura di data mining, entrambi modificabili:  
  
-   Proprietà della struttura di data mining che influiscono sull'intera struttura  
  
-   Proprietà su singole colonne della struttura  
  
 Si noti che alcune proprietà dipendono da altre impostazioni di proprietà. Non è ad esempio possibile impostare le proprietà che controllano la creazione di contenitori, ad esempio <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationMethod%2A> o <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> finché non viene impostato il tipo di dati della colonna su `Discretized`.  
  
 Per altre informazioni sulle proprietà di data mining, vedere [Colonne della struttura di data mining](mining-structure-columns.md).  
  
### <a name="to-change-the-properties-of-a-mining-structure"></a>Per modificare le proprietà di una struttura di data mining  
  
1.  Nella scheda **Struttura di data mining** di Progettazione modelli di data mining fare clic con il pulsante destro del mouse sulla struttura di data mining o su una colonna della struttura e quindi scegliere **Proprietà**.  
  
     A destra dello schermo verrà visualizzata la finestra **Proprietà** , se non è già visualizzata.  
  
2.  Nella finestra **Proprietà** selezionare il valore corrispondente alla proprietà che si vuole modificare e quindi immettere il nuovo valore.  
  
     Il nuovo valore diventerà effettivo quando si seleziona un elemento diverso nella finestra di progettazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative alla struttura di data mining](mining-structure-tasks-and-how-tos.md)  
  
  
