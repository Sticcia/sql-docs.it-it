---
title: sp_help_spatial_geography_index_xml (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_spatial_geography_index_xml_TSQL
- sp_help_spatial_geography_index_xml
dev_langs: TSQL
helpviewer_keywords: sp_help_spatial_geography_index_xml procedure
ms.assetid: 821d4127-3ce5-4474-8561-043404a20d81
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 47f5b0043338691ce02bc567c8a9d5e1d4943050
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpspatialgeographyindexxml-transact-sql"></a>sp_help_spatial_geography_index_xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Restituisce il nome e il valore per un determinato set di proprietà su un **geography** indice spaziale. È possibile scegliere di restituire un set principale di proprietà oppure tutte le proprietà dell'indice.  
  
 I risultati vengono restituiti in un frammento XML in cui vengono visualizzati il nome e valore delle proprietà selezionate.  
  
||  
|-|  
|**Si applica a**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (da[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] a [versione corrente](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Icona di collegamento a un argomento](../../database-engine/configure-windows/media/topic-link.gif "Icona di collegamento a un argomento")[Convenzioni della sintassi Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
sp_help_spatial_geography_index_xml [ @tabname =] 'tabname'   
     [ , [ @indexname = ] 'indexname' ]   
     [ , [ @verboseoutput = ] 'verboseoutput' ]   
     [ , [ @query_sample = ] 'query_sample' ]   
     [ ,.[ @xml_output = ] 'xml_output' ]   
```  
  
## <a name="arguments"></a>Argomenti  
 Vedere [Stored procedure di argomenti e le proprietà dell'indice spaziale](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="properties"></a>Proprietà  
 Vedere [Stored procedure di argomenti e le proprietà dell'indice spaziale](../../relational-databases/system-stored-procedures/spatial-index-stored-procedures-arguments-and-properties.md).  
  
## <a name="permissions"></a>Permissions  
 Per accedere alla procedura, l'utente deve essere assegnato a un ruolo PUBLIC. È necessario disporre dell'autorizzazione READ ACCESS per il server e l'oggetto.  
  
## <a name="remarks"></a>Osservazioni  
 Le proprietà che contengono valori NULL non sono incluse nel set restituito.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente usa `sp_help_spatial_geography_index_xml` per esaminare l'indice spaziale **SIndx_SpatialTable_geography_col2** definiti nella tabella **geography_col** per l'esempio di query specificata in  **@qs**. L'esempio restituisce le proprietà principali dell'indice specificato in un frammento XML in cui vengono visualizzati il nome e il valore delle proprietà selezionate.  
  
 Un [XQuery](../../xquery/xquery-basics.md) viene quindi eseguito nel set di risultati, la restituzione di una proprietà specifica.  
  
```  
declare @qs geography  
        ='POLYGON((-90.0 -180, -90 180.0, 90 180.0, 90 -180, -90 -180.0))';  
declare @x xml;  
exec sp_help_spatial_geography_index_xml 'geography_col', 'SIndx_SpatialTable_geography_col2', 0, @qs, @x output;  
select @x.value('(/Primary_Filter_Efficiency/text())[1]', 'float');  
```  
  
 Simile a [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md), questa stored procedure fornisce accesso a livello di programmazione più semplice per le proprietà di un **geography** indice spaziale e segnala il set di risultati in XML.  
  
 Il rettangolo di selezione di un **geography** è la terra intera.  
  
## <a name="requirements"></a>Requisiti  
  
## <a name="see-also"></a>Vedere anche  
 [Indice spaziale Stored procedure](http://msdn.microsoft.com/library/1be0f34e-3d5a-4a1f-9299-bd482362ec7a)   
 [sp_help_spatial_geography_index](../../relational-databases/system-stored-procedures/sp-help-spatial-geography-index-transact-sql.md)   
 [Panoramica degli indici spaziali](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Nozioni fondamentali su XQuery](../../xquery/xquery-basics.md)   
 [Riferimento al linguaggio XQuery](../../xquery/xquery-language-reference-sql-server.md)  
  
  