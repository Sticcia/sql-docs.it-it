---
title: Sum (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bdf003a65e6923acf2bbf5c17e93d412e2d194fa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241376"
---
# <a name="sum-mdx"></a>Sum (MDX)


  Restituisce la somma di un'espressione numerica valutata su un set specifico.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Sum( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione set MDX (Multidimensional Expression) valida.  
  
 *Numeric_Expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Note  
 Se si specifica un'espressione numerica, questa viene valutata sull'intero set e quindi sommata. Se non viene specificata un'espressione numerica, il set specificato viene valutato nel contesto corrente dei membri del set e quindi sommato. Se la funzione SUM viene applicata a un'espressione non numerica, i risultati saranno indefiniti.  
  
> [!NOTE]  
>  Durante il calcolo della somma di un set di numeri, in Analysis Services vengono ignorati i valori Null.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene restituita la somma di Reseller Sales Amounts per tutti i membri della gerarchia di attributi Product.Category per gli anni di calendario 2001 e 2002.  
  
```  
WITH MEMBER Measures.x AS SUM  
   ( { [Date].[Calendar Year].&[2001]  
         , [Date].[Calendar Year].&[2002] }  
      , [Measures].[Reseller Sales Amount]  
    )  
SELECT Measures.x ON 0  
,[Product].[Category].Members ON 1  
FROM [Adventure Works]  
```  
  
 Nell'esempio seguente viene restituita la somma dei costi di spedizione delle vendite Internet per il mese di luglio 2002 fino al giorno 20 luglio.  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 L'esempio seguente usa la parola chiave WITH MEMBER e il **somma** per definire un membro calcolato nella dimensione Measures che contiene la somma della misura Reseller Sales Amount per i membri Canada e United States della funzione di Gerarchia dell'attributo Country nella dimensione Geography.  
  
```  
WITH MEMBER Measures.NorthAmerica AS SUM   
      (  
         {[Geography].[Country].&[Canada]  
            , [Geography].[Country].&[United States]}  
       ,[Measures].[Reseller Sales Amount]  
      )  
SELECT {[Measures].[NorthAmerica]} ON 0,  
[Product].[Category].members ON 1  
FROM [Adventure Works]  
```  
  
 Spesso, il **somma** funzione viene usata con la **CURRENTMEMBER** funzione o funzioni, ad esempio **YTD** che restituiscono un set che varia a seconda dell'elemento currentmember di una gerarchia. Nella query seguente, ad esempio, viene restituita la somma della misura di Internet Sales Amount per tutte le date dall'inizio dell'anno di calendario alla data visualizzata sull'asse delle righe:  
  
 `WITH MEMBER MEASURES.YTDSUM AS`  
  
 `SUM(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDSUM} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
