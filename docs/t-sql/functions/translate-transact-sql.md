---
title: CONVERTIRE (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
caps.latest.revision: 5
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 583c414206a0acc79d1abdfff34728c38711a855
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="translate-transact-sql"></a>CONVERTIRE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Restituisce la stringa fornita come primo argomento, dopo alcuni caratteri specificati nel secondo argomento vengono convertite in un set di caratteri di destinazione.

## <a name="syntax"></a>Sintassi   
```
TRANSLATE ( inputString, characters, translations) 
```

## <a name="arguments"></a>Argomenti   

inputString   
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere (nvarchar, varchar, nchar, char).

caratteri   
È un [espressione](../../t-sql/language-elements/expressions-transact-sql.md) di qualsiasi tipo di carattere contenente caratteri che devono essere sostituiti.

traduzioni   
È un carattere [espressione](../../t-sql/language-elements/expressions-transact-sql.md) corrispondente secondo argomento di tipo e lunghezza.

## <a name="return-types"></a>Tipi restituiti   
Restituisce un'espressione di caratteri dello stesso tipo `inputString` in caratteri del secondo argomento vengono sostituiti con i caratteri corrispondenti dal terzo argomento.

## <a name="remarks"></a>Osservazioni   

`TRANSLATE`funzione restituirà un errore se i caratteri e le traduzioni hanno lunghezze diverse. `TRANSLATE`funzione deve restituire input subisce modifiche se i valori null vengono forniti come argomenti di sostituzione o di caratteri. Il comportamento del `TRANSLATE` funzione deve essere identica al [sostituire](../../t-sql/functions/replace-transact-sql.md) (funzione).   

Il comportamento del `TRANSLATE` funzione equivale a utilizzare più `REPLACE` funzioni.

`TRANSLATE`è sempre le regole di confronto SC specifico.

## <a name="examples"></a>Esempi   

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. Sostituire quadrate e parentesi graffe con parentesi graffe regolare    
La query seguente sostituisce quadrate e parentesi graffe nella stringa di input con parentesi:
```
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```
[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]
```
2*(3+4)/(7-2)
```

>  [!NOTE]
>  Il `TRANSLATE` funzione in questo esempio è equivalente a ma molto contratti rispetto all'utilizzo di istruzione seguenti `REPLACE`:`SELECT REPLACE(REPLACE(REPLACE(REPLACE('2*[3+4]/{7-2}','[','('), ']', ')'), '{', '('), '}', ')');` 


###  <a name="b-convert-geojson-points-into-wkt"></a>B. Convertire i punti GeoJSON WKT    
GeoJSON è un formato per la codifica di un'ampia gamma di strutture di dati geografici. Con il `TRANSLATE` (funzione), gli sviluppatori è possono convertire facilmente i punti GeoJSON in formato WKT e viceversa. La query seguente sostituisce quadrate e parentesi graffe nell'input con parentesi graffe regolari:   
```tsql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]   


|Punto  |Coordinate |  
---------|--------- |
(137.4  72.3) |[137.4,72.3] |


## <a name="see-also"></a>Vedere anche

[Funzioni stringa (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)   
[REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)   

