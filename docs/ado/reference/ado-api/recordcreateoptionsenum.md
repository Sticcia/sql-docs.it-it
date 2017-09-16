---
title: RecordCreateOptionsEnum | Documenti Microsoft
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
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f108d977c278d9f86ca47853e07c7960ee574b8
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
Specifica se un oggetto esistente **Record** deve essere aperto o un nuovo **Record** creato per il [Record](../../../ado/reference/ado-api/record-object-ado.md) oggetto [aprire](../../../ado/reference/ado-api/open-method-ado-record.md) metodo. I valori possono essere combinati con un operatore AND.  
  
|Costante|Valore|Description|  
|--------------|-----------|-----------------|  
|**adCreateCollection**|0x2000|Crea un nuovo **Record** in corrispondenza del nodo specificato da *origine* parametro, anziché l'apertura di un oggetto esistente **Record**. Se l'origine punta a un nodo esistente, quindi si verifica un errore di run-time, a meno che non **adCreateCollection** viene combinato con **adOpenIfExists** o **adCreateOverwrite**.|  
|**adCreateNonCollection**|0|Crea un nuovo **Record** di tipo [adSimpleRecord](../../../ado/reference/ado-api/recordtypeenum.md).|  
|**adCreateOverwrite**|0x4000000|Modifica il flag di creazione **adCreateCollection**, **adCreateNonCollection**, e **adCreateStructDoc**. Quando o viene utilizzato con questo valore e uno dei valori dei flag di creazione, se l'URL di origine fa riferimento a un nodo esistente o **Record**, quindi esistente **Record** viene sovrascritto e un nuovo uno al suo posto viene creato. Questo valore non può essere utilizzato insieme a **adOpenIfExists**.|  
|**adCreateStructDoc**|0x80000000|Crea un nuovo **Record** di tipo [adStructDoc oggetto](../../../ado/reference/ado-api/recordtypeenum.md), anziché un oggetto esistente **Record**.|  
|**adFailIfNotExists**|-1|Valore predefinito. Restituisce un errore di run-time se *origine* punta a un nodo inesistente.|  
|**adOpenIfExists**|0x2000000|Modifica il flag di creazione **adCreateCollection**, **adCreateNonCollection**, e **adCreateStructDoc**. Quando o viene utilizzato con questo valore e uno dei valori dei flag di creazione, se l'URL di origine fa riferimento a un nodo esistente o **Record** dell'oggetto, quindi il provider deve aprire esistente **Record** anziché creare un nuovo uno. Questo valore non può essere utilizzato insieme a **adCreateOverwrite**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC equivalente  
 Queste costanti non dispongono di equivalenti ADO/WFC.  
  
## <a name="applies-to"></a>Si applica a  
 [Open (metodo) (Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)