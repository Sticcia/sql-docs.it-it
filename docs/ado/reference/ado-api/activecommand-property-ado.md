---
title: Esempio di proprietà ActiveCommand (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::ActiveCommand
helpviewer_keywords:
- ActiveCommand property [ADO]
ms.assetid: fb4088d5-5968-42d6-aeaa-3955046bb4da
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4dfdb60f9a394fa4d11e9b66ffb1f4b205881293
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63156293"
---
# <a name="activecommand-property-ado"></a>Proprietà ActiveCommand (ADO)
Indica la [comandi](../../../ado/reference/ado-api/command-object-ado.md) oggetto che ha creato l'oggetto associato [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un **Variant** che contiene un **comando** oggetto. Valore predefinito è un riferimento a un oggetto null.  
  
## <a name="remarks"></a>Note  
 Il **ActiveCommand** proprietà è di sola lettura.  
  
 Se un **comandi** oggetto non è stato usato per creare l'oggetto corrente **Recordset**, quindi un **Null** riferimento all'oggetto viene restituito.  
  
 Utilizzare questa proprietà per trovare l'oggetto associato **comandi** dell'oggetto quando si dispone solo risultante **Recordset** oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Esempio di proprietà ActiveCommand (VB)](../../../ado/reference/ado-api/activecommand-property-example-vb.md)   
 [Esempio di proprietà ActiveCommand (JScript)](../../../ado/reference/ado-api/activecommand-property-example-jscript.md)   
 [Esempio di proprietà ActiveCommand (VC + +)](../../../ado/reference/ado-api/activecommand-property-example-vc.md)   
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)
