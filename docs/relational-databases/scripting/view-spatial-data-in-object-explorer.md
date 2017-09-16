---
title: Visualizzare dati spaziali in Esplora oggetti | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
caps.latest.revision: 8
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c5757bcb84f441e81f3da7b91e6acf449696cc30
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="view-spatial-data-in-object-explorer"></a>Visualizzazione di dati spaziali in Esplora oggetti
  La finestra **Risultati spaziali** dell'editor di query fornisce strumenti di mapping visivo per la visualizzazione di risultati di dati spaziali in aggiunta alla visualizzazione dei dati in formato griglia nella finestra **Risultati** . Per visualizzare i dati spaziali nella finestra **Risultati spaziali** , i risultati delle query devono contenere almeno una colonna di dati spaziali con dati geometrici e geografici.  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>Per visualizzare i dati spaziali nella finestra Risultati spaziali  
  
1.  Nell'editor di query fare clic sulla scheda **Risultati spaziali** .  
  
    > [!NOTE]  
    >  Questa finestra non è disponibile se i risultati delle query non contengono dati spaziali o si richiede la restituzione dei risultati come testo.  
  
2.  Selezionare la colonna che si desidera visualizzare nell'elenco **Selezionare la colonna spaziale** . Se la tabella contiene una sola colonna spaziale, questa sarà l'opzione predefinita dell'elenco.  
  
3.  Selezionare la colonna non spaziale che si vuole usare come etichette dei dati nell'elenco **Selezionare la colonna etichetta** .  
  
4.  Selezionare la proiezione desiderata per i dati geografici nell'elenco **Selezionare la proiezione** . La proiezione predefinita è Equirectangular. Le altre proiezioni disponibili sono Mercator, Robinson e Bonne.  
  
    > [!NOTE]  
    >  **Selezionare la proiezione** non è disponibile se la colonna spaziale contiene dati geometrici.  
  
5.  Regolare il dispositivo di scorrimento **Zoom** per aumentare la dimensione visiva degli elementi di cui è stato eseguito il mapping. Per le forme poligonali, l'etichetta è visibile solo se la forma è grande abbastanza da contenere il testo dell'etichetta.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra Risultati spaziali](../../relational-databases/scripting/spatial-results-window.md)   
 [Editor di query del Motore di database &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Editor di query e di testo &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  