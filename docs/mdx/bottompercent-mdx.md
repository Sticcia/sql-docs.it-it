---
title: BottomPercent (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a627ea8e5dd7a8f8266fcf0ea374e6abcde4bdc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208792"
---
# <a name="bottompercent-mdx"></a>BottomPercent (MDX)


  Dispone un set in ordine crescente e restituisce un set di tuple con i valori più bassi il cui totale cumulativo è uguale o maggiore della percentuale specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
BottomPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Percentuale*  
 Espressione numerica valida che specifica la percentuale di tuple da restituire.  
  
 *Numeric_Expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Note  
 Il **BottomPercent** funzione calcola la somma dell'espressione numerica specificata valutata su un set specificato, disponendo il set in ordine crescente. La funzione restituisce quindi gli elementi con i valori più bassi la cui percentuale cumulativa del valore sommato totale corrisponde almeno alla percentuale specificata. La funzione restituisce il subset più piccolo di un set il cui totale cumulativo corrisponde almeno alla percentuale specificata. Gli elementi restituiti sono ordinati dal più grande al più piccolo.  
  
> [!IMPORTANT]  
>  Il **BottomPercent** funzione, come le [TopPercent](../mdx/toppercent-mdx.md) function, rispetta mai la gerarchia. Per ulteriori informazioni, vedere la funzione Order.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituito per la categoria Bike il set più piccolo di membri del livello City nella gerarchia Geography della dimensione Geography per l'anno fiscale 2003 il cui totale cumulativo utilizzando la misura Reseller Sales Amount corrisponde almeno al 15% del totale cumulativo (a partire dai membri di questo set con il numero di vendite più basso).  
  
```  
SELECT  
[Product].[Product Categories].Bikes ON 0,  
BottomPercent  
   ({[Geography].[Geography].[City].Members}  
   , 15  
   , ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)  
   ) ON 1  
FROM [Adventure Works]  
WHERE ([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
