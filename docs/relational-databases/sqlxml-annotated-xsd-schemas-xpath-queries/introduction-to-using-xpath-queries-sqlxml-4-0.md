---
title: Introduzione all'utilizzo di query XPath (SQLXML 4.0) | Documenti Microsoft
ms.custom: 
ms.date: 03/17/2017
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
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
caps.latest.revision: "29"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9113df3519ab212f3647b96c63620167c7913ffb
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2017
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a>Introduzione all'utilizzo di query XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Una query XML Path Language (XPath) può essere specificata come parte di un URL o all'interno di un modello. La struttura del frammento risultante viene determinata dallo schema di mapping mentre i valori vengono recuperati dal database. Questo processo è concettualmente simile alla creazione di viste mediante l'istruzione CREATE VIEW e alla scrittura di query SQL relative a tali viste.  
  
> [!NOTE]  
>  Per comprendere le query XPath in SQLXML 4.0, è necessario avere familiarità con le viste XML e con concetti correlati quali i modelli e lo schema di mapping. Per ulteriori informazioni, vedere [Introduzione a schemi XSD con annotazioni &#40; SQLXML 4.0 &#41; ](../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)e lo standard XPath definito per il World Wide Web Consortium (W3C).  
  
 Un documento XML è costituito da nodi, quali un nodo di elemento, un nodo di attributo, un nodo di testo e così via. Si consideri, ad esempio, il documento XML seguente:  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 In questo documento,  **\<cliente >** è un nodo element, **cid** è un nodo di attributo e **"Importante"** è un nodo di testo.  
  
 XPath è un linguaggio di navigazione grafica utilizzato per selezionare un set di nodi da un documento XML. Ogni operatore XPath consente di selezionare un set di nodi in base a un set di nodi selezionato da un operatore XPath precedente. Ad esempio, dato un set di  **\<cliente >** consente di selezionare tutti i nodi, XPath  **\<ordine >** nodi con il **data** valore di dell'attributo**"7/14/1999"**. Il set di nodi risultante contiene tutti gli ordini con data 7/14/1999.  
  
 Il linguaggio XPath è definito dal World Wide Web Consortium (W3C) come linguaggio di navigazione standard. SQLXML 4.0 implementa un subset della specifica XPath del W3C, disponibile all'indirizzo xpath-http://www.w3.org/TR/1999/PR-19991008.html.  
  
 Di seguito vengono elencate alcune delle differenze principali tra l'implementazione di XPath del W3C e l'implementazione di SQLXML 4.0.  
  
-   **Query di livello principale**  
  
     SQLXML 4.0 non supporta la query radice (/). Ogni query XPath deve iniziare con un livello superiore  **\<ElementType >** nello schema.  
  
-   **La segnalazione degli errori**  
  
     La specifica XPath del W3C non definisce condizioni di errore. Le query XPath che non consentono di selezionare nodi restituiscono un set di nodi vuoto. In SQLXML 4.0 una query può restituire diversi tipi di messaggio di errore.  
  
-   **Ordine del documento**  
  
     In SQLXML 4.0 l'ordine dei documenti non è sempre definito. Pertanto e i predicati numerici assi tale ordine del documento utilizzare (ad esempio **seguenti**) non sono implementate.  
  
     La mancanza di un ordine dei documenti indica inoltre che il valore di stringa di un nodo può essere valutato solo se il nodo in questione è mappato a una singola colonna in una singola riga. Non è possibile convertire in stringa un elemento con elementi figlio o un nodo IDREFS o NMTOKENS.  
  
    > [!NOTE]  
    >  In alcuni casi, il **i campi chiave** annotazione o le chiavi di **relazione** annotazione può comportare un ordine deterministico dei documenti. Tuttavia, non l'utilizzo principale di queste annotazioni per ulteriori informazioni, vedere [identificazione di colonne chiave mediante SQL: Key-campi &#40; SQLXML 4.0 &#41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) e [specificando le relazioni tramite SQL: Relationship &#40; SQLXML 4.0 &#41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).  
  
-   **Tipi di dati**  
  
     SQLXML 4.0 presenta limitazioni nell'implementazione di XPath **stringa**, **numero**, e **booleano** tipi di dati. Per ulteriori informazioni, vedere [tipi di dati XPath &#40; SQLXML 4.0 &#41; ](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md).  
  
-   **Query di prodotto incrociato**  
  
     SQLXML 4.0 non supporta query XPath di prodotto incrociato, quale `Customers[Order/@OrderDate=Order/@ShipDate]`. In questa query vengono selezionati tutti gli elementi Customer con un elemento Order per il quale OrderDate è uguale a ShipDate di un elemento Order qualsiasi.  
  
     SQLXML 4.0 non supporta invece query come `Customer[Order[@OrderDate=@ShippedDate]]`, in cui vengono selezionati gli elementi Customer con elemento Order per il quale OrderDate è uguale al relativo elemento ShipDate.  
  
-   **Sicurezza e gestione degli errori**  
  
     A seconda dello schema e dell'espressione di query XPath utilizzati, è possibile che gli errori [!INCLUDE[tsql](../../includes/tsql-md.md)] vengano esposti agli utenti in determinate condizioni.  
  
 Nelle tabelle delle sezioni seguenti vengono forniti dettagli su come l'implementazione nelle aree indicate delle query XPath in SQLXML 4.0 sia diversa da quella definita nella specifica del W3C.  
  
## <a name="supported-functionality"></a>Funzionalità supportata  
 Nella tabella seguente vengono mostrate le caratteristiche del linguaggio XPath implementate in SQLXML 4.0.  
  
|Funzionalità|Elemento|Collegamento a query di esempio|  
|-------------|----------|----------------------------|  
|Assi|**attributo**, **figlio**, **padre**, e **self** assi|[Specificare gli assi nelle query XPath &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|Predicati con valori booleani, tra i quali sono inclusi predicati successivi e nidificati||[Specifica di operatori aritmetici in query XPath &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Tutti gli operatori relazionali|=, !=, <, \<=, >, >=|[Specifica di operatori relazionali nelle query XPath &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Operatori aritmetici|+, -, *, div|[Specifica di operatori aritmetici in query XPath &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Funzioni di conversione esplicita|**Number ()**, **String ()**, **Boolean)**|[Specifica di funzioni di conversione esplicita in query XPath &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|operatori booleani|AND, OR|[Specifica di operatori booleani in query XPath &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|funzioni booleane|**true ()**, **false ()**, **NOT)**|[Specifica di funzioni booleane in query XPath &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|variabili XPath||[Definizione di variabili XPath in query XPath &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a>Funzionalità non supportata  
 Nella tabella seguente vengono mostrate le caratteristiche del linguaggio XPath non implementate in SQLXML 4.0.  
  
|Funzionalità|Elemento|  
|-------------|----------|  
|Assi|**predecessore**, **ancestor-or-self**, **discendenti**, **descendant-or-self (/ /)**, **seguente**, **successivi**, **dello spazio dei nomi**, **precedente**, **precedente nodi di pari livello**|  
|Predicati con valori numerici||  
|Operatori aritmetici|mod|  
|Funzioni nodo|**predecessore**, **ancestor-or-self**, **discendenti**, **descendant-or-self (/ /)**, **seguente**, **successivi**, **dello spazio dei nomi**, **precedente**, **precedente nodi di pari livello**|  
|Funzioni per i valori stringa|**String ()**, **Concat ()**, **starts-with**, **Contains ()**, **substring-before()**,  **substring-after()**, **substring**, **string-length()**, **normalize()**, **Translate)**|  
|funzioni booleane|**lang)**|  
|Funzioni numeriche|**SUM ()**, **floor ()**, **Ceiling ()**, **Round)**|  
|Operatore Union|&#124;|  
  
 Quando si specificano query XPath in un modello, si noti il comportamento seguente:  
  
-   XPath può contenere caratteri come < o & che presentano significati speciali in XML (e il modello è un documento XML). Evitare tali caratteri utilizzando la codifica XML oppure specificare XPath nell'URL.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di query XPath in SQLXML 4.0](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/using-xpath-queries-in-sqlxml-4-0.md)  
  
  