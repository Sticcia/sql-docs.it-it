---
title: Sys. xml_indexes (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.xml_indexes_TSQL
- xml_indexes_TSQL
- sys.xml_indexes
- xml_indexes
dev_langs: TSQL
helpviewer_keywords: sys.xml_indexes catalog view
ms.assetid: 3408de72-b067-4fda-b5d5-8e856dfd9db3
caps.latest.revision: "34"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 23c5fc72f377b08e77b8b2c8167919bcbc707ec3
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sysxmlindexes-transact-sql"></a>sys.xml_indexes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Restituisce una riga per indice XML.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] alla [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)), [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].|  
  
|Nome colonna|Tipo di dati|Description|  
|-----------------|---------------|-----------------|  
|**\<colonne ereditate >**||Eredita le colonne da [Sys. Indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md).|  
|**using_xml_index_id**|**int**|NULL = Indice XML primario.<br /><br /> Nonnull = Indice XML secondario.<br /><br /> Nonnull è un riferimento di tipo self join all'indice XML primario.|  
|**secondary_type**|**Char (1)**|Descrizione del tipo di indice secondario:<br /><br /> P = Indice XML secondario PATH<br /><br /> V = Indice XML secondario VALUE<br /><br /> R = Indice XML secondario PROPERTY<br /><br /> NULL = Indice XML primario|  
|**seconday_type_desc**|**nvarchar(60)**|Descrizione del tipo di indice secondario:<br /><br /> PATH = Indice XML secondario PATH<br /><br /> VALUE = Indice XML secondario VALUE<br /><br /> PROPERTY = Indice XML secondario PROPERTY<br /><br /> NULL = Indice XML primario|  
|**xml_index_type**|**tinyint**|Tipo di indice:<br /><br /> 0 = indice XML primario<br /><br /> 1 = indice XML secondario<br /><br /> 2 = indice XML selettivo<br /><br /> 3 = indice XML selettivo secondario|  
|**xml_index_type_description**|**nvarchar(60)**|Descrizione del tipo di indice:<br /><br /> PRIMARY_XML<br /><br /> Indice XML secondario<br /><br /> Indice XML selettivo<br /><br /> Indice XML selettivo secondario|  
|**path_id**|**int**|NULL per tutti gli indici XML ad eccezione dell'indice XML selettivo secondario.<br /><br /> Altrimenti, l'ID del percorso promosso su cui si basa l'indice XML selettivo secondario. Questo valore è lo stesso di path_id della vista di sistema sys.selective_xml_index_paths.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Per altre informazioni, vedere [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Viste del catalogo &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Oggetto viste del catalogo &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  