---
title: Cache della libreria di cursori | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95a8e01b42f8bdc2036457b5c8a9e0e4088c16fa
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241041"
---
# <a name="cursor-library-cache"></a>Cache della libreria di cursori
> [!IMPORTANT]  
>  Questa funzionalità verrà rimossa in una versione futura di Windows. Evitare di utilizzarla nelle nuove attività di sviluppo e pianificare la modifica delle applicazioni che utilizzano attualmente questa funzionalità. Microsoft consiglia di usare le funzionalità del driver del cursore.  
  
 Per ogni riga di dati nel set di risultati, la libreria di cursori memorizza nella cache i dati per ogni colonna associata, la lunghezza dei dati in ogni colonna associata e lo stato della riga. La libreria di cursori utilizza i valori nella cache sia restituita attraverso **SQLFetch** e **SQLFetchScroll** e per costruire istruzioni ricercate per operazioni posizionate. Per altre informazioni, vedere [costruzione di istruzioni di eseguire la ricerca](../../../odbc/reference/appendixes/constructing-searched-statements.md).  
  
 In questa sezione vengono trattati gli argomenti seguenti.  
  
-   [Dati della colonna](../../../odbc/reference/appendixes/column-data.md)  
  
-   [Lunghezza dei dati colonna](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [Stato riga](../../../odbc/reference/appendixes/row-status.md)  
  
-   [Percorso della cache](../../../odbc/reference/appendixes/location-of-cache.md)
