---
title: STGeometryN (tipo di dati geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeometryN (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STGeometryN method
ms.assetid: 53755f69-cd50-475b-b3b8-a1a9157cf03a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 19c11e02f561919767cc9eb67b68cc863442ceb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628989"
---
# <a name="stgeometryn-geography-data-type"></a>STGeometryN (tipo di dati geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Restituisce un elemento **geography** specificato in un tipo **GeometryCollection** o in uno dei sottotipi. Quando STGeometryN() viene usato su un sottotipo di **GeometryCollection**, ad esempio **MultiPoint** o **MultiLineString**, questo metodo restituisce l'istanza **geography** se chiamato con N = 1.  
  
## <a name="syntax"></a>Sintassi  
  
```  
  
.STGeometryN ( expression )  
```  
  
## <a name="arguments"></a>Argomenti  
 *expression*  
 Espressione **int** compresa tra 1 e il numero di istanze **geography** in **GeometryCollection**.  
  
## <a name="return-types"></a>Tipi restituiti  
 Tipo [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restituito: **geography**  
  
 Tipo CLR restituito: **SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 Questo metodo restituisce Null se il parametro è maggiore del risultato di [STNumGeometries()](../../t-sql/spatial-geography/stnumgeometries-geography-data-type.md) e genererà un'eccezione **ArgumentOutOfRangeException** se il parametro *expression* è minore di 1.  
  
## <a name="examples"></a>Esempi  
 Nell'esempio seguente viene creata un'istanza `MultiPoint``geography` e viene usato `STGeometryN()` per trovare la seconda istanza `geography` del tipo **GeometryCollection**.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('MULTIPOINT(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STGeometryN(2).ToString();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Metodi OGC sulle istanze geografiche](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
