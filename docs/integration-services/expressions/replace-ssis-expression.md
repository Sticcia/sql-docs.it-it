---
title: REPLACE (espressione SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 229e8b3d06d9524936be25758ee22d65234d25a4
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65725095"
---
# <a name="replace-ssis-expression"></a>REPLACE (espressione SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Viene restituita un'espressione di caratteri dopo aver sostituito una stringa di caratteri nell'espressione con un'altra stringa di caratteri o una stringa vuota.  
  
> [!NOTE]  
>  Vengono utilizzate spesso stringhe lunghe dalla funzione REPLACE. Le conseguenze del troncamento possono essere gestite normalmente oppure generare un avviso o un errore. Per altre informazioni, vedere [Sintassi &#40;SSIS&#41;](../../integration-services/expressions/syntax-ssis.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a>Argomenti  
 *character_expression*  
 Espressione di caratteri valida in cui la funzione esegue la ricerca.  
  
 *searchstring*  
 Espressione di caratteri valida che la funzione tenta di individuare.  
  
 *replacementstring*  
 Espressione di caratteri valida che costituisce l'espressione da sostituire.  
  
## <a name="result-types"></a>Tipi restituiti  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 La lunghezza di *searchstring* deve essere diversa da zero.  
  
 La lunghezza di *replacementstring* può essere zero.  
  
 Gli argomenti *searchstring* e *replacementstring* possono usare variabili e colonne.  
  
 È possibile utilizzare REPLACE solo con il tipo di dati DT_WSTR. Per gli argomenti*character_expression1, character_expression2,* e *character_expression3* costituiti da valori letterali stringa o da colonne di dati con tipo di dati DT_STR, prima di eseguire l'operazione della funzione REPLACE viene eseguito il cast implicito al tipo di dati DT_WSTR. Per gli altri tipi di dati è necessario il cast esplicito al tipo di dati DT_WSTR. Per altre informazioni, vedere [Cast &#40;espressione SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 Se un argomento qualsiasi è Null, REPLACE restituirà Null.  
  
## <a name="expression-examples"></a>Esempi di espressione  
 In questo esempio viene utilizzato un valore letterale stringa. Il risultato restituito è "All Terrain Bike".  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 In questo esempio viene rimossa la stringa "Bike" dalla colonna **Product** .  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 In questo esempio vengono sostituiti alcuni valori nella colonna **DaysToManufacture** . La colonna ha tipo di dati integer e l'espressione include il cast di **DaysToManufacture** al tipo di dati DT_WSTR.  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a>Vedere anche  
 [SUBSTRING &#40;espressione SSIS&#41;](../../integration-services/expressions/substring-ssis-expression.md)   
 [Funzioni &#40;espressione SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
