---
title: Misure nel Report di convalida incrociata | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- root mean square error [data mining]
- cross-validation [data mining]
- mean absolute error [data mining]
- log score [data mining]
- likelihood [data mining]
ms.assetid: a07b1665-7f72-4266-82a4-43a91ae2571d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: df327dbf712e82100ea0edb3c2943ade9d6e1b87
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62721923"
---
# <a name="measures-in-the-cross-validation-report"></a>Misure nel report di convalida incrociata
  Durante la convalida incrociata, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] consente di dividere i dati di una struttura di data mining in più sezioni trasversali e quindi di eseguire il test della struttura e di tutti i modelli di data mining associati in modo iterativo. In base a questa analisi, viene restituito un set di misure di accuratezza standard per la struttura e ciascun modello.  
  
 Nel report sono contenute alcune informazioni di base sul numero di riduzioni nei dati e la quantità di dati in ciascuna riduzione, nonché un set di metriche generali che consentono di descrivere la distribuzione dei dati. Confrontando la metrica generale per ogni sezione trasversale, è possibile valutare l'affidabilità della struttura o del modello.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] viene inoltre visualizzato un set di misure dettagliate per i modelli di data mining. Queste misure dipendono dal tipo di modello e dal tipo di attributo analizzato, ad esempio se è discreto o continuo.  
  
 Questa sezione fornisce un elenco delle misure contenute nel report **Convalida incrociata** e il relativo significato. Per informazioni dettagliate sulla modalità di calcolo di ogni misura, vedere [Formule per la convalida incrociata](cross-validation-formulas.md).  
  
## <a name="list-of-measures-in-the-cross-validation-report"></a>Elenco di misure nel report di convalida incrociata  
 Nella tabella seguente vengono elencate le misure visualizzate nel report di convalida incrociata. Le misure vengono raggruppate per *tipo di test*, specificato nella colonna di sinistra della tabella seguente. Nella colonna di destra viene elencato il nome della misura, come visualizzato nel report, e viene fornita una breve spiegazione del significato.  
  
|tipo di test|Misure e descrizioni|  
|---------------|-------------------------------|  
|Clustering|Misure applicate ai modelli di clustering:<br /><br /> **Probabilità case**: Questa misura indica di solito la probabilità che un case appartenga a un cluster specifico. <br />                      Per la convalida incrociata, i punteggi vengono sommati, quindi divisi per il numero di case, pertanto il punteggio indicato rappresenta una probabilità del case media.|  
|Classificazione|Misure applicate ai modelli di classificazione:<br /><br /> **Vero positivo**/<br />                      **Vero negativo**/ **falso positivo**/ **falso positivo**: Conteggio delle righe o dei valori nella partizione in cui lo stato stimato corrisponde allo stato di destinazione e la probabilità di stima è maggiore della soglia specificata. Sono esclusi i case con valori mancanti per l'attributo di destinazione, ovvero i conteggi di tutti i valori potrà non essere sommati|  
||**Superato/Non superato**: Conteggio delle righe o dei valori nella partizione in cui lo stato stimato corrisponde allo stato di destinazione e il valore della probabilità di stima è maggiore di 0.|  
|Probabilità|Misure di probabilità applicate a più tipi di modello:<br /><br /> **Accuratezza**: Rapporto tra la probabilità della stima effettiva e la probabilità marginale nei test case. Righe associate a valori mancanti per l'attributo di destinazione sono escluse. Tramite questa misura viene generalmente mostrato quanto la probabilità del risultato di destinazione migliori in caso di utilizzo del modello.<br /><br /> **Radice errore quadratico medio**: Radice quadrata dell'errore medio per tutti i case della partizione divisa per il numero di case nella partizione, escluse le righe associate a valori mancanti per l'attributo di destinazione. Radice errore quadratico medio è uno stimatore comune per modelli predittivi. Per il punteggio viene eseguita la media dei residui per ciascun case per produrre un singolo indicatore di errore del modello.<br /><br /> **Punteggio in forma logaritmica**: Logaritmo della probabilità effettiva per ciascun case sommato e quindi diviso per il numero di righe nel set di dati di input, escluse le righe associate a valori mancanti per l'attributo di destinazione. Poiché la probabilità è rappresentata come frazione decimale, i punteggi in forma logaritmica sono sempre numeri negativi. Un numero più vicino a 0 corrisponde a un punteggio migliore. Mentre punteggi non elaborati possono avere distribuzioni non regolari o non simmetriche, un punteggio in forma logaritmica è analogo a una percentuale.|  
|Valutazione|Misure che si applicano solo ai modelli per la stima, che consentono di stimare un attributo numerico continuo:<br /><br /> **Radice errore quadratico medio**: Errore medio quando il valore stimato viene confrontato con il valore effettivo. Radice errore quadratico medio è uno stimatore comune per modelli predittivi. Per il punteggio viene eseguita la media dei residui per ciascun case per produrre un singolo indicatore di errore del modello.<br /><br /> **Errore assoluto medio**: Errore medio quando i valori stimati vengono confrontati con i valori effettivi, calcolati come media della somma assoluta degli errori. L'errore assoluto medio è utile per capire quanto le stime siano vicine ai valori effettivi. Un punteggio più piccolo indica che le stime sono più accurate.<br /><br /> **Log Score**: Logaritmo della probabilità effettiva per ciascun case sommato e quindi diviso per il numero di righe nel set di dati di input, escluse le righe associate a valori mancanti per l'attributo di destinazione. Poiché la probabilità è rappresentata come frazione decimale, i punteggi in forma logaritmica sono sempre numeri negativi. Un numero più vicino a 0 corrisponde a un punteggio migliore. Mentre punteggi non elaborati possono avere distribuzioni non regolari o non simmetriche, un punteggio in forma logaritmica è analogo a una percentuale.|  
|Aggregazioni|Aggregare le misure forniscono un'indicazione della varianza nei risultati per ogni partizione:<br /><br /> **Media**: Media dei valori della partizione per una misura specifica.<br /><br /> **Deviazione standard**: Media della deviazione rispetto al valore medio per una misura specifica, calcolata in tutte le partizioni di un modello. Per la convalida incrociata, un valore superiore per questo punteggio implica una variazione sostanziale tra le riduzioni.|  
  
## <a name="see-also"></a>Vedere anche  
 [Test e convalida &#40;Data mining&#41;](testing-and-validation-data-mining.md)  
  
  
