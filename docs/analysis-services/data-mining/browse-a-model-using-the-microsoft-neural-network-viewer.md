---
title: Visualizzare un modello utilizzando il visualizzatore Microsoft Neural Network | Documenti Microsoft
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
- mining model content, viewing
- classification mining model [Analysis Services]
- Microsoft Neural Network Viewer
- regression algorithms [Analysis Services]
- Neural Network Viewer [Analysis Services]
- neural network model [Analysis Services]
ms.assetid: 2343d746-c4f4-499b-9d3c-17d63310a9a3
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fea303682881b5cb660dbdc7b5c411dc0880ef4e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="browse-a-model-using-the-microsoft-neural-network-viewer"></a>Visualizzare un modello utilizzando il Visualizzatore Microsoft Neural Network
  Il Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network disponibile in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di visualizzare i modelli di data mining compilati con l'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network. L'algoritmo [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network, che consente di creare modelli di data mining di classificazione e regressione in grado di analizzare più input e output, è molto utile a scopo di analisi ed esplorazione. Per ulteriori informazioni su questo algoritmo, vedere [Microsoft Neural Network Algorithm](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md).  
  
 Quando si esplora un modello utilizzando il Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network Viewer, si sceglie in genere un attributo di destinazione e uno stato, quindi si utilizza il visualizzatore per determinare in che modo gli attributi di input influiscono sul risultato.  
  
 Si supponga ad esempio di conoscere questi fatti su una classe di clienti potenziali:  
  
-   Età media (dai 40 ai 50 anni).  
  
-   Possiede una casa.  
  
-   Ha due figli che vivono ancora a casa.  
  
 Come correlare questi attributi alla probabilità che il cliente effettuerà un acquisto?  
  
 Compilando un modello di rete neurale utilizzando il comportamento di acquisto come risultato, è possibile esplorare più combinazioni sugli attributi del cliente, ad esempio il reddito elevato, e individuare quale combinazione di attributi influirà con maggiore probabilità sul comportamento di acquisto. È ad esempio possibile accertare che il fattore determinante è la distanza che devono percorrere per recarsi al lavoro.  
  
 Per visualizzare informazioni più dettagliate, ad esempio le equazioni che rappresentano ogni modello individuato, è possibile cambiare vista e utilizzare il visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Generic Content Tree. Per altre informazioni, vedere [Visualizzare un modello usando Microsoft Generic Content Tree Viewer](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md) o [Microsoft Generic Content Tree Viewer &#40;Data mining&#41;](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c).  
  
##  <a name="BKMK_ViewerTabs"></a> Schede del visualizzatore  
 Per la visualizzazione di un modello di data mining in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]viene utilizzato il visualizzatore appropriato nella scheda **Visualizzatore modello di data mining** di Progettazione modelli di data mining. Per l'esplorazione dei modelli di data mining della rete neurale, nel Visualizzatore [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network sono disponibili le schede seguenti:  
  
-   [Input](#BKMK_Inputs)  
  
-   [Output](#BKMK_Outputs)  
  
-   [Variabili](#BKMK_Characteristics)  
  
###  <a name="BKMK_Inputs"></a> Input  
 Usare la scheda **Input** per scegliere gli attributi e i valori che verranno usati come input dal modello. Per impostazione predefinita, il visualizzatore viene aperto con tutti gli attributi. In questa vista predefinita, il modello sceglie quali valori di attributo sono quelli più importanti da visualizzare.  
  
 Per selezionare un attributo di input, fare clic all'interno della colonna **Attributo** della griglia **Input** e selezionare un attributo nell'elenco a discesa. Nell'elenco sono inclusi solo gli attributi del modello.  
  
 Il primo valore distinto viene visualizzato nella colonna **Valore** . Se si fa clic sul valore predefinito, viene visualizzato un elenco contenente tutti gli stati possibili dell'attributo associato. È possibile selezionare lo stato che si intende esaminare e il numero di attributi desiderato.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Outputs"></a> Output  
 Usare la scheda **Output** per scegliere l'attributo risultante da esaminare. È possibile scegliere due stati del risultato qualsiasi da confrontare, presupponendo che le colonne siano state definite come attributi stimabili alla creazione del modello.  
  
 Per selezionare un attributo, usare l'elenco **OutputAttribute** . Successivamente, è possibile selezionare due stati associati all'attributo dagli elenchi **Valore 1** e **Valore 2** . Questi due stati dell'attributo di output verranno confrontati nel riquadro **Variabili** .  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Characteristics"></a> Variabili  
 La griglia della scheda **Variabili** contiene le colonne seguenti: **Attributo**, **Valore**, **Predilige [valore 1]**e **Predilige [valore 2]**. Per impostazione predefinita, le colonne vengono ordinate in base al valore di **Predilige [valore 1]**. Se si fa clic su un'intestazione di colonna, viene modificato l'ordinamento della colonna selezionata.  
  
 Una barra a destra dell'attributo indica lo stato dell'attributo di output prediletto dallo stato dell'attributo di input specificato. La dimensione della barra indica in quale misura lo stato di input è prediletto dallo stato di output.  
  
 [Torna all'inizio](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>Vedere anche  
 [Microsoft Neural Network Algorithm](../../analysis-services/data-mining/microsoft-neural-network-algorithm.md)   
 [Attività e procedure relative al visualizzatore modello di data mining](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Attività e procedure relative al visualizzatore modello di data mining](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Strumenti di data mining](../../analysis-services/data-mining/data-mining-tools.md)   
 [Visualizzatori modello di data mining](../../analysis-services/data-mining/data-mining-model-viewers.md)  
  
  