---
title: LinRegR2 (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 42c703e703e8c557b4de8466a0cd1b686217fd4b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63136209"
---
# <a name="linregr2-mdx"></a>LinRegR2 (MDX)


  Calcola la regressione lineare di un set e restituisce il coefficiente di determinazione R<sup>2</sup>.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
LinRegR2(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>Argomenti  
 *Set_Expression*  
 Espressione MDX (Multidimensional Expression) valida che restituisce un set.  
  
 *Numeric_Expression_y*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse Y.  
  
 *Numeric_Expression_x*  
 Espressione numerica valida che in genere è un'espressione MDX (Multidimensional Expression) di coordinate di celle che restituisce un numero che rappresenta i valori per l'asse X.  
  
## <a name="remarks"></a>Note  
 La regressione lineare, che utilizza il metodo dei minimi quadrati, calcola l'equazione di una retta di regressione, ovvero la retta di migliore approssimazione per una serie di punti. Retta di regressione contiene l'equazione seguente, in cui una è l'inclinazione e b è l'intercetta:  
  
 y = ax+b  
  
 Il **LinRegR2** funzione valuta la setagainst specificato il primo expressionto numerico ottenere i valori per l'asse y. La funzione valuta quindi il set specificato in base alla seconda espressione numerica, se specificata, per ottenere i valori per l'asse X. Se il secondo expressionis numerica non specificata, la funzione utilizza il contesto corrente delle celle nel set specificato come valori per l'asse x. Se non si specifica la x-axisargument viene spesso usato con la dimensione temporale.  
  
 Dopo aver ottenuto il set di punti, il **LinRegR2** funzione restituisce il coefficiente statistico R<sup>2</sup> che descrive l'adattamento dell'equazione lineare ai punti.  
  
> [!NOTE]  
>  Il **LinRegR2** funzione ignora le celle vuote o che contengono testo o valori logici. Tuttavia, la funzione include celle con valori zero.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente restituisce il coefficiente statistico R<sup>2</sup> che descrive la bontà dell'adattamento dell'equazione di regressione lineare ai punti per le vendite unitarie e le misure relative alle vendite Negozio.  
  
```  
LinRegR2(LastPeriods(10), [Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Guida di riferimento alle funzioni MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
