---
title: FilterGroupEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89cab313736a8d5acf2f7796ea79fb5649f85ab2
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028130"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
Specifica il gruppo di record da filtrare da una [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|I filtri per visualizzare solo i record interessati dall'ultima [eliminare](../../../ado/reference/ado-api/delete-method-ado-recordset.md), [Risincronizza](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md), oppure [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) chiamare.|  
|**adFilterConflictingRecords**|5|Filtri per visualizzare i record che non hanno superato l'ultimo aggiornamento batch.|  
|**adFilterFetchedRecords**|3|I filtri per visualizzare i record nella cache corrente, vale a dire, i risultati dell'ultima chiamata a recuperare i record dal database.|  
|**adFilterNone**|0|Rimuove il filtro corrente e ripristina tutti i record per la visualizzazione.|  
|**adFilterPendingRecords**|1|I filtri per visualizzare solo i record che sono stati modificati ma non sono ancora stati inviati al server. Applicabile solo per la modalità di aggiornamento batch.|  
  
## <a name="adowfc-equivalent"></a>Equivalente di ADO o WFC  
 Package: **com.ms.wfc.data**  
  
|Costante|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>Si applica a  
 [Proprietà Filter](../../../ado/reference/ado-api/filter-property.md)
