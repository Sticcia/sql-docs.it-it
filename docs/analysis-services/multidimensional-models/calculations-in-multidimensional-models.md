---
title: Calcoli nei modelli multidimensionali | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c72d43c95013074051356c690ac2d7abf0a575e0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62990505"
---
# <a name="calculations-in-multidimensional-models"></a>Calcoli nei modelli multidimensionali
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La scheda **Calcoli** in Progettazione cubi consente di creare membri calcolati, set denominati e altri calcoli MDX (Multidimensional Expressions).  
  
 La scheda **Calcoli** include i tre riquadri seguenti:  
  
-   Il riquadro **Libreria script** contiene l'elenco dei calcoli inclusi in un cubo e consente di creare, organizzare e selezionare i calcoli da modificare.  
  
-   Il riquadro **Strumenti di calcolo** include metadati, funzioni e modelli in base ai quali creare i calcoli.  
  
-   Il riquadro Espressioni di calcolo supporta la visualizzazione Form e visualizzazione Script.  
  
  
## <a name="creating-a-new-calculation"></a>Creazione di un nuovo calcolo  
 Per creare un nuovo calcolo, nella scheda **Calcoli** di Progettazione cubi scegliere **Nuovo membro calcolato** , **Nuovo set denominato**o **Nuovo comando script**dal menu **Cubo**, a seconda del tipo di calcolo da creare. È anche possibile fare clic sui pulsanti corrispondenti sulla barra degli strumenti o fare clic con il pulsante destro del mouse in un punto qualsiasi all'interno del riquadro **Libreria script** e quindi scegliere uno dei comandi dal menu di scelta rapida. In questo modo viene aggiunto un nuovo calcolo al riquadro **Libreria script** e i campi corrispondenti vengono visualizzati nel form di calcolo nel riquadro delle espressioni di calcolo. In caso di creazione di un nuovo script, questa operazione apre la visualizzazione Script nel riquadro Espressioni di calcolo. Per altre informazioni sulla creazione dei tre tipi di calcoli, vedere [Creare membri calcolati](../../analysis-services/multidimensional-models/create-calculated-members.md), [Creare set denominati](../../analysis-services/multidimensional-models/create-named-sets.md)e [Definire le assegnazioni e altri comandi script](../../analysis-services/multidimensional-models/define-assignments-and-other-script-commands.md).  
  
## <a name="editing-scripts"></a>Modifica di script  
 Per modificare gli script, usare il riquadro delle espressioni di calcolo nella scheda **Calcoli** . Nel riquadro Espressioni di calcolo sono disponibili due modalità di visualizzazione, ovvero Script e Form. Nella visualizzazione Form vengono visualizzate le espressioni e le proprietà relative a un unico comando. Quando si modifica uno script MDX la visualizzazione Form viene riempita da una casella di espressione.  
  
 Nella visualizzazione Script è disponibile un editor del codice in cui è possibile modificare gli script. Quando nel riquadro delle espressioni di calcolo è attiva la visualizzazione Script, il riquadro **Libreria script** è nascosto. La visualizzazione Script offre codifica a colori, corrispondenza delle parentesi, completamento automatico e blocchi di codice MDX. Le aree di codice MDX possono essere compresse o espanse per semplificare le operazioni di modifica.  
  
 Per passare dalla visualizzazione Form alla visualizzazione Script e viceversa, scegliere **Mostra calcoli in** dal menu **Cubo**e quindi **Script** o **Form**. È anche possibile fare clic su **Visualizzazione Form** o **Visualizzazione Script** sulla barra degli strumenti.  
  
## <a name="changing-solve-order"></a>Modifica dell'ordine di valutazione  
 I calcoli vengono valutati in base all'ordine riportato nel riquadro **Libreria script** . Per modificare l'ordine di valutazione dei calcoli, fare clic con il pulsante destro del mouse su un calcolo qualsiasi e quindi scegliere **Sposta su** o **Sposta giù** dal menu di scelta rapida. È anche possibile fare clic su un calcolo e quindi su **Sposta su** o **Sposta giù** sulla barra degli strumenti.  
  
 È possibile sostituire questo ordine manualmente per celle calcolate e membri calcolati. Per altre informazioni sull'ordine di calcolo e di valutazione, vedere [Informazioni sull'ordine di calcolo e di valutazione &#40;MDX&#41;](../../analysis-services/multidimensional-models/mdx/mdx-data-manipulation-understanding-pass-order-and-solve-order.md).  
  
## <a name="deleting-a-calculation"></a>Eliminazione di un calcolo  
 Per eliminare un calcolo esistente, nel riquadro **Libreria script** della scheda **Calcoli** selezionare il calcolo da eliminare e quindi scegliere **Elimina** dal menu **Modifica** o fare clic su **Elimina** sulla barra degli strumenti. È anche possibile fare clic con il pulsante destro del mouse sul calcolo desiderato nel riquadro **Libreria script** e quindi scegliere **Elimina** dal menu di scelta rapida.  
  
  
