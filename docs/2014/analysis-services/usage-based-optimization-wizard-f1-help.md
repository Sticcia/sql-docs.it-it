---
title: F1 Guida della procedura guidata di ottimizzazione basata sull'utilizzo | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.usagebasedoptimizationwizard.f1
helpviewer_keywords:
- Usage-Based Optimization Wizard
ms.assetid: e5f5a938-ae7c-4f4e-9416-a7f94ac82763
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 732b1c979f0dbf3a346ad85fc11bb8e0c5097c4f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62756140"
---
# <a name="usage-based-optimization-wizard-f1-help"></a>Guida sensibile al contesto dell'Ottimizzazione guidata basata sulle statistiche di utilizzo
  L'Ottimizzazione guidata basata sulle statistiche di utilizzo è simile alla Progettazione guidata aggregazioni per quanto concerne l'output e consente di progettare aggregazioni per una partizione. Le aggregazioni progettate tramite l'Ottimizzazione guidata basata sulle statistiche di utilizzo, tuttavia, sono basate su un modello di utilizzo specifico delle query registrate nel log di query di un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Le aggregazioni garantiscono miglioramenti delle prestazioni poiché consentono a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] di recuperare totali precalcolati direttamente dall'archiviazione del cubo senza dover ricalcolare i dati da un'origine dati sottostante per ogni query.  
  
 Per aprire l'Ottimizzazione guidata basata sulle statistiche di utilizzo dall'interno di [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], aprire la finestra di progettazione del cubo per un progetto [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , quindi fare clic sulla scheda **Aggregazioni** . Fare clic sul pulsante **Ottimizzazione basata sulle statistiche di utilizzo** nella barra degli strumenti.  
  
 Per aprire l'Ottimizzazione guidata basata sulle statistiche di utilizzo dall'interno di [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], collegarsi a un database di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] e aprire la cartella **Cubi** . Selezionare un cubo, quindi aprire la cartella **Gruppi di misure** ed espandere il gruppo di misure che si desidera modificare. Fare clic con il pulsante destro del mouse sulla cartella **Partizioni** , quindi selezionare **Ottimizzazione basata sulle statistiche di utilizzo**.  
  
 Per progettare queste aggregazioni, è possibile utilizzare Progettazione guidata aggregazioni. Questa procedura guidata consente di eseguire in modo semplificato i passaggi seguenti:  
  
-   Selezionare le impostazioni standard o personalizzate per le opzioni di archiviazione e di memorizzazione nella cache di una partizione, di un gruppo di misure o di un cubo.  
  
-   Determinare conteggi stimati o effettivi per gli oggetti a cui fa riferimento la partizione, il gruppo di misure o il cubo.  
  
-   Specificare le opzioni e i limiti di aggregazione per ottimizzare le prestazioni dell'archiviazione e delle query offerte dalle aggregazioni progettate.  
  
-   Salvare ed eventualmente elaborare la partizione, il gruppo di misure o il cubo per generare le aggregazioni definite.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] include la Progettazione guidata aggregazioni per progettare aggregazioni basate su analisi statistiche della struttura della partizione per creare una progettazione di aggregazione che possa essere limitata in base alle dimensioni di archiviazione o al miglioramento delle prestazioni stimato. È possibile utilizzare la Progettazione guidata aggregazioni per migliorare le prestazioni generali di una partizione, tuttavia la progettazione delle aggregazioni non è concepita per far fronte ad esigenze specifiche degli utenti aziendali. Tramite l'Ottimizzazione guidata basata sulle statistiche di utilizzo è possibile ottenere una progettazione delle aggregazioni mirata a risolvere esigenze specifiche, ma la procedura può garantire questi risultati solo se il log di query per l'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] contiene informazioni sufficienti per creare tali query.  
  
 In genere le due procedure guidate vengono utilizzate insieme per migliorare le prestazioni in fase di distribuzione e in seguito. È consigliabile utilizzare prima la Progettazione guidata aggregazioni quando la partizione (o il cubo o il gruppo di misure che contiene la partizione) viene inizialmente distribuita, per garantire un miglioramento generale delle prestazioni. Dopo un periodo di tempo durante il quale sono state registrate le query degli utenti aziendali per la partizione nel log di query, sarà possibile utilizzare l'Ottimizzazione guidata basata sulle statistiche di utilizzo per ottimizzare la progettazione delle aggregazioni in modo da gestire al meglio i requisiti relativi alle prestazioni e alle query degli utenti aziendali.  
  
> [!NOTE]  
>  er ulteriori informazioni sulla configurazione del log di query, vedere [Configurazione del log di query di Analysis Services](instances/log-operations-in-analysis-services.md?view=sql-server-2014#bkmk_querylog).  
  
## <a name="in-this-section"></a>In questa sezione  
  
-   [Selezione partizioni da modificare &#40;procedura guidata basata sulle statistiche&#41;](select-partitions-to-modify-usage-based-optimization-wizard.md)  
  
-   [Specificare i criteri di Query &#40;procedura guidata basata sulle statistiche&#41;](specify-query-criteria-usage-based-optimization-wizard.md)  
  
-   [Verifica delle query che verranno ottimizzate &#40;Ottimizzazione guidata basata sull'utilizzo&#41;](review-the-queries-that-will-be-optimized-usage-based-optimization-wizard.md)  
  
-   [Controlla utilizzo aggregazioni &#40;procedura guidata basata sulle statistiche basate sull'utilizzo&#41;](review-aggregation-usage-usage-based-optimiation-wizard.md)  
  
-   [Impostazione conteggi oggetti &#40;procedura guidata basata sulle statistiche&#41;](specify-object-counts-usage-based-optimization-wizard.md)  
  
-   [Impostare le opzioni di aggregazione &#40;procedura guidata basata sulle statistiche&#41;](set-aggregation-options-usage-based-optimization-wizard.md)  
  
-   [Completamento procedura guidata &#40;procedura guidata basata sulle statistiche&#41;](completing-the-wizard-usage-based-optimization-wizard.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Le aggregazioni e progettazione di aggregazioni](multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)   
 [Cubi nei modelli multidimensionali](multidimensional-models/cubes-in-multidimensional-models.md)   
 [Guida F1 guidata di progettazione delle aggregazioni](aggregation-design-wizard-f1-help.md)   
 [Procedure guidate di Analysis Services &#40;dati multidimensionali&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
