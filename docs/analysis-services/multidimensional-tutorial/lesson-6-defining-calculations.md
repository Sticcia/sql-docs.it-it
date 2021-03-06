---
title: 'Lezione 6: Definizione di calcoli | Microsoft Docs'
ms.date: 05/06/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5e4b4dbae844177fe121fcf1b22f4f6bf68c8584
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65403883"
---
# <a name="lesson-6-defining-calculations"></a>Lezione 6: Definizione di calcoli
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]

In questa lezione verranno descritte le procedure per definire calcoli, che sono espressioni MDX (Multidimensional Expressions) o script. I calcoli consentono di definire membri calcolati e set denominati, nonché di eseguire altri comandi script per estendere le capacità di un cubo di [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . È ad esempio possibile eseguire un comando script per definire un sottocubo e quindi assegnare un calcolo alle celle incluse nel sottocubo.  
  
Quando si definisce un nuovo calcolo in Progettazione cubi, il calcolo viene aggiunto al riquadro **Libreria script** della scheda **Calcoli** di Progettazione cubi e i campi relativi al tipo di calcolo specifico vengono visualizzati in un form di calcoli nel riquadro **Espressione** . L'esecuzione dei calcoli segue lo stesso ordine di visualizzazione all'interno del riquadro **Libreria script** . È possibile riordinare i calcoli facendo clic con il pulsante destro del mouse su un calcolo specifico e quindi scegliendo **Sposta su** o **Sposta giù**oppure facendo clic su un calcolo specifico e quindi facendo clic sull'icona **Sposta su** o **Sposta giù** nella barra degli strumenti della scheda **Calcoli** .  
  
Nella scheda **Calcoli** è possibile aggiungere nuovi calcoli e visualizzare o modificare calcoli esistenti in una delle due visualizzazioni seguenti del riquadro **Espressione** :  
  
-   Visualizzazione Form. Questa visualizzazione mostra le espressioni e le proprietà di un unico comando in formato grafico. Quando si modifica uno script MDX la visualizzazione Form viene riempita da una casella di espressione.  
  
-   Visualizzazione Script. Questa visualizzazione mostra tutti gli script di calcolo in un editor del codice, che consente di modificare facilmente gli script di calcolo. Quando il riquadro **Espressione** si trova nella visualizzazione Script, la **Libreria script** è nascosta. La visualizzazione Script offre codifica a colori, corrispondenza delle parentesi, completamento automatico e blocchi di codice MDX. I blocchi di codice MDX possono essere espanse o compresse per facilitare la modifica.  
  
Per passare tra queste visualizzazioni nel riquadro **Espressione** fare clic su **Visualizzazione Form** o **Visualizzazione Script** nella barra degli strumenti **Calcoli** .  
  
> [!NOTE]  
> Se [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] rileva un errore di sintassi in un calcolo, la visualizzazione Form non viene visualizzata finché l'errore non viene corretto nella visualizzazione Script.  
  
È inoltre possibile utilizzare la Configurazione guidata funzionalità di Business Intelligence per aggiungere determinati calcoli a un cubo. È possibile ad esempio utilizzare questa procedura guidata per aggiungere funzionalità di Business Intelligence per le gerarchie temporali, il che significa definire membri calcolati per calcoli temporali, ad esempio calcoli dei dati di un periodo rispetto alla data corrente, medie mobili o incremento tra periodi. Per altre informazioni [Definire calcoli delle funzionalità di Business Intelligence per le gerarchie temporali mediante la Configurazione guidata funzionalità di Business Intelligence](../multidimensional-models/define-time-intelligence-calculations-using-the-business-intelligence-wizard.md).  
  
> [!IMPORTANT]  
> Lo script di calcolo inizia con il comando CALCULATE nella scheda **Calcoli** . Il comando CALCULATE consente di controllare l'aggregazione delle celle del cubo e deve essere modificato solo se si desidera specificare manualmente la modalità di aggregazione delle celle del cubo.  
  
Per altre informazioni, vedere [Calcoli](../multidimensional-models-olap-logical-cube-objects/calculations.md)e [Calcoli nei modelli multidimensionali](../multidimensional-models/calculations-in-multidimensional-models.md).  
  
> [!NOTE]  
> I progetti completati per tutte le lezioni in questa esercitazione sono disponibili online. È possibile passare a qualsiasi lezione utilizzando il progetto completato della lezione precedente come punto iniziale. [Fare clic qui](http://go.microsoft.com/fwlink/?LinkID=221866) per scaricare i progetti di esempio usati in questa esercitazione.  
  
In questa lezione sono incluse le attività seguenti:  
  
[Definizione dei membri calcolati](lesson-6-1-defining-calculated-members.md)  
In questa attività vengono definiti i membri calcolati.  
  
[Definizione dei set denominati](lesson-6-2-defining-named-sets.md)  
In questa procedura vengono definiti i set denominati.  
  
## <a name="next-lesson"></a>Lezione successiva  
[Lezione 7: Definizione degli indicatori di prestazioni chiave &#40;indicatori KPI&#41;](lesson-7-defining-key-performance-indicators-kpis.md)  
  
## <a name="see-also"></a>Vedere anche  
[Scenario di Analysis Services Tutorial](analysis-services-tutorial-scenario.md)  
[Creare set denominati](../multidimensional-models/create-named-sets.md)  
[Creare membri calcolati](../multidimensional-models/create-calculated-members.md)  
  
  
  
