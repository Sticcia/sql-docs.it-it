---
title: Scrivi metodo | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_Write
- _Stream::Write
helpviewer_keywords:
- Write method [ADO]
ms.assetid: 02982e6a-ac5f-4af2-b82e-ce12534b84b2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 52561b6d240a58e59490d607c8729b5d878b96a7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62642433"
---
# <a name="write-method"></a>Metodo Write
Scrive dati binari in una [Stream](../../../ado/reference/ado-api/stream-object-ado.md) oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
Stream.Write Buffer  
```  
  
#### <a name="parameters"></a>Parametri  
 *Buffer*  
 Oggetto **Variant** che contiene una matrice di byte da scrivere.  
  
## <a name="remarks"></a>Note  
 Byte specificati vengono scritti per il **Stream** oggetto senza spazi intermedi ogni byte.  
  
 L'oggetto corrente [posizione](../../../ado/reference/ado-api/position-property-ado.md) è impostato sul byte successivo i dati scritti. Il **scrivere** metodo non tronca il resto dei dati in un flusso. Se si desidera troncare i byte, chiamare [SetEOS](../../../ado/reference/ado-api/seteos-method.md).  
  
 Se si scrivono corrente [EOS](../../../ado/reference/ado-api/eos-property.md) posizione, la [Size](../../../ado/reference/ado-api/size-property-ado-stream.md) del **Stream** aumenterà per includere eventuali nuovi byte, e **EOS** sposterà per il nuovo ultimo byte i **Stream**.  
  
> [!NOTE]
>  Il **scrivere** metodo viene utilizzato con flussi binari ([tipo](../../../ado/reference/ado-api/type-property-ado-stream.md) viene **adTypeBinary**). Per i flussi di testo (**tipo** viene **adTypeText**), utilizzare [WriteText](../../../ado/reference/ado-api/writetext-method.md).  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Stream (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Metodo WriteText](../../../ado/reference/ado-api/writetext-method.md)
