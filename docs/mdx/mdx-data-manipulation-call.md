---
title: Istruzione CALL (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4052134e9fd7d3c6877894c61480897e40982b59
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63187682"
---
# <a name="mdx-data-manipulation---call"></a>Manipolazione dei dati MDX - CALL


  Esegue una stored procedure che restituisce un valore void nell'ambito corrente o facoltativamente in un cubo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
CALL SP_Name   
   [ (SP_Argument   
      [, SP_Argument ,...n]  
      ) ]   
[ONCube_Expression]  
```  
  
## <a name="arguments"></a>Argomenti  
 *SP_Name*  
 Espressione stringa valida che specifica il nome di una stored procedure.  
  
 *SP_Argument*  
 Espressione stringa valida che specifica un argomento per la stored procedure chiamata.  
  
 *Cube_Expression*  
 Stringa espressione di cubo valida che specifica il nome del cubo.  
  
## <a name="remarks"></a>Note  
 Il **CHIAMARE** istruzione viene eseguita una stored procedure registrata specificata, includendo facoltativamente uno o più argomenti per la stored procedure specificata. Il **CHIAMARE** istruzione deve essere utilizzato solo con le stored procedure che restituiscono void. Questa istruzione non può essere combinata con altre funzioni o altri operatori in un'espressione MDX. Le stored procedure registrate che restituiscono valori possono essere chiamate direttamente all'interno delle espressioni MDX e combinate con altre funzioni e altri operatori MDX.  
  
 Se non viene specificato un cubo, l'istruzione esegue la stored procedure sul cubo corrente.  
  
> [!NOTE]  
>  Se la stored procedure non è registrata sul client, il **CHIAMARE** istruzione prova a chiamare la stored procedure da un'istanza di [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzioni MDX di manipolazione dei dati &#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)   
 [Uso di stored procedure &#40;MDX&#41;](../mdx/using-stored-procedures-mdx.md)  
  
  
