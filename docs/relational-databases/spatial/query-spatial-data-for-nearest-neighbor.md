---
title: Query dei dati spaziali per Nearest Neighbor | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-spatial
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7af4ad5d-484e-45b4-aa16-83c33b358bb6
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8cac116f89d0cf1fde83a00dfd42c02e1fc5e2f0
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# Query dei dati spaziali per Nearest Neighbor
<a id="query-spatial-data-for-nearest-neighbor" class="xliff"></a>
  La query Nearest Neighbor è una query comune utilizzata con dati spaziali. Le query Nearest Neighbor vengono utilizzate per trovare gli oggetti spaziali più vicini a un oggetto spaziale specifico. Un localizzatore di archivio per un sito Web, ad esempio, deve spesso trovare i percorsi di archivio più vicini alla posizione di un cliente.  
  
 Una query Nearest Neighbor può essere scritta in una varietà di formati di query validi, ma per l'utilizzo di un indice spaziale è necessario utilizzare la sintassi seguente.  
  
## Sintassi
<a id="syntax" class="xliff"></a>  
  
```  
SELECT TOP ( number )  
        [ WITH TIES ]  
        [ * | expression ]   
        [, ...]  
    FROM spatial_table_reference, ...   
        [ WITH   
            (   
                [ INDEX ( index_ref ) ]   
                [ , SPATIAL_WINDOW_MAX_CELLS = <value>]   
                [ ,... ]   
            )   
        ]  
    WHERE   
        column_ref.STDistance ( @spatial_ object )   
            {   
                [ IS NOT NULL ] | [ < const ] | [ > const ]   
                | [ <= const ] | [ >= const ] | [ <> const ] ]   
            }  
            [ AND { other_predicate } ]   
    }  
    ORDER BY column_ref.STDistance ( @spatial_ object ) [ ,...n ]  
[ ; ]  
  
```  
  
## Query Nearest Neighbor e indici spaziali
<a id="nearest-neighbor-query-and-spatial-indexes" class="xliff"></a>  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]vengono usate le clausole **TOP** e **ORDER BY** per eseguire una query Nearest Neighbor nelle colonne di dati spaziali. La clausola **ORDER BY** contiene una chiamata al metodo `STDistance()` per il tipo di dati della colonna spaziale. La clausola **TOP** indica il numero di oggetti da restituire per la query.  
  
 Per utilizzare un indice spaziale in una query Nearest Neighbor, è necessario soddisfare i requisiti seguenti:  
  
1.  In una delle colonne spaziali deve essere presente un indice spaziale e tale colonna deve essere usata dal metodo `STDistance()` nelle clausole **WHERE** e **ORDER BY** .  
  
2.  La clausola **TOP** non può contenere un'istruzione **PERCENT** .  
  
3.  La clausola **WHERE** deve contenere un metodo `STDistance()` .  
  
4.  Se nella clausola **WHERE** sono presenti più predicati, il predicato che contiene il metodo `STDistance()` deve essere connesso con una congiunzione **AND** ad altri predicati. Il metodo `STDistance()` non può trovarsi in una parte facoltativa della clausola **WHERE** .  
  
5.  La prima espressione nella clausola **ORDER BY** deve usare il metodo `STDistance()` .  
  
6.  L'ordinamento per la prima espressione `STDistance()` nella clausola **ORDER BY** deve essere **ASC**.  
  
7.  Devono essere filtrate tutte le righe per le quali `STDistance` restituisce **NULL** .  
  
> [!WARNING]  
>  I metodi che accettano tipi di dati **geography** o **geometry** come argomenti restituiranno **NULL** se gli identificatori SRID non sono gli stessi per i tipi.  
  
 Per gli indici utilizzati nelle query Nearest Neighbor è consigliabile utilizzare i nuovi schemi a mosaico di indice spaziale. Per altre informazioni sugli schemi a mosaico di indice spaziale, vedere [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md).  
  
## Esempio
<a id="example" class="xliff"></a>  
 Nell'esempio di codice seguente viene illustrata una query Nearest Neighbor nella quale può essere utilizzato un indice spaziale. Nell'esempio viene utilizzata la tabella `Person.Address` del database `AdventureWorks2012` .  
  
```tsql  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
WHERE SpatialLocation.STDistance(@g) IS NOT NULL  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 Creare un indice spaziale nella colonna SpatialLocation per vedere in che modo viene utilizzato un indice spaziale in una query Nearest Neighbor. Per ulteriori informazioni sulla creazione di indici spaziali, vedere [Create, Modify, and Drop Spatial Indexes](../../relational-databases/spatial/create-modify-and-drop-spatial-indexes.md).  
  
## Esempio
<a id="example" class="xliff"></a>  
 Nell'esempio di codice seguente viene illustrata una query Nearest Neighbor nella quale non può essere utilizzato un indice spaziale.  
  
```tsql  
USE AdventureWorks2012  
GO  
DECLARE @g geography = 'POINT(-121.626 47.8315)';  
SELECT TOP(7) SpatialLocation.ToString(), City FROM Person.Address  
ORDER BY SpatialLocation.STDistance(@g);  
  
```  
  
 Nella query manca una clausola **WHERE** che usa `STDistance()` in un formato specificato nella sezione relativa alla sintassi, quindi la query non può usare un indice spaziale.  
  
## Vedere anche
<a id="see-also" class="xliff"></a>  
 [Dati spaziali &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
