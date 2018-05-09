---
title: DrilldownMemberTop (MDX) | Documenti Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DRILLDOWNMEMBERTOP
dev_langs:
- kbMDX
helpviewer_keywords:
- DrilldownMemberTop function
ms.assetid: b6575544-1fd3-4fa1-aa2e-272d307c7750
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 37e3ccd951f3ead2432f2f2e5aee13e729b79346
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="drilldownmembertop-mdx"></a>DrilldownMemberTop (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Esegue il drill-down dei membri di un set specificato presenti in un secondo set specificato, limitando il set di risultati al numero specificato di membri. La funzione esegue in alternativa il drill-down su un set di tuple utilizzando la prima gerarchia di tuple o la gerarchia specificata facoltativamente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
DrillDownMemberTop(<Set_Expression1>, <Set_Expression2>, <Count> [,[<Numeric_Expression>] [,[<Hierarchy>]] [,[RECURSIVE][,INCLUDE_CALC_MEMBERS]]])  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression1*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Set_Expression2*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Count*  
 Espressione numerica valida che specifica il numero di tuple che devono essere restituite.  
  
 *Numeric_expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
 *Gerarchia*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Ricorsivo*  
 Una parola chiave che indica il confronto ricorsivo tra set.  
  
 *Include_Calc_Members*  
 Una parola chiave per consentire l'inclusione dei membri calcolati nei risultati del drill-down.  
  
## <a name="remarks"></a>Osservazioni  
 Se viene specificata un'espressione numerica, la **DrilldownMemberTop** funzione dispone in ordine decrescente, gli elementi figlio di ogni membro nel primo set in base al valore dell'espressione numerica, valutato sul set di membri figlio. Se non viene specificata un'espressione numerica, la funzione dispone in ordine decrescente i membri figlio di ogni membro nel primo set in base ai valori delle celle rappresentate dal set di membri figlio, determinato dal contesto di query. Questo comportamento è simile alle funzioni TopCount e Head (MDX) che restituiscono un set di membri in ordine naturale, senza alcun ordinamento.  
  
 Dopo l'ordinamento, il **DrilldownMemberTop** funzione restituisce un set che contiene i membri padre e il numero di membri figlio, specificato in *conteggio,* con il valore più alto e sono contenute in entrambi i set.  
  
 Se **RICORSIVA** è specificato, la funzione ordina il primo set come descritto in precedenza, quindi confronta in modo ricorsivo i membri del primo set, organizzati in una gerarchia, con il secondo set *.* La funzione recupera il numero più alto di membri figlio di ogni membro nel primo set presente anche nel secondo set.  
  
 Il primo set può contenere tuple anziché membri. La funzione per il drill-down di tuple è un'estensione di OLE DB e restituisce un set di tuple anziché di membri.  
  
 Il **DrilldownMemberTop** è simile alla funzione di [DrilldownMember](../mdx/drilldownmember-mdx.md) funzione, ma anziché includere tutti gli elementi figlio per ogni membro nel primo set che è anche presente nel secondo set, il **DrilldownMemberTop** funzione restituisce il numero più alto di membri figlio per ogni membro.  
  
 Query sulla proprietà XMLA MdpropMdxDrillFunctions consente di verificare il livello di supporto che il server garantisce per le funzioni di drill; vedere [proprietà XMLA supportate &#40;XMLA&#41; ](../analysis-services/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties.md) per informazioni dettagliate.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente esegue il drill-down della categoria clothing per restituire le tre sottocategorie di abbigliamento con la quantità superiore di ordini spediti.  
  
```  
SELECT DrilldownMemberTop   ({[Product].[Product Categories].[All Products],        
[Product].[Product Categories].[Category].Bikes,        
[Product].[Product Categories].[Category].Clothing},     
{[Product].[Product Categories].[Category].Clothing},     
3,     
[Measures].[Reseller Order Quantity])     
ON 0     
FROM [Adventure Works]     
WHERE [Measures].[Reseller Order Quantity]  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento alla funzione MDX & #40; MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  