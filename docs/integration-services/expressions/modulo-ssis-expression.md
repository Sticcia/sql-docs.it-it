---
title: (Modulo) (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '% (modulo operator)'
- remainder of division operation
- modulo operator (%)
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 1fada6d5b7d8599b1bdfbc67d47c2ac6c1553686
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725182"
---
# <a name="modulo-ssis-expression"></a>(Modulo) (espressione SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Viene restituito il resto Integer dopo aver diviso la prima espressione numerica per la seconda.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
dividend % divisor  
  
```  
  
## <a name="arguments"></a>Argomenti  
 *dividend*  
 Espressione numerica da dividere. *dividend* può essere qualsiasi espressione numerica valida. Per altre informazioni, vedere [Tipi di dati di Integration Services](../../integration-services/data-flow/integration-services-data-types.md)  
  
 *divisor*  
 Espressione numerica per cui dividere il dividendo. *divisor* può essere qualsiasi espressione numerica valida, tranne zero.  
  
## <a name="result-types"></a>Tipi restituiti  
 Dipendenti dai tipi di dati dei due argomenti. Per altre informazioni, vedere [Tipi di dati nelle espressioni di Integration Services](../../integration-services/expressions/integration-services-data-types-in-expressions.md).  
  
## <a name="remarks"></a>Remarks  
 Entrambe le espressioni devono restituire tipi di dati Integer con o senza segno.  
  
 Se uno degli operandi è Null, il risultato sarà Null.  
  
 Non è consentito il calcolo del modulo di una divisione per zero.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene calcolato il modulo di una divisione tra due valori letterali numerici. Il risultato è 3.  
  
```  
42 % 13  
```  
  
 In questo esempio viene calcolato il modulo della divisione della colonna **SalesQuota** per un valore letterale numerico.  
  
```  
SalesQuota % 12  
```  
  
 In questo esempio viene calcolato il modulo di una divisione tra le due variabili numeriche **Sales$** e **Month**. Poiché il nome include il carattere $, la variabile **Sales$** deve essere racchiusa tra parentesi. Per altre informazioni, vedere [Identificatori &#40;SSIS&#41;](../../integration-services/expressions/identifiers-ssis.md).  
  
```  
@[Sales$] % @Month  
```  
  
 In questo esempio l'operatore Modulo viene usato per determinare se il valore della variabile **Value** è pari o dispari, quindi viene usato l'operatore condizionale per restituire una stringa che descrive il risultato. Per altre informazioni, vedere [? : &#40;condizionale&#41; &#40;espressione SSIS&#41;](../../integration-services/expressions/conditional-ssis-expression.md).  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Precedenza e associatività degli operatori](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [Operatori &#40;espressione SSIS&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
