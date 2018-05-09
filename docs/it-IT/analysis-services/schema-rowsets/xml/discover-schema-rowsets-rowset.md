---
title: Set di righe DISCOVER_SCHEMA_ROWSETS | Documenti Microsoft
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
- DISCOVER_SCHEMA_ROWSETS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_SCHEMA_ROWSETS rowset
ms.assetid: e5012aa0-6ef8-497f-96c1-2772e2394f62
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fafe6ed5d5a81cb73ddc53a68408e4548ac92699
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/03/2018
---
# <a name="discoverschemarowsets-rowset"></a>Set di righe DISCOVER_SCHEMA_ROWSETS
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Restituisce nomi, restrizioni, descrizione e altre informazioni per tutti i valori di enumerazione ed eventuali valori di enumerazione specifici del provider supportati dal provider [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA).  
  
 Se si chiama il [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md) metodo con il **DISCOVER_SCHEMA_ROWSETS** valore di enumerazione nel [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md) elemento, il **Discover**metodo restituisce il **DISCOVER_SCHEMA_ROWSETS** set di righe.  
  
## <a name="rowset-columns"></a>Colonne del set di righe  
 Il set di righe DISCOVER_SCHEMA_ROWSETS contiene le colonne seguenti.  
  
|Nome colonna|Indicatore del tipo|Lunghezza|Description|  
|-----------------|--------------------|------------|-----------------|  
|**NomeSchema**|**DBTYPE_WSTR**||Nome dello schema o della richiesta. Questa richiesta restituisce i valori nell'enumerazione *RequestTypes* .|  
|**SchemaGuid**|**DBTYPE_GUID**||GUID dello schema.|  
|**Restrizioni**|**DBTYPE_HCHAPTER**||Matrice di restrizioni supportate dal provider.|  
|**Description**|**DBTYPE_WSTR**||Descrizione localizzabile dello schema.|  
|**RestrictionsMask**|**DBTYPE_UI8**|||  
  
 Questo set di righe dello schema non è ordinato.  
  
 Per un provider che supporta tre restrizioni per il set di righe dello schema DBSCHEMA_MEMBERS, la matrice **Restrictions** potrebbe restituire il risultato seguente. Gli elementi nel risultato fanno riferimento ai nomi delle colonne nello schema.  
  
```  
<Restrictions>  
      <CATALOG_NAME type="string" />   
      <SCHEMA_NAME type="string" />   
      <CUBE_NAME type="string" />   
</Restrictions>  
```  
  
## <a name="restriction-columns"></a>Colonne di restrizione  
 Il set di righe **DISCOVER_SCHEMA_ROWSETS** può essere limitato sulle colonne elencate nella tabella seguente.  
  
|Nome colonna|Indicatore del tipo|Stato della restrizione|  
|-----------------|--------------------|-----------------------|  
|**NomeSchema**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>Vedere anche  
 [XML for Analysis i rowset dello Schema](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  