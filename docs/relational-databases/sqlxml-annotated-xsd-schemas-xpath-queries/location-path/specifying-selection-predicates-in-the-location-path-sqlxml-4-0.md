---
title: Specifica di selezione predicati nel percorso (SQLXML 4.0) | Documenti Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
caps.latest.revision: "28"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b2b476304fddd169a253a3777bb1a0fb4d53087f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a>Definizione di predicati di selezione nel percorso (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Un predicato filtra un set di nodi rispetto a un asse (simile a una clausola WHERE in un'istruzione SELECT). Il predicato viene specificato tra parentesi. Per filtrare ogni nodo nel set di nodi, l'espressione del predicato viene valutata con il nodo come nodo di contesto e con il numero di nodi nel set di nodi come dimensioni del contesto. Se l'espressione del predicato restituisce TRUE per il nodo, il nodo viene incluso nel set di nodi risultante.  
  
 XPath consente inoltre l'applicazione di filtri basata sulla posizione. Un'espressione del predicato valutata in numero seleziona il nodo dell'ordinale. Il percorso `Customer[3]`, ad esempio, restituisce il terzo cliente. Predicati numerici di questo tipo non sono supportati. Sono supportate solo le espressioni del predicato che restituiscono un risultato booleano.  
  
> [!NOTE]  
>  Per informazioni sulle limitazioni di questa implementazione di XPath e le differenze tra i file e la specifica W3C, vedere [Introduzione alle query XPath che utilizzano &#40; SQLXML 4.0 &#41; ](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="selection-predicate-example-1"></a>Il predicato di selezione: Esempio 1  
 L'espressione XPath seguente (percorso) seleziona dal nodo di contesto corrente tutti i  **\<cliente >** gli elementi figlio che sono il **CustomerID** attributo con valore ALFKI:  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 In questa query XPath `child` e `attribute` sono nomi di asse. `Customer`è il test di nodo (TRUE se `Customer` è un  **\<nodo elemento >**perché  **\<elemento >** è il tipo di nodo principale per il `child` asse). `attribute::CustomerID="ALFKI"` è il predicato. Nel predicato, `attribute` è l'asse e `CustomerID` è il test di nodo (TRUE se **CustomerID** è un attributo del nodo di contesto, perché  **\<attributo >** è l'entità tipo di nodo di **attributo** asse).  
  
 Utilizzando la sintassi abbreviata, la query XPath può essere specificata anche nel modo seguente:  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a>Il predicato di selezione: Esempio 2  
 L'espressione XPath seguente (percorso) seleziona dal nodo di contesto corrente tutti i  **\<ordine >** nipoti che includono il **SalesOrderID** attributo con valore 1:  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 In questa espressione XPath `child` e `attribute` sono nomi di asse. `Customer`, `Order` e `SalesOrderID` sono i test di nodo. `attribute::OrderID="1"` è il predicato.  
  
 Utilizzando la sintassi abbreviata, la query XPath può essere specificata anche nel modo seguente:  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a>Il predicato di selezione: Esempio 3  
 L'espressione XPath seguente (percorso) seleziona dal nodo di contesto corrente tutti i  **\<cliente >** figli che includono uno o più  **\<ContactName >** elementi figlio:  
  
```  
child::Customer[child::ContactName]  
```  
  
 In questo esempio si presuppone che il  **\<ContactName >** è un elemento figlio del  **\<cliente >** elemento nel documento XML, che è considerato  *mapping incentrato* in uno schema XSD con annotazioni.  
  
 In questa espressione XPath `child` è il nome dell'asse. `Customer`è il test di nodo (TRUE se `Customer` è un  **\<elemento >** nodo perché  **\<elemento >** è il tipo di nodo principale per `child` asse). `child::ContactName` è il predicato. Nel predicato, `child` è l'asse e `ContactName` è il test di nodo (TRUE se `ContactName` è un  **\<elemento >** nodo).  
  
 Questa espressione restituisce solo il  **\<cliente >** gli elementi figlio del nodo di contesto che hanno  **\<ContactName >** gli elementi figlio.  
  
 Utilizzando la sintassi abbreviata, la query XPath può essere specificata anche nel modo seguente:  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a>Il predicato di selezione: Esempio 4  
 L'espressione XPath seguente seleziona  **\<cliente >** gli elementi figlio del nodo di contesto che non dispongono di  **\<ContactName >** gli elementi figlio:  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 In questo esempio si presuppone che  **\<ContactName >** è un elemento figlio del  **\<cliente >** nell'elemento del documento XML e il campo ContactName non è necessaria la database.  
  
 In questo esempio, `child` è l'asse. `Customer`è il test di nodo (TRUE se `Customer` è un \<elemento > nodo). `not(child::ContactName)` è il predicato. Nel predicato, `child` è l'asse e `ContactName` è il test di nodo (TRUE se `ContactName` è un \<elemento > nodo).  
  
 Utilizzando la sintassi abbreviata, la query XPath può essere specificata anche nel modo seguente:  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a>Il predicato di selezione: Esempio 5  
 L'espressione XPath seguente seleziona dal nodo di contesto corrente tutti i  **\<cliente >** figli che includono il **CustomerID** attributo:  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 In questo esempio, `child` è l'asse e `Customer` è test di nodo (TRUE se `Customer` è un \<elemento > nodo). `attribute::CustomerID` è il predicato. Nel predicato, `attribute` è l'asse e `CustomerID` è il predicato (TRUE se `CustomerID` è un  **\<attributo >** nodo).  
  
 Utilizzando la sintassi abbreviata, la query XPath può essere specificata anche nel modo seguente:  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a>Predicato di selezione: esempio 6  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 include il supporto per query XPath che contengono un prodotto incrociato nel predicato, come illustrato nell'esempio seguente:  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 La query seleziona tutti i clienti con un elemento `Order` per cui `OrderDate` è uguale a `ShipDate` di qualsiasi `Order`.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione a schemi XSD con annotazioni &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)   
 [Formattazione XML sul lato client &#40; SQLXML 4.0 &#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  