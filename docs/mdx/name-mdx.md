---
title: Name (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 143fb6409e430b8fcbda7c073b8614cd0ecfcbe2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63277549"
---
# <a name="name-mdx"></a>Name (MDX)


  Restituisce il nome di una dimensione, una gerarchia, un livello o un membro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Dimension expression syntax  
Dimension_Expression.Name  
  
Hierarchy expression syntax  
Hierarchy_Expression.Name  
  
Level_expression syntax  
Level_Expression.Name  
  
Member expression syntax  
Member_Expression.Name  
```  
  
## <a name="arguments"></a>Argomenti  
 *Dimension_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una dimensione.  
  
 *Hierarchy_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce una gerarchia.  
  
 *Level_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un livello.  
  
 *Member_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un membro.  
  
## <a name="remarks"></a>Note  
 Il **nome** funzione restituisce il nome dell'oggetto, non il nome univoco.  
  
## <a name="examples"></a>Esempi  
  
### <a name="dimension-hierarchy-and-level-expression-example"></a>Esempio di espressione di dimensione, gerarchia e livello  
 Nell'esempio seguente vengono restituiti il nome della dimensione Date e i nomi della gerarchia e del livello per il membro luglio 2001.  
  
```  
WITH MEMBER Measures.DimensionName AS [Date].Name  
MEMBER Measures.HierarchyName AS [Date].[Calendar].[July 2001].Hierarchy.Name  
MEMBER Measures.LevelName as [Date].[Calendar].[July 2001].Level.Name  
  
SELECT {Measures.DimensionName, Measures.HierarchyName, Measures.LevelName} ON 0  
from [Adventure Works]  
```  
  
### <a name="member-expression-example"></a>Esempio di espressione di membro  
 Nell'esempio seguente viene restituito il nome del membro, con il valore, la chiave e la didascalia di tale membro.  
  
```  
WITH MEMBER MemberName AS [Date].[Calendar].[July 1, 2001].Name  
MEMBER Measures.ValueColumn as [Date].[Calendar].[July 1, 2001].MemberValue  
MEMBER Measures.KeyColumn as [Date].[Calendar].[July 1, 2001].Member_Key  
MEMBER Measures.NameColumn as [Date].[Calendar].[July 1, 2001].Member_Name  
  
SELECT {Measures.MemberName, Measures.ValueColumn, Measures.KeyColumn, Measures.NameColumn} ON 0  
from [Adventure Works]  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
