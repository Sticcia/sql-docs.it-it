---
title: Funzione Previous (Generatore Report e SSRS) | Documenti Microsoft
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
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 9cbaa857daff88ffa155f29ff83c16d6d9a6b856
ms.contentlocale: it-it
ms.lasthandoff: 08/09/2017

---
# <a name="report-builder-functions---previous-function"></a>Funzioni di Generatore report - funzione precedente
  Restituisce il valore o il valore di aggregazione specificato per l'istanza precedente di un elemento all'interno dell'ambito specificato.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a>Parametri  
 *espressione*  
 (**Variant** o **Binary**) Espressione da usare per identificare i dati e per cui recuperare il valore precedente, ad esempio `Fields!Fieldname.Value` o `Sum(Fields!Fieldname.Value)`.  
  
 *ambito*  
 (**String**) Facoltativo. Nome di un gruppo o di un'area dati oppure valore Null (**Nothing** in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]) che specifica l'ambito da cui recuperare il valore precedente specificato da *expression*.  
  
## <a name="return-type"></a>Tipo restituito  
 Restituisce un valore **Variant** o **Binary**.  
  
## <a name="remarks"></a>Osservazioni  
 La funzione **Previous** restituisce il valore precedente per l'espressione valutata nell'ambito specificato dopo l'applicazione di tutti i criteri di ordinamento e di filtro.  
  
 Se in *expression* non è contenuta un'aggregazione, la funzione **Previous** viene impostata per impostazione predefinita sull'ambito corrente per l'elemento del report.  
  
 In un gruppo di dettagli usare **Previous** per specificare il valore di un riferimento di campo nell'istanza precedente della riga di dettaglio.  
  
> [!NOTE]  
>  La funzione **Previous** supporta solo i riferimenti di campo nel gruppo di dettagli. Ad esempio, per una casella di testo nel gruppo di dettagli, tramite `=Previous(Fields!Quantity.Value)` vengono restituiti i dati per il campo `Quantity` dalla riga precedente. Nella prima riga tramite questa espressione viene restituito un valore Null (**Nothing** in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).  
  
 Se in *expression* è contenuta una funzione di aggregazione in cui viene usato un ambito predefinito, **Previous** consente di aggregare i dati nell'istanza precedente dell'ambito dati specificato nella chiamata di funzione di aggregazione.  
  
 Se *expression* contiene una funzione di aggregazione che specifica un ambito diverso da quello predefinito, il parametro *scope* per la funzione **Previous** deve essere un ambito di contenuto per l'ambito specificato nella chiamata di funzione di aggregazione.  
  
 Le funzioni **Level**, **InScope**, **Aggregate** e **Previous** non possono essere usate nel parametro *expression*. Non è possibile specificare il parametro *recursive* per una funzione di aggregazione.  
  
 Per altre informazioni, vedere [Riferimento a funzioni di aggregazione &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) e [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40;Generatore report e SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="examples"></a>Esempi  
  
### <a name="description"></a>Description  
 L'esempio di codice seguente, se inserito nella riga di dati predefinita di un'area dati, fornisce il valore per il campo `LineTotal` nella riga precedente.  
  
### <a name="code"></a>Codice  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a>Description  
 Nell'esempio seguente è illustrata un'espressione che calcola la somma delle vendite in un giorno del mese specifico e il valore precedente relativo allo stesso giorno del mese in un anno precedente. L'espressione viene aggiunta a una riga di una cella che appartiene al gruppo figlio `GroupbyDay`. Il gruppo padre è `GroupbyMonth`, che dispone di un gruppo padre `GroupbyYear`. L'espressione visualizza i risultati per GroupbyDay (ambito predefinito), quindi per `GroupbyYear` (elemento padre del gruppo padre `GroupbyMonth`).  
  
 Ad esempio, per un'area dati con un gruppo padre denominato `Year`che ha un gruppo figlio denominato `Month`che a sua volta ha un gruppo figlio denominato `Day` (3 livelli annidati). L'espressione `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` in una riga associata al gruppo `Day` restituisce il valore delle vendite per lo stesso giorno e mese dell'anno precedente.  
  
### <a name="code"></a>Codice  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle espressioni nei report &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Esempi di espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Tipi di dati in espressioni &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Ambito di espressioni per totali, aggregazioni e raccolte predefinite &#40; Generatore report e SSRS &#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  