---
title: Elemento DiscretizationBucketCount (ASSL) | Documenti Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DiscretizationBucketCount Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DiscretizationBucketCount
helpviewer_keywords:
- DiscretizationBucketCount element
ms.assetid: 551a73ae-59e1-4079-a2d9-988df96b5e07
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a9beb1b2930004786c4342836af5f39cbc7c314f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="discretizationbucketcount-element-assl"></a>Elemento DiscretizationBucketCount (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Contiene il numero di bucket per la discretizzazione.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
  
<DimensionAttribute> <!-- or ScalarMiningStructureColumn -->  
   ...  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>Caratteristiche elemento  
  
|Caratteristica|Descrizione|  
|--------------------|-----------------|  
|Tipo di dati e lunghezza|Valore intero|  
|Valore predefinito|Nessuno|  
|Cardinalità|0-1: elemento facoltativo che può ricorrere una sola volta.|  
  
## <a name="element-relationships"></a>Relazioni elemento  
  
|Relazione|Elemento|  
|------------------|-------------|  
|Elemento padre|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md), [ScalarMiningStructureColumn](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)|  
|Elementi figlio|Nessuno|  
  
## <a name="remarks"></a>Osservazioni  
 Il valore di **DiscretizationBucketCount** elemento determina quanti gruppi o "bucket" vengono creati quando i valori per il **DimensionAttribute** o **ScalarMiningStructureColumn**  vengono discretizzati o organizzati in un set di gruppi specifico. Se l'elemento non è specificato o se viene specificato zero per il valore dell'elemento, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] crea un numero appropriato di gruppi a seconda del metodo di discretizzazione. Per ulteriori informazioni sui metodi di discretizzazione, vedere [metodi di discretizzazione &#40;Data Mining&#41;](../../../analysis-services/data-mining/discretization-methods-data-mining.md).  
  
 Gli elementi che corrispondono ai padri di **DiscretizationBucketCount** nel modello a oggetti oggetti AMO (Analysis Management) sono <xref:Microsoft.AnalysisServices.DimensionAttribute> e <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>.  
  
## <a name="see-also"></a>Vedere anche  
 [Elemento DiscretizationMethod &#40;ASSL&#41;](../../../analysis-services/scripting/properties/discretizationmethod-element-assl.md)   
 [Proprietà & #40; ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  