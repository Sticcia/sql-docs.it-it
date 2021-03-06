---
title: 'Passaggio 4b: Recuperare il conteggio delle righe | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3091d379bca6c061437e7767fdf6f99d69dc9861
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149146"
---
# <a name="step-4b-fetch-the-row-count"></a>Passaggio 4b: Recuperare il conteggio delle righe
Il passaggio successivo è recuperare il conteggio delle righe, come illustrato nella figura seguente.  
  
 ![Illustra il recupero del conteggio delle righe](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 Se l'istruzione eseguita nel passaggio 3 è un' **UPDATE**, **eliminare**, o **Inserisci** istruzione, l'applicazione recupera il conteggio delle righe interessate con  **SQLRowCount**. Per altre informazioni, vedere [che determina il numero di righe interessate](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md).  
  
 A questo punto, l'applicazione restituisce al passaggio 3 per l'esecuzione di un'altra istruzione nella stessa transazione o procede al passaggio 5 per eseguire il commit o rollback della transazione.
