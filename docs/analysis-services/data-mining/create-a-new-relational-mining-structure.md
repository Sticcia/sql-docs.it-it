---
title: Creare una nuova struttura di Data Mining relazionale | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mining structures [Analysis Services], relational
- mining structures [Analysis Services], creating
- relational mining models [Analysis Services]
ms.assetid: 55bac3bd-700e-4f91-bcc6-f3cd8c026da1
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6784d7ab5e13d5e842794041589db515a6fd2a30
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-new-relational-mining-structure"></a>Creare una nuova struttura di data mining relazionale
  Usare la Creazione guidata modello di data mining per creare una nuova struttura di data mining che usa dati da un database relazionale o da un'altra origine, quindi salvare la struttura ed eventuali modelli correlati in un database di [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
## <a name="to-create-a-relational-mining-structure"></a>Per creare una struttura di data mining relazionale  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sulla cartella **Strutture di data mining** in un progetto di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , quindi scegliere **Nuova struttura di data mining**.  
  
     Verrà avviata la Creazione guidata modello di data mining.  
  
2.  Nella pagina iniziale **Creazione guidata modello di data mining** fare clic su **Avanti**.  
  
3.  Nella pagina **Selezione metodo di definizione** selezionare **Da database relazionale o data warehouse esistente**, quindi fare clic su **Avanti**.  
  
4.  Nella pagina **Select the Data Mining Technique** (Selezione di una tecnica di data mining) selezionare l'algoritmo di data mining che si desidera usare, quindi fare clic su **Avanti**.  
  
     Per altre informazioni sugli algoritmi di data mining, vedere [Algoritmi di data mining &#40;Analysis Services - Data mining&#41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md).  
  
5.  Nella pagina **Selezione vista origine dati** in **Viste origine dati disponibili** fare clic sulla vista origine dati che si desidera usare, quindi su **Avanti**.  
  
     Per altre informazioni sulla creazione di una vista origine dati, vedere [Viste origine dati in modelli multidimensionali](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md).  
  
6.  Nella pagina **Impostazione tipi di tabelle** in **Tabelle di input**selezionare una tabella del case e una tabella annidata.  
  
7.  Nella pagina **Impostazione dati di training** in **Struttura modello di data mining**selezionare le colonne chiave, di input e stimabile.  
  
     Dopo avere selezionato la colonna stimabile, è possibile fare clic sul pulsante **Suggerisci** per visualizzare la finestra di dialogo **Suggerisci colonne correlate** . È possibile accettare le colonne suggerite facendo clic su **OK** in questa finestra di dialogo per includere le colonne selezionate nella struttura di data mining oppure modificare le selezioni nella colonna **Input** , quindi fare clic su **OK**. Per ignorare i suggerimenti, fare clic su **Annulla**.  
  
8.  Scegliere **Avanti**.  
  
9. Nella pagina **Impostazione tipo di contenuto e dati delle colonne** in **Struttura modello di data mining**è possibile modificare il tipo di contenuto e di dati per ogni colonna.  
  
    > [!NOTE]  
    >  È possibile fare clic su **Rileva** per rilevare automaticamente se una colonna contiene dati continui o discreti. Dopo avere fatto clic su questo pulsante, i tipi di contenuto e di dati verranno aggiornati nelle colonne **Tipo di contenuto** e **Tipo di dati**. Per altre informazioni sui tipi di contenuto e i tipi di dati, vedere [Tipi di contenuto &#40;Data mining&#41;](../../analysis-services/data-mining/content-types-data-mining.md) e [Tipi di dati &#40;data mining&#41;](../../analysis-services/data-mining/data-types-data-mining.md).  
  
10. Scegliere **Avanti**.  
  
11. Nella pagina **Completamento procedura guidata** specificare un nome per la struttura di data mining e per il modello di data mining iniziale correlato di cui verrà eseguita la creazione, quindi fare clic su **Fine**.  
  
## <a name="see-also"></a>Vedere anche  
 [Attività e procedure relative alla struttura di data mining](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  