---
title: Supporto dei tipi di parametri con valori di tabella OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 27ae90e05784c18d85f84daa9955818d3133ad07
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63046505"
---
# <a name="ole-db-table-valued-parameter-type-support"></a>Supporto del tipo di parametro con valori di tabella OLE DB
  In questo argomento viene descritto il supporto del tipo OLE DB per i parametri con valori di tabella.  
  
## <a name="table-valued-parameter-rowset-object"></a>Oggetto set di righe di parametri con valori di tabella  
 È possibile creare un oggetto set di righe specifico per i parametri con valori di tabella. Si crea l'oggetto set di righe di parametri con valori di tabella usando ITableDefinitionWithConstraints::CreateTableWithConstraints o IOpenRowset:: OPENROWSET. A questo scopo, impostare il membro *eKind* del parametro *pTableID* su DBKIND_GUID_NAME e specificare CLSID_ROWSET_INMEMORY come membro *guid*. Il nome del tipo di server per il parametro con valori di tabella deve essere specificato nel *pwszName* appartenente *pTableID* quando si usa IOpenRowset:: OPENROWSET. L'oggetto set di righe di parametri con valori di tabella si comporta come un normale oggetto del provider OLE DB di SQL Server Native Client.  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtypetable"></a>DBTYPE_TABLE  
 Un nuovo tipo, DBTYPE_TABLE, rappresenta un tipo di tabella. Tale tipo specifica i parametri con valori di tabella nelle varie interfacce OLE DB in cui è richiesto un oggetto DBTYPE.  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 Il formato di DBTYPE_TABLE è identico a quello di DBTYPE_IUNKNOWN. Si tratta di un puntatore a un oggetto nel buffer di dati. Per una specifica completa nelle associazioni, il consumer inserisce dati nel buffer DBOBJECT, con *iid* impostato su una delle interfacce dell'oggetto set di righe (IID_IRowset). Se non viene specificato alcun oggetto DBOBJECT nelle associazioni, si presuppone che l'oggetto sia IID_IRowset.  
  
 Le conversioni da e verso DBTYPE_TABLE per altri tipi non sono supportate. IConvertType::CanConvert restituisce S_FALSE per la conversione non supportata per tutte le richieste diverse dalla conversione da DBTYPE_TABLE a DBTYPE_TABLE. In questa situazione si presuppone l'uso di DBCONVERTFLAGS_PARAMETER sull'oggetto Command.  
  
## <a name="methods"></a>Metodi  
 Per informazioni sui metodi OLE DB che supportano i parametri con valori di tabella, vedere [tipo di parametro OLE DB Table-Valued supporta &#40;metodi&#41;](ole-db-table-valued-parameter-type-support-methods.md).  
  
## <a name="properties"></a>Proprietà  
 Per informazioni sulle proprietà OLE DB che supportano i parametri con valori di tabella, vedere [tipo di parametro OLE DB Table-Valued supporta &#40;proprietà&#41;](ole-db-table-valued-parameter-type-support-properties.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri con valori di tabella &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)   
 [Usare parametri con valori di tabella &#40;OLE DB&#41;](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
