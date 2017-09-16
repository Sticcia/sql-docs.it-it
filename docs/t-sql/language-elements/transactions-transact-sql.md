---
title: Transazioni (Transact-SQL) | Documenti Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Transactions
- Transactions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- transactions [SQL Server]
- transactions [SQL Server], about transactions
- UOW [SQL Server]
- unit of work [SQL Server]
ms.assetid: 1485c375-921a-42af-a871-bb333cc08d3e
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 8660d0ac8d6205a94fdab24f41e41bac40a8671e
ms.contentlocale: it-it
ms.lasthandoff: 09/01/2017

---
# <a name="transactions-transact-sql"></a>Transazioni (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Una transazione corrisponde a una singola unità di lavoro. Se la transazione viene eseguita correttamente, viene eseguito il commit di tutte le modifiche dei dati apportate durante la transazione e tali modifiche diventano parte permanente del database. Se si verificano errori durante l'esecuzione della transazione ed è necessario annullarla o eseguirne il rollback, verranno cancellate tutte le modifiche dei dati.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supporta le modalità per le transazioni seguenti.  
  
 Transazioni con autocommit  
 Ogni istruzione corrisponde a una transazione.  
  
 Transazioni esplicite  
 Ogni transazione viene avviata in modo esplicito tramite l'istruzione BEGIN TRANSACTION e terminata con un'istruzione esplicita COMMIT o ROLLBACK.  
  
 Transazioni implicite  
 Una nuova transazione viene avviata in modo implicito al termine di una transazione precedente, ma tutte le transazioni vengono terminate in modo esplicito con un'istruzione COMMIT o ROLLBACK.  
  
 Transazioni definite a livello di ambito di batch  
 Applicabile solo a MARS (Multiple Active Result Set). Una transazione definita a livello di ambito di batch è una transazione [!INCLUDE[tsql](../../includes/tsql-md.md)] esplicita o implicita che inizia in una sessione MARS. Se per una transazione definita a livello di ambito di batch non è stato eseguito il commit o il rollback quando il batch è completato, il rollback viene eseguito automaticamente da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>Argomenti della sezione  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sono disponibili le seguenti istruzioni Transaction.  
  
|||  
|-|-|  
|[INIZIO DELLA TRANSAZIONE DISTRIBUITA](../../t-sql/language-elements/begin-distributed-transaction-transact-sql.md)|[ROLLBACK DELLA TRANSAZIONE](../../t-sql/language-elements/rollback-transaction-transact-sql.md)|  
|[INIZIO DELLA TRANSAZIONE](../../t-sql/language-elements/begin-transaction-transact-sql.md)|[ROLLBACK WORK](../../t-sql/language-elements/rollback-work-transact-sql.md)|  
|[ESEGUIRE IL COMMIT DELLE TRANSAZIONI](../../t-sql/language-elements/commit-transaction-transact-sql.md)|[SALVATAGGIO DELLE TRANSAZIONI](../../t-sql/language-elements/save-transaction-transact-sql.md)|  
|[ESEGUIRE IL COMMIT DI LAVORO](../../t-sql/language-elements/commit-work-transact-sql.md)||  
  
## <a name="see-also"></a>Vedere anche  
 [SET IMPLICIT_TRANSACTIONS &#40; Transact-SQL &#41;](../../t-sql/statements/set-implicit-transactions-transact-sql.md)   
 [@@TRANCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/trancount-transact-sql.md)  
  
  