---
title: StdevP (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14117ed4a3e3e7afc0152c5e659d1c7f040957e9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150133"
---
# <a name="stdevp-mdx"></a>StdevP (MDX)


  Restituisce la deviazione standard della popolazione di un'espressione numerica valutata su un set, utilizzando la formula della popolazione distorta (dividendo *n*).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
StdevP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_Expression*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero.  
  
## <a name="remarks"></a>Note  
 Il **StdevP** funzione Usa la formula della popolazione distorta formula, mentre le [Stdev](../mdx/stdev-mdx.md) funzione utilizza la formula della popolazione non distorta.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene restituita la deviazione standard per Internet Order Quantity, valutata sui primi tre mesi dell'anno di calendario 2003 utilizzando la formula della popolazione distorta.  
  
```  
WITH MEMBER Measures.x AS   
   StdevP   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
