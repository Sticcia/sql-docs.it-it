---
title: Attributi (scheda struttura dimensione, progettazione dimensioni) (Analysis Services - dati multidimensionali) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.attributespane.f1
ms.assetid: 627eaa08-7638-4edd-bdfa-0d8175a7cde5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 522bffc53240a7456ee77911b4f3044ffe0f231c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62650847"
---
# <a name="attributes-dimension-structure-tab-dimension-designer-analysis-services---multidimensional-data"></a>Attributi (scheda Struttura dimensione, Progettazione dimensioni) (Analysis Services – Dati multidimensionali)
  Utilizzare questo riquadro per gestire gli attributi associati alla dimensione selezionata. È possibile trascinare gli attributi da questo riquadro al riquadro **Gerarchie** per creare gerarchie e livelli. Per altre informazioni, vedere [Hierarchies &#40;Dimension Structure Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](hierarchies-dimension-designer-analysis-services-multidimensional-data.md).  
  
 Per creare un attributo trascinare una colonna dal riquadro **Vista origine dati** al riquadro **Attributi** mentre è attiva la modalità Elenco, Albero o Griglia. Per rimuovere un attributo scegliere **Elimina** dal menu di scelta rapida.  
  
 **Per visualizzare il riquadro attributi**  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]aprire il progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , quindi aprire la dimensione che si desidera utilizzare.  
  
2.  Se non è selezionata, fare clic sulla scheda **Struttura dimensione** .  
  
## <a name="options"></a>Opzioni  
 **Attributi**  
 Consente di visualizzare gli attributi disponibili nella dimensione selezionata. È possibile visualizzare questa opzione nelle modalità seguenti:  
  
-   Modalità Elenco  
  
     Utilizzare questa modalità per creare e modificare gerarchie. Per visualizzare gli attributi in modalità Elenco, scegliere **Mostra attributi in** dal menu di scelta rapida, quindi fare clic su **Elenco**.  
  
-   Modalità Albero  
  
     Utilizzare questa modalità per creare e modificare gerarchie. Per visualizzare gli attributi in modalità Albero, scegliere **Mostra attributi in** dal menu di scelta rapida, quindi fare clic su **Albero**.  
  
-   Modalità Griglia  
  
     Utilizzare questa modalità per creare dimensioni in modo manuale o modificare proprietà degli attributi. Per visualizzare gli attributi in modalità Griglia, scegliere **Mostra attributi** sul menu di scelta rapida, quindi fare clic su **Griglia**.  
  
## <a name="grid-mode-options"></a>Opzioni modalità Griglia  
 Quando gli attributi vengono visualizzati in modalità Griglia, è possibile accedere alle colonne elencate nella tabella seguente.  
  
 **Name**  
 Consente di visualizzare il nome dell'attributo.  
  
 **Usage**  
 Consente di impostare l'utilizzo dell'attributo selezionato. Fare clic sulla freccia rivolta verso il basso per selezionare un valore tra quelli disponibili:  
  
|Value|Descrizione|  
|-----------|-----------------|  
|Regular|Identifica un attributo regolare.|  
|Chiave|Identifica l'attributo chiave per la dimensione. Corrisponde ai membri foglia della dimensione. Per ogni dimensione può esistere un solo attributo chiave. Per apportare modifiche fare clic sul pulsante con i puntini di sospensione (**...**) accanto alla proprietà **KeyColumns** nel riquadro **Proprietà** .|  
|Parent|Indica l'attributo padre per una relazione padre-figlio. L'attributo figlio in questa relazione deve essere sempre l’attributo chiave.|  
|AccountType|Indica un attributo di tipo Conto. Viene utilizzato dal server o dal motore quando la funzione di aggregazione per una misura è impostata su "ByAccount".|  
  
 **Tipo**  
 Consente di impostare il tipo di attributo. Fare clic sulla freccia rivolta verso il basso per selezionare un’impostazione fra quelle disponibili:  
  
 **Colonna chiave**  
 Consente di visualizzare il tipo di dati delle colonne sottostanti. Quando si crea un nuovo attributo, fare clic sulla freccia rivolta verso il basso per selezionare un'impostazione tra quelle disponibili.  
  
 **Nome colonna**  
 Consente di visualizzare la posizione della colonna sottostante. Quando si crea un nuovo attributo, fare clic sulla freccia rivolta verso il basso per scegliere tra **Uguale alla chiave** e **Colonna separata**. Se si sceglie **Colonna separata** , la proprietà **NameColumn** nel riquadro **Proprietà** imposta la colonna in cui viene archiviato il nome da utilizzare per l'attributo.  
  
## <a name="see-also"></a>Vedere anche  
 [Struttura dimensione &#40;progettazione dimensioni&#41; &#40;Analysis Services - dati multidimensionali&#41;](dimension-structure-dimension-designer-analysis-services-multidimensional-data.md)   
 [Gerarchie di &#40;scheda struttura dimensione, progettazione dimensioni&#41; &#40;Analysis Services - dati multidimensionali&#41;](hierarchies-dimension-designer-analysis-services-multidimensional-data.md)   
 [Sulla barra degli strumenti &#40;scheda struttura dimensione, progettazione dimensioni&#41; &#40;Analysis Services - dati multidimensionali&#41;](toolbar-dimension-structure-designer-analysis-services-multidimensional-data.md)  
  
  
