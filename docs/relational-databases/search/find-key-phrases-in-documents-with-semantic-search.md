---
title: Trovare frasi chiave nei documenti tramite la ricerca semantica | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6c005c3de0b3cd1e8e5562c038321a53e04da38a
ms.contentlocale: it-it
ms.lasthandoff: 06/22/2017

---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a>Trovare frasi chiave nei documenti mediante ricerca semantica
  Viene descritto come individuare le frasi chiave nei documenti o nelle colonne di testo configurati per l'indicizzazione semantica statistica.  

##  <a name="howtofind"></a> Individuare le frasi chiave nei documenti con SEMANTICKEYPHRASETABLE  
 Per identificare le frasi chiave in documenti specifici o identificare documenti che contengono frasi chiave specifiche, eseguire una query sulla funzione [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
 SEMANTICKEYPHRASETABLE restituisce una tabella con zero, una o più righe per le frasi chiave associate alle colonne nella tabella specificata. A questa funzione per i set di righe è possibile fare riferimento nella clausola FROM di un'istruzione SELECT come se fosse un normale nome di tabella.  
  
> [!NOTE]  
>  In questa versione solo singole parole vengono indicizzate per la ricerca semantica. Le frasi composte da più parole (n-grammi) non vengono indicizzate. Inoltre, varie forme della stessa parola vengono indicizzate separatamente; ad esempio "calcolo" e "calcoli" vengono indicizzati separatamente.  
  
 Per informazioni dettagliate sui parametri necessari per la funzione SEMANTICKEYPHRASETABLE e sulla tabella dei risultati restituita, vedere [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md).  
  
> [!IMPORTANT]  
>  Per le colonne di destinazione deve essere abilitata l'indicizzazione full-text e semantica.  
  
###  <a name="HowToTopPhrases"></a> Esempio 1: trovare le principali frasi chiave in un documento specifico  
 L'esempio seguente recupera le prime 10 frasi chiave dal documento specificato tramite la variabile @DocumentId nella colonna Document della tabella Production.Document del database di esempio AdventureWorks. La variabile @DocumentId rappresenta un valore della colonna chiave dell'indice full-text.  
  
```tsql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 La funzione **SEMANTICKEYPHRASETABLE** recupera in modo efficiente questi risultati tramite una ricerca nell'indice anziché un'analisi della tabella.  
  
###  <a name="HowToTopDocuments"></a> Esempio 2: trovare i documenti principali che contengono una frase chiave specifica  
 Nell'esempio seguente vengono recuperati i primi 25 documenti che contengono la frase chiave "supporto" dalla colonna Documento della tabella Production.Document del database di esempio AdventureWorks.  
  
```tsql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  