---
title: StreamReadEnum | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a781fb44d547237dab71c81a99a14ef0f2694b1a
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="streamreadenum"></a>StreamReadEnum
Specifica se leggere l'intero flusso o la riga successiva in un [flusso](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|Valore predefinito. Legge tutti i byte dal flusso, dalla posizione corrente a partire al [fine del flusso](../../../ado/reference/ado-api/eos-property.md) marcatore. Ciò è valido solo **StreamReadEnum** valore con flussi binari ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) è **adTypeBinary**).|  
|**adReadLine**|-2|Legge la riga successiva dal flusso (definito dal [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) proprietà).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Read, metodo](../../../ado/reference/ado-api/read-method.md)|[Metodo ReadText](../../../ado/reference/ado-api/readtext-method.md)|