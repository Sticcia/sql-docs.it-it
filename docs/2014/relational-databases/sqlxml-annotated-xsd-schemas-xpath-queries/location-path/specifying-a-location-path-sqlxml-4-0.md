---
title: Specificare un percorso (SQLXML 4.0) | Documenti di Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- absolute location path
- node-set [SQLXML]
- XPath queries [SQLXML], location paths
- relative location path [SQLXML]
- location path for XPath query
ms.assetid: a23a2b75-bc69-49f0-99db-05e14dc15bc0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c814d1b486a7ba7736cf19119a66ab0845d33c6b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127585"
---
# <a name="specifying-a-location-path-sqlxml-40"></a>Definizione di un percorso (SQLXML 4.0)
  Le query XPath vengono specificate sotto forma di espressione. Sono disponibili diversi tipi di espressioni. Un percorso è un'espressione che seleziona un set di nodi relativo al nodo di contesto. Il risultato della valutazione di un percorso è un set di nodi.  
  
## <a name="types-of-location-paths"></a>Tipi di percorsi  
 È possibile definire un percorso in una delle forme seguenti:  
  
-   **Percorso assoluto**  
  
     Un percorso assoluto inizia in corrispondenza del nodo radice del documento ed è costituito da una barra (/), eventualmente seguita da un percorso relativo. La barra (/) seleziona il nodo radice del documento.  
  
-   **Percorso relativo**  
  
     Un percorso relativo inizia in corrispondenza del nodo di contesto nel documento. Un percorso è costituito da una sequenza di uno o più passi separati da una barra (/). Ogni passo seleziona un set di nodi relativi al nodo di contesto. La sequenza iniziale dei passi seleziona un set di nodi relativi a un nodo di contesto. Ogni nodo nel set viene utilizzato come nodo di contesto per il passo successivo. I set di nodi identificati dal passo vengono uniti in join. Ad esempio, **child:: Order/child::** consente di selezionare la  **\<OrderDetail >** figlio dell'elemento il  **\<ordine >** elemento elementi figlio del nodo di contesto.  
  
    > [!NOTE]  
    >  Nell'implementazione SQLXML 4.0 di XPath, ogni query XPath inizia in corrispondenza del contesto radice, anche se XPath non è assoluto in modo esplicito. Una query XPath che inizia con "Customer", ad esempio, viene considerata come "/Customer". Nella query XPath **Customer [Order]**, Customer inizia in corrispondenza del contesto radice, ma Order inizia in corrispondenza del contesto di Customer. Per altre informazioni, vedere [Introduzione alle query XPath utilizzando &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="location-steps"></a>Passi  
 Un percorso (assoluto o relativo) è costituito da passi che contengono tre parti:  
  
-   **Axis**  
  
     L'asse specifica la relazione all'interno dell'albero tra i nodi selezionati dal passo e dal nodo di contesto. Sono supportati gli assi `parent`, `child`, `attribute` e `self`. Se nel percorso viene specificato un asse `child`, tutti i nodi selezionati dalla query sono figli del nodo di contesto. Se viene specificato un asse `parent`, il nodo selezionato è il nodo padre del nodo di contesto. Se viene specificato un asse `attribute`, i nodi selezionati sono gli attributi del nodo di contesto.  
  
-   **test di nodo**  
  
     Un test di nodo specifica il tipo di nodo selezionato dal passo. Ogni asse, `child`, `parent`, `attribute` e `self`, è associato a un tipo di nodo principale. Per il `attribute` asse, il tipo di nodo principale viene  **\<attributo >**. Per il `parent`, `child`, e `self` assi, il tipo di nodo principale viene  **\<elemento >**.  
  
     Ad esempio, se il percorso specifica **child:: Customer**, il  **\<cliente >** sono selezionati gli elementi figlio del nodo di contesto. Poiché il `child` asse ha  **\<elemento >** come tipo di nodo principale, il test di nodo Customer è TRUE se Customer è un  **\<elemento >** nodo.  
  
-   **Predicati di selezione (zero o più)**  
  
     Un predicato filtra un set di nodi rispetto a un asse. La definizione di predicati di selezione in un'espressione XPath è un'operazione simile alla definizione di una clausola WHERE in un'istruzione SELECT. Il predicato viene specificato tra parentesi. L'applicazione del test specificato nei predicati di selezione filtra i nodi restituiti dal test di nodo. Per filtrare ogni nodo nel set di nodi, l'espressione del predicato viene valutata con il nodo come nodo di contesto e con il numero di nodi nel set di nodi come dimensioni del contesto. Se l'espressione del predicato restituisce TRUE per il nodo, il nodo viene incluso nel set di nodi risultante.  
  
     La sintassi per un passo è costituita dal nome dell'asse e dal test di nodo separati da due caratteri due punti (::), seguiti da zero o più espressioni, ciascuna tra parentesi quadre. Ad esempio, l'espressione XPath (percorso) **child:: Customer [@CustomerID= 'ALFKI']** Seleziona tutti i  **\<cliente >** gli elementi figlio del nodo di contesto. Quindi il test nel predicato viene applicato al set di nodi, che restituisce solo le  **\<cliente >** nodi elemento con attributo valore 'ALFKI' per la relativa **CustomerID** attributo.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Specifica di un asse &#40;SQLXML 4.0&#41;](specifying-an-axis-sqlxml-4-0.md)  
 Vengono forniti esempi di definizione di un asse.  
  
 [Specifica di un Test di nodo nel percorso &#40;SQLXML 4.0&#41;](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 Vengono forniti esempi di definizione di un test di nodo.  
  
 [Specificando selezione predicati nel percorso &#40;SQLXML 4.0&#41;](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 Vengono forniti esempi di definizione di predicati di selezione.  
  
  
