---
title: Unione di dati tramite l'unione trasformazione tutti | Documenti Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merging datasets [Integration Services]
- merging inputs [Integration Services]
- combining datasets
- Union All transformation
- datasets [Integration Services], merging
ms.assetid: 78304403-a81c-4101-b87e-ec80ddfdac98
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b2f9933f48083b0849ba01312979911bacb4fd86
ms.contentlocale: it-it
ms.lasthandoff: 08/03/2017

---
# <a name="merge-data-by-using-the-union-all-transformation"></a>Unione di dati tramite la trasformazione Unione input multipli
  È possibile aggiungere e configurare una trasformazione Unione input multipli solo se il pacchetto include già almeno un'attività Flusso di dati e due origini dati.  
  
 La trasformazione Unione input multipli consente di combinare più input. Il primo input connesso alla trasformazione è l'input di riferimento, mentre gli input connessi successivamente sono gli input secondari. L'output include le colonne dell'input di riferimento.  
  
### <a name="to-combine-inputs-in-a-data-flow"></a>Per combinare più input in un flusso di dati  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]fare doppio clic sul pacchetto in Esplora soluzioni per aprire il pacchetto in Progettazione [!INCLUDE[ssIS](../../../includes/ssis-md.md)] e quindi fare clic sulla scheda **Flusso di dati** .  
  
2.  Dalla **casella degli strumenti**trascinare la trasformazione Unione input multipli all'area di progettazione della scheda **Flusso di dati** .  
  
3.  Connettere la trasformazione Unione input multipli al flusso di dati trascinando un connettore dall'origine dati o da una trasformazione precedente alla trasformazione Unione input multipli.  
  
4.  Fare doppio clic sulla trasformazione Unione input multipli.  
  
5.  In **Editor trasformazione Unione input multipli** eseguire il mapping di una colonna dell'input a una colonna nell'elenco **Nome colonna di output**, facendo clic su una riga e quindi selezionando una colonna nell'elenco degli input. Selezionare  **\<ignorare >** nell'elenco di input per ignorare il mapping della colonna.  
  
    > [!NOTE]  
    >  Il mapping tra due colonne può essere eseguito solo se i relativi metadati corrispondono.  
  
    > [!NOTE]  
    >  Le colonne degli input secondari di cui non è stato eseguito il mapping alle colonne di riferimento, nell'output vengono impostate su valori Null.  
  
6.  Facoltativamente, modificare i nomi delle colonne nell'elenco **Nome colonna di output** .  
  
7.  Ripetere i passaggi 5 e 6 per ogni colonna di ogni input.  
  
8.  Scegliere **OK**.  
  
9. Per salvare il pacchetto aggiornato, scegliere **Salva elementi selezionati** dal menu **File** .  
  
## <a name="see-also"></a>Vedere anche  
 [Union All Transformation](../../../integration-services/data-flow/transformations/union-all-transformation.md)   
 [Trasformazioni di Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Percorsi in Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Attività flusso di dati](../../../integration-services/control-flow/data-flow-task.md)  
  
  