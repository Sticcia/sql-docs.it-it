---
title: Gestione degli aggiornamenti non riusciti | Documenti Microsoft
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updates [ADO], dealing with failed updates
ms.assetid: 299c37bd-19ff-4261-8571-b9665687e075
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dc8facd3f93f0c752739c20d61352d8c4ab2f63f
ms.contentlocale: it-it
ms.lasthandoff: 09/09/2017

---
# <a name="dealing-with-failed-updates"></a>Gestione degli aggiornamenti non riusciti
Quando un aggiornamento si conclude con errori, come si risolve gli errori dipende la natura e il livello di gravità degli errori e la logica dell'applicazione. Tuttavia, se il database è condiviso con altri utenti, è un tipico errore che un altro utente modifica il campo prima di procedere. Questo tipo di errore viene chiamato un conflitto. ADO rileva questa condizione e segnala un errore.  
  
## <a name="remarks"></a>Osservazioni  
 Se sono presenti errori di aggiornamento, questi verranno intercettati in una routine di gestione degli errori. Filtrare il Recordset con la costante adFilterConflictingRecords in modo che solo le righe in conflitto sono visibili. In questo esempio, la strategia di risoluzione degli errori è semplicemente per stampare l'autore nomi e cognomi (au_fname e au_lname).  
  
 Il codice per avvisare l'utente per il conflitto di aggiornamento è simile al seguente:  
  
```  
objRs.Filter = adFilterConflictingRecords  
objRs.MoveFirst  
Do While Not objRst.EOF  
   Debug.Print "Conflict: Name =  "; objRs!au_fname; " "; objRs!au_lname  
   objRs.MoveNext  
Loop  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Modalità batch](../../../ado/guide/data/batch-mode.md)