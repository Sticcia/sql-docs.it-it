---
title: Selezionare i membri (configurazione guidata Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2d15a32302aa5d7a4ee3ca087944effc017ce8c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62747514"
---
# <a name="select-members-business-intelligence-wizard"></a>Selezione membri (Configurazione guidata funzionalità di Business Intelligence)
  Utilizzare la pagina **Selezione membri** per determinare i membri ai quali, durante la Configurazione guidata funzionalità di Business Intelligence, dovrà essere applicata la funzionalità di conversione valuta specificata nella pagina **Impostazione opzioni di conversione valuta** .  
  
> [!NOTE]  
>  Questa pagina non viene visualizzata se la Configurazione guidata funzionalità di Business Intelligence viene avviata da Progettazione dimensioni oppure facendo clic con il pulsante destro del mouse su una dimensione in Esplora soluzioni in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="options"></a>Opzioni  
 **Dimensione Measures**  
 Consente di applicare la funzionalità di conversione valuta a una o più misure nel cubo.  
  
 Se selezionata, nella griglia vengono visualizzate le opzioni elencate nella tabella seguente.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Tipi di misure predefiniti**|Consente di includere la funzionalità di conversione valuta per la misura specificata.|  
|**Misure**|Consente di selezionare la misura nel gruppo di misure di tipo Tasso che contiene il tasso di cambio da usare quando la misura selezionata in **Tipi di misure predefiniti** viene convertita.|  
  
 **Gerarchia conto**  
 Consente di applicare la funzionalità di conversione valuta a uno o più membri nella gerarchia conto della dimensione di tipo Conti inclusa nel cubo. La gerarchia conto corrisponde alla gerarchia all'interno dell'account della dimensione la cui proprietà `Type` è impostata su *Account*.  
  
 Se selezionata, nella griglia vengono visualizzate le opzioni elencate nella tabella seguente.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Membro conto**|Consente di includere la funzionalità di conversione valuta per il membro della gerarchia conto specificato.|  
|**Misure**|Consente di selezionare la misura nel gruppo di misure di tipo Tasso che contiene il tasso di cambio da utilizzare quando le misure per il membro selezionato in **Membro conto** vengono convertite.|  
  
 **Gerarchia conto basata sul tipo**  
 Consente di applicare la funzionalità di conversione valuta a tutti i membri di attributi inclusi nella gerarchia conto la cui proprietà `Type` è impostata su un tipo di conto specificato.  
  
 Se selezionata, nella griglia vengono visualizzate le opzioni elencate nella tabella seguente.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|**Tipo di account**|Consente di includere la funzionalità di conversione valuta per il tipo di conto specificato.|  
|**Misure**|Consente di selezionare la misura nel gruppo di misure di tipo Tasso che contiene il tasso di cambio da utilizzare quando le misure per i membri degli attributi che utilizzano il tipo di conto selezionato in **Tipo conto** vengono convertite.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida sensibile al contesto della Configurazione guidata funzionalità di Business Intelligence](business-intelligence-wizard-f1-help.md)   
 [Finestra di progettazione del cubo &#40;Analysis Services - dati multidimensionali&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Finestra di progettazione della dimensione &#40;Analysis Services - dati multidimensionali&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
