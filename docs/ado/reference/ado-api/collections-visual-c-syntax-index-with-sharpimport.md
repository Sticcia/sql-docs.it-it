---
title: 'Raccolte (indice sintassi Visual C++ con #import) | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- 'syntax indexes [ADO], ADO for Visual C++ syntax with #import'
- 'collections [ADO], ADO for Visual C++ syntax with #import'
- 'ADO for Visual C++ syntax with #import [ADO]'
- '#import [ADO]'
ms.assetid: 36fbca8e-1884-44b5-806b-d15e30f42fe6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1fa18eeacad58195c42d03b12f03332c332b0a35
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63155219"
---
# <a name="collections-visual-c-syntax-index-with-import"></a>Raccolte (indice sintassi Visual C++ con #import)
È utile sapere che le raccolte ereditano alcuni metodi e proprietà comuni.  
  
 Ereditano tutte le raccolte il **conteggio** proprietà e **aggiornare** metodo e tutte le raccolte di aggiungono il **elemento** proprietà. Il **errori** raccolta aggiunge le **Clear** (metodo). Il **parametri** raccolta eredita le **Append** e **Elimina** metodi, mentre il **campi** raccolta aggiunge le **Append**, **eliminare**, e **Update** metodi.  
  
## <a name="properties-collection"></a>Raccolta delle proprietà  
  
### <a name="methods"></a>Metodi  
  
```  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="errors-collection"></a>Raccolta di errori  
  
### <a name="methods"></a>Metodi  
  
```  
HRESULT Clear( );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="parameters-collection"></a>Raccolta Parameters  
  
### <a name="methods"></a>Metodi  
  
```  
HRESULT Append( IDispatch * Object );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="fields-collection"></a>Raccolta Fields  
  
### <a name="methods"></a>Metodi  
  
```  
HRESULT Append( _bstr_t Name, enum DataTypeEnum Type, long DefinedSize, enum FieldAttributeEnum Attrib, const _variant_t & FieldValue = vtMissing );  
HRESULT Delete( const _variant_t & Index );  
HRESULT Refresh( );  
HRESULT Update( );  
```  
  
### <a name="properties"></a>Proprietà  
  
```  
long GetCount( ); __declspec(property(get=GetCount)) long Count;  
PropertyPtr GetItem( const _variant_t & Index ); __declspec(property(get=GetItem)) PropertyPtr Item[];  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Errors Collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [Fields Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Parameters Collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Raccolta delle proprietà (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
