---
title: Proprietà CommandTimeout (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c5bb74384e043130ccfe4c3399b363b25d40737c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63315953"
---
# <a name="commandtimeout-property-ado"></a>Proprietà CommandTimeout (ADO)
Indica per quanto tempo di attesa durante l'esecuzione di un comando prima di terminare il tentativo e generare un errore.  
  
## <a name="settings-and-return-values"></a>Le impostazioni e valori restituiti  
 Imposta o restituisce un **lungo** valore che indica, in secondi, quanto tempo di attesa per un comando da eseguire. Valore predefinito è 30.  
  
## <a name="remarks"></a>Note  
 Usare la **CommandTimeout** proprietà in un [connessione](../../../ado/reference/ado-api/connection-object-ado.md) oggetto o [comando](../../../ado/reference/ado-api/command-object-ado.md) oggetto per consentire l'annullamento di un [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) (metodo) chiamare, a causa di ritardi di rete del traffico o con intensa attività di server. Se l'intervallo impostato **CommandTimeout** proprietà scade prima che il comando viene completato l'esecuzione, si verifica un errore e ADO Annulla il comando. Se si imposta la proprietà su zero, ADO attenderà per un periodo illimitato fino al completamento dell'esecuzione. Assicurarsi che il provider e l'origine dati a cui si sta scrivendo il supporto di codice le **CommandTimeout** funzionalità.  
  
 Il **CommandTimeout** impostazione in un **connessione** oggetto non ha alcun effetto sul **CommandTimeout** impostazione in un **comando** oggetto al stessa **connessione**, vale a dire il **comando** dell'oggetto **CommandTimeout** non eredita il valore della proprietà di **connessione** dell'oggetto **CommandTimeout** valore.  
  
 In un **connessione** oggetto, il **CommandTimeout** proprietà rimane impostato su lettura/scrittura dopo la **connessione** viene aperto.  
  
## <a name="applies-to"></a>Si applica a  
  
|||  
|-|-|  
|[Oggetto Command (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Oggetto Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, dimensioni e direzione (esempio di proprietà (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, dimensioni ed esempio di proprietà direzione (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, dimensioni e direzione (esempio di proprietà (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Proprietà ConnectionTimeout (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
