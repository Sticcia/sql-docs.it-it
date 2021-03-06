---
title: Proprietà FilterAxis (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset::FilterAxis
- FilterAxis
helpviewer_keywords:
- FilterAxis property [ADO MD]
ms.assetid: 9c656963-531e-4cd1-b698-d5f42a9b7ba3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5015888cfafcce56c97f2369d418ed7be842dd28
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63295365"
---
# <a name="filteraxis-property-ado-md"></a>Proprietà FilterAxis (ADO MD)
Indica le informazioni di filtro relative corrente [cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="return-values"></a>Valori restituiti  
 Restituisce un [asse](../../../ado/reference/ado-md-api/axis-object-ado-md.md) oggetto ed è di sola lettura.  
  
## <a name="remarks"></a>Note  
 Usare la **FilterAxis** proprietà per restituire informazioni sulle dimensioni che sono stati utilizzati per suddividere i dati. Il [DimensionCount](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md) proprietà delle **asse** restituisce il numero di dimensioni di sezionamento. Questo asse è in genere ha una sola riga.  
  
 Il **asse** restituito da **FilterAxis** non è inclusa nel [assi](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) raccolta per un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) oggetto.  
  
## <a name="applies-to"></a>Si applica a  
 [Oggetto Cellset (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Axis (ADO MD)](../../../ado/reference/ado-md-api/axis-object-ado-md.md)   
 [Oggetto Dimension (ADO MD)](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)   
 [Proprietà DimensionCount (ADO MD)](../../../ado/reference/ado-md-api/dimensioncount-property-ado-md.md)
