---
title: SQL statico | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd82e2c3c44f05a27e9d14442d8d0fb58e1986cc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63232056"
---
# <a name="static-sql"></a>SQL statico
Embedded SQL illustrato nella [Embedded SQL riportato di seguito](../../odbc/reference/embedded-sql-example.md) è noto come SQL statico. SQL statico viene chiamato perché le istruzioni SQL nel programma sono statiche. vale a dire, essi non modificare ogni volta che viene eseguito il programma. Come descritto nella sezione precedente, queste istruzioni vengono compilate quando viene compilato il resto del programma.  
  
 SQL statico funziona bene in molte situazioni e può essere usato in qualsiasi applicazione per cui l'accesso ai dati può essere determinato in fase di progettazione di programma. Ad esempio, un programma di immissione dell'ordine Usa sempre la stessa istruzione per inserire un nuovo ordine e un sistema di prenotazione della compagnia aerea utilizza sempre la stessa istruzione per modificare lo stato di una postazione da disponibile a riservato. Ognuna di queste istruzioni potrebbe procedere alla generalizzazione tramite l'uso di variabili host. valori diversi possono essere inseriti in un ordine di vendita e che è possibile riservare posti diversi. Poiché tali istruzioni possono essere impostate come hardcoded nel programma, tali programmi hanno il vantaggio che le istruzioni devono essere analizzati, convalidati e ottimizzati solo una volta, in fase di compilazione. Questo codice relativamente veloce.
