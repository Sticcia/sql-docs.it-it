---
title: Aggiungere un parametro multivalore a un Report | Documenti Microsoft
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1df54edd5857ac2816fa4b164d268835d9713638
ms.openlocfilehash: 44d81cbf6e89d5e3a387f3660417195fdb17c7dd
ms.contentlocale: it-it
ms.lasthandoff: 09/12/2017

---
# <a name="add-a-multi-value-parameter-to-a-report"></a>Aggiunta di un parametro multivalore a un report
  È possibile aggiungere un parametro a un report che consente all'utente di selezionare più valori per il parametro.  
  
 È possibile passare più valori di parametro al report nell'URL del report. Per un esempio di URL in cui è incluso un parametro multivalore, vedere [Passare un parametro del report in un URL](../../reporting-services/pass-a-report-parameter-within-a-url.md).  
  
 Per informazioni su come passare più valori di parametro a una stored procedure, vedere [Working With Multi-Select Parameters for SSRS Reports](http://go.microsoft.com/fwlink/?LinkId=321529) (Utilizzo di parametri a selezione multipla per report SSRS) nel sito Web mssqltips.com.  
  
## <a name="to-add-a-multi-value-parameter"></a>Per aggiungere un parametro multivalore  
  
1.  In Generatore report aprire il report a cui si desidera aggiungere il parametro multivalore.  
  
2.  Fare clic con il pulsante destro del mouse sul set di dati del report e quindi scegliere **Proprietà set di dati**.  
  
3.  Aggiungere una variabile alla query del set di dati modificando il testo della query nella casella **Query** o aggiungendo un filtro mediante la finestra Progettazione query. Per ulteriori informazioni, vedere [compila una Query in Progettazione Query relazionale &#40; Generatore report e SSRS &#41; ](../../reporting-services/report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md).  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    > *  Il testo della query non deve includere l'istruzione DECLARE per la variabile di query.  
    > *  Il testo per la variabile di query deve includere l'operatore **IN** , come mostrato nell'esempio precedente.  
    > *  Assicurarsi di racchiudere la variabile tra parentesi, come mostrato sopra. In caso contrario, il rendering del report non viene eseguito e viene visualizzato il messaggio di errore "Dichiarare la variabile scalare".  
  
    Un parametro del set di dati per un set di dati incorporato o un set di dati condiviso viene creato automaticamente per la variabile di query. Un parametro del report viene creato automaticamente per il parametro del set di dati.  
  
4.  Nel riquadro **Dati report** espandere il nodo **Parametri** , fare clic con il pulsante destro del mouse sul parametro del report che è stato creato automaticamente per il parametro del set di dati e quindi scegliere **Proprietà parametri**.  
  
5.  Nella scheda **Generale** selezionare **Consenti più valori** per consentire a un utente di selezionare più valori per il parametro.  
  
6.  Facoltativamente, nella scheda dei valori **Disponibile** specificare un elenco di valori disponibili da visualizzare all'utente.  
  
     Tale elenco limita le scelte dell'utente ai soli valori validi per il parametro. Per più valori, la funzionalità **Seleziona tutto** è disponibile all'inizio dell'elenco, in modo che l'utente possa selezionare o deselezionare tutti i valori con un solo clic. Se si sceglie di ottenere i valori disponibili per il parametro del report da una query del set di dati, assicurarsi di selezionare un set di dati che non contenga la variabile di query associata allo stesso parametro del report.  
  
     Per ulteriori informazioni, vedere [aggiungere, modificare o eliminare valori disponibili per un parametro di Report &#40; Generatore report e SSRS &#41; ](../../reporting-services/report-design/add-change-or-delete-available-values-for-a-report-parameter.md).  

## <a name="see-also"></a>Vedere anche  
 [Aggiunta di parametri di propagazione a un report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Aggiungere, modificare o eliminare un parametro di report &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  
