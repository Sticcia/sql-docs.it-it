---
title: Mapping dei tipi di dati in set di righe e parametri | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- SQL Server Native Client OLE DB provider, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
ms.assetid: 3d831ff8-3b79-4698-b2c1-2b5dd2f8235c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0979892b6770b9a9c2d0d9c4e8a0d734d873c085
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062199"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a>Mapping dei tipi di dati in set di righe e parametri
  Nei set di righe e come valori di parametro, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client rappresenta [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] i dati usando l'esempio OLE DB definiti tipi di dati, registrati nelle funzioni **IColumnsInfo:: GetColumnInfo** e **ICommandWithParameters:: GetParameterInfo**.  
  
|Tipo di dati di SQL Server|Tipo di dati OLE DB|  
|--------------------------|----------------------|  
|**bigint**|DBTYPE_I8|  
|**binary**|DBTYPE_BYTES|  
|**bit**|DBTYPE_BOOL|  
|**char**|DBTYPE_STR|  
|**datetime**|DBTYPE_DBTIMESTAMP|  
|**datetime2**|DBTYPE_DBTIME2|  
|**decimal**|DBTYPE_NUMERIC|  
|**float**|DBTYPE_R8|  
|**image**|DBTYPE_BYTES|  
|**int**|DBTYPE_I4|  
|**money**|DBTYPE_CY|  
|**nchar**|DBTYPE_WSTR|  
|**ntext**|DBTYPE_WSTR|  
|**numeric**|DBTYPE_NUMERIC|  
|**nvarchar**|DBTYPE_WSTR|  
|**real**|DBTYPE_R4|  
|**smalldatetime**|DBTYPE_DBTIMESTAMP|  
|**smallint**|DBTYPE_I2|  
|**smallmoney**|DBTYPE_CY|  
|**sql_variant**|DBTYPE_VARIANT, DBTYPE_SQLVARIANT|  
|**sysname**|DBTYPE_WSTR|  
|**text**|DBTYPE_STR|  
|**timestamp**|DBTYPE_BYTES|  
|**tinyint**|DBTYPE_UI1|  
|**UDT**|DBTYPE_UDT|  
|**uniqueidentifier**|DBTYPE_GUID|  
|**varbinary**|DBTYPE_BYTES|  
|**varchar**|DBTYPE_STR|  
|**XML**|DBTYPE_XML|  
  
 Il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client supporta le conversioni di dati richieste dal consumer, come illustrato nella figura.  
  
 Gli oggetti **sql_variant** possono contenere dati di qualsiasi tipo di dati di [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ad eccezione di text, ntext, image, varchar(max), nvarchar(max), varbinary(max), xml, timestamp e dei tipi CLR definiti dall'utente di Microsoft .NET Framework. Per un'istanza di dati sql_variant, inoltre, il tipo di dati di base sottostante non può corrispondere a sql_variant. La colonna può ad esempio contenere valori **smallint** per alcune righe, valori **float** per altre righe e valori **char**/**nchar** per la parte restante delle righe.  
  
> [!NOTE]  
>  Il **sql_variant** tipo di dati è simile al tipo di dati Variant in Microsoft Visual Basic? e ai tipi DBTYPE_VARIANT e DBTYPE_SQLVARIANT di OLE DB.  
  
 Quando i dati **sql_variant** vengono recuperati come DBTYPE_VARIANT, vengono inseriti in una struttura VARIANT nel buffer. Tuttavia i sottotipi presenti nella struttura VARIANT non possono eseguire il mapping a sottotipi definiti nel tipo di dati **sql_variant**. Perché tutti i sottotipi siano corrispondenti, è necessario che i dati **sql_variant** vengano quindi recuperati come DBTYPE_SQLVARIANT.  
  
## <a name="dbtypesqlvariant-data-type"></a>Tipo di dati DBTYPE_SQLVARIANT  
 Per supportare le **sql_variant** tipo di dati, il [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provider OLE DB Native Client espone un tipo di dati specifico del provider denominato DBTYPE_SQLVARIANT. Quando i dati **sql_variant** vengono recuperati come DBTYPE_SQLVARIANT, vengono archiviati in una struttura SSVARIANT specifica del provider. La struttura SSVARIANT contiene tutti i sottotipi che corrispondono ai sottotipi del tipo di dati **sql_variant**.  
  
 La proprietà di sessione SSPROP_ALLOWNATIVEVARIANT deve essere inoltre impostata su TRUE.  
  
## <a name="provider-specific-property-sspropallownativevariant"></a>Proprietà SSPROP_ALLOWNATIVEVARIANT specifica del provider  
 Durante il recupero dei dati è possibile specificare in modo esplicito il tipo di dati da restituire per una colonna o un parametro. È anche possibile servirsi di **IColumnsInfo** per ottenere le informazioni sulle colonne da usare per definire l'associazione. Quando **IColumnsInfo** viene usato a tale scopo, se la proprietà di sessione SSPROP_ALLOWNATIVEVARIANT è FALSE (valore predefinito), viene restituito DBTYPE_VARIANT per le colonne **sql_variant**. Se la proprietà SSPROP_ALLOWNATIVEVARIANT è FALSE, DBTYPE_SQLVARIANT non è supportato. Se la proprietà SSPROP_ALLOWNATIVEVARIANT è impostata su TRUE, il tipo di colonna viene restituito come DBTYPE_SQLVARIANT, nel qual caso il buffer conterrà la struttura SSVARIANT. Durante il recupero dei dati **sql_variant** come DBTYPE_SQLVARIANT la proprietà di sessione SSPROP_ALLOWNATIVEVARIANT deve essere impostata su TRUE.  
  
 La proprietà SSPROP_ALLOWNATIVEVARIANT fa parte del set di proprietà DBPROPSET_SQLSERVERSESSION specifico del provider ed è una proprietà di sessione.  
  
 La proprietà DBTYPE_VARIANT si applica a tutti gli altri provider OLE DB.  
  
## <a name="sspropallownativevariant"></a>SSPROP_ALLOWNATIVEVARIANT  
 La proprietà SSPROP_ALLOWNATIVEVARIANT è una proprietà di sessione e fa parte del set di proprietà DBPROPSET_SQLSERVERSESSION.  
  
|||  
|-|-|  
|SSPROP_ALLOWNATIVEVARIANT|Digitare:  VT_BOOL<br /><br /> L/S: Lettura/scrittura<br /><br /> Impostazione predefinita: VARIANT_FALSE<br /><br /> Descrizione: Determina se i dati recuperati come DBTYPE_VARIANT o DBTYPE_SQLVARIANT.<br /><br /> VARIANT_TRUE: Tipo di colonna viene restituito come DBTYPE_SQLVARIANT nel quale caso il buffer conserva la struttura SSVARIANT.<br /><br /> VARIANT_FALSE: Tipo di colonna viene restituito come DBTYPE_VARIANT e il buffer presenta la struttura VARIANT.|  
  
## <a name="see-also"></a>Vedere anche  
 [Tipi di dati &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
