---
title: Proprietà CommandStream (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Command::CommandStream
helpviewer_keywords:
- CommandStream property [ADO]
ms.assetid: f78f61b6-87e0-48dc-961e-83d0e20da58e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b1048e8d243bd19d86d60c3c4f92e4e4b9d137a9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267274"
---
# <a name="commandstream-property-ado"></a>Proprietà CommandStream (ADO)
Indica il flusso usato come input per un [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce il flusso usato come input per un **comando** oggetto. Il formato per questo flusso è specifico del provider; vedere la documentazione del provider per informazioni dettagliate. Questa proprietà è simile al [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md) proprietà, che consente di specificare una stringa per l'input di un **comando**.  
  
## <a name="remarks"></a>Note  
 **CommandStream** e **CommandText** si escludono a vicenda. Quando l'utente imposta il **CommandStream** proprietà, il **CommandText** verrà impostata su una stringa vuota (""). Se l'utente imposta il **CommandText** proprietà, il **CommandStream** verrà impostata su **Nothing**.  
  
 I comportamenti del **Command.Parameters.Refresh** e **Command. Prepare** metodi sono definiti dal provider. I valori dei parametri in un flusso non possono essere aggiornati.  
  
 Il flusso di input non è disponibile ad altri oggetti ADO che restituiscono l'origine di un **comando**. Ad esempio, se il [origine](../../../ado/reference/ado-api/source-property-ado-recordset.md) di un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) è impostata su un **comando** oggetto che dispone di un flusso come input, **Recordset.Source** continua a restituire il **CommandText** proprietà, che contiene una stringa vuota (""), anziché il contenuto del flusso dei **CommandStream** proprietà.  
  
 Quando si usa un flusso del comando (come specificato da **CommandStream**), valido solo [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) valori per il [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) sono proprietà  **adCmdText** e **adCmdUnknown**. Qualsiasi altro valore causa un errore.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà CommandText (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [Proprietà Dialect](../../../ado/reference/ado-api/dialect-property.md)   
 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)
