---
title: Recuperare i file | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- version control services [SQL Server], file retrieval
- file retrieval [SQL Server]
- retrieving files
ms.assetid: 37b74426-e262-43b2-a81f-79b1fd1a36ec
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 548fac7dbc7d1f2750a130da9847be406361d8bf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843667"
---
# <a name="retrieve-files"></a>Recupero di file
  Dopo aver aperto un progetto incluso nel controllo del codice sorgente, è possibile utilizzare [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] per recuperare le copie locali dei file di progetto dall'archivio del controllo del codice sorgente e salvarle nella directory locale in cui si trova il progetto.  
  
 È possibile utilizzare il controllo del codice sorgente integrato per recuperare i file nei modi seguenti:  
  
-   **Leggi ultima versione (ricorsivo)** comando  
  
     Consente di recuperare l'ultima versione archiviata dei file selezionati. Se viene selezionata una soluzione o un progetto, questo comando consente di recuperare l'ultima versione di tutti i file della soluzione o del progetto.  
  
-   **Ottenere** comando  
  
     Consente di visualizzare il **ottenere** nella finestra di dialogo è possibile usare per recuperare la versione più recente di un file selezionato o per recuperare un subset dei file nella soluzione selezionata o nel progetto.  
  
### <a name="to-retrieve-the-latest-version-of-all-the-files-in-a-project"></a>Per recuperare l'ultima versione di tutti i file in un progetto  
  
1.  In Esplora soluzioni selezionare il progetto desiderato.  
  
2.  Nel **File** dal menu **controllo del codice sorgente**, quindi fare clic su **Leggi ultima versione (ricorsivo)**.  
  
 Le versioni più recenti dei file nel progetto verranno recuperate nel percorso del progetto sul disco locale.  
  
#### <a name="to-retrieve-only-certain-files-in-a-project"></a>Per recuperare solo alcuni file in un progetto  
  
1.  In Esplora soluzioni selezionare l'elemento che si desidera recuperare.  
  
2.  Nel **File** dal menu **controllo del codice sorgente**, quindi fare clic su **ottenere**.  
  
3.  Nel **ottenere** finestra di dialogo, fare clic su **OK**. In alternativa, se in Esplora soluzioni è stato selezionato un progetto o una soluzione, deselezionare le caselle di controllo accanto agli elementi che non si desidera recuperare.  
  
## <a name="see-also"></a>Vedere anche  
 [Ottenere la finestra di dialogo &#40;controllo del codice sorgente&#41;](../../2014/database-engine/get-dialog-box-source-control.md)   
 [Impostare e recuperare le informazioni sulla versione](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [Visualizzare cronologia progetti](../../2014/database-engine/view-project-history.md)   
 [Visualizzazione dello stato dei file](../../2014/database-engine/view-file-status.md)  
  
  
